# 🚀 Guía Rápida - Study Vault Frontend

## ⚡ Instalación en 5 Minutos

### Paso 1: Configurar Credenciales AWS

1. **Copia el archivo de configuración**:
   ```bash
   # En la carpeta frontend/
   copy config.example.js config.js
   ```

2. **Obtén tus credenciales AWS**:
   - Ve a AWS Console → IAM → Users
   - Crea un nuevo usuario con acceso programático
   - Guarda el Access Key ID y Secret Access Key

3. **Edita `config.js`**:
   ```javascript
   credentials: {
       accessKeyId: 'TU_ACCESS_KEY_AQUI',
       secretAccessKey: 'TU_SECRET_KEY_AQUI'
   }
   ```

### Paso 2: Configurar CORS en S3

Para **AMBOS** buckets (input y output):

1. Ve a S3 → Selecciona el bucket → Pestaña Permissions
2. Scroll hasta "Cross-origin resource sharing (CORS)"
3. Click Edit y pega:

```json
[
    {
        "AllowedHeaders": ["*"],
        "AllowedMethods": ["GET", "PUT", "POST", "DELETE", "HEAD"],
        "AllowedOrigins": ["*"],
        "ExposeHeaders": ["ETag"]
    }
]
```

### Paso 3: Ejecutar Localmente

**Opción A - Python** (más fácil):
```bash
cd frontend
python -m http.server 8000
```

**Opción B - Node.js**:
```bash
npm install -g http-server
cd frontend
http-server -p 8000
```

**Opción C - VS Code**:
- Instala extensión "Live Server"
- Click derecho en `index.html` → "Open with Live Server"

### Paso 4: Abrir en Navegador

Abre: `http://localhost:8000`

¡Listo! 🎉

---

## 🎯 Uso Básico

1. **Arrastra** un archivo `.txt` a la zona de upload
2. **Click** en "Upload & Convert"
3. **Espera** 10-30 segundos (verás animación)
4. **Descarga** tu archivo MP3 generado

---

## ❌ Problemas Comunes

### Error: "AWS Configuration Required"
✅ **Solución**: Edita `config.js` con tus credenciales reales

### Error: "Connection Failed"
✅ **Solución**: 
- Verifica que las credenciales sean correctas
- Asegúrate de tener internet

### Error: "Upload Failed"
✅ **Solución**: 
- Configura CORS en ambos buckets S3
- Verifica que el usuario IAM tenga permisos S3

### Los archivos no aparecen
✅ **Solución**:
- Verifica que la Lambda esté configurada correctamente
- Revisa CloudWatch Logs
- Espera hasta 2 minutos

---

## 🔐 Seguridad para GitHub

**ANTES de hacer commit**:

1. Asegúrate que `config.js` está en `.gitignore`
2. Verifica que NO subirás tus credenciales:
   ```bash
   git status
   # NO debe aparecer config.js
   ```

3. Solo sube `config.example.js`

---

## 📚 Recursos Útiles

- [Documentación AWS SDK JavaScript](https://docs.aws.amazon.com/sdk-for-javascript/)
- [Amazon Polly Voices](https://docs.aws.amazon.com/polly/latest/dg/voicelist.html)
- [S3 CORS Configuration](https://docs.aws.amazon.com/AmazonS3/latest/userguide/cors.html)

---

## 🤝 Soporte

Si algo no funciona:
1. Revisa la consola del navegador (F12)
2. Verifica CloudWatch Logs en AWS
3. Confirma que todos los servicios estén desplegados
4. Revisa la sección de troubleshooting en README.md

---

**¡Éxito con tu proyecto! 🚀**
