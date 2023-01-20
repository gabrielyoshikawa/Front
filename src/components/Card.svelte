<script>
    export let text;
</script>

<div>
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
</div>

<style>

</style>
   