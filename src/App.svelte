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
    <p class="QQQQQ">{JSON.stringify(promise.Friday.dayName)}</p>
    {:catch error}
      <p style="color: red">{error.message}</p>
    {/await}
  </div>


  <div class="conteudo">
      <!-- <div class="dia">

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

      </div> -->
      <div class="CCCCC"><h1>C</h1></div>
      <div class="ABCDE"><h1>A</h1></div>
      <div class="AAAAA"><h1>B</h1></div>
      <div class="BBBBB"><h1>C</h1></div>
  </div>
</div>

<style>
  * {
      margin: 0;
      padding: 0;
    }
    .titulo {
      color: rgb(70, 55, 55);
      background-color: #ebf4f5;
      height: 5%;
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
      font-size: 100%;
      padding: 2%;
    }
    .QQQQQ {
      text-align: center;
    }
    .container {
      background: white;
      height: 95vh;
      width: 100%;
    }
    .conteudo { 
      background: #6f84a5;
      float: left;
      height: 100%;
      width: 100%;
    }
    /* .dia {
      font-family: Arial, Helvetica, sans-serif;
      font-weight: bold;
      font-size: 100%;
      margin-top: 5%;
      margin-left: 40%;
    } */
    .ABCDE {
      background-color: red;
      float: left;
      margin-left: 10%;
      margin-right: 10%;
    }
    .AAAAA {
      background-color: blue;
      float: left;
      margin-left: 10%;
      margin-right: 10%;
    }
    .BBBBB {
      background: green;
      float: left;
      margin-left: 10%;
      margin-right: 10%;
    }
    .CCCCC {
      background-color: yellow;
      text-align: center;
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
