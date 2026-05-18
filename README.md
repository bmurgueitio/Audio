<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>TTS Bloc</title>

<style>
body{
    margin:0;
    background:#111;
    color:white;
    font-family:sans-serif;
}

#topbar{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    padding:10px;
    background:#1b1b1b;
    box-sizing:border-box;
    display:flex;
    justify-content:flex-end;
    z-index:10;
}

button{
    background:#ff4444;
    color:white;
    border:none;
    padding:12px 18px;
    border-radius:10px;
    font-size:16px;
}

#editor{
    padding:90px 20px 40px 20px;
    min-height:100vh;
    box-sizing:border-box;
    font-size:22px;
    line-height:1.6;
    outline:none;
    white-space:pre-wrap;
}
</style>
</head>

<body>

<!-- Oculto para el TTS -->
<div id="topbar" aria-hidden="true">
    <button id="clearBtn">Eliminar todo</button>
</div>

<div
    id="editor"
    contenteditable="true"
    spellcheck="false"
></div>

<script>
const editor = document.getElementById("editor");
const clearBtn = document.getElementById("clearBtn");

// Cargar contenido guardado
editor.innerText = localStorage.getItem("tts_text") || "";

// Guardado automático
editor.addEventListener("input", () => {
    localStorage.setItem("tts_text", editor.innerText);
});

// Eliminar contenido
clearBtn.addEventListener("click", () => {

    const confirmar = confirm("¿Eliminar todo el texto?");

    if(confirmar){
        editor.innerText = "";
        localStorage.removeItem("tts_text");
    }

});
</script>

</body>
</html>
