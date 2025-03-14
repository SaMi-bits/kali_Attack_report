# kali_Attack_report
Este repositorio documenta un ejercicio práctico de seguridad ofensiva realizado en un entorno de laboratorio controlado utilizando Kali Linux. El objetivo fue explorar técnicas de explotación utilizando herramientas específicas para pruebas éticas.

---

## Aviso de Responsabilidad

> **Este ejercicio fue realizado en un entorno controlado y con fines educativos.**  
> El uso no autorizado de las técnicas aquí descritas en sistemas ajenos es ilegal y contrario a las prácticas éticas en ciberseguridad.  
> **No me hago responsable** por el mal uso de esta información. 

---

## Herramientas Utilizadas

- **Kali Linux**: Sistema operativo utilizado para pruebas de penetración.  
- **`curl`**: Herramienta de línea de comandos para realizar peticiones HTTP.  
- **`cookies.txt`**: Archivo para manejar cookies de sesión en las peticiones.  
- **Terminal Bash**: Para la ejecución de comandos en el entorno Kali.

---

## Descripción del Ataque

1. **Objetivo:** Simular un ataque de fuerza bruta mediante peticiones `POST` en un entorno web local.  
2. **Herramienta Principal:** `curl` para automatizar peticiones con parámetros personalizados.  
3. **Parámetros Utilizados:**
    - `-b cookies.txt`: Para gestionar cookies de sesión.
    - `-d "username=admin&password=1234"`: Datos del formulario de login.
    - `-H "Content-Type: application/x-www-form-urlencoded"`: Cabecera indicando el tipo de contenido.
    - `-H "User-Agent: Mozilla/5.0"`: Emulación de un navegador.
    - `-H "Referer:https://192.168.1.1/login.html"`: Referencia a la página de origen.
    - `-L`: Seguir redirecciones.

4. **Comando Ejecutado:**  
```bash
curl -c cookies.txt -b cookies.txt -L -d "username=admin&password=1234" \
-H "Content-Type: application/x-www-form-urlencoded" \
-H "Referer:https://192.168.1.1/login.html" \
-H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)" \
http://192.168.1.1/goform/WebLogin
