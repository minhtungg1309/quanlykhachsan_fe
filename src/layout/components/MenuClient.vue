<template>

    <div class="card mt-1 shadow-sm">
        <nav class="navbar navbar-expand-lg navbar-light bg-light rounded">
            <div class="container-fluid">
                <button class="navbar-toggler" type="button" data-bs-toggle="collapse"
                    data-bs-target="#navbarSupportedContent2" aria-controls="navbarSupportedContent2"
                    aria-expanded="false" aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarSupportedContent2">
                    <!-- Căn giữa các nav-item -->
                    <ul class="navbar-nav mx-auto mb-2 mb-lg-0 justify-content-center">
                        <!-- Home -->
                        <li class="nav-item me-3">
                            <router-link to="/" class="nav-link active nav-hover" aria-current="page">
                                Home
                            </router-link>
                        </li>
                        <!-- Đặt Phòng -->
                        <li class="nav-item me-3">
                            <router-link to="/dat-phong" class="nav-link nav-hover">
                                Đặt Phòng
                            </router-link>
                        </li>
                        <!-- Loại Phòng -->
                        <li class="nav-item me-3">
                            <router-link to="/tim-loai-phong" class="nav-link nav-hover">
                                Loại Phòng
                            </router-link>
                        </li>
                        <!-- Phòng -->
                        <li class="nav-item me-3">
                            <router-link to="/danh-sach-phong" class="nav-link nav-hover">
                                Phòng
                            </router-link>
                        </li>
                        <!-- Dropdown -->
                        <li class="nav-item dropdown me-3">
                            <a class="nav-link dropdown-toggle nav-hover" href="#" role="button"
                                data-bs-toggle="dropdown" aria-expanded="false">
                                Bài Viết
                            </a>
                            <ul class="dropdown-menu">
                                <template v-for="(v, k) in ds_chuyen_muc" :key="k">
                                    <router-link :to="'/bai-viet/' + v.slug_chuyen_muc" class="dropdown-item">
                                        {{ v.ten_chuyen_muc }}
                                    </router-link>
                                </template>
                            </ul>
                        </li>
                    </ul>


                    <!-- Login/Register -->
                    <template v-if="!is_check">
                        <form class="d-flex">
                            <router-link to="/khach-hang/dang-nhap">
                                <button class="btn btn-primary me-2" type="button">
                                    Đăng Nhập
                                </button>
                            </router-link>
                            <router-link to="/khach-hang/dang-ky">
                                <button class="btn btn-outline-primary" type="button">
                                    Đăng Ký
                                </button>
                            </router-link>
                        </form>
                    </template>

                    <!-- User Dropdown -->
                    <template v-else>
                        <div class="user-box dropdown">
                            <a class="d-flex align-items-center nav-link dropdown-toggle" href="#" role="button"
                                data-bs-toggle="dropdown" aria-expanded="false">
                                <img src="https://t3.ftcdn.net/jpg/05/53/79/60/360_F_553796090_XHrE6R9jwmBJUMo9HKl41hyHJ5gqt9oz.jpg"
                                    class="user-img rounded-circle" alt="user avatar" width="40" height="40">
                                <div class="user-info ps-2">
                                    <p class="user-name mb-0"><b>{{ ten_hien_thi }}</b></p>
                                    <p class="designation mb-0 text-dark">Khách Hàng</p>
                                </div>
                            </a>
                            <ul class="dropdown-menu dropdown-menu-end">
                                <li>
                                    <router-link to="/khach-hang/hoa-don" class="dropdown-item">
                                        <span>Hóa Đơn Đặt Phòng</span>
                                    </router-link>
                                </li>
                                <li><a v-on:click="dangXuat()" class="dropdown-item">
                                        <span>Đăng Xuất</span>
                                    </a>
                                </li>
                                <li><a v-on:click="dangXuatAll()" class="dropdown-item"><span>Đăng Xuất Tất
                                            Cả</span></a>
                                </li>
                            </ul>
                        </div>
                    </template>
                </div>
            </div>
        </nav>
    </div>


