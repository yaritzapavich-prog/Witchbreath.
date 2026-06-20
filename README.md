<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Witchbreath | Mercado Arcano</title>
    <link href="https://fonts.googleapis.com/css2?family=Cinzel+Decorative:wght@700&family=Playfair+Display:ital,wght@0,400;0,700;1,400&display=swap" rel="stylesheet">
    <style>
        /* Diseño visual: Fondo cósmico y modo oscuro */
        body {
            margin: 0;
            padding: 0;
            background-color: #05050a;
            background-image: 
                radial-gradient(circle at 15% 50%, rgba(76, 29, 149, 0.4), transparent 50%),
                radial-gradient(circle at 85% 30%, rgba(30, 58, 138, 0.4), transparent 50%),
                url('https://www.transparenttextures.com/patterns/stardust.png');
            color: #e0d0b8;
            font-family: 'Playfair Display', serif;
            min-height: 100vh;
        }

        /* Barra de navegación */
        header {
            text-align: center;
            padding: 2rem 0;
            background: rgba(0, 0, 0, 0.7);
            border-bottom: 2px solid #d4af37;
            box-shadow: 0 4px 20px rgba(212, 175, 55, 0.2);
        }

        h1 {
            font-family: 'Cinzel Decorative', cursive;
            font-size: 4rem;
            color: #d4af37;
            margin: 0;
            text-shadow: 0 0 15px rgba(212, 175, 55, 0.6), 0 0 30px rgba(138, 43, 226, 0.5);
            letter-spacing: 5px;
        }

        nav {
            margin-top: 1.5rem;
        }

        nav a {
            color: #d4af37;
            text-decoration: none;
            font-size: 1.2rem;
            margin: 0 20px;
            text-transform: uppercase;
            letter-spacing: 2px;
            transition: color 0.3s, text-shadow 0.3s;
            font-weight: bold;
        }

        nav a:hover {
            color: #fff;
            text-shadow: 0 0 10px #d4af37;
        }

        /* Contenedor principal y cuadrícula (4 artículos por fila en pantallas grandes) */
        main {
            max-width: 1400px;
            margin: 3rem auto;
            padding: 0 20px;
        }

        .category-title {
            font-family: 'Cinzel Decorative', cursive;
            color: #d4af37;
            font-size: 2.5rem;
            border-bottom: 1px solid rgba(212, 175, 55, 0.3);
            margin-top: 3rem;
            padding-bottom: 10px;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 2rem;
        }

        /* Tarjetas de productos (Dark Mode) */
        .card {
            background: rgba(20, 20, 30, 0.85);
            border: 1px solid #d4af37;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
            transition: transform 0.3s, box-shadow 0.3s;
            display: flex;
            flex-direction: column;
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0; bottom: 0;
            border: 2px solid transparent;
            border-radius: 8px;
            transition: border-color 0.3s;
            pointer-events: none;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(138, 43, 226, 0.4);
        }

        .card:hover::before {
            border-color: rgba(212, 175, 55, 0.5);
        }

        .card img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 4px;
            border-bottom: 2px solid #8a2be2;
            margin-bottom: 15px;
        }

        .card h3 {
            font-family: 'Cinzel Decorative', cursive;
            color: #fff;
            margin: 0 0 10px 0;
            font-size: 1.5rem;
        }

        .desc-fantasiosa {
            font-style: italic;
            color: #a9a9b3;
            font-size: 0.95rem;
            margin-bottom: 15px;
            line-height: 1.4;
        }

        /* Datos del Registro Algorítmico */
        .registro-datos {
            background: rgba(0, 0, 0, 0.5);
            padding: 15px;
            border-radius: 4px;
            border-left: 3px solid #d4af37;
            font-size: 0.9rem;
            flex-grow: 1;
        }

        .registro-datos p {
            margin: 5px 0;
            color: #ddd;
        }

        .registro-datos strong {
            color: #d4af37;
        }

        /* Etiquetas de Estado (Booleanos modelados) */
        .badge {
            padding: 3px 8px;
            border-radius: 4px;
            font-weight: bold;
            font-size: 0.85rem;
            text-transform: uppercase;
        }

        .seguro {
            color: #0f0;
            text-shadow: 0 0 5px #0f0;
            border: 1px solid #0f0;
        }

        .maldito {
            color: #ff3333;
            text-shadow: 0 0 10px #ff0000, 0 0 20px #ff0000;
            border: 1px solid #ff0000;
            background: rgba(255, 0, 0, 0.1);
        }

        .riesgo {
            color: #ffa500;
            text-shadow: 0 0 5px #ffa500;
            border: 1px solid #ffa500;
        }

        /* Botón de compra interactivo */
        .btn-comprar {
            background: linear-gradient(45deg, #4b3621, #8b6508);
            border: 1px solid #d4af37;
            color: #fff;
            font-family: 'Cinzel Decorative', cursive;
            font-size: 1.1rem;
            padding: 10px;
            margin-top: 15px;
            cursor: pointer;
            border-radius: 4px;
            transition: all 0.3s;
            text-transform: uppercase;
        }

        .btn-comprar:hover {
            background: linear-gradient(45deg, #8b6508, #d4af37);
            color: #000;
            box-shadow: 0 0 15px #d4af37;
        }

        /* Notificación mágica */
        #notificacion {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%) translateY(-100px);
            background: rgba(20, 0, 40, 0.95);
            border: 2px solid #8a2be2;
            color: #fff;
            padding: 15px 30px;
            border-radius: 30px;
            font-family: 'Cinzel Decorative', cursive;
            font-size: 1.2rem;
            box-shadow: 0 0 30px rgba(138, 43, 226, 0.8);
            opacity: 0;
            transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            z-index: 1000;
            pointer-events: none;
        }

        #notificacion.mostrar {
            transform: translateX(-50%) translateY(0);
            opacity: 1;
        }
    </style>
