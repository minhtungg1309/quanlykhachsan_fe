<template>
    <div class="container py-4">
        <!-- Form Tìm Kiếm -->
        <div class="row mb-4">
            <div class="card shadow-sm">
                <div class="card-body">
                    <div class="row g-3">
                        <div class="col-md-2">
                            <label class="form-label fw-bold">Ngày Đến</label>
                            <input v-model="tt_dat.ngay_den" type="date" class="form-control">
                        </div>
                        <div class="col-md-2">
                            <label class="form-label fw-bold">Ngày Đi</label>
                            <input v-model="tt_dat.ngay_di" type="date" class="form-control">
                        </div>
                        <div class="col-md-2">
                            <label class="form-label fw-bold">Số Phòng</label>
                            <input v-model="tt_dat.so_phong" type="number" class="form-control"
                                placeholder="Số lượng phòng">
                        </div>
                        <div class="col-md-2">
                            <label class="form-label fw-bold">Số Người Lớn</label>
                            <input v-model="tt_dat.nguoi_lon" type="number" class="form-control"
                                placeholder="Số người lớn">
                        </div>
                        <div class="col-md-2">
                            <label class="form-label fw-bold">Trẻ Em</label>
                            <input v-model="tt_dat.tre_em" type="number" class="form-control" placeholder="Số trẻ em">
                        </div>
                        <div class="col-md-2">
                            <label class="form-label d-block opacity-0">Tìm Kiếm</label>
                            <button v-on:click="chuyenTrang()" class="btn btn-warning w-100 text-white fw-bold">
                                Tìm Kiếm
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Danh Sách Loại Phòng -->
        <div class="row g-4">
            <template v-for="(v, k) in ds_loai_phong" :key="k">
                <div class="col-lg-4 col-md-6">
                    <router-link to="/dat-phong" class="card border-0 shadow-sm room-card">
                        <img v-bind:src="v.hinh_anh" class="card-img-top" alt="Hình ảnh phòng">
                        <div class="card-body">
                            <h5 class="card-title text-dark fw-bold mb-3">{{ v.ten_loai_phong }}</h5>
                            <div class="row mb-3">
                                <div class="col-12 d-flex flex-wrap text-secondary small">
                                    <p class="me-4 mb-1"><i class="fa-solid fa-expand me-1"></i>{{ v.dien_tich }}
                                        m<sup>2</sup></p>
                                    <p class="me-4 mb-1"><i class="fa-solid fa-bed me-1"></i> {{ v.so_giuong }} Giường
                                    </p>
                                    <p class="mb-1"><i class="fa-solid fa-person me-1"></i>{{ v.so_nguoi_lon }} Người
                                        lớn & {{ v.so_tre_em }} Trẻ em</p>
                                </div>
                            </div>
                            <div class="d-flex justify-content-between align-items-center">
                                <a href="javascript:;" class="btn btn-outline-danger rounded-pill">
                                    <i class="bx bx-star"></i> Yêu Thích
                                </a>
                                <a href="javascript:;" class="btn btn-primary rounded-pill">
                                    Chọn Phòng
                                </a>
                            </div>
                        </div>
                    </router-link>
                </div>
            </template>
        </div>
    </div>



</template>
<script>
import axios from 'axios';
import { createToaster } from "@meforma/vue-toaster";
const toaster = createToaster({ position: "top-right" });
export default {
    data() {
        return {
            ds_loai_phong: [],
            tt_dat: {},
        }
    },
    mounted() {
        this.LaydulieuLoaiPhong();
    },
    methods: {
        LaydulieuLoaiPhong() {
            axios
                .get('http://127.0.0.1:8000/api/client/loai-phong/data')
                .then((res) => {
                    this.ds_loai_phong = res.data.loai_phong;
                })
        },
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
/* Form tìm kiếm */
.card {
    border-radius: 10px;
}

/* Card loại phòng */
.room-card {
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    border-radius: 10px;
}

.room-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}

.room-card img {
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    height: 240px;
    object-fit: cover;
}

.room-card .card-body {
    padding: 20px;
}

.room-card .card-title {
    font-size: 18px;
}

.room-card p {
    margin-bottom: 0;
}
</style>
