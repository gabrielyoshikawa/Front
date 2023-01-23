<script>

    const testeFetch = async () => {
        const resp = await fetch("http://localhost:3000/");
        const resp2 = await resp.json();
        console.log(resp2);

        return resp2;
    };

const promise = testeFetch();

</script>

<div class="conteudo">

    <div class="box_dia">
  
      <div class="dia_noite">Dia</div>
  
      <div class="texto_temperatura">
        <p>Temp Mín</p>
        <p>Temp Atual</p>
        <p>Temp Máx</p>
      </div>
  
      <div class="valor_temperatura">
        {#await promise then promise}
        <p>{(promise.Friday.tempMin + " F")}</p>
        {/await}
  
        {#await promise then promise}
        <p>{(promise.Friday.temp + " F")}</p>
        {/await}
  
        {#await promise then promise}
        <p>{(promise.Friday.tempMax + " F")}</p>
        {/await}
      </div>
  
      <div class="texto_vento">
        <p>Wind Mín</p>
        <p>Wind Atual</p>
        <p>Wind Máx</p>
      </div>
  
      <div class="valor_vento">
        {#await promise then promise}
        <p>{(promise.Friday.windMin + " mph")}</p>
        {/await}
        {#await promise then promise}
        <p>{(promise.Friday.windAvg + " mph")}</p>
        {/await}
        {#await promise then promise}
        <p>{(promise.Friday.windMax + " mph")}</p>
        {/await}
      </div>
  
    </div>
  
    <div class="box_noite">
    
      <div class="dia_noite">Noite</div>
      
      <div class="texto_temperatura">
        <p>Temp Mín</p>
        <p>Temp Atual</p>
        <p>Temp Máx</p>
      </div>
  
      <div class="valor_temperatura">
        {#await promise then promise}
        <p>{(promise["Friday Night"].tempMin + " F")}</p>
        {/await}
        {#await promise then promise}
        <p>{(promise["Friday Night"].temp + " F")}</p>
        {/await}
        {#await promise then promise}
        <p>{(promise["Friday Night"].tempMax + " F")}</p>
        {/await}
      </div>
  
      <div class="texto_vento">
        <p>Wind Mín</p>
        <p>Wind Atual</p>
        <p>Wind Máx</p>
      </div>
    
      <div class="valor_vento">
        {#await promise then promise}
        <p>{(promise["Friday Night"].windMin + " mph")}</p>
        {/await}
        {#await promise then promise}
        <p>{(promise["Friday Night"].windAvg + " mph")}</p>
        {/await}
        {#await promise then promise}
        <p>{(promise["Friday Night"].windMax + " mph")}</p>
        {/await}
      </div>
    
    </div>
  
  </div>

  <style>

    .conteudo { 
      background-image: linear-gradient(to right, #cdc9c9, #cfcccd, #d2d0d1, #d4d4d4, #d7d7d7);      
      min-height: 100vh;
      height: fit-content;
      width: 100%;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      align-items: center;
    }

    .box_dia, .box_noite {
      background-image: linear-gradient(to right, #a7a2a2, #a19b9b, #9b9595, #958e8e, #8f8888);      
      width: 350px;
      height: 450px;
      border-radius: 5px;
      display: flex;
      flex-direction: column;
      justify-content: space-evenly;
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