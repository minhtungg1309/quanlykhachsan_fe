<template>


    <div class="container">
        <div class="row">
            <div class="card">
                <div class="card-body">
                    <div class="row align-items-center">
                        <div class="col-md-6">
                            <img src="https://pix8.agoda.net/geo/poi/147722/0c74a84a1cd4095a112223cc2c2ba063.jpg?ce=0&s=1024x"
                                alt="Resort" class="card-img img-fluid rounded shadow-sm"
                                style="max-height: 400px; object-fit: cover;">
                        </div>
                        <div class="col-md-6">
                            <div class="card-body">
                                <h5 class="card-title mt-1 text-danger">Resort</h5>
                                <h2 class="card-title">Khám Phá Thiên Đường Nghỉ Dưỡng tại Resort</h2>
                                <div class="row">
                                    <div class="col-lg-6">
                                        <p>
                                            Resort không chỉ là một khách sạn thông thường mà còn là một chốn thiên
                                            đường mang đến trải nghiệm
                                            nghỉ dưỡng đẳng cấp. Với thiết kế hiện đại, tinh tế cùng không gian sang
                                            trọng, mỗi căn phòng tại đây
                                            đều được bài trí hoàn hảo với tầm nhìn tuyệt đẹp hướng ra biển xanh bao la
                                            hoặc khu vườn nhiệt đới mát lành.
                                        </p>
                                        <p>
                                            Tại Resort, du khách sẽ được tận hưởng hệ thống tiện ích đỉnh cao như spa
                                            thư giãn chuyên nghiệp,
                                            phòng gym trang bị hiện đại, nhà hàng phục vụ đa dạng món ăn từ Á đến Âu,
                                            cùng khu vực bar bên hồ bơi
                                            tạo nên không gian thư giãn hoàn hảo.
                                        </p>
                                    </div>
                                    <div class="col-lg-6">
                                        <p>
                                            Dịch vụ khách hàng luôn là tâm điểm tại Resort. Đội ngũ nhân viên tận tâm,
                                            chuyên nghiệp, và chu đáo
                                            luôn sẵn sàng phục vụ suốt 24/7, đảm bảo rằng mọi nhu cầu của bạn đều được
                                            đáp ứng kịp thời, mang lại cảm giác thoải mái như ở nhà.
                                        </p>
                                        <p>
                                            Không chỉ dừng lại ở một địa điểm nghỉ dưỡng lý tưởng, Resort còn là sự lựa
                                            chọn hoàn hảo cho những sự kiện quan trọng.
                                            Với hệ thống phòng hội nghị đa năng, rộng rãi, trang thiết bị hiện đại, đây
                                            là nơi lý tưởng để tổ chức hội thảo,
                                            sự kiện doanh nghiệp, hoặc tiệc cưới đầy ấn tượng.
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                </div>
            </div>
        </div>
        <div class="row">
            <div class="card">
                <div class="card-body">
                    <div class="row">
                        <!-- Ngày Đến -->
                        <div class="col-12 col-sm-6 col-md-4 mb-3">
                            <label class="form-label">Ngày Đến</label>
                            <input v-bind:min="tt_dat.min_ngay_den" v-on:change="doiNgayDen()" v-model="tt_dat.ngay_den"
                                type="date" class="form-control">
                        </div>

                        <!-- Ngày Đi -->
                        <div class="col-12 col-sm-6 col-md-4 mb-3">
                            <label class="form-label">Ngày Đi</label>
                            <input v-bind:min="tt_dat.min_ngay_di" v-model="tt_dat.ngay_di" type="date"
                                class="form-control">
                        </div>

                        <!-- Số Phòng -->
                        <div class="col-12 col-sm-6 col-md-4 mb-3">
                            <label class="form-label">Số Phòng</label>
                            <input v-model="tt_dat.so_phong" type="number" class="form-control"
                                placeholder="Nhập số lượng phòng">
                        </div>

                        <!-- Số Người Lớn -->
                        <div class="col-12 col-sm-6 col-md-4 mb-3">
                            <label class="form-label">Số Người Lớn</label>
                            <input v-model="tt_dat.nguoi_lon" type="number" class="form-control"
                                placeholder="Nhập số người lớn">
                        </div>

                        <!-- Trẻ Em -->
                        <div class="col-12 col-sm-6 col-md-4 mb-3">
                            <label class="form-label">Trẻ Em</label>
                            <input v-model="tt_dat.tre_em" type="number" class="form-control"
                                placeholder="Nhập số trẻ em">
                        </div>

                        <!-- Nút Tìm Kiếm -->
                        <div class="col-12 col-sm-6 col-md-4 mb-3">
                            <button v-on:click="chuyenTrang()" class="btn btn-warning w-100"
                                style="margin-top: 28px;">Tìm Kiếm</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>


        <div class="row">
            <div class="card">
                <div class="card-body">
                    <div class="row">
                        <div class="col-lg-3">
                            <div class="card radius-10 bg-gradient-cosmic">
                                <div class="card-body">
                                    <div class="d-flex align-items-center">
                                        <div class="me-auto">
                                            <p class="mb-0 text-white">Phòng Suite</p>
                                            <h4 class="my-1 text-white">4805 khách</h4>
                                            <p class="mb-0 font-13 text-white">Giảm 10% khi đặt từ 2 phòng
                                            </p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="col-lg-3">
                            <div class="card radius-10 bg-gradient-ibiza">
                                <div class="card-body">
                                    <div class="d-flex align-items-center">
                                        <div class="me-auto">
                                            <p class="mb-0 text-white">Phòng Standard</p>
                                            <h4 class="my-1 text-white">3550 khách</h4>
                                            <p class="mb-0 font-13 text-white">Giảm 15% khi đặt phòng đôi
                                            </p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="col-lg-3">
                            <div class="card radius-10 bg-gradient-ohhappiness">
                                <div class="card-body">
                                    <div class="d-flex align-items-center">
                                        <div class="me-auto">
                                            <p class="mb-0 text-white">Phòng Superior</p>
                                            <h4 class="my-1 text-white">3220 khách</h4>
                                            <p class="mb-0 font-13 text-white">Giảm 12 % khi đi nhóm bạn từ
                                                5 người</p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="col-lg-3">
                            <div class="card radius-10 bg-gradient-kyoto">
                                <div class="card-body">
                                    <div class="d-flex align-items-center">
                                        <div class="me-auto">
                                            <p class="mb-0 text-white">Phòng Deluxe</p>
                                            <h4 class="my-1 text-white">3217 khách</h4>
                                            <p class="mb-0 font-13 text-white">Giảm 3$ cho khách đặt qua đêm
                                            </p>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="row">
            <div class="card shadow-lg">
                <div class="card-body">
                    <!-- Search and Filter Section -->
                    <div class="row align-items-center mb-4">
                        <div class="col-lg-3 col-xl-2">
                            <h5 class="text-primary fw-bold">Danh Sách Loại Phòng</h5>
                        </div>
                        <div class="col-lg-9 col-xl-10">
                            <form class="d-flex justify-content-end align-items-center">
                                <div class="input-group me-3" style="max-width: 400px;">
                                    <span class="input-group-text bg-light"><i
                                            class="bx bx-search text-primary"></i></span>
                                    <input type="text" class="form-control" placeholder="Tìm Kiếm Loại Phòng">
                                </div>
                                <div class="btn-group">
                                    <button type="button" class="btn btn-outline-primary">Loại Phòng</button>
                                    <button type="button"
                                        class="btn btn-outline-primary dropdown-toggle dropdown-toggle-split"
                                        data-bs-toggle="dropdown" aria-expanded="false">
                                        <i class="bx bx-chevron-down"></i>
                                    </button>
                                    <ul class="dropdown-menu">
                                        <li><a class="dropdown-item" href="#">Phòng Standard</a></li>
                                        <li><a class="dropdown-item" href="#">Phòng Superior</a></li>
                                        <li><a class="dropdown-item" href="#">Phòng Deluxe</a></li>
                                        <li><a class="dropdown-item" href="#">Phòng Suite</a></li>
                                        <li><a class="dropdown-item" href="#">Phòng View Biển</a></li>
                                        <li><a class="dropdown-item" href="#">Phòng VIP</a></li>
                                    </ul>
                                </div>
                            </form>
                        </div>
                    </div>

                    <!-- Room Carousel Section -->
                    <div class="carousel-container">
                        <carousel :items-to-show="4" :loop="true">
                            <slide v-for="(v, k) in ds_loai_phong" :key="k" class="p-2">
                                <div class="col">
                                    <router-link to="/dat-phong" class="card border-0 shadow-sm rounded room-card">
                                        <img v-bind:src="v.hinh_anh"
                                            style="width: 100%; height: 230px; object-fit: cover;"
                                            class="card-img-top rounded-top room-img" alt="Hình ảnh phòng">
                                        <div class="card-body">
                                            <h5 class="card-title text-dark fw-bold">{{ v.ten_loai_phong }}</h5>
                                            <div class="d-flex align-items-center mt-3">
                                                <p class="mb-0 me-4 text-muted"><i class="fa-solid fa-expand"></i> {{
                                                    v.dien_tich }}m<sup>2</sup></p>
                                                <p class="mb-0 text-muted"><i class="fa-solid fa-bed"></i> {{
                                                    v.so_giuong }} Giường</p>
                                            </div>
                                            <hr>
                                            <div class="d-flex justify-content-between">
                                                <a href="javascript:;" class="btn btn-outline-danger rounded-pill">
                                                    <i class="bx bx-star"></i> Yêu Thích
                                                </a>
                                                <router-link to="/dat-phong" href="javascript:;"
                                                    class="btn btn-primary rounded-pill">
                                                    Chọn Phòng
                                                </router-link>
                                            </div>
                                        </div>
                                    </router-link>
                                </div>
                            </slide>
                            <template #addons>
                                <navigation />
                                <pagination />
                            </template>
                        </carousel>
                    </div>
                </div>
            </div>
        </div>

    </div>

    <div class="container-fluid">
        <div class="row">
            <div class="col-md-12">
                <img src="../../../assets/img_homepage/banner.png" class="img-fluid">
            </div>
        </div>
    </div>


    <div class="container mt-5">
        <div class="row">
            <div class="col-lg-12 text-center">
                <h2><b>Review</b></h2>
                <hr>
            </div>
        </div>
        <div class="row">
            <div class="card">
                <div class="card-body">
                    <div class="row">
                        <div id="carouselExampleCaptions_2" class="carousel slide">
                            <div class="carousel-indicators">
                                <button type="button" data-bs-target="#carouselExampleCaptions_2" data-bs-slide-to="0"
                                    class="active" aria-current="true" aria-label="Slide 1"></button>
                                <button type="button" data-bs-target="#carouselExampleCaptions_2" data-bs-slide-to="1"
                                    aria-label="Slide 2"></button>
                                <button type="button" data-bs-target="#carouselExampleCaptions_2" data-bs-slide-to="2"
                                    aria-label="Slide 3"></button>
                            </div>
                            <div class="carousel-inner">
                                <div class="carousel-item active">
                                    <div class="row">
                                        <template v-for="(v, k) in ds_review" :key="k">
                                            <template v-if="k < 3">
                                                <div class="col-lg-4 ">
                                                    <div class="card">
                                                        <div class="card-body ">
                                                            <div class="row">
                                                                <div class="col-md-12 text-center mb-2">
                                                                    <img v-bind:src="v.avatar" alt="" class="user-img">
                                                                </div>
                                                                <hr>
                                                                <h5 class="mt-0">{{ v.ho_va_ten }}</h5>
                                                                <p class="mb-2">{{ v.noi_dung }}</p>
                                                                <hr>
                                                                <div class="d-flex align-items-center mt-2 fs-6">
                                                                    <div class="cursor-pointer">
                                                                        <template v-for="items in v.sao_danh_gia"
                                                                            :key="items">
                                                                            <i class="bx bxs-star text-warning"></i>
                                                                        </template>
                                                                        <template v-for="items in (5 - v.sao_danh_gia)"
                                                                            :key="items">
                                                                            <i class="bx bxs-star text-secondary"></i>
                                                                        </template>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </template>
                                        </template>
                                    </div>
                                </div>
                                <div class="carousel-item">
                                    <div class="row">
                                        <template v-for="(value, key) in ds_review" :key="key">
                                            <template v-if="key > 2 && key < 6">
                                                <div class="col-lg-4 d-flex">
                                                    <div class="card">
                                                        <div class="card-body ">
                                                            <div class="row">
                                                                <div class="col-md-12 text-center mb-2">
                                                                    <img v-bind:src="value.avatar" alt=""
                                                                        class="user-img">
                                                                </div>
                                                                <hr>
                                                                <h5 class="mt-0">{{ value.ho_va_ten }}</h5>
                                                                <p class="mb-2">{{ value.noi_dung }}</p>
                                                                <hr>
                                                                <div class="d-flex align-items-center mt-2 fs-6">
                                                                    <div class="cursor-pointer">
                                                                        <template v-for="items in value.sao_danh_gia"
                                                                            :key="items">
                                                                            <i class="bx bxs-star text-warning"></i>
                                                                        </template>
                                                                        <template
                                                                            v-for="items in (5 - value.sao_danh_gia)"
                                                                            :key="items">
                                                                            <i class="bx bxs-star text-secondary"></i>
                                                                        </template>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                            </template>
                                        </template>
                                    </div>
                                </div>
                            </div>
                            <button class="carousel-control-prev" type="button"
                                data-bs-target="#carouselExampleCaptions_2" data-bs-slide="prev">
                                <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                                <span class="visually-hidden">Previous</span>
                            </button>
                            <button class="carousel-control-next" type="button"
                                data-bs-target="#carouselExampleCaptions_2" data-bs-slide="next">
                                <span class="carousel-control-next-icon" aria-hidden="true"></span>
                                <span class="visually-hidden">Next</span>
                            </button>
                        </div>

                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
