
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



# 🌐 Uso de servidores Git y remotos

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. ¿Por qué usar un servidor Git?** | Un servidor o servicio de alojamiento permite compartir repositorios, colaborar con otras personas y mantener una copia remota del historial. GitHub es una de las plataformas más usadas. | — |
| **2. Protocolos de acceso** | Los repositorios remotos suelen utilizar **HTTPS** o **SSH**. <br> - HTTPS: autenticación administrada por la plataforma. <br> - SSH: claves criptográficas configuradas en la cuenta. | — |
| **3. HTTPS y SSH** | Ejemplo de URL HTTPS: <br> `https://github.com/usuario/repositorio.git` <br><br> Ejemplo de URL SSH: <br> `git@github.com:usuario/repositorio.git` <br><br> ⚠️ No publiques contraseñas, tokens ni claves privadas en el repositorio. | — |
| **4. Configurar un remoto** | Si ya tienes un repositorio local, puedes asociarlo a un remoto vacío. Comprueba la URL y la rama actual antes de publicar para evitar errores. | `git remote add origin URL` <br> `git push -u origin main` |
| **5. Buenas prácticas** | - Verifica los permisos antes de publicar. <br> - Usa autenticación segura. <br> - Evita incluir secretos en commits. <br> - Revisa qué archivos se van a subir. <br> - Si se filtra una credencial, revócala o rótala de inmediato. | — |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git remote -v` | Consulta los remotos configurados. |
| `git remote add origin URL` | Añade un remoto llamado origin. |
| `git push -u origin main` | Publica main y establece su seguimiento, si la rama se llama main. |
| `ssh-keygen -t ed25519 -C "tu-correo@ejemplo.com"` | Genera una clave SSH en sistemas compatibles; protege la clave privada. |


# 🤝 Trabajo distribuido y colaboración en Git

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. Trabajo distribuido** | En Git, cada colaborador dispone de una copia completa del historial. Los equipos acuerdan cómo compartir cambios, revisar propuestas y decidir qué commits se integran. | — |
| **2. Modelos de colaboración** | - **Flujo centralizado**: varias personas publican en un repositorio compartido si tienen permisos. <br> - **Flujo basado en integración**: los colaboradores proponen cambios y una persona responsable los revisa antes de integrarlos. <br> - En proyectos públicos es habitual crear un **fork**, trabajar en una rama y abrir un *pull request*. | — |
| **3. Contribuir a un proyecto** | Antes de contribuir: <br> - Lee las instrucciones del proyecto. <br> - Identifica la rama de destino. <br> - Revisa las convenciones. <br> - Mantén los cambios enfocados. <br> - Describe claramente los commits. <br> - Ejecuta las pruebas pertinentes. | `git switch -c mejora-documentacion` <br> `git add README.md` <br> `git commit -m "Mejora la documentación"` |
| **4. Revisar y mantener cambios** | Quien mantiene el proyecto revisa la propuesta, solicita ajustes cuando sea necesario y decide cómo integrarla. Una revisión útil se centra en: <br> - Corrección <br> - Claridad <br> - Pruebas <br> - Compatibilidad con el proyecto | — |
| **5. Comunicación y trazabilidad** | Describe qué problema resuelve el cambio, cómo se verificó y si existen limitaciones. Una buena descripción facilita revisar el trabajo y entender decisiones futuras. | — |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git clone URL` | Obtiene una copia del proyecto. |
| `git switch -c mejora-documentacion` | Crea una rama de trabajo. |
| `git add README.md` | Prepara el archivo modificado. |
| `git commit -m "Mejora la documentación"` | Registra el cambio. |
| `git push -u origin mejora-documentacion` | Publica la rama para revisión. |



