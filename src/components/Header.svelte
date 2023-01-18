<script>
    function aaa() {
        alert("Teste");
    }
</script>

<div class="background">
    <div class="titulo"></div>
    <div class="menu">
        <button onclick="aaa()">ABC</button>
    </div>
    <div class="conteudo"></div>
</div>

<style>
    * {
        margin: 0;
        padding: 0;
        background-color: gray;
    }

    .background {
        height: 100vh;
        width: 100vw;
    }

    .titulo {
        background: yellow;
        height: 5%;
        width: 100%;
    }

    .menu {
        background: purple;
        float: left;
        height: 100%;
        width: 13%;
    }
    .conteudo {
        background: red;
        float: left;
        height: 100%;
        width: 87%;
    }
</style>