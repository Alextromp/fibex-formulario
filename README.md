<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prueba - Envío a Arelis Albes</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: #f0f2f5;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            background: white;
            max-width: 650px;
            width: 100%;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.15);
            text-align: center;
        }

        .logo {
            margin-bottom: 25px;
        }

        .logo h1 {
            font-size: 32px;
            color: #0033a0;
            font-weight: 800;
        }

        .logo h1 span {
            color: #ffcc00;
        }

        .logo p {
            color: #666;
            font-size: 14px;
        }

        .cliente-info {
            background: #f8f9fa;
            padding: 18px 20px;
            border-radius: 12px;
            margin-bottom: 20px;
            text-align: left;
        }

        .cliente-info p {
            margin: 4px 0;
            font-size: 14px;
            color: #333;
        }

        .cliente-info strong {
            color: #0033a0;
        }

        .mensaje-preview {
            background: #f0f2f5;
            padding: 20px;
            border-radius: 12px;
            margin-bottom: 20px;
            text-align: left;
            font-size: 14px;
            max-height: 400px;
            overflow-y: auto;
            white-space: pre-wrap;
            word-wrap: break-word;
            border: 1px solid #ddd;
        }

        .mensaje-preview .label {
            font-size: 11px;
            color: #888;
            text-transform: uppercase;
            font-weight: 700;
            margin-bottom: 10px;
            display: block;
            letter-spacing: 1px;
        }

        .btn-group {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin-top: 10px;
        }

        .btn {
            padding: 14px 28px;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 700;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            flex: 1;
            min-width: 180px;
        }

        .btn-wsp {
            background: #25D366;
            color: white;
        }

        .btn-wsp:hover {
            background: #1da851;
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(37,211,102,0.3);
        }

        .btn-copy {
            background: #0033a0;
            color: white;
        }

        .btn-copy:hover {
            background: #002277;
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,51,160,0.3);
        }

        .btn-back {
            background: #95a5a6;
            color: white;
        }

        .btn-back:hover {
            background: #7f8c8d;
            transform: translateY(-2px);
        }

        .btn-link {
            background: #e67e22;
            color: white;
        }

        .btn-link:hover {
            background: #d35400;
            transform: translateY(-2px);
        }

        .toast {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            background: #27ae60;
            color: white;
            padding: 16px 28px;
            border-radius: 10px;
            font-weight: 600;
            box-shadow: 0 8px 30px rgba(0,0,0,0.2);
            display: none;
            z-index: 999;
            animation: slideUp 0.3s ease;
        }

        .toast.error {
            background: #e74c3c;
        }

        @keyframes slideUp {
            from { transform: translateX(-50%) translateY(50px); opacity: 0; }
            to { transform: translateX(-50%) translateY(0); opacity: 1; }
        }

        .instrucciones {
            background: #fff3cd;
            padding: 15px;
            border-radius: 10px;
            margin-top: 20px;
            text-align: left;
            font-size: 13px;
            color: #856404;
            border: 1px solid #ffc107;
        }

        .instrucciones strong {
            color: #0033a0;
        }

        .enlace-info {
            background: #eaf4ff;
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 15px;
            font-size: 13px;
            color: #0033a0;
            border: 1px solid #b3d4ff;
            word-break: break-all;
        }

        .enlace-info strong {
            color: #0033a0;
        }

        @media (max-width: 480px) {
            .container { padding: 20px; }
            .btn { min-width: 100%; }
            .mensaje-preview { font-size: 12px; max-height: 300px; }
        }
    </style>
</head>
<body>

<div class="container">

    <!-- LOGO -->
    <div class="logo">
        <h1>FIBEX<span>+</span></h1>
        <p>Prueba de envío - Arelis Albes</p>
    </div>

    <!-- ENLACE DEL FORMULARIO -->
    <div class="enlace-info">
        <strong>🔗 Enlace del formulario:</strong><br>
        <span id="enlaceFormulario">Cargando...</span>
    </div>

    <!-- DATOS DEL CLIENTE -->
    <div class="cliente-info">
        <p><strong>👤 Nombre:</strong> Arelis Albes</p>
        <p><strong>📱 Teléfono:</strong> 0414-4072340</p>
        <p><strong>📍 Sector:</strong> Balencey</p>
        <p><strong>📡 Servicio actual:</strong> Sin servicio</p>
        <p><strong>🆔 ID:</strong> #8</p>
    </div>

    <!-- VISTA PREVIA DEL MENSAJE -->
    <div class="mensaje-preview" id="mensajePreview">
        <span class="label">📨 VISTA PREVIA DEL MENSAJE</span>
        <span id="mensajeTexto">Cargando mensaje...</span>
    </div>

    <!-- BOTONES -->
    <div class="btn-group">
        <button class="btn btn-wsp" onclick="enviarWhatsApp()">📱 Enviar WhatsApp</button>
        <button class="btn btn-copy" onclick="copiarMensaje()">📋 Copiar mensaje</button>
    </div>
    <div class="btn-group">
        <button class="btn btn-link" onclick="abrirFormulario()">🔗 Abrir formulario</button>
        <button class="btn btn-back" onclick="window.close()">⬅️ Cerrar</button>
    </div>

    <!-- INSTRUCCIONES -->
    <div class="instrucciones">
        <strong>📸 IMPORTANTE:</strong> Al enviar por WhatsApp, <strong>adjunta las 4 imágenes</strong> en este orden:<br>
        1. Fachada de la tienda<br>
        2. Plan XFULL (1.5GB → $55 + IVA)<br>
        3. Plan FULL (800~1GB → $45 + IVA)<br>
        4. Plan FIBEX TELECOM (Internet + TV + Seguro)
    </div>

