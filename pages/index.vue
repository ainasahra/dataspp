<template>
  <div>
    <h1> dataspp</h1>
    <Nuxt-link to="/tambah"> isi data </Nuxt-link>
    <table border="1" width="50%" class="table bg-dark text-light">
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
        <tr v-for="s,index in datas" :key="s.id">
        <td>{{ index+1 }}</td>
        <td>{{ s.nama_siswa }}</td>
        <td>{{ s.kelas }}</td>
        <td>{{ s.jurusan }}</td>
        <td>{{ s.pembayaran_bulan }}</td>
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
  .from("siswa")
  .select()
  datas.value = data
  console.log(data)
}

onMounted (() => {
  getData()
})
</script>