# 📂 Git vs GitHub y colaboración en repositorios

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. Git y GitHub no son lo mismo** | **Git** es el sistema de control de versiones que funciona localmente y en distintos servicios. <br> **GitHub** es una plataforma que aloja repositorios Git y añade herramientas de colaboración, revisión, seguimiento y automatización. | — |
| **2. Crear y configurar un repositorio** | Al crear un repositorio se elige nombre, visibilidad y opciones iniciales. <br> - **Público**: visible para cualquiera. <br> - **Privado**: acceso limitado a personas autorizadas. <br> Si el proyecto ya existe localmente, sigue las instrucciones de GitHub para conectarlo sin sobrescribir archivos o historiales. | `git remote add origin URL` |
| **3. Archivos importantes** | - `README.md`: presenta propósito, instrucciones y estructura del proyecto. <br> - `.gitignore`: indica qué archivos no debe seguir Git. <br> - **Licencia**: explica permisos de reutilización cuando corresponde. | — |
| **4. Colaboración** | GitHub permite: <br> - Revisar cambios mediante *pull requests*. <br> - Discutir propuestas en comentarios. <br> - Registrar tareas mediante *issues*. <br> Estas herramientas complementan el historial técnico de Git con contexto y comunicación. | `git push -u origin main` <br> `git pull origin main` |
| **5. Seguridad y mantenimiento** | - Usa permisos adecuados. <br> - Activa medidas de seguridad disponibles. <br> - Revisa los archivos antes de publicarlos. <br> - No incluyas contraseñas, tokens ni datos privados. | `git status` |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git remote add origin URL` | Conecta el repositorio local a GitHub. |
| `git push -u origin main` | Publica la rama main si ese es el nombre configurado. |
| `git pull origin main` | Obtiene e integra cambios de main. |
| `git status` | Revisa el estado antes de publicar. |


# 🛠️ Herramientas de Git

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. Inspeccionar commits y cambios** | Git permite consultar qué cambió, quién hizo una confirmación y cuándo. Los comandos de inspección son útiles para entender regresiones y verificar el alcance de una modificación. | `git show` |
| **2. Seleccionar y organizar cambios** | Es posible preparar solo partes de un archivo con herramientas interactivas. Esto ayuda a mantener commits pequeños y enfocados, en lugar de mezclar cambios no relacionados. | — |
| **3. Guardar trabajo temporalmente** | `git stash` permite apartar temporalmente cambios locales para cambiar de contexto. Antes de usarlo, consulta el estado del repositorio y recuerda que el contenido guardado debe recuperarse cuando sea necesario. | `git stash` <br> `git stash pop` |
| **4. Buscar y diagnosticar** | Git incluye herramientas para buscar texto en archivos seguidos, revisar cuándo se introdujo una línea y localizar la confirmación que pudo causar un problema. | `git grep "texto"` <br> `git blame archivo.txt` <br> `git bisect start` |
| **5. Recuperación y precaución** | Algunos comandos avanzados pueden cambiar referencias o descartar cambios. Antes de usar `reset`, limpieza de archivos o reescritura de historial, asegúrate de comprender el efecto y conserva una copia de cualquier trabajo importante. | — |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git show` | Muestra detalles de una confirmación. |
| `git stash` | Guarda temporalmente cambios locales. |
| `git stash pop` | Recupera cambios guardados y los retira de la lista si se aplican correctamente. |
| `git grep "texto"` | Busca texto en los archivos seguidos por Git. |
| `git blame archivo.txt` | Muestra la última confirmación asociada a cada línea. |
| `git bisect start` | Inicia una búsqueda binaria para localizar una regresión; requiere seguir el procedimiento de bisect. |



