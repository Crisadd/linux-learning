# 📖 Installation In Windows

> **The best way to learn Linux (and programming in general) is by doing.**
> Practice makes perfect.


# Ubuntu en Windows con WSL2 (Guía para practicar Linux)

## Objetivo

Instalar **Ubuntu usando WSL2 (Windows Subsystem for Linux)** para
practicar Linux de forma nativa en Windows.


## Ventajas
-   No necesita una máquina virtual.
-   Consume muy pocos recursos.
-   Se integra perfectamente con Windows.
-   Compatible con Visual Studio Code.
-   Es la opción utilizada por muchísimos desarrolladores y DevOps.

------------------------------------------------------------------------

# Instalación

## 1. Abrir PowerShell como Administrador

Buscar **PowerShell** en el menú Inicio.

Seleccionar:

**Ejecutar como administrador**

------------------------------------------------------------------------

## 2. Instalar WSL2

Ejecutar:

``` powershell
wsl --install
```

Este comando instala automáticamente:

-   WSL2
-   Ubuntu
-   Todo lo necesario para comenzar

------------------------------------------------------------------------

## 3. Reiniciar la computadora

Una vez finalizada la instalación.

------------------------------------------------------------------------

## 4. Abrir Ubuntu

Desde el menú Inicio buscar:

    Ubuntu

La primera vez solicitará crear un usuario.

Ejemplo:


Username:
# crisad

Password:
# Charmnd...


> La contraseña no se muestra mientras se escribe. Es completamente
> normal.

------------------------------------------------------------------------

## 5. Actualizar Ubuntu

``` bash
sudo apt update
sudo apt upgrade -y
```

Ingresar la contraseña creada anteriormente.

------------------------------------------------------------------------

# Verificar la instalación

Ejecutar:

``` bash
pwd
ls
mkdir prueba
cd prueba
touch archivo.txt
ls
```

Si todo funciona correctamente, Ubuntu ya está listo para usar.

------------------------------------------------------------------------

# Comandos básicos para practicar

``` bash
pwd
ls
cd
mkdir
touch
rm
cp
mv
cat
less
head
tail
grep
find
chmod
chown
sudo
nano
vim
```

------------------------------------------------------------------------

# Mini laboratorio de práctica

Crear la siguiente estructura:

``` text
linux-lab/
├── documents/
│   ├── notes.txt
│   └── passwords.txt
├── scripts/
│   └── backup.sh
├── photos/
└── temp/
```

## Después de instalar la extensión

Cuando Ubuntu ya esté funcionando, vamos a ejecutar estos comandos:

Actualizar Ubuntu:

sudo apt update
sudo apt upgrade -y

Instalar Git:

sudo apt install git -y

Verificar:

git --version

Crear tu carpeta de trabajo:

mkdir ~/linux-learning
cd ~/linux-learning

Abrir VS Code:

code .
Lo bueno es que ya no vas a usar PowerShell para practicar Linux

A partir de ahora prácticamente todo lo vas a hacer desde la terminal de Ubuntu.

Por ejemplo, cuando hagas los ejercicios de Linux Journey que ya empezaste (como File Permissions), los vas a probar directamente en Linux en lugar de solo leer la teoría. Esa práctica es la que realmente te va a hacer ganar soltura.

🚀 Tengo una idea para organizar todo tu aprendizaje: cuando terminemos de configurar Ubuntu, podemos crear un entorno profesional con una estructura de carpetas (linux-learning, python-learning, devops-labs, etc.), configurar Git y GitHub, y dejar tu PC lista para todo el roadmap hacia Cloud/DevOps. Te va a quedar un entorno limpio y muy parecido al que se usa en un trabajo real.