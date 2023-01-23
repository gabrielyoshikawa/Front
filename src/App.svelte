<script>
  const testeFetch = async () => {
    const resp = await fetch("http://localhost:3000/");
    const resp2 = await resp.json();
    console.log(resp2)

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

    <div class="dia_noite">Dia</div>

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
  
    <div class="dia_noite">Noite</div>
    
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
    background-color: rgb(194, 193, 193);
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
    background-color: rgb(194, 193, 193);
    border: 0;
    font-size: 20px;
    min-width: 50px;
  }
  .conteudo { 
      background-image: linear-gradient(to right, #cdc9c9, #cfcccd, #d2d0d1, #d4d4d4, #d7d7d7);      
      min-height: 100vh;
      height: min-content;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
  }
  .box_dia, .box_noite {
    background-image: linear-gradient(to right, #a7a2a2, #a19b9b, #9b9595, #958e8e, #8f8888);      
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
  .dia_noite {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 20px;
    padding: 5% 0;
    background-color: rgb(177, 175, 175);
    border-bottom: 2px solid rgb(68, 61, 61);
  }
</style>
