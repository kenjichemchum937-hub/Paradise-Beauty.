<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lista de Productos</title>

    <link rel="stylesheet" href="estilosp.css">
</head>

<body>

    <!-- ENCABEZADO -->

    <header>

        <h1>Paradise Beauty</h1>

        <nav>
            <a href="Pagina.html">Inicio</a>
            <a href="Productos.html">Productos</a>
            <a href="Bolsa de compras.html">Bolsa de Compras</a>
            <a href="Contacto.html">Contacto</a>
        </nav>

    </header>

    <!-- TITULO -->

    <section class="titulo-productos">

        <h2>Catálogo de Maquillaje</h2>

        <p>
            Descubre todos nuestros productos de belleza.
        </p>

    </section>

    <!-- LISTA DE PRODUCTOS -->

    <section class="lista-productos">

        <div class="tarjeta">
            <img src="img_p/Balsamo.jpeg" alt="Balsamo ">
            <h3>Balsamo con diseño de fresa</h3>
            <p>Balsamo con diseño, colo y sabor de  fresa.</p>
            <button onclick="agregarAlCarrito('Balsamo',20)">
                Agregar al carrito
            </button>
        </div>

        <div class="tarjeta">
            <img src="img_p/Barniz.jpeg" alt="Barniz de uñas">
            <h3>Barniz de uñas marca bissú</h3>
            <p>$45 MXN</p>
            <button onclick="agregarAlCarrito('Barniz de uñas',45)">
                Agregar al carrito
            </button>
        </div>

        <div class="tarjeta">
            <img src="img_p/sombras.jpeg" alt="Paleta de sombras con diseño de bts">
            <h3>Paleta de Sombras con diseño de bts</h3>
            <p>$120 MXN</p>
            <button onclick="agregarAlCarrito('Paleta de Sombras',120)">
                Agregar al carrito
            </button>
        </div>

        <div class="producto">
            <img src="img_p/brochas.jpeg" alt="Kit de brochas">
            <h3>Kit de Brochas</h3>
            <p>$35 MXN</p>
            <button onclick="agregarAlCarrito('Kit de Brochas',35)">
                Agregar al carrito
            </button>
        </div>

        <div class="producto">
            <img src="img_p/Rubores.jpeg" alt="Rubor">
            <h3>Rubor Rosado</h3>
            <p>$60 MXN</p>
            <button onclick="agregarAlCarrito('Rubor',60)">
                Agregar al carrito
            </button>
        </div>

        <div class="producto">
            <img src="img_p/rimel.jpeg" alt="Rímel">
            <h3>Rímel Explosiva y Exactitud</h3>
            <p>$50 MXN</p>
            <button onclick="agregarAlCarrito('Rimel',50)">
                Agregar al carrito
            </button>
        </div>

        <div class="producto">
            <img src="img_p/delineador.jpeg" alt="Delineador">
            <h3>Delineador Negro</h3>
            <p>$35 MXN</p>
            <button onclick="agregarAlCarrito('Delineador',35)">
                Agregar al carrito
            </button>
        </div>

        <div class="producto">
            <img src="img_p/corrector.jpeg" alt="Corrector">
            <h3>Corrector HD</h3>
            <p>$75 MXN</p>
            <button onclick="agregarAlCarrito('Corrector',75)">
                Agregar al carrito
            </button>
        </div>

        <div class="producto">
            <img src="img_p/primer.jpeg" alt="Primer">
            <h3>Primer Facial</h3>
            <p>$160 MXN</p>
            <button onclick="agregarAlCarrito('Rubor',160)">
                Agregar al carrito
            </button>
        </div>

        <div class="producto">
            <img src="img_p/fijador.jpeg" alt="Spray fijador">
            <h3>Spray Fijador de maquillaje</h3>
            <p>$70 MXN</p>
            <button onclick="agregarAlCarrito('Spray fijador',70)">
                Agregar al carrito
            </button>
        </div>

    </section>

    <!-- CARRITO -->
<div class="carrito">
    <h2>Carrito de Compras</h2>
    <ul id="carrito"></ul>
    <h3>Total: $<span id="total">0</span></h3>
    <button onclick="vaciarCarrito()">
        Vaciar carrito
    </button>
    <br><br>
    <a href="Bolsa de compras.html" class="boton-carrito">
        Ir a mi bolsa de compras
    </a>
</div>    
    <!-- FOOTER -->

    <footer>

        <p>
            © 2026 Paradise Beauty |
            Todos los derechos reservados
        </p>

    </footer>
<script>

    function agregarAlCarrito(nombre, precio){

        let carrito =
        JSON.parse(localStorage.getItem("carrito")) || [];

        carrito.push({
            nombre: nombre,
            precio: precio
        });

        localStorage.setItem(
            "carrito",
            JSON.stringify(carrito)
        );

        mostrarCarrito();
    }

    function mostrarCarrito(){

        let carrito =
        JSON.parse(localStorage.getItem("carrito")) || [];
        const lista =
        document.getElementById("carrito");
        lista.innerHTML = "";
        let total = 0;
        if(carrito.length === 0){
            let li =
            document.createElement("li");
            li.textContent =
            "No hay productos en el carrito.";
            lista.appendChild(li);
        }
        carrito.forEach(item => {
            let li =
            document.createElement("li");
            li.textContent =
            item.nombre + " - $" + item.precio;
            lista.appendChild(li);
            total += item.precio;
        });
        document.getElementById("total")
        .textContent = total;
    }
    function vaciarCarrito(){
        localStorage.removeItem("carrito");
        mostrarCarrito();
    }
    mostrarCarrito();
</script>
</body>
</html>
