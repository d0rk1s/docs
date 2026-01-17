# Conversaciones WhatsApp - Documentación

Esta sección contiene 5 tutoriales completos sobre el sistema conversacional de WhatsApp (ClinicAgent).

## Archivos Creados

1. **overview.mdx** - Visión general del sistema conversacional
   - Arquitectura del agente (LangChain + OpenAI)
   - Capacidades del bot (agendar, reagendar, cancelar)
   - Mensajes de voz con Whisper API
   - Herramientas disponibles (get_availability, create_appointment, etc.)
   - Optimizaciones de performance (cache, temperatura LLM, token reduction)
   - Inteligencia conversacional (fechas relativas, selección de servicios)
   - Integración con Twilio y WhatsApp
   - Grace period (30 días)
   - LangSmith tracing y PostgreSQL conversation memory

2. **view-conversations.mdx** - Monitorear conversaciones
   - Acceder a lista de conversaciones
   - Filtros por estado (Activa, Pausada, Finalizada)
   - Filtros por fecha y búsqueda
   - Interpretar estados (qué significa cada uno)
   - Acciones disponibles (ver, pausar, enviar mensaje)
   - Indicadores visuales (badges, mensajes recientes)
   - Casos de uso (monitoreo, auditoría, troubleshooting)

3. **message-history.mdx** - Revisar historial completo
   - Acceder al historial de una conversación
   - Elementos del historial (mensajes de paciente vs bot)
   - Metadatos técnicos (herramientas, latencia, cache status, IDs, errores)
   - Funcionalidades interactivas (expandir/contraer, copiar, buscar)
   - Indicadores visuales (transcripción de voz, mensajes con errores)
   - Casos de uso (validar citas, debugging, analizar performance)
   - Exportar historial (copiar texto, descargar JSON)

4. **pause-bot.mdx** - Pausar el bot para control manual
   - Qué sucede al pausar (bot deja de responder automáticamente)
   - Formas de pausar (desde lista o desde historial)
   - Cuándo pausar (conversación circular, paciente frustrado, consulta compleja, queja, mensaje proactivo)
   - Enviar mensaje manual después de pausar
   - Reactivar el bot
   - Notificar al paciente (mensajes recomendados)
   - Mejores prácticas (pausar proactivamente, identificarse, reactivas cuando esté resuelto)
   - Métricas a monitorear (% pausadas, tiempo promedio pausado)

5. **send-manual-message.mdx** - Enviar mensajes como staff
   - Prerrequisitos (bot debe estar pausado)
   - Enviar mensaje en conversación existente (pausar → escribir → enviar → esperar/reactivar)
   - Enviar mensaje proactivo nuevo (restricción 24h, templates de WhatsApp Business)
   - Formatear mensajes (negrita, cursiva, saltos de línea, emojis)
   - Plantillas de mensajes comunes (confirmación, recordatorio, cancelación, queja, seguimiento, promoción)
   - Mejores prácticas (identificación, tono profesional, claridad, CTA clara, respuesta rápida)
   - Indicadores de entrega (enviando → enviado → entregado → leído)
   - Troubleshooting (botón deshabilitado, errores, mensaje no entregado, multimedia)

## Contexto Técnico del Sistema (de CLAUDE.md)

- **ClinicAgent**: LangChain 1.0 + OpenAI (GPT-4o-mini) para conversación natural
- **PostgreSQL-backed conversation memory**: Tabla `conversation_messages` con índices optimizados
- **Tool-based architecture con caching transparente**: TTL de 3-10 min según herramienta
- **Twilio integration para WhatsApp messaging**: Webhook en `/whatsapp/webhook`
- **LangSmith tracing para observabilidad**: Todas las conversaciones rastreadas
- **WhatsApp voice messages**: Transcripción automática vía Whisper API
- **Formato E.164 obligatorio para teléfonos**: `+34612345678`
- **30-day grace period**: Si clínica sin citas, WhatsApp se desactiva automáticamente

## Características Destacadas en los Tutoriales