import { createToaster } from "@meforma/vue-toaster";
const toaster = createToaster({ position: "top-right" });
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
export default {
    components: {
        Carousel,
        Slide,
        Pagination,
        Navigation,
    },
    data() {
        return {
            ds_review: [],
            ds_slide: [],
            ds_loai_phong: [],
            tt_dat: {},
        }
    },
    mounted() {
        this.layDuLieuHomepage();
        // this.layDuLieuSlide();
        this.getToday();
    },
    methods: {
        getToday() {
            var today = new Date();
            var dd = String(today.getDate()).padStart(2, '0');
            var mm = String(today.getMonth() + 1).padStart(2, '0'); //January is 0!
            var yyyy = today.getFullYear();
            today = yyyy + '-' + mm + '-' + dd;
            this.tt_dat.min_ngay_di = today;
            this.tt_dat.min_ngay_den = today;
        },
        doiNgayDen() {
            this.tt_dat.min_ngay_di = this.tt_dat.ngay_den;
            if (this.tt_dat.ngay_di < this.tt_dat.ngay_den) {
                this.tt_dat.ngay_di = this.tt_dat.ngay_den;
            }
        },
        layDuLieuHomepage() {
            axios
                .get('http://127.0.0.1:8000/api/homepage/data')
                .then((res) => {
                    this.ds_review = res.data.dataReview;
                    this.ds_slide = res.data.dataSlide;
                    this.ds_loai_phong = res.data.dataLoaiPhong;
                })
        },
        // layDuLieuReview() {
        //     axios
        //         .get('http://127.0.0.1:8000/api/review/data')
        //         .then((res) => {
        //             this.ds_review = res.data.review;
        //         })
        // },
        // layDuLieuSlide() {
        //     axios
        //         .get('http://127.0.0.1:8000/api/slide/data')
        //         .then((res) => {
        //             this.ds_slide = res.data.slide;
        //         })
        // },
        chuyenTrang() {
            this.$router.push({
                name: "datPhong",
                params: {
                    'ngay_den': this.tt_dat.ngay_den,
                    'ngay_di': this.tt_dat.ngay_di,
                    'so_phong': this.tt_dat.so_phong,
                    'nguoi_lon': this.tt_dat.nguoi_lon,
                    'tre_em': this.tt_dat.tre_em,
                },
            });
        }
    },
}
</script>
<style>
.room-card {
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.room-card:hover {
    transform: scale(1.05);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.15);
}

.room-img {
    transition: opacity 0.3s ease;
}

.room-card:hover .room-img {
    opacity: 0.85;
}

.room-card .btn {
    transition: background-color 0.3s ease, color 0.3s ease;
}

.room-card:hover .btn-primary {
    background-color: #0056b3;
    color: #fff;
}

.room-card:hover .btn-outline-danger {
    background-color: #dc3545;
    color: #fff;
}
</style>
