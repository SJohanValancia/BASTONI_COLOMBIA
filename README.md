<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BASTONI - Bienvenida</title>
    <style>
        /* Estilos generales */
        body {
            margin: 0;
            padding: 0;
            background-color: #000; 
            color: #fff;
            font-family: Arial, sans-serif;
        }

        /* Estilos del pop-up */
        #popup, #second-popup, #shirt-popup, #pagos, #nequi, #daviplata{
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
        }
        
        #finn{
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            }

        #confirmacion{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.8);
        display: none;
        justify-content: center;
        align-items: center;
        z-index: 1000;
        }
    
        .pop-envio{
       
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.8);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
        }
        /* Caja del pop-up */
        #popup-content, #second-popup-content, #shirt-popup-content {
            background: linear-gradient(135deg, #4d4d4d, #7f7f7f);
            border: 2px solid #fff;
            padding: 30px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.2);
            width: 350px;
            height: auto;
        }

        /* Título en blanco neón */
        h1 {
            color: #ffffff;
            text-shadow: 0 0 10px #ffffff;
            margin-bottom: 20px;
        }

        p {
            color: #ffffff;
            margin-bottom: 10px;
        }

        /* Estilos del input */
        .input-container {
            position: relative;
            width: 100%;
            text-align: center;
            margin-bottom: 20px;
        }

        .input-line {
            width: 0;
            border-bottom: 2px solid #fff;
            margin: 0 auto;
            transition: width 0.5s ease-in-out;
        }

        input[type="text"], input[type="email"] {
            border: none;
            outline: none;
            background: none;
            color: white;
            font-size: 20px;
            padding: 10px;
            opacity: 0;
            transition: opacity 0.5s ease-in-out;
        }

        input[type="text"]:focus + .input-line, input[type="email"]:focus + .input-line {
            width: 200px;
        }

        input[type="text"]:focus, input[type="email"]:focus {
            opacity: 1;
        }

        /* Estilos del botón de enviar */
        button {
            padding: 17px 40px;
            border-radius: 50px;
            cursor: pointer;
            border: 0;
            background-color: white;
            box-shadow: rgb(0 0 0 / 5%) 0 0 8px;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            font-size: 15px;
            transition: all 0.5s ease;
            margin-top: 20px;
        }

        button:hover {
            letter-spacing: 3px;
            background-color: hsl(261deg 80% 48%);
            color: hsl(0, 0%, 100%);
            box-shadow: rgb(93 24 220) 0px 7px 29px 0px;
        }

        button:active {
            letter-spacing: 3px;
            background-color: hsl(261deg 80% 48%);
            color: hsl(0, 0%, 100%);
            box-shadow: rgb(93 24 220) 0px 0px 0px 0px;
            transform: translateY(10px);
            transition: 100ms;
        }

        
        /* Animación de cerrar pop-up */
        #popup.closing, #second-popup.closing, #shirt-popup.closing {
            animation: closePopup 0.6s forwards;
        }

        @keyframes closePopup {
            0% {
                transform: scaleY(1);
            }
            100% {
                transform: scaleY(0);
            }
        }

        /* Estilos del catálogo */
        #catalog {
            display: none;
            padding: 20px;
            text-align: center;
            
        }

        .shirt {
            margin: 20px;
            border: 1px solid #d3b86f;
            padding: 10px;
            border-radius: 5px;
            width: 250px; /* Aumentar el ancho del cuadro de la camisa */
            height: 400px; /* Aumentar la altura del cuadro de la camisa */
            display: inline-block;
            cursor: pointer;
            transition: transform 0.3s;
            position: relative; /* Para el precio */
            margin-top: 3cm; /* Elevar 3 cm hacia abajo */
            overflow: hidden; /* Para ocultar el precio cuando no esté visible */
            background-image: linear-gradient(144deg,#d0d177, #45415c 50%,#a8c0c2);
        }

        .shirt img {
            width: 100%;
            height: auto; /* Mantener la proporción de la imagen */
            border-radius: 5px;
            transition: transform 0.3s ease; 
        }

        
        .shirt:hover {
            transform: translateY(-2cm); /* Elevar el cuadrado al pasar el cursor */
        }

        /* Estilos para el precio */
        .price {
            color: #fff; /* Cambiar a blanco */
            font-size: 18px;
            margin-top: 10px;
            position: absolute; /* Para posicionar el precio */
            bottom: -3cm; /* Ajusta esto para mover el precio hacia abajo */
            left: 0;
            right: 0;
            text-align: center;
            opacity: 0; /* Inicialmente oculto */
            transition: opacity 0.3s; /* Efecto de aparición */
        }
        
        #camisa {
            color: #000; /* Cambiar a blanco */
            font-size: 18px;
            margin-top: 10px;
            position: absolute; /* Para posicionar el precio */
            bottom: -50; /* Ajusta esto para mover el precio hacia abajo */
            left: 0;
            right: 0;
            text-align: center;
    
        }
        
        



        .shirt:hover .price {
            opacity: 1; /* Mostrar el precio al pasar el cursor */
            bottom: 4cm; /* Mover el precio hacia arriba un poco cuando se eleva */
        }

        .rating {
            display: inline-block;
          }
          
          .rating input {
            display: none;
          }
          
          .rating label {
            float: right;
            cursor: pointer;
            color: #ccc;
            transition: color 0.3s;
          }
          
          .rating label:before {
            content: '\2605';
            font-size: 30px;
          }
          
          .rating input:checked ~ label,
          .rating label:hover,
          .rating label:hover ~ label {
            color: #6f00ff;
            transition: color 0.3s;
          }

        /* Estilos para el pop-up de la camisa */
        #shirt-popup-content {
            
            width: 150 px;
            display: flex;
            justify-content: space-between;
            align-items: center; 
            
            
           
            
        }

        #shirt-popup-content img {
            width: 150px;
            margin-right: 20px;
            
        }

        .size-selector {
            margin-top: 20px;
            text-align: left;
            
        }

        .quantity-selector {
            margin-top: 20px;
            text-align: left;
           
        }

        /* Estilos del mensaje de error */
        #error-message {
            color: red;
            display: none;
            margin-top: 10px;
        }
        
 
        /* Estilos para las opciones de tallas */
        .size-option {
            display: inline-block;
            width: 30px;
            height: 30px;
            border: 2px solid white;
            border-radius: 50%;
            line-height: 30px;
            text-align: center;
            cursor: pointer;
            margin-right: 10px;
            transition: all 0.3s;
        }

        .size-option.selected {
            background-color: white;
            color: black;
        }

        button {
            padding: 17px 40px;
            border-radius: 50px;
            cursor: pointer;
            border: 0;
            background-color: white;
            box-shadow: rgb(0 0 0 / 5%) 0 0 8px;
            letter-spacing: 1.5px;
            text-transform: uppercase;
            font-size: 15px;
            transition: all 0.5s ease;
            margin-top: 20px;
        }

        /* === removing default button style ===*/