</div>

<!-- TOAST -->
<div class="toast" id="toast">✅ Mensaje copiado al portapapeles</div>

<script>
    // ============================================================
    // CONFIGURACIÓN - ENLACE REAL DEL FORMULARIO
    // ============================================================

    const usuarioGitHub = "Alextromp";
    const enlaceBase = `https://${usuarioGitHub}.github.io/fibex-formulario/`;

    // ============================================================
    // DATOS DEL CLIENTE
    // ============================================================

    const cliente = {
        id: 8,
        nombre: "Arelis Albes",
        telefono: "0414-4072340",
        sector: "Balencey",
        servicio: "Sin servicio"
    };

    // ============================================================
    // GENERAR ENLACE DEL FORMULARIO PARA EL CLIENTE
    // ============================================================

    function generarEnlaceCliente(cliente) {
        const params = new URLSearchParams({
            nombre: cliente.nombre,
            telefono: cliente.telefono,
            sector: cliente.sector,
            servicio: cliente.servicio
        });
        return `${enlaceBase}?${params.toString()}`;
    }

    const enlaceCliente = generarEnlaceCliente(cliente);

    // ============================================================
    // GENERAR MENSAJE
    // ============================================================

    function generarMensaje(cliente) {
        const nombre = cliente.nombre.split(' ')[0];
        const enlace = generarEnlaceCliente(cliente);
        return `*¡${nombre} llegó el momento de cambiar!*

En el mes de papá y del mundial te ponemos a ganar.

Con la factura de tu servicio de Internet actual te damos la bienvenida a lo grande.

Activando uno de estos planes tendrás instalación *gratis* (ONT estándar + tu router) o 75% de descuento en nuestra full equipo (ONT con WiFi 6 Mesh lista para navegar).

Además disfrutas del mes de papá y del mundial sin más nada que pagar.

Y para demostrarte lo mucho que valoramos tu decisión de cambiar, Julio y Agosto te sale a la mitad.

*¡Llegó tu momento de cambiar!*

📍 Ubicación de la tienda:
https://share.google/E6tdLCtQ8FOjMWg8i

✅ SÍ - Acepto la promoción
👉 ${enlace} 👈
(CAMBIATE YA)

*¡Vente con nosotros!*

Listos para darte la bienvenida...`;
    }

    // ============================================================
    // MOSTRAR MENSAJE EN PANTALLA
    // ============================================================

    function mostrarMensaje() {
        const mensaje = generarMensaje(cliente);
        document.getElementById('mensajeTexto').textContent = mensaje;
        document.getElementById('enlaceFormulario').textContent = enlaceCliente;
    }

    // ============================================================
    // ENVIAR POR WHATSAPP
    // ============================================================

    function enviarWhatsApp() {
        const mensaje = generarMensaje(cliente);
        const telefono = cliente.telefono.replace(/[^0-9+]/g, '');
        const url = `https://wa.me/${telefono}?text=${encodeURIComponent(mensaje)}`;
        window.open(url, '_blank');
        mostrarToast(`📱 WhatsApp abierto para ${cliente.nombre}`);
    }

    // ============================================================
    // COPIAR MENSAJE
    // ============================================================

    function copiarMensaje() {
        const mensaje = generarMensaje(cliente);

        if (navigator.clipboard && navigator.clipboard.writeText) {
            navigator.clipboard.writeText(mensaje).then(() => {
                mostrarToast('✅ Mensaje copiado al portapapeles');
            }).catch(() => {
                copiarManual(mensaje);
            });
        } else {
            copiarManual(mensaje);
        }
    }

    function copiarManual(mensaje) {
        const textarea = document.createElement('textarea');
        textarea.value = mensaje;
        textarea.style.position = 'fixed';
        textarea.style.opacity = '0';
        document.body.appendChild(textarea);
        textarea.select();
        document.execCommand('copy');
        document.body.removeChild(textarea);
        mostrarToast('✅ Mensaje copiado al portapapeles');
    }

    // ============================================================
    // ABRIR FORMULARIO
    // ============================================================

    function abrirFormulario() {
        window.open(enlaceCliente, '_blank');
        mostrarToast('🔗 Abriendo formulario...');
    }

    // ============================================================
    // TOAST
    // ============================================================

    function mostrarToast(mensaje, tipo = 'success') {
        const toast = document.getElementById('toast');
        toast.textContent = mensaje;
        toast.className = 'toast' + (tipo === 'error' ? ' error' : '');
        toast.style.display = 'block';
        clearTimeout(toast._timeout);
        toast._timeout = setTimeout(() => {
            toast.style.display = 'none';
        }, 4000);
    }

    // ============================================================
    // INICIALIZAR
    // ============================================================

    mostrarMensaje();
    console.log('🚀 Prueba para Arelis Albes cargada');
    console.log('📋 Cliente:', cliente);
    console.log('🔗 Enlace del formulario:', enlaceCliente);
    console.log('📨 Mensaje:', generarMensaje(cliente));
</script>

</body>
</html>
