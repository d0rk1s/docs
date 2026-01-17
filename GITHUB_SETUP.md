# Configuración del Repositorio GitHub

## Añadir URL de la Documentación en "About"

### Opción 1: Desde la Interfaz Web de GitHub

1. **Ve al repositorio**: https://github.com/d0rk1s/docs

2. **Editar About**:
   - En la página principal del repo, busca la sección **"About"** (arriba a la derecha)
   - Haz clic en el **⚙️ icono de engranaje** (Settings)

3. **Configurar campos**:
   - **Description**: `Clinic Management System - Official Documentation`
   - **Website**: `https://[tu-proyecto].mintlify.app` (la URL que obtengas de Mintlify)
   - **Topics**: Añade tags como: `documentation`, `mintlify`, `clinic-management`, `fastapi`, `medical`

4. **Guardar**:
   - ✅ Marca "Use your GitHub Pages website"
   - Haz clic en **"Save changes"**

### Opción 2: Usando GitHub CLI (gh)

```bash
# Instalar GitHub CLI si no lo tienes
# https://cli.github.com/

# Actualizar descripción del repo
gh repo edit d0rk1s/docs \
  --description "Clinic Management System - Official Documentation" \
  --homepage "https://[tu-proyecto].mintlify.app"

# Añadir topics
gh repo edit d0rk1s/docs \
  --add-topic "documentation" \
  --add-topic "mintlify" \
  --add-topic "clinic-management" \
  --add-topic "fastapi" \
  --add-topic "medical"
```

### Opción 3: Usando la API de GitHub

```bash
# Usando curl con tu token de GitHub
curl -X PATCH \
  -H "Authorization: token YOUR_GITHUB_TOKEN" \
  -H "Accept: application/vnd.github.v3+json" \
  https://api.github.com/repos/d0rk1s/docs \
  -d '{
    "description": "Clinic Management System - Official Documentation",
    "homepage": "https://[tu-proyecto].mintlify.app",
    "topics": ["documentation", "mintlify", "clinic-management", "fastapi", "medical"]
  }'
```

## Resultado Esperado

Después de configurar, el About del repositorio mostrará:

```
📝 Clinic Management System - Official Documentation

🔗 https://docs-xxx.mintlify.app

Topics: documentation • mintlify • clinic-management • fastapi • medical
```

## Añadir Badge de Estado (Opcional)

Puedes añadir un badge de Mintlify al README:

```markdown
# Clinic Management System - Documentation

[![Mintlify](https://img.shields.io/badge/docs-mintlify-blue)](https://[tu-proyecto].mintlify.app)

Documentación oficial del sistema de gestión de clínicas.

## 📖 Ver Documentación

La documentación completa está disponible en: **[https://[tu-proyecto].mintlify.app](https://[tu-proyecto].mintlify.app)**
```

## Verificación

1. Ve a: https://github.com/d0rk1s/docs
2. Deberías ver:
   - Descripción del proyecto en About
   - Link clickeable a la documentación
   - Topics/tags añadidos
