# Vulnerable admin login Page
El código proporcionado es un ejemplo básico de una página web con un formulario de inicio de sesión. La funcionalidad principal del código es permitir que los usuarios ingresen un nombre de usuario y una contraseña para iniciar sesión. Si se ingresan las credenciales correctas ("admin" como nombre de usuario y "admin" como contraseña), el usuario es redirigido a una página de bienvenida.

```
<!-- Aqui se declararn las variables y se crea la seccion para el login de usuario -->

<body>
  <div class="container">
    <h2>Login</h2>
    <form id="login-form">
      <div class="form-group">
        <label for="username">Username</label>
        <input type="text" id="username" class="form-control" required>
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input type="password" id="password" class="form-control" required>
      </div>
      <button type="submit" class="btn-login">Login</button>
    </form>
    <div id="message" class="message"></div>
  </div>

<!-- Aqui termina la declaracion de las variables -->

<!-- Aqui comienza el script para iniciar sesion como usuario -->
  <script>
    document.getElementById('login-form').addEventListener('submit', function(event) {
      event.preventDefault();

      var username = document.getElementById('username').value;
      var password = document.getElementById('password').value;

      if (username === 'admin' && password === 'admin') { // Username y password genericos que se encuentran almacenados en el frontend
        window.location.href = 'admin.html';
      } else {
        document.getElementById('message').textContent = 'Invalid username or password';
      }
    });
  </script>
<!-- Aqui terminal script para iniciar sesion -->
```

Sin embargo, este código presenta algunas vulnerabilidades y malas prácticas de seguridad que se deben tener en cuenta:

1. Contraseñas genéricas: En el código de ejemplo, se utiliza una contraseña genérica ("admin"). Esto es una mala práctica de seguridad, ya que las contraseñas deben ser fuertes y únicas para cada usuario. Se recomienda implementar una política de contraseñas seguras y almacenar las contraseñas de manera segura utilizando técnicas como el hash y el salting.

2. Credenciales expuestas en el frontend: En el código proporcionado, las credenciales ("admin" como nombre de usuario y contraseña) se encuentran expuestas directamente en el frontend del aplicativo. Esto significa que cualquier persona que revise el código fuente de la página web podría ver las credenciales sin esfuerzo. Esta es una grave vulnerabilidad, ya que expone las credenciales confidenciales de los usuarios. Para solucionar esto, se debe implementar un sistema de autenticación más seguro donde las credenciales sean manejadas en el backend y no se expongan en el frontend.

4. Falta de protección contra ataques de fuerza bruta: El código actual no implementa ninguna medida de protección contra ataques de fuerza bruta, donde un atacante intenta adivinar las credenciales probando diferentes combinaciones. Se recomienda implementar medidas de seguridad como bloqueo de cuenta después de varios intentos fallidos, reCAPTCHA o implementación de un mecanismo de espera progresiva.

6. Falta de encriptación de las comunicaciones: El código no utiliza encriptación en las comunicaciones entre el cliente y el servidor. Esto significa que las credenciales enviadas a través del formulario de inicio de sesión podrían ser interceptadas por atacantes si la conexión no está asegurada con HTTPS. Es fundamental implementar HTTPS para garantizar la seguridad de las comunicaciones.

8. Falta de validación de entrada y sanitización: El código no realiza una validación adecuada de la entrada de usuario. Se deben aplicar filtros y validaciones para asegurarse de que los datos ingresados sean seguros y cumplan con los requisitos establecidos. Esto incluye la validación del nombre de usuario y la contraseña para evitar ataques como inyecciones SQL o scripts maliciosos.
