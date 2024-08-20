# Configurando Git por primera vez  

## Tu Identidad  

1. Establecer tu nombre de usuario y dirección de correo electrónico.  

```
$ git config --global user.name "JRichard-Prado"
$ git config --global user.email "jrichip@hotmail.com"
```  
2. Comprobando tu Configuración  `git config --list` 
~~~ bash
    diff.astextplain.textconv=astextplain
    filter.lfs.clean=git-lfs clean -- %f
    filter.lfs.smudge=git-lfs smudge -- %f
    filter.lfs.process=git-lfs filter-process
    filter.lfs.required=true
    http.sslbackend=openssl
    http.sslcainfo=C:/Program Files/Git/mingw64/etc/ssl/certs/ca-bundle.crt
    core.autocrlf=true
    core.fscache=true
    core.symlinks=false
    core.symlinks=false
    pull.rebase=false
    init.defaultbranch=master
    filter.lfs.smudge=git-lfs smudge -- %f
    filter.lfs.process=git-lfs filter-process
    filter.lfs.required=true
    filter.lfs.clean=git-lfs clean -- %f
    user.name=JRichard-Prado
    user.email=jrichip@hotmail.com
    init.defaultbranch=main
(END)
~~~  
> Para una clave específica ejecutando `git config user.name` tambien `config user.email`  
~~~ bash
    $ git config user.name
    JRichard-Prado

    $ git config user.email
    jrichip@hotmail.com
~~~

> ¿Cómo obtener ayuda? ejecutando `$ git help config`  

## Obteniendo un repositorio Git

1. Inicializando un repositorio en un directorio existente `git init` Esto crea un subdirectorio nuevo llamado .git

## Ejemplo:  
* Crear un directorio nuevo `mkdir ejemplo_git_init` ingresar dentro `cd ejemplo_git_init/` verificar el contenido con `ls -la`  
~~~bash
total 4
drwxr-xr-x 1 User 197121 0 mar. 16 11:52 ./
drwxr-xr-x 1 User 197121 0 mar. 16 11:52 ../
~~~  
Inicializando el repositorio git `git init` y verificar el directorio .git `ls -la`  
~~~bash
$ git init
Initialized empty Git repository in C:/Users/User/Documents/GitHub/ejemplo_git_init/.git/
~~~  
~~~bash
$ ls -la
total 8
drwxr-xr-x 1 User 197121 0 mar. 16 11:57 ./
drwxr-xr-x 1 User 197121 0 mar. 16 11:52 ../
drwxr-xr-x 1 User 197121 0 mar. 16 11:57 .git/
~~~
> Revisando el estado `git status` ya tendriamos listo el git en local 
~~~ bash
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
~~~
2. Si deseas empezar a controlar versiones de archivos existentes debes hacer una confirmación inicial `git add` y `git commit`
## **Ejemplo: markdown**  

* **Creamos un archivo** markdown `touch ejemplo.md` luego revisamos el estado 
~~~ bash
$ git status -s
?? ejemplo.md
~~~ 
~~~ bash
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        ejemplo.md

nothing added to commit but untracked files present (use "git add" to track)
~~~ 

* **Modificar y Pasar a Staging Area** `git add ejemplo.md` y revisar estado  
~~~
$ git status -s
A  ejemplo.md
~~~
~~~
$ git add ejemplo.md

User@DESKTOP-7S8SE4N MINGW64 ~/Documents/GitHub/Git-GitHub (main)
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   ejemplo.md
~~~ 
* **Confirmar tus Cambios** guardar a **Git-Repository** `git commit -m 'texto descriptivo'` y vericamos el estado  
~~~bash
$ git commit -m 'Texto descriptivo: ejemplo git'
[main 651f3a5] Texto descriptivo: ejemplo git
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 ejemplo.md

$ git status -s
 M git_github_tutorial.md
~~~  
~~~bash
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   git_github_tutorial.md

no changes added to commit (use "git add" and/or "git commit -a")
~~~
* **Historial de Confirmaciones todos los commit** `git log --oneline` ó `git log`
~~~bash
36cd6f0 (HEAD -> main, origin/main) git log
cabe7f8 status git inicial
6a28302 edit ortografia
2bd2314 ejemplo git init
~~~  
~~~bash
Author: JRichard-Prado <jrichip@hotmail.com>
Date:   Sat Mar 16 20:40:12 2024 +0100

Date:   Sat Mar 16 20:40:12 2024 +0100

    git log

