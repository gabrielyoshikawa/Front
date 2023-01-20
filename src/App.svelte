<script>
    import Header from "./components/Header.svelte";

  const testeFetch = async () => {
    const testeResp = await fetch("http://localhost:3000/");
    const cde = await testeResp.json();

    console.log(cde);
    return cde;
  };

  const promise = testeFetch();
</script>

<div class="titulo">
    
  <div class="titulo_conteudo">
    <div class="setaEsquerda"><i class="fas fa-caret-left"></i></div>
  </div>

  <div class="titulo_conteudo">
    <div class="display_dia">
      {#await promise then promise}
      {(promise.Today.dayName)}
      {/await}
    </div>
  </div>

  <div class="titulo_conteudo">
    <div class="setaDireita"><i class="fas fa-caret-right"></i></div>
  </div>

</div>

<div class="conteudo">

  <div class="box_dia">

    <div class="dia_noite">Dia</div>

    <div class="conteudo_conteudo_temperatura">
      {#await promise then promise}
      {(promise.Today.tempMin + " F")}
      {/await}
    </div>

    <div class="conteudo_conteudo_temperatura">
      {#await promise then promise}
      {(promise.Today.temp + " F")}
      {/await}
    </div>

    <div class="conteudo_conteudo_temperatura">
      {#await promise then promise}
      {(promise.Today.tempMax + " F")}
      {/await}
    </div>

    <div class="conteudo_icons">
      <i class="fas fa-temperature-low"></i>
    </div>

    <div class="conteudo_icons">
      <i class="fas fa-thermometer-half"></i>
    </div>

    <div class="conteudo_icons">
      <i class="fas fa-temperature-high"></i>
    </div>

    <div class="conteudo_conteudo_vento">
      {#await promise then promise}
      {(promise.Today.windMin + " mph")}
      {/await}
    </div>

    <div class="conteudo_conteudo_vento">
      {#await promise then promise}
      {(promise.Today.windAvg + " mph")}
      {/await}
    </div>

    <div class="conteudo_conteudo_vento">
      {#await promise then promise}
      {(promise.Today.windMax + " mph")}
      {/await}
    </div>

  </div>

</div>

<div class="box_noite">

  <div class="dia_noite">Noite</div>

  <div class="conteudo_conteudo_temperatura">
    {#await promise then promise}
    {(promise.Tonight.tempMin + " F")}
    {/await}
  </div>

  <div class="conteudo_conteudo_temperatura">
    {#await promise then promise}
    {(promise.Tonight.temp + " F")}
    {/await}
  </div>

  <div class="conteudo_conteudo_temperatura">
    {#await promise then promise}
    {(promise.Tonight.tempMax + " F")}
    {/await}
  </div>

  <div class="conteudo_icons">
    <i class="fas fa-temperature-low"></i>
  </div>

  <div class="conteudo_icons">
    <i class="fas fa-thermometer-half"></i>
  </div>

  <div class="conteudo_icons">
    <i class="fas fa-temperature-high"></i>
  </div>

  <div class="conteudo_conteudo_vento">
    {#await promise then promise}
    {(promise.Tonight.windMin + " mph")}
    {/await}
  </div>

  <div class="conteudo_conteudo_vento">
    {#await promise then promise}
    {(promise.Tonight.windAvg + " mph")}
    {/await}
  </div>

  <div class="conteudo_conteudo_vento">
    {#await promise then promise}
    {(promise.Tonight.windMax + " mph")}
    {/await}
  </div>

</div>

<style>
  * {
      margin: 0;
      padding: 0;
    }
    .titulo {
      background-image: linear-gradient(to right, #cdc9c9, #cfcccd, #d2d0d1, #d4d4d4, #d7d7d7);
      width: 100%;
      height: 10%;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .titulo_conteudo {
      float: left;
      padding: 20px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      padding-right: 5%;
      padding-left: 5%;
      font-family: Arial, Helvetica, sans-serif;
    }
    .conteudo { 
      background-image: linear-gradient(to right, #cdc9c9, #cfcccd, #d2d0d1, #d4d4d4, #d7d7d7);      
      height: 100vh;
      width: 100%;
      position: relative;
    }

    .box_dia {
      background-image: linear-gradient(to right, #a7a2a2, #a19b9b, #9b9595, #958e8e, #8f8888);      
      width: 300px;
      height: 300px;
      position: absolute;
      top: 50%;
      left: 50%;
      margin: -350px 0 0 -150px;
      border-radius: 10px;
    }

    .box_noite {
      background-image: linear-gradient(to right, #a7a2a2, #a19b9b, #9b9595, #958e8e, #8f8888);
      width: 300px;
      height: 300px;
      position: absolute;
      top: 103%;
      left: 50%;
      margin: -350px 0 0 -150px;
      border-radius: 10px;
    }

    .conteudo_conteudo_temperatura {
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      padding: 5%;
      float: left;
      margin-left: 9%;
    }

    .conteudo_conteudo_vento {
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      float: left;
      background-color: white;
      margin: 20px;
    }

    .conteudo_icons {
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      padding: 5%;
      float: left;
      margin-left: 5%;
      margin-left: 10%;
      background-color: white;
    }
    
    .dia_noite {
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      padding: 5%;
      background-color: white;
    }

</style>