### 1. Mensajes de Voz (Notas de Voz)
- Soporte completo para audio de WhatsApp (OGG, MP3, M4A, AMR, WAV)
- Transcripción con OpenAI Whisper API
- Latencia 5-10s (2-5s transcripción + 3-5s procesamiento)
- Mejoras de calidad (2025-11-16): prompt hints, detección de alucinaciones, keywords de dominio
- Costo: ~$0.006 por minuto (~$5-20/mes uso típico)

### 2. Optimizaciones de Performance
- **Tool Cache**: Reduce queries duplicadas en 99%+ (543ms → 2.35ms)
- **Temperatura LLM**: 0.3 (consistencia) + top_p 0.95 (nucleus sampling)
- **Token Optimization**: ~93 tokens/mensaje ahorrados (smart default date en código)
- **Prompt reduction**: ~150-200 tokens/mensaje (eliminada lista manual de herramientas)

### 3. Inteligencia Conversacional
- **Fechas relativas**: Delegado al LLM con calendario visual (no heurísticas determinísticas)
- **Selección de servicios**: ServiceMapper con threshold 0.05 (muy permisivo)
- **Manejo de contexto obsoleto**: Heurística conservadora (solo patrones determinísticos)

### 4. Fixes Críticos Documentados
- Timezone conversion bug (2025-11-05): Slots en local timezone (+01:00) no UTC
- Multi-clinic patient name update (2025-11-05): Actualiza nombre al más reciente
- Stale availability context bug (2025-11-17): Limpia cache cuando criterios cambian
- LLM parallel tool call date calculation (2025-11-04): Prohíbe llamadas paralelas date-dependent

## Navegación en mint.json

La sección "Conversaciones WhatsApp" se agregó al `mint.json` con el siguiente orden:

```json
{
  "group": "Conversaciones WhatsApp",
  "pages": [
    "whatsapp/overview",
    "whatsapp/view-conversations",
    "whatsapp/message-history",
    "whatsapp/pause-bot",
    "whatsapp/send-manual-message"
  ]
}
```

## Formato Mintlify MDX

Todos los archivos siguen el estándar Mintlify con:

- **Frontmatter YAML**: `title`, `description`
- **Componentes Mintlify**: `<Card>`, `<CardGroup>`, `<Steps>`, `<Step>`, `<Tip>`, `<Warning>`, `<Note>`, `<Accordion>`, `<AccordionGroup>`, `<Tabs>`, `<Tab>`
- **Markdown estándar**: Headers, listas, tablas, code blocks, enlaces
- **Diagramas Mermaid**: Flujos de arquitectura y procesos
- **Ejemplos de código**: Mensajes de WhatsApp, plantillas, JSON

## Calidad y Completitud

- ✅ 5 tutoriales completos (14-17KB cada uno)
- ✅ Estructura consistente con otros tutoriales del proyecto (appointments, services, etc.)
- ✅ Contexto técnico extraído de CLAUDE.md (100% preciso con arquitectura actual)
- ✅ Casos de uso reales y troubleshooting
- ✅ Mejores prácticas y ejemplos concretos
- ✅ Plantillas de mensajes reutilizables
- ✅ Indicadores visuales y metadatos técnicos explicados
- ✅ Integración con otros tutoriales (cross-links a appointments, etc.)

## Próximos Pasos (No Implementados)

Funcionalidades mencionadas como "en desarrollo" en los tutoriales:

1. **Exportación de conversaciones a CSV/Excel** (view-conversations.mdx)
2. **Pausa masiva de conversaciones (batch)** (pause-bot.mdx)
3. **Envío masivo de mensajes (broadcast)** (send-manual-message.mdx)
4. **Envío de multimedia (imágenes, videos, documentos)** (send-manual-message.mdx)

Estas se documentaron como "Funcionalidad en desarrollo" para guiar desarrollo futuro.

## Autor

Creado por Claude Code (Sonnet 4.5) el 2026-01-17.

Basado en especificaciones de CLAUDE.md y arquitectura existente del sistema.