</template>
<script>
import axios from 'axios';
import { createToaster } from "@meforma/vue-toaster";
const toaster = createToaster({ position: "top-right" });
export default {
    data() {
        return {
            ten_hien_thi: 'Chưa đăng nhập',
            is_check: false,
            ds_chuyen_muc: [],
        }
    },
    mounted() {
        this.checkLogin();
        this.layDuLieuChuyenMuc();
    },
    methods: {
        checkLogin() {
            axios
                .get('http://127.0.0.1:8000/api/kiem-tra-token-khach-hang', {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("token_khachhang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        this.is_check = true;
                        this.ten_hien_thi = localStorage.getItem('ho_ten');
                    }
                });
        },
        layDuLieuChuyenMuc() {
            axios
                .get('http://127.0.0.1:8000/api/client/chuyen-muc/data')
                .then((res) => {
                    this.ds_chuyen_muc = res.data.chuyen_muc;
                })
        },
        dangXuat() {
            axios
                .get('http://127.0.0.1:8000/api/khach-hang/dang-xuat', {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("token_khachhang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        toaster.success('Thông báo<br>' + res.data.message);
                        window.localStorage.removeItem('token_khachhang');
                        window.localStorage.removeItem('ho_ten');
                        this.is_check = false;
                        this.$router.push('/');
                    } else {
                        toaster.error('Thông báo<br>' + res.data.message);
                    }
                })
        },
        dangXuatAll() {
            axios
                .get('http://127.0.0.1:8000/api/khach-hang/dang-xuat-all', {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("token_khachhang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        toaster.success('Thông báo<br>' + res.data.message);
                        window.localStorage.removeItem('token_khachhang');
                        window.localStorage.removeItem('ho_ten');
                        this.is_check = false;
                        this.$router.push('/');
                    } else {
                        toaster.error('Thông báo<br>' + res.data.message);
                    }
                })
        }

    },
}
</script>
<style>
/* Định dạng cơ bản */
.navbar-nav .nav-link {
    color: #333;
    /* Màu chữ mặc định */
    transition: color 0.3s;
    /* Hiệu ứng chuyển đổi màu */
}

.navbar-nav .nav-link:hover {
    color: #ffc107;
    /* Màu chữ vàng khi hover */
}

/* Dropdown items */
.navbar-nav .dropdown-item {
    color: #333;
    /* Màu chữ mặc định */
    transition: color 0.3s;
    /* Hiệu ứng chuyển đổi màu */
}

.navbar-nav .dropdown-item:hover {
    color: #ffc107;
    /* Màu chữ vàng khi hover */
}

/* Media queries cho các màn hình nhỏ (ví dụ: điện thoại di động) */
@media (max-width: 767px) {

    /* Cải thiện thanh điều hướng khi màn hình nhỏ */
    .navbar-nav {
        flex-direction: column;
        /* Sắp xếp các mục theo chiều dọc */
        align-items: center;
        /* Căn giữa các mục */
        margin-top: 10px;
        /* Tăng khoảng cách giữa navbar và các mục */
    }

    .navbar-nav .nav-item {
        margin-bottom: 10px;
        /* Thêm khoảng cách giữa các mục */
    }

    .navbar-toggler {
        display: block;
        /* Đảm bảo nút toggler luôn hiển thị trên màn hình nhỏ */
    }

    .navbar-collapse {
        width: 100%;
        /* Đảm bảo phần collapse chiếm toàn bộ chiều rộng */
    }

    /* Tối ưu các nút Đăng Nhập và Đăng Ký */
    .d-flex {
        flex-direction: column;
        /* Sắp xếp các nút đăng nhập, đăng ký theo chiều dọc */
        align-items: center;
        /* Căn giữa các nút */
    }

    .navbar-nav .nav-link {
        padding: 10px 15px;
        /* Thêm padding cho các liên kết */
        font-size: 16px;
        /* Giảm kích thước chữ trên màn hình nhỏ */
    }

    /* Chỉnh sửa dropdown */
    .dropdown-menu {
        position: relative;
        /* Đảm bảo dropdown không bị lệch */
    }

    /* Chỉnh sửa hình ảnh người dùng */
    .user-img {
        width: 35px;
        height: 35px;
    }

    /* Điều chỉnh khoảng cách cho các liên kết trong dropdown */
    .dropdown-menu .dropdown-item {
        padding: 8px 15px;
    }
}

/* Nếu thiết bị có màn hình lớn hơn, không thay đổi gì thêm */
@media (min-width: 768px) {
    .navbar-nav {
        flex-direction: row;
        /* Sắp xếp các mục ngang */
    }
}
</style>