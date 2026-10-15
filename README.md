
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

