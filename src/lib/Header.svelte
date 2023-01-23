<script>

  const testeFetch = async () => {
    const resp = await fetch("http://localhost:3000/");
    const resp2 = await resp.json();

    return resp2;
  };

  const promise = testeFetch();

  function aaa() {
    alert('aaa');
  }

</script>

<div class="titulo">
    
  <div class="titulo_conteudo">
    <button type="submit" on:click={aaa} class="setaEsquerda"><i class="fas fa-caret-left"></i></button>
  </div>

  <div class="titulo_conteudo">
    <div class="display_dia">
      {#await promise then promise}
      {(promise.Friday.dayName)}
      {/await}
    </div>
  </div>

  <div class="titulo_conteudo">
    <button type="submit" on:click={aaa} class="setaDireita"><i class="fas fa-caret-right"></i></button>
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
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: rgb(194, 193, 193);
      /* border: 0; */
      font-size: 20px;
      padding-right: 5%;
      padding-left: 5%;
    }

</style>