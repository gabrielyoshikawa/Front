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
      <p>{(promise.Today.tempMin + " F")}</p>
      {/await}

      {#await promise then promise}
      <p>{(promise.Today.temp + " F")}</p>
      {/await}

      {#await promise then promise}
      <p>{(promise.Today.tempMax + " F")}</p>
      {/await}
    </div>

    <div class="conteudo_icons_temp">
      <i class="fas fa-temperature-low"></i>

      <i class="fas fa-thermometer-half"></i>

      <i class="fas fa-temperature-high"></i>
    </div>

    <div class="conteudo_conteudo_vento">
      {#await promise then promise}
      <p>{(promise.Today.windMin + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise.Today.windAvg + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise.Today.windMax + " mph")}</p>
      {/await}
    </div>

    <div class="conteudo_icons_wind">
      <i class="fas fa-wind"></i>
      <i class="fas fa-wind"></i>
      <i class="fas fa-wind"></i>
    </div>

  </div>

  <div class="box_noite">
  
    <div class="dia_noite">Noite</div>
  
    <div class="conteudo_icons_temp">
      <i class="fas fa-temperature-low"></i>
      <i class="fas fa-thermometer-half"></i>
      <i class="fas fa-temperature-high"></i>
    </div>

    <div class="conteudo_conteudo_temperatura">
      {#await promise then promise}
      <p>{(promise.Tonight.tempMin + " F")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise.Tonight.temp + " F")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise.Tonight.tempMax + " F")}</p>
      {/await}
    </div>
  

    <div class="conteudo_conteudo_vento">
      {#await promise then promise}
      <p>{(promise.Tonight.windMin + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise.Tonight.windAvg + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise.Tonight.windMax + " mph")}</p>
      {/await}
    </div>

    <div class="conteudo_icons_wind">
      <i class="fas fa-wind"></i>
      <i class="fas fa-wind"></i>
      <i class="fas fa-wind"></i>
    </div>
  
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
      min-height: 100vh;
      height: fit-content;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
      align-items: center;
    }

    .box_dia, .box_noite {
      background-image: linear-gradient(to right, #a7a2a2, #a19b9b, #9b9595, #958e8e, #8f8888);      
      width: 300px;
      height: 300px;
      border-radius: 10px;
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      margin: 10px 0;
    }

    .conteudo_conteudo_temperatura, .conteudo_conteudo_vento, .conteudo_icons_temp, .conteudo_icons_wind{
      display: flex;
      width: 100%;
      flex-direction: row;
      justify-content: space-around;
      align-items: center;
      font-size: 20px;
      padding: 5% 0;
    }
    
    .dia_noite {
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 20px;
      padding: 5% 0;
      background-color: rgb(177, 175, 175);
    }

</style>
