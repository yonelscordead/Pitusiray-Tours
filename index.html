// netlify/functions/culqi-charge.js
// Esta función recibe el token de Culqi y procesa el cargo en el servidor

exports.handler = async (event) => {
    if (event.httpMethod !== 'POST') {
        return { statusCode: 405, body: 'Method Not Allowed' };
    }

    try {
        const { token, amount, description, email } = JSON.parse(event.body);

        // ⚠️ Llave SECRETA de prueba — en Netlify la guardas como variable de entorno CULQI_SECRET_KEY
        const secretKey = process.env.CULQI_SECRET_KEY || 'sk_test_f6tP2GrUJY6BiYgF';

        const response = await fetch('https://api.culqi.com/v2/charges', {
            method: 'POST',
            headers: {
                'Content-Type':  'application/json',
                'Authorization': 'Bearer ' + secretKey
            },
            body: JSON.stringify({
                amount:           amount,       // en centavos, ej: 10000 = $100.00
                currency_code:    'USD',
                email:            email,
                source_id:        token,
                description:      description || 'Reserva Pitusiray Tours',
                capture:          true,
                antifraud_details: {
                    address:           'Cusco',
                    address_city:      'Cusco',
                    country_code:      'PE',
                    first_name:        'Cliente',
                    last_name:         'Pitusiray',
                    phone:             '919030430'
                }
            })
        });

        const data = await response.json();

        if (data.object === 'charge' && data.outcome && data.outcome.type === 'venta_exitosa') {
            return {
                statusCode: 200,
                body: JSON.stringify({
                    success:     true,
                    charge_id:   data.id,
                    amount:      data.amount,
                    message:     '¡Pago procesado correctamente!'
                })
            };
        } else {
            return {
                statusCode: 400,
                body: JSON.stringify({
                    success: false,
                    message: data.user_message || data.merchant_message || 'Error al procesar el pago'
                })
            };
        }

    } catch (err) {
        return {
            statusCode: 500,
            body: JSON.stringify({ success: false, message: 'Error interno: ' + err.message })
        };
    }
};