.button {
    margin: 0;
    height: auto;
    background: transparent;
    padding: 0;
    border: none;
    cursor: pointer;
  }
  
  /* button styling */
  .button {
    --border-right: 6px;
    --text-stroke-color: rgba(255,255,255,0.6);
    --animation-color: #37FF8B;
    --fs-size: 2em;
    letter-spacing: 3px;
    text-decoration: none;
    font-size: var(--fs-size);
    font-family: "Arial";
    position: relative;
    text-transform: uppercase;
    color: transparent;
    -webkit-text-stroke: 1px var(--text-stroke-color);
  }
  /* this is the text, when you hover on button */
  .hover-text {
    position: absolute;
    box-sizing: border-box;
    content: attr(data-text);
    color: var(--animation-color);
    width: 0%;
    inset: 0;
    border-right: var(--border-right) solid var(--animation-color);
    overflow: hidden;
    transition: 0.5s;
    -webkit-text-stroke: 1px var(--animation-color);
  }
  /* hover */
  .button:hover .hover-text {
    width: 100%;
    filter: drop-shadow(0 0 23px var(--animation-color))
    
  }
     /* seccion de envios */
     
     #payment-section {
      
        margin: 0;
        padding: 0;
        box-sizing: border-box;
        font-family: 'Segoe UI', sans-serif;
    }

    body {
        background: linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 20px;
        color: #fff;
    }

    .shipping-form {
        width: 100%;
        max-width: 800px;
        background: rgba(15, 23, 42, 0.6);
        backdrop-filter: blur(10px);
        border-radius: 20px;
        border: 1px solid rgba(255, 255, 255, 0.1);
        padding: 40px;
        box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
    }

    h2 {
        font-size: 1.8em;
        margin-bottom: 30px;
        color: #60a5fa;
        text-align: center;
    }

    .form-grid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 20px;
    }

    .full-width {
        grid-column: 1 / -1;
    }

    .form-group {
        margin-bottom: 20px;
    }

    label {
        display: block;
        margin-bottom: 8px;
        color: #94a3b8;
        font-size: 0.9em;
    }

    input, select, textarea {
        width: 100%;
        padding: 12px 16px;
        background: rgba(15, 23, 42, 0.8);
        border: 1px solid rgba(255, 255, 255, 0.1);
        border-radius: 8px;
        color: white;
        font-size: 1em;
        transition: all 0.3s ease;
    }

    input:focus, select:focus, textarea:focus {
        outline: none;
        border-color: #3b82f6;
        box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.3);
    }

    textarea {
        resize: vertical;
        min-height: 100px;
    }

    .submit-btn {
        background: #3b82f6;
        color: white;
        border: none;
        padding: 15px 30px;
        border-radius: 8px;
        cursor: pointer;
        font-size: 1em;
        transition: all 0.3s ease;
        width: 100%;
        margin-top: 20px;
    }

    .submit-btn:hover {
        background: #2563eb;
        transform: translateY(-2px);
    }

    @media (max-width: 768px) {
        .form-grid {
            grid-template-columns: 1fr;
        }

        .shipping-form {
            padding: 20px;
        }
    }

    .tipo-envio {
        display: flex;
        gap: 15px;
        margin-bottom: 20px;
    }

    .tipo-envio label {
        display: flex;
        align-items: center;
        gap: 5px;
        cursor: pointer;
    }

    .tipo-envio input[type="radio"] {
        width: auto;
    }

    .card {
        background: rgba(30, 41, 59, 0.5);
        padding: 15px;
        border-radius: 8px;
        margin-top: 20px;
    }

    
    
    
      .close-button {
       
        
        position: absolute;
        top: 20px;
        right: 20px;
        background: none;
        border: none;
        color: white;
        font-size: 24px;
        cursor: pointer;
      }

        
        
    

    .input-container {
      position: relative;
  padding: 20px 0 0;
  width: 100%;
  max-width: 180px;
}

#name-input{
  font-family: inherit;
  width: 100%;
  border: none;
  border-bottom: 2px solid #9b9b9b;
  outline: 0;
  font-size: 17px;
  color: #fff;
  padding: 7px 0;
  background: transparent;
  transition: border-color 0.2s;
}

#name-input::placeholder {
  color: transparent;
}

#name-input:placeholder-shown ~ .form__label {
  font-size: 17px;
  cursor: text;
  top: 20px;
}

.form__label {
  position: absolute;
  top: 0;
  display: block;
  transition: 0.2s;
  font-size: 17px;
  color: #9b9b9b;
  pointer-events: none;
}

#name-input:focus {
  padding-bottom: 6px;
  font-weight: 700;
  border-width: 3px;
  border-image: linear-gradient(to right, #116399, #38caef);
  border-image-slice: 1;
}

#name-input:focus ~ .form__label {
  position: absolute;
  top: 0;
  display: block;
  transition: 0.2s;
  font-size: 17px;
  color: #38caef;
  font-weight: 700;
}

