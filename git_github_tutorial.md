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
> Reviando el estado `git status`  
~~~ bash
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
~~~
2. Si deseas empezar a controlar versiones de archivos existentes debes hacer una confirmación inicial `git add` y `git commit`
## **Ejemplo:**  

* Creamos un markdown `touch ejemplo.md` luego revisamos el estado 
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

* Pasar a **Staging Area** `git add ejemplo.md` y revisar estado  
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
* Finalmente levar a **.Git-Repository** `git commit -m 'ejemplo git'` y vericamos el estado  
~~~bash
$ git commit -m 'ejemplo git'
[main 651f3a5] ejemplo git
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

## Clonando un repositorio existente  

* Con una conexion ssh `git clone git@github.com:JRichard-Prado/Git-GitHub.git git_test`

* Utilizando Https `git clone https://github.com/JRichard-Prado/Git-GitHub.git`


`git remote -v show`