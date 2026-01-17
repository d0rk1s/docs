# Actualizar URL de Mintlify

Después de obtener tu URL de Mintlify (ej: https://docs-xxx.mintlify.app), 
ejecuta estos comandos para actualizar todos los links:

```bash
cd /c/Users/Cate/Documents/mintlify

# Reemplaza YOUR_MINTLIFY_URL_HERE con tu URL real
# Ejemplo: sed -i 's|YOUR_MINTLIFY_URL_HERE|https://docs-clinic.mintlify.app|g' README.md

# Windows (Git Bash)
sed -i 's|YOUR_MINTLIFY_URL_HERE|TU_URL_AQUI|g' README.md

# Commit y push
git add README.md
git commit -m "Update Mintlify URL in README"
git push origin main
```

O edita manualmente el README.md y reemplaza `YOUR_MINTLIFY_URL_HERE` con tu URL.
