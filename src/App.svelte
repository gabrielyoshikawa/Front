<script>
  const testeFetch = async () => {
    const resp = await fetch("http://localhost:3000/");
    const resp2 = await resp.json();

    return resp2;
  };

  const promise = testeFetch();

  const add = () => {
    if (index < 12) {
      index = index + 2;
    } else {
      index = 0;
    }
  }

  const reduce = () => {
    if (index > 0) {
      index = index - 2;
    } else {
      index = 12;
    }
  }

  let index = 0;
</script>

<div class="titulo">
  <i></i>
  {#await promise then promise}

    <div class="titulo_conteudo">
      <button type="submit" on:click={reduce} class="setaEsquerda"><i class="fas fa-caret-left" /></button>
    </div>

    <div class="titulo_conteudo">
      <div class="display_dia">
        {promise[index].diaSemana}
      </div>
    </div>

    <div class="titulo_conteudo">
      <button type="submit" on:click={add} class="setaDireita"><i class="fas fa-caret-right" /></button>
    </div>

  {/await}
</div>

<div class="conteudo">

  <div class="box_dia">

    <div class="indicador_dia">Dia</div>

    <div class="texto_temperatura">
      <p>Temp Mín</p>
      <p>Temp Média</p>
      <p>Temp Máx</p>
    </div>

    <div class="valor_temperatura">
      {#await promise then promise}
      <p>{(promise[index].tempMin + " F")}</p>
      {/await}

      {#await promise then promise}
      <p>{(promise[index].temp + " F")}</p>
      {/await}

      {#await promise then promise}
      <p>{(promise[index].tempMax + " F")}</p>
      {/await}
    </div>

    <div class="texto_vento">
      <p>Vento Mín</p>
      <p>Vento Médio</p>
      <p>Vento Máx</p>
    </div>

    <div class="valor_vento">
      {#await promise then promise}
      <p>{(promise[index].windMin + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise[index].windAvg + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise[index].windMax + " mph")}</p>
      {/await}
    </div>

  </div>

  <div class="box_noite">
  
    <div class="indicador_noite">Noite</div>
    
    <div class="texto_temperatura">
      <p>Temp Mín</p>
      <p>Temp Média</p>
      <p>Temp Máx</p>
    </div>

    <div class="valor_temperatura">
      {#await promise then promise}
      <p>{(promise[index+1].tempMin + " F")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise[index+1].temp + " F")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise[index+1].tempMax + " F")}</p>
      {/await}
    </div>

    <div class="texto_vento">
      <p>Vento Mín</p>
      <p>Vento Médio</p>
      <p>Vento Máx</p>
    </div>
  
    <div class="valor_vento">
      {#await promise then promise}
      <p>{(promise[index+1].windMin + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise[index+1].windAvg + " mph")}</p>
      {/await}
      {#await promise then promise}
      <p>{(promise[index+1].windMax + " mph")}</p>
      {/await}
    </div>
  
  </div>

</div>

<style>
  * {
    margin: 0;
    padding: 0;
  }
  .titulo {
    background-color: #e2e7e7;
    width: 100%;
    height: 10%;
    display: flex;
    justify-content: center;
    align-items: center;
    border-bottom: 2px solid rgb(68, 61, 61);
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
  .setaEsquerda, .setaDireita {
    background-color: #e2e7e7;
    border: 0;
    font-size: 20px;
    min-width: 50px;
  }
  .conteudo { 
    background-color: #a9dbf1;    
    min-height: 100vh;
    height: min-content;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
  }
  .box_dia, .box_noite {
    background-color: #e2e7e7;
    width: 350px;
    min-height: 350px;
    border-radius: 5px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    margin: 20px 0;
  }
  .valor_temperatura, .valor_vento, .texto_temperatura, .texto_vento{
    display: flex;
    width: 100%;
    flex-direction: row;
    justify-content: space-around;
    align-items: center;
    font-size: 20px;
    padding: 5% 0;
    border-bottom: 2px solid rgb(68, 61, 61);
  }
  .indicador_dia {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 20px;
    padding: 5% 0;
    background-image: url("../public/images/blue_sky.png");
    border-bottom: 2px solid rgb(68, 61, 61);
    color: white;
  }
  .indicador_noite {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 20px;
    padding: 5% 0;
    background-image: url("../public/images/night_sky.png");
    border-bottom: 2px solid rgb(68, 61, 61);
    color: white;
  }

</style>
