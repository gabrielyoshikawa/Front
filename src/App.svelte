<script>
  const testeFetch = async () => {
    const testeResp = await fetch("http://localhost:3000/");
    const cde = await testeResp.json();

    console.log(cde);
    return cde;
  };

  const promise = testeFetch();
</script>

<div class="container">
  <div class="titulo">
    <img src="public/images/cloud.png" alt="" width="10%">
    {#await promise then promise}
    {#each Object.keys(promise) as key}
      <!-- <p>{JSON.stringify(promise[key])}</p> -->
    {/each}
    <p>{JSON.stringify(promise.Friday.dayName)}</p>
    {:catch error}
      <p style="color: red">{error.message}</p>
    {/await}
  </div>

  <div class="menu">
    <button class="btn"><img src="public/images/menu-hamburguer.png" alt="" width="50%" height="50%"></button>
  </div>

  <div class="conteudo">
      <div class="dia">

        <div class="allTemps">
          <p>Dia</p>
          <div class="temperaturaMin">
            {#await promise then promise}
            <p>{JSON.stringify(promise.Friday.tempMin + " F")}</p>
            {/await}
          </div>

          <div class="temperatura">
            {#await promise then promise}
            <p>{JSON.stringify(promise.Friday.temp + " F")}</p>
            {/await}
          </div>

          <div class="temperaturaMax">
            {#await promise then promise}
            <p>{JSON.stringify(promise.Friday.tempMax + " F")}</p>
            {/await}
          </div>

        </div>

      </div>
  </div>
</div>

<style>
  * {
      margin: 0;
      padding: 0;
    }
    .titulo {
      text-align: center;
      color: rgb(70, 55, 55);
      background-color: #ebf4f5;
      height: 5%;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
      font-size: 100%;
      padding: 2%;
    }
    .container {
      background: white;
      height: 95vh;
      width: 100%;
    }
    .menu {
      background: #6f84a5;
      float: left;
      height: 100%;
      width: 15%;
    }
    .conteudo { 
      background: #6f84a5;
      float: left;
      height: 100%;
      width: 85%;
    }
    .dia {
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
      font-size: 100%;
      margin-top: 5%;
      margin-left: 40%;
    }
    .allTemps {
      text-align: center;
      margin-left: -85%;
      float: center;
    }
    .temperaturaMin {
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
      font-size: 100%;
      float: left;
      margin-left: 30%;
    }
    .temperatura {
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
      font-size: 100%;
      float: left;
    }
    .temperaturaMax {
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
      font-size: 100%;
      float: left;
    }

    .btn {
      width: 100%;
      height: 8%;
      background: #6f84a5;
      border: none;
      margin-top: 10%;
    }
    .btn:hover {
      background-color: blue;
    }
</style>