commit cabe7f8792e0b0eeafd634533064a4278cb26e9b
Author: JRichard-Prado <jrichip@hotmail.com>
Date:   Sat Mar 16 12:16:22 2024 +0100

    status git inicial
~~~  
  - Navegando dentro del log `git reset --hard cabe7f8` 
  ~~~bash
  HEAD is now at cabe7f8 status git inicial
  ~~~  
  ~~~ bash
  $ git log --oneline
    cabe7f8 (HEAD -> main) status git inicial
    6a28302 edit ortografia
    2bd2314 ejemplo git init
    a1e7c27 ejemplo git
  ~~~
## Deshacer Cosas 
- si confirmas y luego te das cuenta que olvidaste preparar los cambios de un archivo.

  ~~~ bash
  $ git commit -m 'initial commit'
  $ git add forgotten_file
  $ git commit --amend
  ~~~
## Trabajar con Remotos - Clonando un repositorio existente  
  - **Ver los remotos** que tienes configurados
    ~~~ bash
    Prado@DESKTOP-72MFJHI MINGW64 ~/Desktop/Angular/Angular (main)
    $ git remote
    origin
    ~~~
    ~~~ bash
    $ git remote -v show
    origin  https://github.com/JRichard-Prado/Git-GitHub.git (fetch)
    origin  https://github.com/JRichard-Prado/Git-GitHub.git (push)
    ~~~
- **Añadir Repositorios** Remotos 

    (pedira contraseña de usuario github)

  ~~~ bash
  git remote add origin https://github.com/JRichard-Prado/Angular.git
  ~~~
  Mediante llave ssh 
  ~~~ bash 
  Prado@DESKTOP-72MFJHI MINGW64 ~/Desktop/Angular/Angular (main)
  $ git remote add origin git@github.com:JRichard-Prado/Angular.git
  ~~~
- **Eliminar y Renombrar Remotos**

  ~~~ bash
  $ git remote rename pb paul
  $ git remote
  origin
  paul
  ~~~
  ~~~ bash 
  $ git remote rm paul
  $ git remote
  origin
  ~~~
* Clonar Con una conexion ssh `git clone git@github.com:JRichard-Prado/Git-GitHub.git git_test`


* Utilizando Https `git clone https://github.com/JRichard-Prado/Git-GitHub.git`
- Ir al directorio destino
  ~~~ bash
  Prado@DESKTOP-72MFJHI MINGW64 ~/Desktop/Angular/Angular (main)
  $ cd C:/Users/Prado/Desktop

  Prado@DESKTOP-72MFJHI MINGW64 ~/Desktop
  ~~~
  ~~~ bash
  Prado@DESKTOP-72MFJHI MINGW64 ~/Desktop
  $ git clone https://github.com/JRichard-Prado/Git-GitHub.git
  Cloning into 'Git-GitHub'...
  remote: Enumerating objects: 47, done.
  remote: Counting objects: 100% (47/47), done.
  remote: Compressing objects: 100% (31/31), done.
  remote: Total 47 (delta 25), reused 33 (delta 14), pack-reused 0 (from 0)
  Receiving objects: 100% (47/47), 7.37 KiB | 198.00 KiB/s, done.
  Resolving deltas: 100% (25/25), done.
  ~~~
  ~~~ bash
  Prado@DESKTOP-72MFJHI MINGW64 ~/Desktop
  $ cd Git-GitHub/
  ~~~
  ~~~ bash
  $ ls
  git_github_tutorial.md  README.md
  ~~~

## Traer y Combinar Remotos
## Enviar a Tus Remotos
- El comando para hacerlo es simple: git push `[nombre-remoto] [nombre-rama]` verificar configuracion de remotos con `git remote -v show`
  ~~~
  Prado@DESKTOP-72MFJHI MINGW64 ~/Desktop/Angular/Angular (main)
  $ git remote -v show
  origin  git@github.com:JRichard-Prado/Angular.git (fetch)
  origin  git@github.com:JRichard-Prado/Angular.git (push)
  ~~~

  ~~~ bash
  $ git push origin main
  Enumerating objects: 39, done.
  Counting objects: 100% (39/39), done.
  Delta compression using up to 2 threads
  Compressing objects: 100% (37/37), done.
  Writing objects: 100% (39/39), 125.50 KiB | 1.53 MiB/s, done.
  Total 39 (delta 4), reused 0 (delta 0), pack-reused 0 (from 0)
  remote: Resolving deltas: 100% (4/4), done.?[K
  To github.com:JRichard-Prado/Angular.git
  * [new branch]      main -> main
  ~~~