</head>
<body>

    <header>
        <h1>Witchbreath</h1>
        <nav>
            <a href="#alquimia">Alquimia</a>
            <a href="#armamento">Armamento</a>
            <a href="#artefactos">Artefactos</a>
            <a href="#reliquias">Reliquias</a>
        </nav>
    </header>

    <div id="notificacion">✨ ¡Artefacto reclamado con éxito! ✨</div>

    <main>
        <h2 id="alquimia" class="category-title">Alquimia</h2>
        <div class="grid">
            <div class="card">
                <img src="https://images.unsplash.com/photo-1572916962208-8e62d4750c60?q=80&w=400&auto=format&fit=crop" alt="Poción">
                <h3>Poción de Salud Mayor</h3>
                <p class="desc-fantasiosa">Destilada con lágrimas de fénix y rocío lunar. Restaura la vitalidad de la carne y repara las fracturas del espíritu.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ALQ-001</p>
                    <p><strong>Categoría:</strong> Alquimia</p>
                    <p><strong>Precio:</strong> 50.00 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1628155930542-3c7a64e2c848?q=80&w=400&auto=format&fit=crop" alt="Poción">
                <h3>Poción Amortentia</h3>
                <p class="desc-fantasiosa">El filtro de amor más poderoso conocido. Su aroma cambia según lo que más atraiga al que la huele.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ALQ-002</p>
                    <p><strong>Categoría:</strong> Alquimia</p>
                    <p><strong>Precio:</strong> 70.00 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1608682885974-b52964dd128e?q=80&w=400&auto=format&fit=crop" alt="Poción">
                <h3>Poción Multi Jugos</h3>
                <p class="desc-fantasiosa">Asume la forma de otro ser durante una hora. Advertencia: No mezclar con esencias de animales.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ALQ-003</p>
                    <p><strong>Categoría:</strong> Alquimia</p>
                    <p><strong>Precio:</strong> 75.50 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1519011985187-444d62641929?q=80&w=400&auto=format&fit=crop" alt="Polvo">
                <h3>Polvo de Hadas</h3>
                <p class="desc-fantasiosa">Recogido en el equinoccio. Un solo pellizco y pensamientos felices te harán levitar más allá de las nubes.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ALQ-004</p>
                    <p><strong>Categoría:</strong> Alquimia</p>
                    <p><strong>Precio:</strong> 75.50 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1599824647366-2679cbf260a9?q=80&w=400&auto=format&fit=crop" alt="Veneno">
                <h3>Extracto de Belladona</h3>
                <p class="desc-fantasiosa">Un veneno mortal y sutil, utilizado en oscuros rituales de nigromancia. Manipular con guantes de piel de dragón.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ALQ-005</p>
                    <p><strong>Categoría:</strong> Alquimia</p>
                    <p><strong>Precio:</strong> 90.00 Oro</p>
                    <p><strong>Stock:</strong> 4</p>
                    <p><strong>Estado:</strong> <span class="badge maldito">¡Maldito!</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
        </div>

        <h2 id="armamento" class="category-title">Armamento</h2>
        <div class="grid">
            <div class="card">
                <img src="https://images.unsplash.com/photo-1655182960683-176f18370162?q=80&w=400&auto=format&fit=crop" alt="Martillo">
                <h3>Mjolnir</h3>
                <p class="desc-fantasiosa">Forjado en el corazón de una estrella moribunda. Solo aquellos dignos de corazón podrán levantarlo.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ARM-001</p>
                    <p><strong>Categoría:</strong> Armamento</p>
                    <p><strong>Precio:</strong> 1500.00 Oro</p>
                    <p><strong>Stock:</strong> 1</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1589255659223-9366df044b70?q=80&w=400&auto=format&fit=crop" alt="Arco">
                <h3>Arco de Cupido</h3>
                <p class="desc-fantasiosa">Dispara flechas etéreas que no hieren la carne, sino que subyugan la voluntad y el corazón del objetivo.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ARM-002</p>
                    <p><strong>Categoría:</strong> Armamento</p>
                    <p><strong>Precio:</strong> 2000.00 Oro</p>
                    <p><strong>Stock:</strong> 1</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1590201131102-3c81e3381fc2?q=80&w=400&auto=format&fit=crop" alt="Espada">
                <h3>Espada de Fuego</h3>
                <p class="desc-fantasiosa">Su hoja arde con la llama eterna de los reinos inferiores. Ilumina las mazmorras más oscuras.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ARM-003</p>
                    <p><strong>Categoría:</strong> Armamento</p>
                    <p><strong>Precio:</strong> 700.00 Oro</p>
                    <p><strong>Stock:</strong> 3</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1542157585-ef20bfcce579?q=80&w=400&auto=format&fit=crop" alt="Sable">
                <h3>Sable de Luz</h3>
                <p class="desc-fantasiosa">Un arma elegante para una era más civilizada. Su haz de plasma corta a través de casi cualquier material conocido.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ARM-004</p>
                    <p><strong>Categoría:</strong> Armamento</p>
                    <p><strong>Precio:</strong> 900.00 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1605806616949-1e87b487bc2a?q=80&w=400&auto=format&fit=crop" alt="Espada Dragon">
                <h3>Espada de Dragón</h3>
                <p class="desc-fantasiosa">Tallada de los colmillos de un dragón anciano. Vibra cuando hay criaturas escamosas cerca.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ARM-005</p>
                    <p><strong>Categoría:</strong> Armamento</p>
                    <p><strong>Precio:</strong> 950.00 Oro</p>
                    <p><strong>Stock:</strong> 3</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1635398246476-85e78378c3c2?q=80&w=400&auto=format&fit=crop" alt="Tridente">
                <h3>Tridente de Poseidón</h3>
                <p class="desc-fantasiosa">Controla las mareas y desata tempestades. Tocarlo te permite respirar bajo el agua dulce o salada.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ARM-006</p>
                    <p><strong>Categoría:</strong> Armamento</p>
                    <p><strong>Precio:</strong> 3000.00 Oro</p>
                    <p><strong>Stock:</strong> 1</p>
                    <p><strong>Estado:</strong> <span class="badge riesgo">Riesgo</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
        </div>

        <h2 id="artefactos" class="category-title">Artefactos</h2>
        <div class="grid">
            <div class="card">
                <img src="https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?q=80&w=400&auto=format&fit=crop" alt="Mapa">
                <h3>Mapa del Merodeador</h3>
                <p class="desc-fantasiosa">Revela los secretos de los castillos. Muestra con exactitud la posición de cada alma errante dentro de sus muros.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ART-001</p>
                    <p><strong>Categoría:</strong> Artefactos</p>
                    <p><strong>Precio:</strong> 250.00 Oro</p>
                    <p><strong>Stock:</strong> 2</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1532012197267-da84d127e765?q=80&w=400&auto=format&fit=crop" alt="Libro">
                <h3>Grimorio de Hechizos</h3>
                <p class="desc-fantasiosa">Encuadernado en cuero desconocido. Sus páginas susurran cánticos olvidados cuando cae la noche.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ART-002</p>
                    <p><strong>Categoría:</strong> Artefactos</p>
                    <p><strong>Precio:</strong> 1000.00 Oro</p>
                    <p><strong>Stock:</strong> 5</p>
                    <p><strong>Estado:</strong> <span class="badge riesgo">Riesgo</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1582213782179-e0d53f98f2ca?q=80&w=400&auto=format&fit=crop" alt="Varita">
                <h3>Varita de Saúco</h3>
                <p class="desc-fantasiosa">La varita más poderosa de la historia. Dicen que su lealtad cambia solo a través del derramamiento de sangre.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ART-003</p>
                    <p><strong>Categoría:</strong> Artefactos</p>
                    <p><strong>Precio:</strong> 250.00 Oro</p>
                    <p><strong>Stock:</strong> 5</p>
                    <p><strong>Estado:</strong> <span class="badge riesgo">Riesgo</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1620062758151-5db0b08051df?q=80&w=400&auto=format&fit=crop" alt="Ouija">
                <h3>Tablero Ouija (A)</h3>
                <p class="desc-fantasiosa">Atrae espíritus impacientes. Nunca juegues solo, nunca lo uses en un cementerio y siempre despídete.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ART-004</p>
                    <p><strong>Categoría:</strong> Artefactos</p>
                    <p><strong>Precio:</strong> 250.00 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge maldito">¡Maldito!</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
             <div class="card">
                <img src="https://images.unsplash.com/photo-1620062758151-5db0b08051df?q=80&w=400&auto=format&fit=crop" alt="Ouija">
                <h3>Tablero Ouija (B)</h3>
                <p class="desc-fantasiosa">Edición portátil. Suelen responder almas mentirosas; usar sal y hierro para protección ocular.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ART-005</p>
                    <p><strong>Categoría:</strong> Artefactos</p>
                    <p><strong>Precio:</strong> 100.00 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge maldito">¡Maldito!</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1570303345338-e1f0eddf4946?q=80&w=400&auto=format&fit=crop" alt="Dado">
                <h3>Dado (Game of Thrones)</h3>
                <p class="desc-fantasiosa">Un dado de muchas caras tallado en hueso. Tirarlo define tu destino... o tu muerte instantánea en Poniente.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> ART-006</p>
                    <p><strong>Categoría:</strong> Artefactos</p>
                    <p><strong>Precio:</strong> 100.00 Oro</p>
                    <p><strong>Stock:</strong> 10</p>
                    <p><strong>Estado:</strong> <span class="badge maldito">¡Maldito!</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
        </div>

        <h2 id="reliquias" class="category-title">Reliquias</h2>
        <div class="grid">
            <div class="card">
                <img src="https://images.unsplash.com/photo-1618331835717-801e976710b2?q=80&w=400&auto=format&fit=crop" alt="Caja">
                <h3>La Caja de Pandora</h3>
                <p class="desc-fantasiosa">Contiene todos los males del mundo. Fue sellada por los dioses, se ruega encarecidamente no abrir bajo ningún motivo.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> REL-001</p>
                    <p><strong>Categoría:</strong> Reliquias</p>
                    <p><strong>Precio:</strong> 5000.00 Oro</p>
                    <p><strong>Stock:</strong> 2</p>
                    <p><strong>Estado:</strong> <span class="badge maldito">¡Maldito!</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1601370951403-34e85746f32e?q=80&w=400&auto=format&fit=crop" alt="Piedra">
                <h3>La Piedra Filosofal</h3>
                <p class="desc-fantasiosa">Transmuta cualquier metal en oro puro y produce el Elixir de la Vida. Brillante como un rubí ensangrentado.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> REL-002</p>
                    <p><strong>Categoría:</strong> Reliquias</p>
                    <p><strong>Precio:</strong> 10000.00 Oro</p>
                    <p><strong>Stock:</strong> 1</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1595156475475-407481ba9339?q=80&w=400&auto=format&fit=crop" alt="Diente">
                <h3>Diente de Dragón</h3>
                <p class="desc-fantasiosa">Cálido al tacto, extraído del temible Balerion. Es indestructible y una reliquia inestimable para coleccionistas.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> REL-003</p>
                    <p><strong>Categoría:</strong> Reliquias</p>
                    <p><strong>Precio:</strong> 10000.00 Oro</p>
                    <p><strong>Stock:</strong> 1</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
            <div class="card">
                <img src="https://images.unsplash.com/photo-1444158495047-920fbc8c7d6d?q=80&w=400&auto=format&fit=crop" alt="Capa">
                <h3>Capa de Invisibilidad</h3>
                <p class="desc-fantasiosa">Tejida con hilos de sombra e ilusión. Escóndete de los ojos del mundo terrenal y de la mismísima muerte.</p>
                <div class="registro-datos">
                    <p><strong>ID (Clave):</strong> REL-004</p>
                    <p><strong>Categoría:</strong> Reliquias</p>
                    <p><strong>Precio:</strong> 60.00 Oro</p>
                    <p><strong>Stock:</strong> 1</p>
                    <p><strong>Estado:</strong> <span class="badge seguro">Seguro (No maldito)</span></p>
                </div>
                <button class="btn-comprar" onclick="comprarItem()">Comprar</button>
            </div>
        </div>
    </main>

    <script>
        function comprarItem() {
            const notificacion = document.getElementById('notificacion');
            // Agregar la clase para mostrar
            notificacion.classList.add('mostrar');
            
            // Quitar la clase después de 3 segundos
            setTimeout(() => {
                notificacion.classList.remove('mostrar');
            }, 3000);
        }
    </script>
</body>
</html>
