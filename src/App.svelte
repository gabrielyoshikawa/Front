<script>
  import Header from "./components/Header.svelte";

  async function fetchData() {
      const teste = await fetch("")
    console.log(teste)
      const data = await teste.json("http://localhost:5173/");
    console.log(teste)

    if (teste.ok) {
      return data;
    } else {
      throw new Error(data);
    }
  }

</script>

<div class="container">
  <Header/>

</div>

<style>

</style>
