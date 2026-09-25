# 🧭 Consejos de uso de Git

Guia rapida con lo esencial de Git para participar en las rondas de **La Forja del Código**. No pretende ser un curso completo, sino un resumen practico de los comandos que más vas a usar.

## Índice

- [Configuración inicial](#configuración-inicial-solo-una-vez-por-equipo)
- [Crear o iniciar un repositorio](#crear-o-iniciar-un-repositorio)
- [Flujo basico del día a día](#flujo-básico-del-día-a-día)
- [Ramas (branches)](#ramas-branches)
- [Remotos](#remotos)
- [Revisar historial](#revisar-historial)
- [Deshacer cambios](#deshacer-cambios-los-comandos-que-salvan-vidas)
- [.gitignore](#gitignore)
- [Buenas practicas rápidas](#buenas-prácticas-rápidas)
- [Documentación sugerida](#-documentación-sugerida)

---

## Configuración inicial (solo una vez por equipo)

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

## Crear o iniciar un repositorio

```bash
git init                      # Inicializa un repo nuevo en la carpeta actual
git clone <url>                # Clona un repo existente
```

## Flujo básico del día a día

```bash
git status                     # Ver qué archivos cambiaron
git add archivo.py             # Agregar un archivo específico al staging
git add .                      # Agregar todos los cambios al staging
git commit -m "feat: mensaje"  # Guardar los cambios con un mensaje descriptivo
git push                       # Subir los cambios al repo remoto
git pull                       # Traer los cambios más recientes del remoto
```

> **Regla de oro:** commitea seguido y en pedazos pequeños. Es más fácil revisar (y revertir si algo sale mal) 10 commits chicos que 1 commit gigante con toda la ronda adentro.

## Ramas (branches)

```bash
git branch                     # Ver ramas existentes
git branch nombre-rama         # Crear una rama nueva
git checkout nombre-rama       # Cambiarte a esa rama
git checkout -b nombre-rama    # Crear y cambiarte en un solo paso
git merge nombre-rama          # Fusionar una rama a la actual
```

Úsalas para probar cosas sin romper tu rama principal (`main`), especialmente si trabajas en equipo.

## Remotos

```bash
git remote -v                          # Ver los remotos configurados
git remote add origin <url>            # Conectar tu repo local a uno remoto
git remote set-url origin <url>        # Cambiar la URL del remoto
```

## Revisar historial

```bash
git log                        # Ver historial de commits
git log --oneline              # Versión resumida, una línea por commit
git diff                       # Ver cambios no confirmados aún
```

## Deshacer cambios (los comandos que salvan vidas)

```bash
git restore archivo.py                 # Descartar cambios no confirmados en un archivo
git reset HEAD archivo.py              # Sacar un archivo del staging (sin perder el cambio)
git revert <hash-del-commit>           # Crear un commit nuevo que deshace uno anterior (seguro)
git reset --soft HEAD~1                # Deshacer el último commit, manteniendo los cambios
```

> ⚠️ **Cuidado:** evita `git reset --hard` a menos que estés muy seguro — borra cambios sin posibilidad de recuperarlos fácilmente.

## .gitignore

Archivo que le dice a Git qué **no** debe subir nunca (claves, dependencias, archivos temporales). Ejemplo mínimo:

```gitignore
.env
__pycache__/
node_modules/
*.log
.DS_Store
```

> 🔐 **Seguridad:** revisa siempre que tu `.env` (o cualquier archivo con contraseñas/tokens) esté en el `.gitignore` **antes** de tu primer commit. Si ya subiste una clave por error, cámbiala de inmediato — no basta con borrarla en un commit nuevo, queda visible en el historial.

## Buenas prácticas rápidas

- Haz `git status` antes de cada `add`, así sabes exactamente qué estás por subir.
- Nunca hagas `git add .` a ciegas sin revisar qué archivos cambiaron.
- Usa mensajes de commit descriptivos (ver [`commit-guidelines.md`](./commit-guidelines.md) del repo).
- Haz `git pull` antes de empezar a trabajar si estás en equipo, para evitar conflictos.
- Si algo sale mal, respira: casi todo en Git se puede solucionar. Pregunta antes de forzar algo (`--force`, `--hard`).

---

## 📚 Documentación sugerida

- [Git - Guía oficial](https://git-scm.com/doc)
- [Aprende Git ramificando (interactivo)](https://learngitbranching.js.org/)
- [Pro Git (libro gratuito, en español)](https://git-scm.com/book/es/v2)
- [Midu.dev Buenas practicas para commits)](https://midu.dev/buenas-practicas-escribir-commits-git/)

## 📺 Videos sugeridos

- [MoureDev - Curso COMPLETO de GIT y GITHUB desde CERO para PRINCIPIANTES](https://www.youtube.com/watch?v=3GymExBkKjE)
- [ByteByteGo - Cómo funciona Git: Explicado en 4 minutos](https://www.youtube.com/watch?v=e9lnsKot_SQ)

## 📦 Repositorio sugerido

- [Hello Git (MoureDev)](https://github.com/mouredev/hello-git)
