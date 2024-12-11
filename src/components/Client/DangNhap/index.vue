<template>
    <section class="vh-100">
        <div class="container-fluid h-custom">
            <div class="row d-flex justify-content-center align-items-center h-100">
                <div class="col-md-8 col-lg-6 col-xl-4 offset-xl-1">
                    <!-- Card -->
                    <div class="card shadow-sm p-4" style="background-color: white; border-radius: 15px;">
                        <form>
                            <!-- Đăng nhập qua mạng xã hội -->
                            <div
                                class="d-flex flex-row align-items-center justify-content-center justify-content-lg-start">
                                <p class="lead fw-normal mb-0 me-3">Đăng nhập với</p>
                                <button type="button" class="btn btn-purple btn-floating mx-1">
                                    <i class="fab fa-facebook-f"></i>
                                </button>
                                <button type="button" class="btn btn-purple btn-floating mx-1">
                                    <i class="fab fa-twitter"></i>
                                </button>
                                <button type="button" class="btn btn-purple btn-floating mx-1">
                                    <i class="fab fa-linkedin-in"></i>
                                </button>
                            </div>

                            <div class="divider d-flex align-items-center my-4">
                                <p class="text-center fw-bold mx-3 mb-0">Hoặc</p>
                            </div>

                            <!-- Nhập email -->
                            <div class="form-outline mb-4">
                                <input v-model="login.email" type="email" id="form3Example3"
                                    class="form-control form-control-lg" placeholder="Nhập địa chỉ email hợp lệ" />
                            </div>

                            <!-- Nhập mật khẩu -->
                            <div class="form-outline mb-3">
                                <input v-model="login.password" type="password" id="form3Example4"
                                    class="form-control form-control-lg" placeholder="Nhập mật khẩu" />
                            </div>

                            <div class="d-flex justify-content-between align-items-center">
                                <!-- Checkbox -->
                                <div class="form-check mb-0">
                                    <input class="form-check-input me-2" type="checkbox" id="form2Example3" />
                                    <label class="form-check-label" for="form2Example3">
                                        Ghi nhớ đăng nhập
                                    </label>
                                </div>
                                <router-link to="/quen-mat-khau" class="text-body">
                                    Quên mật khẩu?
                                </router-link>
                            </div>

                            <div class="text-center text-lg-start mt-4 pt-2">
                                <button v-on:click="dangNhap" type="button" class="btn btn-purple btn-lg"
                                    style="padding-left: 2.5rem; padding-right: 2.5rem;">
                                    Đăng nhập
                                </button>
                                <p class="small fw-bold mt-2 pt-1 mb-0">
                                    Chưa có tài khoản?
                                    <router-link to="/khach-hang/dang-ky" class="link-purple">
                                        Đăng ký ngay
                                    </router-link>
                                </p>
                            </div>
                        </form>
                    </div>
                    <!-- End Card -->
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
            login: {},
        }
    },
    mounted() {
        this.checkLogin();
    },
    methods: {
        dangNhap() {
            axios
                .post("http://127.0.0.1:8000/api/khach-hang/dang-nhap", this.login)
                .then((res) => {
                    if (res.data.status) {
                        toaster.success(res.data.message)
                        localStorage.setItem('token_khachhang', res.data.token);
                        localStorage.setItem('ho_ten', res.data.ho_ten);
                        this.$router.push('/');
                    }
                    else {
                        toaster.error(res.data.message)
                    }
                })
                ;
        },
        checkLogin() {
            axios
                .post('http://127.0.0.1:8000/api/kiem-tra-token-khach-hang', {}, {
                    headers: {
                        Authorization: 'Bearer ' + localStorage.getItem("token_khachhang")
                    }
                })
                .then((res) => {
                    if (res.data.status) {
                        this.$router.push('/');
                    }
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
