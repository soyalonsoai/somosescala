# Somos Escala Premium — Plugin Shell

Plugin de [Claude Code](https://claude.com/claude-code) que conecta a los miembros de la comunidad de **Somos Escala** con las skills premium servidas remotamente desde el MCP server de Somos Escala.

> Este repo **NO contiene las skills, references ni templates**. Solo es un conector mínimo. Todo el contenido se sirve desde un servidor MCP privado (ver "Cómo funciona" abajo).

## Quién puede usarlo

Miembros activos de la comunidad de **Somos Escala** (Skool). Al unirte a la comunidad recibes tu **Personal Token** — es la "llave" que te conecta al MCP.

Si no tienes token todavía, escríbenos desde la comunidad.

## Instalación

### 1. Setea tu token como variable de entorno

**macOS / Linux** (agrega a `~/.zshrc` o `~/.bashrc`):
```bash
export SOMOS_ESCALA_TOKEN="tu-token-aquí"
```

**Windows (PowerShell)**:
```powershell
[Environment]::SetEnvironmentVariable("SOMOS_ESCALA_TOKEN", "tu-token-aquí", "User")
```

Cierra y reabre la terminal para que cargue la variable.

### 2. Instala el plugin en Claude Code

```
/plugin marketplace add soyalonsoai/somos-escala-premium-plugin
/plugin install somos-escala-premium@somos-escala-premium-plugin
```

### 3. Verifica que está conectado

En Claude Code, escribe:

```
/mcp
```

Debería listar `somos_escala_premium` con estado conectado. Si dice "Authentication failed", revisa que `SOMOS_ESCALA_TOKEN` esté seteado correctamente.

## Uso

Una vez conectado, simplemente dile a Claude lo que quieres:

> "Quiero crear un bot de WhatsApp con GHL"
> "Tengo un cliente al que le voy a montar un bot de WhatsApp con GoHighLevel"

El asistente **Andrés** se activa automáticamente y te guía paso a paso.

## Skills disponibles

Las skills que tienes activas dependen de tu licencia. Para ver el listado actualizado, en Claude Code:

> "lista las skills que tengo disponibles"

(El LLM llamará a la tool `list_skills` del MCP.)

## Cómo funciona

```
Tú (Claude Code)
  ↓ Authorization: Bearer SOMOS_ESCALA_TOKEN
MCP Server de Somos Escala (en Railway, privado)
  ↓ valida tu licencia
  ↓ sirve skills, references y templates bajo demanda
```

- **El código fuente de las skills NO está en tu máquina.** Vive en el servidor.
- Cada vez que Claude necesita una referencia o un template, llama al MCP en tiempo real.
- Si tu licencia se cancela, el server deja de servirte contenido inmediatamente.

## Soporte

Cualquier duda o problema, escríbenos en la comunidad de Somos Escala.

## License

MIT — el código del plugin shell es abierto. El contenido servido por el MCP es privado y solo accesible con licencia válida.
