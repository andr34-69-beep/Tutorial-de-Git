
# Tutorial-de-Git

Este es un repositorio dedicado a hacer un tutorial de Git guiándome por el libro PDF oficial.

---

# Inicio y control de versiones

## ¿Qué es el control de versiones?

Un sistema de control de versiones registra cambios en archivos a lo largo del tiempo. Permite consultar versiones anteriores, comparar modificaciones y recuperar trabajo cuando ocurre un error.

En proyectos académicos, de programación o documentación, este historial ayuda a entender qué cambió, cuándo se cambió y por qué.

## 2. ¿Qué es Git?

Git es un sistema de control de versiones distribuido. Cada clon de un repositorio contiene una copia del historial, por lo que muchas operaciones pueden hacerse localmente, sin conexión constante a un servidor.

Git identifica el contenido mediante hashes y registra instantáneas del proyecto en las confirmaciones (*commits*).

## 3. Conceptos esenciales

**Repositorio:** carpeta y base de datos donde Git guarda los archivos seguidos y su historial.

**Commit:** registro identificado de un estado del proyecto.

**Directorio de trabajo:** archivos que se están editando.

**Área de preparación (*staging area*):** selección de cambios que se incluirán en el próximo commit.

**Rama (*branch*):** línea de desarrollo que permite trabajar sin alterar directamente otra línea.

## 4. Instalar y comprobar Git

Descarga Git desde https://git-scm.com/downloads y sigue las instrucciones del sistema operativo. En Windows, Git Bash ofrece una terminal con comandos de Git.

Comprueba la instalación ejecutando:

```bash
git --version
```

## 5. Configurar la identidad

Configura el nombre y el correo que aparecerán en los commits. Sustituye los ejemplos por tus datos:

```bash
git config --global user.name "Tu Nombre"
```

```bash
git config --global user.email "tu-correo@ejemplo.com"
```

## 6. Obtener ayuda

Git incluye ayuda para comandos concretos. Puedes consultar `git help config` o `git config -h`.

---

## Comandos de referencia

| Comando | Descripción |
|---|---|
| `git --version` | Comprueba la versión instalada. |
| `git config --global user.name "Tu Nombre"` | Define el nombre para los commits. |
| `git config --global user.email "tu-correo@ejemplo.com"` | Define el correo para los commits. |
| `git config --list` | Muestra la configuración efectiva. |





# FUNDAMENTOS DE GIT

## 1. Crear u obtener un repositorio
Un repositorio puede iniciarse dentro de una carpeta existente o copiarse desde un servidor mediante clonación. Usa `git init` para iniciar un proyecto local y `git clone` para obtener una copia de un repositorio existente.

## 2. El ciclo de trabajo
El flujo más habitual consiste en editar archivos, revisar su estado, seleccionar los cambios con `git add` y guardarlos en el historial con `git commit`.  
Un archivo puede estar modificado, preparado o confirmado. Revisar el estado antes de confirmar evita incluir cambios por accidente.

## 3. Inspeccionar diferencias e historial
- `git diff` ayuda a revisar cambios que todavía no están preparados.  
- `git diff --staged` muestra los cambios preparados.  
- `git log` permite consultar las confirmaciones anteriores.

## 4. Corregir errores con cuidado
Git ofrece mecanismos para retirar archivos del área de preparación, modificar la última confirmación o recuperar versiones.  
Antes de ejecutar comandos que descarten cambios, revisa el estado y asegúrate de que no necesitas el contenido.

## 5. Trabajar con repositorios remotos
Un remoto es una referencia a otro repositorio, por ejemplo uno alojado en GitHub.  
- `git remote -v` muestra las direcciones configuradas.  
- `git push` publica commits.  
- `git pull` obtiene e integra cambios remotos.

## 6. Etiquetas y alias
Las etiquetas permiten señalar puntos importantes del historial, como versiones publicadas.  
Los alias permiten abreviar comandos frecuentes; son opcionales y conviene aprender primero los comandos originales.

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git init` | Inicia un repositorio en la carpeta actual. |
| `git clone URL` | Copia un repositorio remoto. |
| `git status` | Muestra los cambios y su estado. |
| `git add archivo.txt` | Prepara un archivo concreto. |
| `git commit -m "Describe el cambio"` | Guarda una confirmación. |
| `git diff` | Muestra cambios no preparados. |
| `git diff --staged` | Muestra cambios preparados. |
| `git log --oneline` | Resume el historial. |
| `git remote -v` | Muestra los remotos configurados. |
| `git push` | Envía commits al remoto configurado. |
| `git pull` | Obtiene e integra cambios remotos. |



# Ramas en Git

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. ¿Qué es una rama?** | Una rama es una referencia móvil a una confirmación. Permite desarrollar una función o experimentar sin mezclar inmediatamente esos cambios con la rama principal. Son ligeras y no duplican todos los archivos. | — |
| **2. Crear y cambiar de rama** | Antes de cambiar de rama, revisa si tienes modificaciones sin confirmar. Git puede impedir el cambio para proteger tus cambios. Se recomienda `git switch`. | `git switch -c nueva-funcion` <br> `git switch main` |
| **3. Fusionar ramas** | Una fusión integra el trabajo de una rama en otra. Primero se cambia a la rama que recibirá los cambios y luego se ejecuta `git merge`. | `git switch main` <br> `git merge nueva-funcion` |
| **Ejemplo de conflicto** | Si dos ramas modifican la misma línea, Git marca el archivo con secciones: <br> ```<<<<<<< HEAD``` <br> ```Versión en main``` <br> ```=======``` <br> ```Versión en nueva-funcion``` <br> ```>>>>>>> nueva-funcion``` | Resolución: editar el archivo, decidir el contenido final, luego: <br> `git add index.html` <br> `git commit -m "Resolver conflicto"` |
| **4. Administrar ramas** | `git branch` lista las ramas locales. `git branch -d` elimina una rama ya integrada. No elimines ramas con trabajo importante sin revisar. | `git branch` <br> `git branch -d nueva-funcion` |
| **5. Ramas remotas y reorganización** | Las ramas remotas representan el estado conocido en otro repositorio. `fetch`, `pull` y `push` actualizan y comparten cambios. El **rebase** reaplica commits sobre otra base para un historial lineal. | `git fetch origin` <br> `git pull origin main` <br> `git push origin nueva-funcion` <br> `git rebase main` |
| **⚠️ Nota sobre rebase** | Evita reescribir historial que otras personas ya estén usando sin coordinarlo. | — |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git branch` | Lista las ramas locales. |
| `git switch -c nueva-funcion` | Crea una rama y cambia a ella. |
| `git switch main` | Cambia a la rama main, si existe. |
| `git merge nueva-funcion` | Integra la rama indicada en la rama actual. |
| `git branch -d nueva-funcion` | Elimina una rama local integrada. |
| `git fetch` | Actualiza referencias desde un remoto sin integrar automáticamente. |
| `git rebase main` | Reaplica commits de la rama actual sobre main; úsalo con cuidado. |

