<template>
    <div>
        <div class="" style="display: block;">    
            <form @submit.prevent="addData" >
                <div class="" style="display: block;">
                    <label for="nama">Nama siswa</label>
                    <input type="text" v-model="nama">
                </div>
                <div class="">
                    <label for="kelas">Kelas</label>
                    <input type="text" v-model="kelas">
                </div>
                <div class="">
                    <label for="">jurusan</label>
                    <input type="text" v-model="jurusan">
                </div>
                <div class="">
                    <label for="bayar">Jumlah bayar</label>
                    <input type="number" v-model="bayar">
                </div>
                    <button type="submit" class="btn btn-primary text-docaration-none nb-3">Tambah</button>
               
            </form>
        </div>
    </div>
</template>

<script setup>
const supabase = useSupabaseAuthClient()
const nama = ref()
const kelas = ref()
const jurusan = ref()
const bayar = ref()
const addData = async ()=>{
    const {data,error } = await supabase
    .from("siswa")
    .insert({
        nama_siswa:nama.value,
        kelas:kelas.value,
        jurusan:jurusan.value,
        pembayaran_bulan:bayar.value
    })

    alert("data berhasil di tambahkan")
    navigateTo("/")
    if(error){
        alert("pastikan data benar sir^^")
    }
} 


</script>

<style scoped>
thead {
  background-color: rgb(128, 125, 122);
}
tbody {
  background-color: rgb(231, 231, 231) ;
}
</style>
