# Instalación del Certificado de OWASP ZAP en el Navegador

Este documento explica cómo exportar e instalar el certificado generado por OWASP ZAP para evitar advertencias HTTPS al interceptar tráfico cifrado durante auditorías de seguridad.

---

## 🚪 Exportar certificado desde ZAP

1. Abre OWASP ZAP
2. Ve al menú: `Herramientas > Opciones`
3. En el panel izquierdo selecciona: `Certificados de servidor`
4. Haz clic en el botón **"Guardar"** (parte derecha)
5. Guarda el archivo como `zap_cert.crt` o `OWASP_ZAP_Root_CA.crt`

---

## 📃 Importar certificado en Firefox

1. Abre **Firefox**
2. Ve a: `Menú (≡) > Configuración > Privacidad y seguridad`
3. Baja hasta la sección **"Certificados"**
4. Haz clic en **"Ver certificados..."**
5. Pestaña **"Autoridades"** > clic en **"Importar"**
6. Selecciona el archivo `.crt` exportado desde ZAP
7. Marca:
   - ☑ "Confiar en esta CA para identificar sitios web"
8. Acepta y reinicia Firefox si es necesario

---

## 🚀 Importar certificado en Chrome/Edge (Windows)

1. Presiona `Win + R` y escribe `certmgr.msc`
2. Ve a: **Entidades de certificación raíz de confianza > Certificados**
3. Clic derecho sobre **"Certificados"** > **Todas las tareas > Importar**
4. Selecciona tu archivo `.crt`
5. Completa el asistente (elige "colocar todos en este almacén")
6. Finaliza e inicia nuevamente tu navegador

---

## ⚠️ Consideraciones de seguridad
- Este certificado sólo debería estar instalado **mientras trabajas con ZAP**.
- Una vez finalizadas tus pruebas, **elimínalo** del almacén de certificados para prevenir usos no deseados.

---

## 🔧 Verificación

Una vez instalado correctamente, puedes interceptar tráfico HTTPS en ZAP sin que el navegador marque errores SSL.

Puedes comprobarlo visitando cualquier sitio local vulnerable como:
```
http://localhost:3000 (Juice Shop)
```
o sitios HTTPS interceptados en pruebas controladas.
