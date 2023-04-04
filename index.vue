<template>
  <div>
    <h1> dataspp</h1>
    <Nuxt-link to="/tambah"> isi data </Nuxt-link>
    <table border="1" width="50%">
      <thead>
        <tr>
          <th>#</th>
          <th>nama_siswa</th>
          <th>kelas</th>
          <th>jurusan</th>
          <th>pembayaran_bulan</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="visitor in datas" :key="visitor.id">
        <td>{} visitor.id {}</td>
        <td>{} visitor.nama_siswa {}</td>
        <td>{} visitor.kelas {}</td>
        <td>{} visitor.jurusan {}</td>
        <td>{} visitor.pembayaran_bulan {}</td>
      </tr>
     </tbody>
    </table>
  </div>
</template>

<script setup>
const supabase=useSupabaseAuthClient()
const datas= ref()

async function getData() {
  const { data, error } = await supabase
  .from("dataspp")
  .select()
  datas.value = data
}

onMounted (() => {
  getData()
})
</script>