<template>
    <div>
        <!-- Section-->
        <section class="py-5">
            <div class="container px-4 px-lg-5 mt-5">
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">

                    <div v-for="item in items" :key="item.id" class="col mb-5">
                        <div class="card h-100">
                            <!-- Product image-->
                            <img class="card-img-top"
                                :src="item.image" alt="..." />
                            <!-- Product details-->
                            <div class="card-body p-4">
                                <div class="text-center">
                                    <!-- Product name-->
                                    <h5 class="fw-bolder">{{ item.nama_obat }}</h5>
                                    {{ item.harga }}
                                </div>
                            </div>
                            <!-- Product actions-->
                            <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
                                <div class="text-center"><a class="btn btn-primary" href="#">buy</a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script setup>
import axios from 'axios'
const items = ref([])
const getData = async () => {
    const res = await axios.get('http://localhost:8000/api/produk')
    items.value = res.data
    console.log(res.data)
}
onMounted(() => getData())
</script>