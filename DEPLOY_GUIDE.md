# Guía de Despliegue - Mintlify

## Configuración Inicial

### 1. Acceder a Mintlify Dashboard
1. Ve a: https://dashboard.mintlify.com
2. Inicia sesión con GitHub (usa la cuenta `d0rk1s`)

### 2. Conectar el Repositorio
1. En el dashboard, haz clic en **"New Documentation"** o **"+ Add Documentation"**
2. Selecciona **"Connect GitHub Repository"**
3. Busca y selecciona el repositorio: `d0rk1s/docs`
4. Mintlify detectará automáticamente el archivo `mint.json`
5. Haz clic en **"Deploy"**

### 3. Configuración de Despliegue Automático
Una vez conectado, Mintlify configura automáticamente:
- ✅ **GitHub App instalada**: Detecta cambios en cada push a `main`
- ✅ **Despliegue automático**: Se despliega en 1-2 minutos después de cada push
- ✅ **Preview builds**: Genera previews para cada Pull Request

### 4. Obtener URL de Producción
Después del primer despliegue, verás la URL en el dashboard:
- URL por defecto: `https://[tu-proyecto].mintlify.app`
- O puedes configurar un dominio personalizado (ej: `docs.tudominio.com`)

## Verificación

### Comandos locales para probar antes de deployar:
```bash
# Ir al directorio del repo
cd /c/Users/Cate/Documents/mintlify

# Instalar Mintlify CLI (si no lo tienes)
npm i -g mintlify

# Ejecutar preview local
mintlify dev
```

La documentación estará disponible en `http://localhost:3000`

## Workflow de Desarrollo

1. **Hacer cambios locales** en archivos `.mdx`
2. **Probar localmente** con `mintlify dev`
3. **Commit y push**:
   ```bash
   git add .
   git commit -m "Update documentation"
   git push origin main
   ```
4. **Mintlify despliega automáticamente** en 1-2 minutos
5. **Verificar** en la URL de producción

## Dominio Personalizado (Opcional)

Si quieres usar tu propio dominio:

1. En Mintlify Dashboard → Settings → Custom Domain
2. Añade tu dominio (ej: `docs.tudominio.com`)
3. Configura DNS según las instrucciones de Mintlify
4. Mintlify generará certificado SSL automáticamente

## Troubleshooting

### El despliegue falla
- Verifica que `mint.json` sea válido (JSON válido)
- Revisa los logs en Mintlify Dashboard
- Asegúrate de que todas las rutas en `navigation` existan

### Cambios no se reflejan
- Espera 2-3 minutos (puede tomar tiempo)
- Verifica que el push llegó a GitHub
- Limpia caché del navegador (Ctrl+Shift+R)

### Preview local no funciona
```bash
# Reinstalar Mintlify CLI
npm uninstall -g mintlify
npm i -g mintlify

# Limpiar caché
rm -rf .mintlify
mintlify dev
```
