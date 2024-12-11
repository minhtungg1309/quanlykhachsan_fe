<template>
    <section class="vh-100 d-flex align-items-center justify-content-center">
        <div class="container">
            <div class="row justify-content-center">
                <div class="col-md-8 col-lg-6">
                    <div class="card shadow-lg p-5" style="background-color: white; border-radius: 20px;">
                        <div class="text-center">
                            <!-- <img src="https://.com/assets/images/logo-img.png" width="120" alt="Logo" /> -->
                            <h4 class="mt-4 font-weight-bold">Quên Mật Khẩu?</h4>
                            <p class="text-muted">
                                Vui lòng nhập email tài khoản của bạn để nhận liên kết đặt lại mật khẩu.
                            </p>
                        </div>
                        <form>
                            <div class="my-4">
                                <label class="form-label">Email</label>
                                <div class="input-group mb-3">
                                    <span class="input-group-text"><i class="fa-solid fa-envelope"></i></span>
                                    <input v-model="tai_khoan.email" type="email" class="form-control form-control-lg"
                                        placeholder="example@user.com">
                                </div>
                            </div>
                            <div class="d-grid gap-2">
                                <button v-on:click="gui()" type="button" class="btn btn-purple btn-lg">
                                    Gửi Yêu Cầu
                                </button>
                                <router-link to="/khach-hang/dang-nhap">
                                    <button type="button" class="btn btn-light btn-lg w-100">
                                        <i class="fa-solid fa-arrow-left me-1"></i> Quay Lại Đăng Nhập
                                    </button>
                                </router-link>
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
            tai_khoan: {},
        }
    },
    methods: {
        gui() {
            axios
                .post("http://127.0.0.1:8000/api/khach-hang/quen-mat-khau", this.tai_khoan)
                .then((res) => {
                    if (res.data.status) {
                        toaster.success(res.data.message);
                        this.$router.push('/');
                    } else {
                        toaster.error(res.data.message);
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