/* reset input */


    input[type="text"] {
        width: 100%;
        padding: 10px;
        border: 1px solid #fff;
        border-radius: 5px;
        background: none;
        color: white;
    }

    button {
        padding: 10px 20px;
        border: none;
        border-radius: 5px;
        background-color: #fff;
        color: #000;
        cursor: pointer;
        transition: background-color 0.3s;
    }

    button:hover {
        background-color: hsl(261deg 80% 48%);
        color: white;
    }
  
    img.logo {
        width: 20px;
        height: 20px;
      filter:  drop-shadow(
        0 0 10px rgba(0, 0, 0, .8)
      );
    }
    
    .form__group {
      position: relative;
      padding: 20px 0 0;
      width: 100%;
      max-width: 180px;
    }
    
    #quantity-input {
      font-family: inherit;
      width: 100%;
      border: none;
      border-bottom: 2px solid #9b9b9b;
      outline: 0;
      font-size: 17px;
      color: #fff;
      padding: 7px 0;
      background: transparent;
      transition: border-color 0.2s;
    }
    
    #quantity-input::placeholder {
      color: transparent;
    }
    
    #quantity-input:placeholder-shown ~ .form__label {
      font-size: 17px;
      cursor: text;
      top: 20px;
    }
    
    .form__label {
      position: absolute;
      top: 0;
      display: block;
      transition: 0.2s;
      font-size: 17px;
      color: #9b9b9b;
      pointer-events: none;
    }
    
    #quantity-input:focus {
      padding-bottom: 6px;
      font-weight: 700;
      border-width: 3px;
      border-image: linear-gradient(to right, #116399, #38caef);
      border-image-slice: 1;
    }
    
    #quantity-input:focus ~ .form__label {
      position: absolute;
      top: 0;
      display: block;
      transition: 0.2s;
      font-size: 17px;
      color: #38caef;
      font-weight: 700;
    }
    
    /* reset input */


    .form__group {
      position: relative;
      padding: 20px 0 0;
      width: 100%;
      max-width: 180px;
    }
    
    .form__field {
      font-family: inherit;
      width: 100%;
      border: none;
      border-bottom: 2px solid #9b9b9b;
      outline: 0;
      font-size: 17px;
      color: #fff;
      padding: 7px 0;
      background: transparent;
      transition: border-color 0.2s;
    }
    
    .form__field::placeholder {
      color: transparent;
    }
    
    .form__field:placeholder-shown ~ .form__label {
      font-size: 17px;
      cursor: text;
      top: 20px;
    }
    
    .form__label {
      position: absolute;
      top: 0;
      display: block;
      transition: 0.2s;
      font-size: 17px;
      color: #9b9b9b;
      pointer-events: none;
    }
    
    .form__field:focus {
      padding-bottom: 6px;
      font-weight: 700;
      border-width: 3px;
      border-image: linear-gradient(to right, #116399, #38caef);
      border-image-slice: 1;
    }
    
    .form__field:focus ~ .form__label {
      position: absolute;
      top: 0;
      display: block;
      transition: 0.2s;
      font-size: 17px;
      color: #38caef;
      font-weight: 700;
    }
    


    /* Estilos base y reset */
#carrito {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* Overlay (fondo oscuro) */
.overlay {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(3px);
    z-index: 998;
    transition: all 0.3s ease;
}

/* Sidebar del carrito */
.cart-sidebar {
    position: fixed;
    top: 0;
    right: -400px;
    width: 700px;
    height: 100%;
    background: linear-gradient(145deg, #1a1a1a, #2d2d2d);
    box-shadow: -5px 0 15px rgba(0, 0, 0, 0.3);
    z-index: 999;
    transition: all 0.3s ease;
    color: #fff;
}

.cart-sidebar.active {
    right: 0;
}

/* Encabezado del carrito */
.cart-header {
    padding: 20px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(103, 58, 183, 0.1);
}

.cart-header h2 {
    font-size: 1.5rem;
    font-weight: 500;
    color: #673AB7;
}

.close-btn {
    background: none;
    border: none;
    color: #673AB7;
    font-size: 2rem;
    cursor: pointer;
    transition: all 0.2s ease;
}

.close-btn:hover {
    color: #9575CD;
}

/* Contenedor de items */
.cart-items {
    padding: 20px;
    overflow-y: auto;
    max-height: calc(100% - 200px);
}

/* Estilos para cada item */
.cart-item {
    display: flex;
    align-items: center;
    padding: 15px;
    margin-bottom: 15px;
    background: rgba(255, 255, 255, 0.05);
    border-radius: 10px;
    transition: all 0.2s ease;
}

.cart-item:hover {
    background: rgba(103, 58, 183, 0.1);
}

.item-image {
    width: 80px;
    height: 80px;
    border-radius: 8px;
    object-fit: cover;
    margin-right: 15px;
}

.item-details {
    flex: 1;
}

.item-details h3 {
    font-size: 1rem;
    margin-bottom: 5px;
}

.item-price {
    color: #673AB7;
    font-weight: 600;
    margin-bottom: 8px;
}

/* Controles de cantidad */
.quantity-controls {
    display: flex;
    align-items: center;
    gap: 10px;
}

.qty-btn {
    background: rgba(103, 58, 183, 0.2);
    border: none;
    color: #fff;
    width: 25px;
    height: 25px;
    border-radius: 50%;
    cursor: pointer;
    transition: all 0.2s ease;
}

.qty-btn:hover {
    background: #673AB7;
}

.remove-btn {
    background: none;
    border: none;
    color: #ff4444;
    font-size: 1.5rem;
    cursor: pointer;
    padding: 5px;
}

/* Footer del carrito */
.cart-footer {
    position: absolute;
    bottom: 0;
    width: 100%;
    padding: 20px;
    background: rgba(0, 0, 0, 0.2);
    border-top: 1px solid rgba(255, 255, 255, 0.1);
}

.subtotal {
    display: flex;
    justify-content: space-between;
    margin-bottom: 15px;
    font-size: 1.1rem;
}

.subtotal-amount {
    color: #673AB7;
    font-weight: 600;
}

.checkout-btn {
    width: 100%;
    padding: 15px;
    background: #673AB7;
    border: none;
    color: white;
    border-radius: 8px;
    cursor: pointer;
    font-size: 1rem;
    font-weight: 500;
    transition: all 0.2s ease;
}

.checkout-btn:hover {
    background: #9575CD;
}

/* Scrollbar personalizado */
.cart-items::-webkit-scrollbar {
    width: 8px;
}

.cart-items::-webkit-scrollbar-track {
    background: rgba(255, 255, 255, 0.1);
}

.cart-items::-webkit-scrollbar-thumb {
    background: #673AB7;
    border-radius: 4px;
    
}

    </style>

    
</head>
<body>
    

    
        <div id="daviplata">
        <img src="logo-de-bastoni.png" alt="logo" class="daviplata">
        <center>
        <p>el QR estara disponible en unos dias <br> </p>
        <p> mientras tanto puede mandar el dinero al 3225949495</p>
 
        <button id="btn" onclick="atras()">oprima este boton una vez haya pagado
            luego oprima confirmar dirección de envio
        </button>
    </center>


    </div>
    

    
        <div id="nequi">
        <img src="nequi.jpg" alt="logo" class="nequi">
        <center>
            <p> si da la casualidad de que el QR no Funciona <br> </p>
            <p> puede mandar el dinero al 3225949495</p>
        <button id="btn" onclick="atras()">oprima este boton una vez haya pagado
            luego oprima confirmar dirección de envio
        </button>
    </center>

    </div>
    

    <div id="pagos">
        <div id="popup-content">

        <h1>CON QUE DESEA PAGAR </h1>
        <p>recuerde que el precio a pagar seria de 75.000 (valor de la prenda)</p>
        <p>+</p>
        <p>15.000 (valor del envio)</p>
        <p> TOTAL = 90.000 (esto mandara al nequi o daviplata que escoja)</p>
        <p>porfavor poner en mensaje (BASTONI)</p>

        <p style="color: #37FF8B;">para envios desde banco davivienda o bancolombia mandarlos al 3225949495 (tambien sirve para nequi y daviplata)</p>

    <div>
        <button class="btn" id="daviPlata" onclick="daviplata()">daviPlata </button>
        <button class="btn" id="daviPlata" onclick="nequi()">nequi </button>
    </div>

    </div>
</div>
    
    <div class="overlay" id="overlay"></div>
    <div class="cart-sidebar" id="cart-sidebar2" style="display: none;" >
        <div class="cart-header">
            
            <button class="btn" onclick="salirCarrito()" id="salir">x </button>
            <h1>TUS PRODUCTOS SE VEN AQUI</h1>
            

        </div>
        
       
    </div>
</div>

  <center>
  <div id="pop-envio">
    <div id="popup-content">
      <h1>RECUERDA</h1>
        <P>EN BASTONI LOS ENVIOS SON GRATIS A PARTIR DE 2 PRENDAS O MAS , Y LO MEJOR, PUEDES DECIDIR SI PAGAS CUANDO RECIBES TU PRENDA Ó DESEAS PAGAR DE UNA VEZ </P>

        <P>lo hicimos asi, para que confies en nosotros. </P>

        <p style="color: springgreen;">BASTONI: sinonimo de confianza</p>
          <button id="btn" onclick="recuerda()">SEGUIR</button>
    </div>
</div>
</center>

    <!-- Primer pop-up -->
    <div id="popup">
        <div id="popup-content">
            <h1>BIENVENIDOS a BASTONI</h1>
             <p>Ingrese su nombre:</p>
            <div class="input-container">
              <div class="form__group field">
                <input type="input" id="name-input" placeholder="Name" required="">
                <label for="name" class="form__label">Nombre</label>
            </div>
            </div>

            <div class="input-container">
                

            </div>
            <div id="error-message">Esto es necesario para una mejor experiencia, y pueda estar al tanto de las mejores ofertas que vayamos a tener.</div>
              <button id="submit-button" onclick="verCatalogo()">Enviar</button>
        </div>
    </div>

    <!-- Segundo pop-up -->
    <div id="second-popup" style="display:none;">
        <div id="second-popup-content">
            <h1 id="welcome-message"></h1>
            <p>Usted es uno de los afortunados en probar la página web por primera vez.</p>
            <button id="btn" onclick="mostrarCatalogo()">Ver catálogo</button>
        </div>
    </div>

    <!-- Sección del catálogo -->
     
    <div id="catalog"><center>
        
      
        <body>
            <img src="logo-de-bastoni.png" alt="logo" class="img.logo">
        </body>
         
       
       
        <h1>COLECCIÓN</h1>
    
        
        <div id="camisa1" class="shirt" onclick="verCamisa('cruz-frente.jpg', 'Esta camisa fue diseñada con el fin de expresar que debemos dejar los miedos atrás, fracasar no es haberlo hecho mal, fracasar es no haberlo intentado.')">
            <img id="img" src="cruz.jpg" alt="Camisa 1">
            <p class="price"></p>
            <p id="camisa" class="camisa">EL MIEDO ES LO PEOR </p>
            
            
        </div>

        <div id="camisa2" class="shirt" onclick="verCamisa('aguila-de-frente.jpg', 'Esta camisa fue dieñada con el fin de demostrarnos que los sueños se buscan no se esperan, por eso nunca debemos de rendirnos.')">
            <img id="img" src="aguila.jpg" alt="Camisa 2">
            <p class="price"></p>
            <p id="camisa" class="camisa">NUNCA TE RINDAS, LO VAS A LOGRAR</p>
            
        </div>  

        <div id="camisa3" class="shirt" onclick="verCamisa('tiempo_de_frente.jpg', 'Esta camisa fue diseñada para demostrar lo mucho que vale el tiempo, que debemos de disfrutar cada momento con nuestros seres queridos, y haciendo lo que nos gusta .')">
            <img id="img" id="img" src="tiempo.jpg" alt="Camisa 3">
            <p class="price"></p>
            <p id="camisa" class="camisa">NO PERMITAS QUE SE TE ACABE EL TIEMPO</p>
            
        </div> 
        <div id="camisa4" class="shirt" onclick="verCamisa('estres-de-frente.jpg', 'Esta camisa fue diseñada con el fin de demostrarnos una gran solucion al estres y la ansiedad, agradecer por todo lo bueno que tenemos, que muchos desearian tener y no pueden.')">
            <img id="img" src="estres.jpg" alt="Camisa 4">
            <p class="price"></p>
            <p id="camisa" class="camisa">VALORA LAS COSAS QUE TIENES, MUCHOS LAS QUIEREN  </p>
            
        </div>

        <div id="camisa5" class="shirt" onclick="verCamisa('angel-frente.jpg', '(BLANCA) Esta camisa fue diseñada con el fin de mostrarnos que debemos de luchar por nuestros sueños para poder conserguirlos, nadie mas lo hara por nosotros.')">
            <img id="img" src="angel-blanco.jpg" alt="Camisa 5">
            <p class="price"></p>
            <p id="camisa" class="camisa">LAS METAS SE BUSCAN NO SE ESPERAN, LUCHA POR ELLAS </p>      
    </div>

    <div id="camisa4" class="shirt" onclick="verCamisa('aguila-verde-frente.jpg', '(VERDE) Esta camisa fue dieñada con el fin de demostrarnos que los sueños se buscan no se esperan, por eso nunca debemos de rendirnos')">
        <img id="img" src="aguila-erde.jpg" alt="Camisa 4">
        <p class="price"></p>
        <p id="camisa" class="camisa">NUNCA TE RINDAS, LO VAS A LOGRAR  </p>
        
    </div>

    <div id="camisa4" class="shirt" onclick="verCamisa('aguila-blanxa-frente.jpg', '(BLANCA) Esta camisa fue dieñada con el fin de demostrarnos que los sueños se buscan no se esperan, por eso nunca debemos de rendirnos.')">
        <img id="img" src="aguila-blanca.jpg" alt="Camisa 4">
        <p class="price"></p>
        <p id="camisa" class="camisa">NUNCA TE RINDAS, LO VAS A LOGRAR  </p>
        
    </div>

    <div id="camisa4" class="shirt" onclick="verCamisa('reloj-blanco-frente.jpg', '(BLANCA) Esta camisa fue diseñada para demostrar lo mucho que vale el tiempo, que debemos de disfrutar cada momento con nuestros seres queridos, y haciendo lo que nos gusta.')">
        <img id="img" src="posibl-reloj-blanco.jpg" alt="Camisa 4">
        <p class="price"></p>
        <p id="camisa" class="camisa"> NO PERMITAS QUE SE TE ACABE EL TIEMPO </p>
        
    </div>

    <div id="camisa4" class="shirt" onclick="verCamisa('angel-verde-adelante.jpg', '(VERDE) Esta camisa fue diseñada con el fin de mostrarnos que debemos de luchar por nuestros sueños para poder conserguirlos, nadie mas lo hara por nosotros.')">
        <img id="img" src="angel_verde.jpg" alt="Camisa 4">
        <p class="price"></p>
        <p id="camisa" class="camisa">VALORA LAS COSAS QUE TIENES, MUCHOS LAS QUIEREN  </p>
        
    </div>

    <div id="camisa4" class="shirt" onclick="verCamisa('angel-azul-frente.jpg', '(AZUL) Esta camisa fue diseñada con el fin de mostrarnos que debemos de luchar por nuestros sueños para poder conserguirlos, nadie mas lo hara por nosotros.')">
        <img id="img" src="angel-azul.jpg" alt="Camisa 4">
        <p class="price"></p>
        <p id="camisa" class="camisa">VALORA LAS COSAS QUE TIENES, MUCHOS LAS QUIEREN  </p>
        
    </div>

    <div id="camisa4" class="shirt" onclick="verCamisa('logo-de-bastoni.png', 'Escribenos, al 3225949495, mandanos tu diseño, el color de la camisa, y la talla, nosotros nos encargamos de poner tu diseño en la mejor calidad de camisas oversize.')">
        <img id="img" src="logo-de-bastoni.png" alt="Camisa 4">
        <p class="price"></p>
        <p id="camisa" class="camisa"> PERSONALIZA TU CAMSIA  </p>
        
    </div>

    
    
        <h2><button class="button" data-text="Awesome">
            <span class="actual-text">&nbsp;¿QUE NOS DIFERENCIA DE LA COMPETENCIA?&nbsp;</span>
            <span aria-hidden="true" class="hover-text">&nbsp;&nbsp;</span>
        </button> </h2>
        <h3>
            <p style="color: crimson;">1. Filosofía de la Marca:</p>
En BASTONI, creemos que la moda es una forma de expresión personal. Nuestra filosofía se centra en empoderar a nuestros clientes a través de camisas que no solo son estilosas, sino que también cuentan una historia.

        </h3>
        <h3><p style="color: crimson;">2. Diseño Innovador</p>
            Nuestras camisas están diseñadas con un enfoque en la originalidad y la creatividad. Cada prenda es una obra de arte que combina colores vibrantes y patrones únicos, perfectos para quienes buscan destacar en cualquier ocasión.</h3>

            <h3><p style="color: crimson;">3. Calidad Superior</p>
                Utilizamos solo los mejores materiales para asegurar que cada camisa no solo luzca bien, sino que también sea cómoda y duradera. Nos comprometemos a ofrecer productos que superen las expectativas de nuestros clientes. ofreciendo prendas de alto gramaje, y en una tela muy fresca </h3>

                <h3><p style="color: crimson;">4. Componentes de las camisas:</p>
                    nuestras camisas esten diseñadas en algodon (permite que la prenda sea fresca), poliester (permite que la prenda no searrugue o se maree con las lavadas) y lycra (permite que la prenda se pueda estirar y vuelva a su horma original), con un gramaje de 240g

                </h3>
                <h3>
                    <p style="color: crimson;">5. Compromiso con la Sostenibilidad</p>
BASTONI se preocupa por el medio ambiente. Implementamos prácticas sostenibles en nuestros procesos de producción y trabajamos con proveedores que comparten nuestra visión de un futuro más verde.

                </h3>
                <h3>
                    <p style="color: crimson;">6. Atención al Cliente</p>
Nuestro equipo de atención al cliente está siempre listo para ayudar. Valoramos cada interacción y nos esforzamos por brindar una experiencia de compra excepcional. (cualquier inquietud o duda escribir al: <p style="color: chartreuse;">3225949495</p>

                </h3>

                
    </div>
   
    <div id="confirmacion" style="display: none;">
        <div id="popup-content">
        <h1>¿esta seguro de que introdujo todos los datos correctamente?</h1>
        <p>si tiene alguna duda oprima el boton (atras) para volver a la sección de envio</p>
        <p>si no es asi precione (aceptar)</p>
        
        <button id="btn" onclick="fin()">aceptar</button>
        <button id="btn" onclick="atras()">atras</button>
    </div>
</div>
       
<div id="finn" style="display: none;">
    <div id="popup-content">

        <h1>GRACIAS POR SU COMPRA</h1>
        <p>su pedido fue procesado, le estaremos informando via WhatsApp toda la informacion de este, tales como </p>

        <p>1. hora de envio</p>

        <p>2. guia de envio</p>

        <p>si todo esta en orden su pedido sera entregado en un lapso de 1 a 5 dias habiles como maximo, SUELE TARDAR MENOS</p>


    </div>

</div>

      
          

    <!-- Sección de envio -->
     <center>

        <form
        id="envioForm" action="https://formspree.io/f/xzzbeddg"
        method="POST"
        >
        
        <input type="hidden" name="producto" id="producto">
        <input type="hidden" name="cantidad" id="cantidad">
        <input type="hidden" name="talla" id="talla">
        <input type="hidden" name="precio" id="precio">


        
    <div id="payment-section" style="display: none;">
        <button class="close-button" onclick="mostrar_catalogo()">&times;</button>
         
        
          <h2>Información de Envío</h2>
          
  
          <div class="form-grid">
              <!-- Datos del Destinatario -->
              <div class="form__group field">
                <input id="DatosEnvio" type="input" class="form__field" placeholder="Name" name="nombre" required="">
                <label  id="name" class="form__label" >Nombre completo</label>
            </div>
  
            <div class="form__group field">
              <input id="DatosEnvio" type="number" class="form__field" placeholder="Name" name="cel" required="">
              <label  for="name" class="form__label">Numero de teléfono</label>
          </div>

  
          <div class="form__group field">
            <input id="DatosEnvio" type="mail" class="form__field" placeholder="Name" name="correo" required="">
            <label  for="name" class="form__label">Correo Électronico</label>
        </div>

  
        <div class="form__group field">
          <input id="DatosEnvio" type="number" class="form__field" placeholder="Name" name="documento" required="">
          <label  for="name" class="form__label">Número de Documento</label>
      </div>

  
              <!-- Dirección -->
              <div class="form-group">
                <div class="form__group field">
                  <input id="DatosEnvio" type="input" class="form__field" placeholder="Name" name="departamento" required="">
                  <label  for="name" class="form__label">Departamento</label>
              </div>
    
              </div>
  
              <div class="form-group">
                <div class="form__group field">
                  <input id="DatosEnvio" type="input" class="form__field" placeholder="Name" name="ciudad" required="">
                  <label  for="name" class="form__label">Ciudad</label>
              </div>
              </div>
  
              <div class="form-group full-width">
                <div class="form__group field">
                  <input id="DatosEnvio" type="input" class="form__field" placeholder="Name" name="direccion" required="">
                  <label for="direccion" class="form__label">Dirección</label>
                  
              <div class="form-group">
                <div class="form__group field">
               <label for="contraentrega">¿COMO DESEA PAGAR?</label>
               <select name="contraentrega" id="contraentrega">
                <option value="sin">deseo pagar ya</option>
                <option value="con">deseo pagar cuando llegue mi producto</option>
               </select>

              <div class="form-group">
                <label for="talla">CONFIRME LA TALLA QUE DESEA RECIBIR</label>
               <select name="talla" id="talla">
                <option value="S">S</option>
                <option value="M">M</option>
                <option value="L">L</option>
               </select>
  
              <div class="form-group">
                <div class="form__group field">
                  <input id="DatosEnvio" type="input" class="form__field" placeholder="Name" name="barrio" required="">
                  <label  for="name" class="form__label">Barrio</label>
              </div>
              
  
              
              <div class="form-group">
                <div class="form__group field">
                  <input id="DatosEnvio" type="number" class="form__field" placeholder="Name" name="cp"  required="">
                  <label  for="name" class="form__label">código postal</label>
              </div>


  
              <div class="form-group full-width">
                  <label>Referencias adicionales</label>
                  <textarea placeholder="Ej: Casa azul, cerca al parque, instrucciones especiales de entrega..."></textarea>
                  
              </div>
          </div>
  
          <div>
            
          <button type="submit" id="confirmarEnvio" class="submit-btn" onclick="fin()">Confirmar Dirección de Envío</button>
        <div>

            <div>
            
                <button type="button" id="Pasarea" class="submit-btn" onclick="Pasarela()">SI QUIERE PAGAR YA, PRESIONE AQUI</button>
              <div>

          </div>
        </form>


      
          
</center>


<div>
    <!-- Pop-up para camisa seleccionada -->
    <div id="shirt-popup" style="display:none;">
        <div id="shirt-popup-content">
            <img id="shirt-image" src="" alt="Camisa">
            <div>
                <p id="shirt-description"></p>
                <div class="size-selector">
                    <p id="precio">precio: varía segun tu diseño</p>
                    <p id="envioCosto">valor de envio sin contraentrega: 15.000 COP</p>
                    <p id="envioCostoCE">valor de envio con contraentrega: 20.000 COP</p>
                    <p>tallas:</p>
                    <div class="size-option selected" onclick="selectSize(this)">S</div>
                    <div class="size-option" onclick="selectSize(this)">M</div>
                    <div class="size-option" onclick="selectSize(this)">L</div>
                    <div class="rating">
                        <input value="5" name="rating" id="star5" type="radio">
                        <label for="star5"></label>
                        <input value="4" name="rating" id="star4" type="radio">
                        <label for="star4"></label>
                        <input value="3" name="rating" id="star3" type="radio">
                        <label for="star3"></label>
                        <input value="2" name="rating" id="star2" type="radio">
                        <label for="star2"></label>
                        <input value="1" name="rating" id="star1" type="radio">
                        <label for="star1"></label>
                      </div>
                </div>
                <div class="quantity-selector">
                    <p>Cantidad:</p>
                    <input type="number" id="quantity-input" min="1" value="1">
                    
                    <div class="form__group field">

                      <label  for="name" class="form__label">cantidad</label>
                  </div>
                <!-- </div> -->
                  <!-- <button id="buy-button">Comprar</button> -->
                  <!-- <div> -->
                    <div>
                      <button id="buy-button" onclick="seccion_pago()">comprar</button>
                  </div>
                <div>
                <div>
                    <button id="button-cerrar" onclick="mostrar_catalogo()">cerrar</button>
                </div>
               
            </div>
        </div>
    </div>
</div>




    <script>

        function daviplata (){

            document.getElementById("daviplata").style.display="flex";
            document.getElementById("pagos").style.display="none";
             
        
                }
        


        function nequi (){
            
            document.getElementById("nequi").style.display="flex";
            document.getElementById("pagos").style.display="none";
             
        
                }
        


        function Pasarela (){
            const DatosEnvio = document.getElementById('DatosEnvio').value;

            if (!DatosEnvio) {
                alert("Es estrictamente necesario llenar todos los campos de información para el envío, de lo contrario no podra ser efectuada su compra")
                return;
            }
            
            
    document.getElementById("pagos").style.display="flex";
    document.getElementById("payment-section").style.display="none";

            
                    }


        


        function salirCarrito(){

document.getElementById("calalog").style.display="flex"
document.getElementById("cart-sidebar").style.display="none"
document.getElementById("shirt-popup").style.display="none"
document.getElementById("overlay").style.display="none"
        }
        

        // Función para mostrar/ocultar el carrito
function toggleCart() {
    const cart = document.getElementById('cart-sidebar');
    const overlay = document.getElementById('overlay');
    
    if(cart.style.right === '0px') {
        cart.style.right = '-400px';
        overlay.style.display = 'none';
        document.body.style.overflow = 'auto'; // Permite scroll en el body
    } else {
        cart.style.right = '0px';
        overlay.style.display = 'block';
        document.body.style.overflow = 'hidden'; // Previene scroll en el body
    }
}

// Para abrir el carrito (puedes llamar esta función desde cualquier botón)
function openCart() {

    


    
    document.getElementById("cart-sidebar").style.display="flex"
    document.getElementById("shirt-popup").style.display="none"
    const cart = document.getElementById('cart-sidebar');
    const overlay = document.getElementById('overlay');
    cart.style.right = '0px';
    overlay.style.display = 'block';
    document.body.style.overflow = 'hidden';
}

// Cerrar el carrito cuando se hace clic en el overlay
document.getElementById('overlay').addEventListener('click', toggleCart);

// Funcionalidad para los botones de cantidad
document.querySelectorAll('.qty-btn').forEach(button => {
    button.addEventListener('click', function() {
        const span = this.parentElement.querySelector('span');
        let quantity = parseInt(span.textContent);
        
        if(this.textContent === '+') {
            quantity++;
        } else if(this.textContent === '-' && quantity > 1) {
            quantity--;
        }
        
        span.textContent = quantity;
        updateSubtotal();



        
    });
});

// Array para almacenar los productos en el carrito

// Remover items del carrito
document.querySelectorAll('.remove-btn').forEach(button => {
    button.addEventListener('click', function() {
        this.closest('.cart-item').remove();
        updateSubtotal();
    });
}); 

        function fin(){

            if (!DatosEnvio) {
                alert("Es estrictamente necesario llenar todos los campos de información para el envío, de lo contrario no podra ser efectuada su compra")
                return;
            }
        
        
            
            const selectedSize = document.querySelector('.size-option.selected');
            
            // Obtener la cantidad
            const quantity = document.getElementById('quantity-input').value;
            
            // Obtener el nombre de la camisa (desde el elemento padre más cercano con clase 'shirt')
            const shirtName = document.getElementById('shirt-description').innerText;
           
            const paymentSection = document.getElementById('payment-section');
        
            const precio = "75.000"
        
            // Asignar los valores a los inputs ocultos
            document.getElementById('producto').value = shirtName; 
            document.getElementById('cantidad').value = quantity; 
            document.getElementById('talla').value = selectedSize; 
            document.getElementById('precio').value = precio; 
        



        }

        function final(){

            const DatosEnvio = document.getElementById('DatosEnvio').value;

if (!DatosEnvio) {
    alert("Es estrictamente necesario llenar todos los campos de información para el envío, de lo contrario no podra ser efectuada su compra")
    return;
}


            document.getElementById("confirmacion").style.display="flex";
            document.getElementById("payment-section").style.display="none";

        }

function atras(){

    document.getElementById("payment-section").style.display="flex";

    document.getElementById("confirmacion").style.display="none";

    document.getElementById("nequi").style.display="none";

    document.getElementById("daviplata").style.display="none";

}

      document.addEventListener("DOMContentLoaded", function() {
        // Agregar evento al input para detectar cuando se presiona una tecla
        document.getElementById("name-input").addEventListener("keydown", function(event) {
            // Detectar si la tecla presionada es "Enter"
            if (event.key === "Enter") {
                // Simular clic en el botón
                document.getElementById("submit-button").click();

            }
        });
    });
    document.addEventListener("DOMContentLoaded", function() {
      // Agregar evento al input para detectar cuando se presiona una tecla
      document.getElementById("email-input").addEventListener("keydown", function(event) {
          // Detectar si la tecla presionada es "Enter"
          if (event.key === "Enter") {
              // Simular clic en el botón
              document.getElementById("submit-button").click();

          }
      });
  });

  document.addEventListener("DOMContentLoaded", function() {
    // Agregar evento al input para detectar cuando se presiona una tecla
    document.getElementById("btn").addEventListener("keydown", function(event) {
        // Detectar si la tecla presionada es "Enter"
        if (event.key === "Enter") {
            // Simular clic en el botón
            document.getElementById("btn").click();

        }
    });
});

function recuerda(){
  document.getElementById("popup").style.display ="flex";

document.getElementById("pop-envio").style.display ="none";

}

    // Función que será llamada cuando se active el botón
    function buttonActivated() {
        alert("El botón ha sido activado");
    }




      

        function seccion_pago (){
            document.getElementById("catalog").style.display = "none";
            document.getElementById("payment-section").style.display = "flex";
            document.getElementById('shirt-popup').style.display = 'none';
            document.getElementById("payment-form").style.display = "flex";
            
        }

      
function mostrar_catalogo (){
    document.getElementById("shirt-popup").style.display = "none";
    document.getElementById("catalog").style.display = "flex";
}
        
function verCatalogo() {
    const name = document.getElementById('name-input').value;
    

    // Validar campos requeridos
    if (!name) {
        document.getElementById('error-message').style.display = 'block';
        return;
    }

    // Mostrar segundo pop-up
    document.getElementById('popup').classList.add('closing');
    setTimeout(() => {
        document.getElementById('popup').style.display = 'none';
        document.getElementById('welcome-message').innerText = 'Hola ' + name;
        document.getElementById('second-popup').style.display = 'flex';
    }, 600);
}

function mostrarCatalogo() {
    document.getElementById('second-popup').classList.add('closing');
    setTimeout(() => {
        document.getElementById('second-popup').style.display = 'none';
        document.getElementById('catalog').style.display = 'block';
    }, 600);
}

let selectedShirtName = '';

function verCamisa(imagen, descripcion) {
    document.getElementById('shirt-image').src = imagen;
    document.getElementById('shirt-description').innerText = descripcion;
    document.getElementById('shirt-popup').style.display = 'flex';
    
    // Obtener el nombre de la camisa del elemento que fue clickeado
    selectedShirtName = event.currentTarget.querySelector('camisa').innerText;
}


function seleccionarTalla(element) {
    const sizeOptions = document.querySelectorAll('.size-option');
    sizeOptions.forEach(option => option.classList.remove('selected'));
    element.classList.add('selected');
}

function comprarCamisa() {
    const quantity = document.getElementById('quantity-input').value;
    const selectedSize = document.querySelector('.size-option.selected');
    if (!selectedSize) {
        alert('Por favor seleccione una talla.');
        return;
    }
    const size = selectedSize.innerText;
    
    document.getElementById('shirt-popup').style.display = 'none'; // Cerrar el pop-up de camisa
    document.getElementById("catalog").style.display = "none";
            document.getElementById("payment-section").style.display = "flex";
            document.getElementById("payment-form").style.display = "flex";
}
function selectSize(element) {
    // Desmarcar todas las tallas
    const sizes = document.getElementsByClassName('size-option');
    for (let i = 0; i < sizes.length; i++) {
        sizes[i].classList.remove('selected');
    }

    // Marcar la talla seleccionada
    element.classList.add('selected');
}

// Modificar el evento onclick del botón comprar
document.getElementById('buy-button').onclick = function() {
    // Obtener la talla seleccionada
    const selectedSize = document.querySelector('.size-option.selected');
    
    // Obtener la cantidad
    const quantity = document.getElementById('quantity-input').value;
    
    // Obtener el nombre de la camisa (desde el elemento padre más cercano con clase 'shirt')
    const shirtName = document.getElementById('shirt-description').innerText;
   
    const paymentSection = document.getElementById('payment-section');

    const precio = "75.000"

    

    if (paymentSection.style.display === 'none' || paymentSection.style.display === '') {
        paymentSection.style.display = 'flex'; // Muestra la sección
    } else {
        paymentSection.style.display = 'none'; // Oculta la sección
    }
    // Verificar si se seleccionó una talla
    if (!selectedSize) {
        alert('Por favor seleccione una talla antes de continuar con la compra.');
        return;
    }
    
    // Verificar si la cantidad es válida
    if (!quantity || quantity < 1) {
        alert('Por favor seleccione una cantidad válida.');
        return;
    }
    
    // Mostrar mensaje de confirmación con todos los detalles

    alert(`verifique su compra antes de seguir con la informacion de envio::\n\n` +
        `producto: ${shirtName}\n\n` +

          `Cantidad: ${quantity}\n\n` +

         `Talla: ${selectedSize.innerText}\n\n` +

         `precio: ${precio}COP\n\n` +


          `\nPrecione "aceptar" para seguir con el envio`);
    
    
    // Cerrar el popup después de la compra
    document.getElementById('shirt-popup').style.display = 'none';
    document.getElementById("catalog").style.display = "none";
            document.getElementById("payment-section").style.display = "flex";
    
    
    // Resetear las selecciones
    document.querySelector('.size-option.selected')?.classList.remove('selected');
    document.getElementById('quantity-input').value = 1;
}


</script>
</body>


