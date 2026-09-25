# 🤖 Uso Ético de la IA en La Forja del Código

La IA (ChatGPT, Claude, Copilot, etc.) es una herramienta válida y bienvenida en las rondas — la mayoría de nosotros la usamos día a día en el trabajo real. Pero como el objetivo de la Forja es **aprender**, no solo "producir", esta guía busca que la uses de forma que realmente te haga crecer como developer.

## Índice

- [La regla de oro](#la-regla-de-oro)
- [Sí y No del uso de IA](#-sí-y-no-del-uso-de-ia)
- [Sugerencias de prompts útiles](#-sugerencias-de-prompts-útiles)
- [Cómo declarar el uso de IA en tu entrega](#cómo-declarar-el-uso-de-ia-en-tu-entrega)
- [Seguridad con IA](#-seguridad-con-ia)
- [Otros consejos](#-otros-consejos)

---

## La regla de oro

> **Si no puedes explicar una línea de tu propio código, no la entregues sin entenderla primero.**

Usar IA para *acelerar* está perfecto. Usar IA para *evitar aprender* le quita el sentido a la ronda — y se nota en la revisión entre pares, porque ahí sí tendrás que explicar qué hiciste y por qué.

## ✅ Sí y ❌ No del uso de IA

### ✅ Está muy bien:
- Pedir que te explique un error o un concepto que no entiendes.
- Generar un primer boceto/esqueleto de código para no partir de cero, y luego modificarlo tú mismo.
- Pedir feedback o revisión de código que **tú** ya escribiste.
- Usarla para investigar documentación, comparar enfoques o resolver dudas puntuales.
- Pedir ayuda para debuggear, entendiendo el porqué del fix, no solo copiando la solución.
- Usarla para mejorar tu README o redactar mejor tu documentación.

### ❌ Mejor evitar:
- Pegar el enunciado completo de la ronda y copiar la respuesta tal cual, sin revisarla ni entenderla.
- Entregar código que no sabrías explicar si te preguntan en la revisión.
- Pedirle a la IA que resuelva TODO el proyecto de principio a fin sin que tú intervengas.
- Usarla para "camuflar" que no tocaste una tecnología nueva cuando esa era justamente la gracia de la ronda.

## 💡 Sugerencias de prompts útiles

Prompts que te ayudan a **aprender** en vez de solo recibir una respuesta armada:

**Para entender antes de escribir:**
```
Explícame el concepto de [X] como si nunca lo hubiera usado, 
con un ejemplo simple antes de mostrarme código real.
```

**Para generar un punto de partida (no la solución final):**
```
Dame solo la estructura/esqueleto básico de [X], sin implementar 
toda la lógica, para que yo complete el resto.
```

**Para debuggear entendiendo:**
```
Tengo este error: [pega el error]. Antes de darme el fix, 
explícame por qué está pasando esto.
```

**Para revisar tu propio código:**
```
Revisa este código que escribí [pega tu código] y dime qué 
mejorarías, sin reescribirlo tú — solo señala los problemas.
```

**Para comparar enfoques:**
```
¿Cuáles son 2-3 formas distintas de resolver [X] en [tecnología], 
y qué ventajas/desventajas tiene cada una?
```

**Para aprender de errores propios:**
```
¿Qué patrón de error suelo cometer según este código? 
[pega tu código] ¿Qué debería revisar la próxima vez?
```

## Cómo declarar el uso de IA en tu entrega

No es obligatorio, pero se agradece (y da puntos de honestidad ante el grupo) agregar una sección corta en tu README:

```markdown
## Uso de IA
Usé [herramienta] para: [ej. generar el boilerplate inicial del 
modelo, debuggear un error de conexión a la DB, mejorar la 
redacción de este README].
```

Esto no te resta mérito — al contrario, ayuda a que todos aprendamos también **cómo** usar bien estas herramientas, que es una habilidad en sí misma.

## 🔐 Seguridad con IA

- **Nunca pegues tu `.env`, claves, tokens o contraseñas** en un chat de IA, aunque sea "solo para que me ayude a revisar". Quedan en el historial de la herramienta.
- Si compartes código con IA para pedir ayuda, revisa antes que no tenga credenciales hardcodeadas.
- Ojo con pegar código de un repo privado o con datos sensibles de terceros en herramientas de IA públicas.

## 🎯 Otros consejos

- **Usa la IA como a un compañero senior, no como a un oráculo.** Un buen compañero te hace preguntas de vuelta, no solo te da la respuesta.
- **Escribe tú primero, pregunta después.** Intenta resolver el problema 10-15 minutos por tu cuenta antes de preguntar — vas a retener mucho más.
- **Compara respuestas de distintas IAs** si algo no te queda claro; a veces una explica mejor que otra un mismo concepto.
- **No le tengas miedo a la IA, ni dependencia ciega de ella.** El objetivo de la Forja es que salgas de cada ronda sabiendo hacer algo que no sabías antes — con o sin IA de por medio, eso depende de ti.
- **Recuerda o investiga algunos fundamentos de la IA que utilices, crea skills (o como lo llame la IA que uses) para optimizar el contexto**
- Tambien puedes pasar documentos y convertirlos en formato markdown en paginas gratuitas de internet para ahorrar tokens.

## 💡 Repositorios utiles para mejorar el trabajo de la IA

-[Repositorio oficial de antropic para skills](https://github.com/anthropics/skills)
-[Repositorio de multiples Skills](https://github.com/obra/superpowers)

## 📚 Documentacion que puede ayudar

-[Documentación oficial de antropic Skills](https://platform.claude.com/docs/es/agents-and-tools/agent-skills/best-practices)

## 📺 Videos que pueden ayudar

--[Juan gabriel- Tutorial de skill de Claude](https://www.youtube.com/watch?v=h9C4fLQM_2I)