# ⚙️ Personalización de Git

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. Niveles de configuración** | Git puede tener configuraciones del sistema, del usuario y del repositorio. La configuración local de un repositorio prevalece sobre valores globales, lo que permite ajustar proyectos específicos. | — |
| **2. Consultar y cambiar opciones** | `git config` consulta y modifica preferencias como nombre, correo, editor, colores y comportamientos predeterminados. Comprueba el alcance de una opción antes de cambiarla. | `git config --global core.editor "code --wait"` |
| **3. Atributos de Git** | El archivo `.gitattributes` permite definir cómo se tratan ciertos archivos, por ejemplo reglas de fin de línea o filtros. Es útil para mantener un comportamiento consistente entre diferentes sistemas. | `git check-attr --all -- archivo.txt` |
| **4. Hooks** | Los hooks son scripts que se ejecutan en momentos específicos del flujo de Git, como antes de un commit. Pueden automatizar verificaciones, pero requieren cuidado en su configuración y mantenimiento. | — |
| **5. Recomendaciones** | - Documenta las convenciones del equipo. <br> - Evita configuraciones innecesariamente complejas. <br> - Prueba los cambios antes de aplicarlos a un proyecto importante. | — |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git config --global --list` | Muestra la configuración global. |
| `git config --local --list` | Muestra la configuración del repositorio actual. |
| `git config --global core.editor "code --wait"` | Ejemplo de configuración de editor; adapta el comando al editor instalado. |
| `git check-attr --all -- archivo.txt` | Consulta atributos aplicables a un archivo. |



# 🔄 Git y otros sistemas

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. Git como cliente** | Git puede participar en procesos de migración e interoperabilidad con otros sistemas. El método adecuado depende del sistema de origen, de la necesidad de conservar el historial y de las herramientas disponibles. | — |
| **2. Migrar un proyecto** | Antes de migrar, define qué se debe conservar: archivos actuales, ramas, etiquetas, autores, fechas e historial. Realiza una prueba en una copia y verifica que el resultado sea correcto antes de cambiar el flujo de trabajo oficial. | — |
| **3. Verificación posterior** | Compara la estructura de archivos, revisa las ramas y etiquetas, inspecciona las confirmaciones importadas y prueba el proceso habitual de trabajo. Mantén una copia de seguridad del repositorio original durante la transición. | `git log --oneline --all --decorate` <br> `git branch -a` <br> `git tag` |
| **4. Elegir una estrategia** | No existe un procedimiento único para todos los sistemas. Consulta la documentación oficial de la herramienta de origen y de Git, y selecciona un método que preserve los datos requeridos por el proyecto. | — |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git log --oneline --all --decorate` | Inspecciona el historial y las referencias disponibles. |
| `git branch -a` | Lista las ramas locales y las referencias remotas conocidas. |
| `git tag` | Lista las etiquetas existentes. |
| `git fsck` | Verifica la conectividad y validez de objetos del repositorio; úsalo como comprobación técnica, no como sustituto de una copia de seguridad. |



# 🧩 Los entresijos internos de Git

| Sección | Explicación | Ejemplo / Comando |
|---------|-------------|-------------------|
| **1. Comandos de alto y bajo nivel** | Los comandos habituales, llamados de alto nivel (*porcelain*), están diseñados para el trabajo diario. Los comandos de bajo nivel (*plumbing*) permiten examinar y manipular componentes internos de Git. | — |
| **2. Objetos Git** | Git almacena objetos que representan contenido y estructura: <br> - **Blobs**: contenido de archivos. <br> - **Trees**: estructura de directorios. <br> - **Commits**: instantáneas e información de historial. <br> - **Tags**: referencias anotadas. | `git cat-file -t HASH` <br> `git cat-file -p HASH` |
| **3. Referencias** | Las ramas y etiquetas son referencias que ayudan a localizar commits. **HEAD** indica normalmente la rama o confirmación sobre la que se está trabajando. Comprender las referencias ayuda a entender operaciones como cambiar de rama, fusionar o recuperar historial. | `git show-ref` <br> `git reflog` |
| **4. Almacenamiento y transferencia** | Git optimiza el almacenamiento mediante objetos comprimidos y, cuando corresponde, archivos de paquete. Para compartir datos, Git negocia qué objetos necesita enviar o recibir según el protocolo y las referencias involucradas. | — |
| **5. Mantenimiento y recuperación** | Git incluye herramientas para comprobar la integridad del repositorio y recuperar referencias o commits que ya no estén visibles desde una rama. Estas tareas son avanzadas; antes de intervenir en la base de datos interna, haz una copia y consulta la documentación. | `git fsck --full` |

---

## 📌 Comandos de referencia

| Comando | ¿Para qué sirve? |
|---------|------------------|
| `git cat-file -t HASH` | Muestra el tipo de un objeto, si existe en el repositorio. |
| `git cat-file -p HASH` | Muestra el contenido legible de un objeto. |
| `git show-ref` | Muestra referencias locales. |
| `git reflog` | Consulta el registro local de movimientos de referencias. |
| `git fsck --full` | Comprueba la integridad de los objetos del repositorio. |
