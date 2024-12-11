<template>
    <section class="vh-100 d-flex align-items-center justify-content-center">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-md-8 col-lg-6">
                    <div class="card shadow-lg p-5" style="background-color: white; border-radius: 20px;">
                        <div class="text-center">
                            <h3 class="mb-4">Đăng Ký</h3>
                            <p>
                                Bạn đã có tài khoản?
                                <router-link to="/khach-hang/dang-nhap" class="link-purple">
                                    Đăng nhập tại đây
                                </router-link>
                            </p>
                        </div>
                        <form class="row g-3">
                            <!-- Họ Đệm và Tên -->
                            <div class="col-6">
                                <label class="form-label">Họ Đệm</label>
                                <input type="text" class="form-control" v-model="data_dang_ky.ho_lot">
                            </div>
                            <div class="col-6">
                                <label class="form-label">Tên</label>
                                <input type="text" class="form-control" v-model="data_dang_ky.ten">
                            </div>
                            <!-- Email -->
                            <div class="col-12">
                                <label class="form-label">Địa Chỉ Email</label>
                                <input type="email" class="form-control" v-model="data_dang_ky.email">
                            </div>
                            <!-- Số Điện Thoại và Ngày Sinh -->
                            <div class="col-6">
                                <label class="form-label">Số Điện Thoại</label>
                                <input type="tel" class="form-control" v-model="data_dang_ky.so_dien_thoai">
                            </div>
                            <div class="col-6">
                                <label class="form-label">Ngày Sinh</label>
                                <input type="date" class="form-control" v-model="data_dang_ky.ngay_sinh">
                            </div>
                            <!-- Mật khẩu -->
                            <div class="col-6">
                                <label class="form-label">Mật Khẩu</label>
                                <input type="password" class="form-control" v-model="data_dang_ky.password">
                            </div>
                            <div class="col-6">
                                <label class="form-label">Nhập Lại Mật Khẩu</label>
                                <input type="password" class="form-control" v-model="data_dang_ky.re_password">
                            </div>
                            <!-- Quên mật khẩu -->
                            <div class="col-md-12 text-end">
                                <router-link to="/quen-mat-khau" class="link-purple">
                                    Quên mật khẩu?
                                </router-link>
                            </div>
                            <!-- Nút Đăng Ký -->
                            <div class="col-12">
                                <div class="d-grid">
                                    <button type="button" class="btn btn-purple btn-lg" v-on:click="dangKy()">
                                        Đăng Ký
                                    </button>
                                </div>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </section>

</template>
<script>
import axios from 'axios';
import { createToaster } from "@meforma/vue-toaster";
const toaster = createToaster({ position: "top-right" });
export default {
    data() {
        return {
            data_dang_ky: {}
        }
    },
    mounted() {

    },
    methods: {
        dangKy() {
            axios
                .post('http://127.0.0.1:8000/api/dang-ky', this.data_dang_ky)
                .then((res) => {
                    if (res.data.status) {
                        toaster.success(res.data.message);
                        this.data_dang_ky = {};
                    } else {
                        toaster.error(res.data.message)
                    }
                })
                .catch((res) => {
                    var result = Object.entries(res.response.data.errors);
                    result.forEach((v, k) => {
                        toaster.error(v[1][0]);
                    });
                });
        }
    },
}
</script>
<style>
.vh-100 {
    background-image: url('https://media-cdn-v2.laodong.vn/Storage/NewsPortal/2023/8/25/1233238/Sau-Dich-Benh-Covid-.jpg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    display: flex;
    align-items: center;
    justify-content: center;
}

.bg-purple {
    background-color: #0c40ce !important;
}

.btn-purple {
    background-color: #0c40ce;
    border-color: #0c40ce;
    color: white;
}

.btn-purple:hover {
    background-color: #0c40ce;
    border-color: #0c40ce;
}

.link-purple {
    color: #0c40ce;
}

.link-purple:hover {
    color: #0c40ce;
}

.h-custom {
    height: calc(100% - 73px);
}
</style>
