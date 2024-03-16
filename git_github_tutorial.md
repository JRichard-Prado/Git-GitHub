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
> para una clave específica ejecutando `git config user.name` tambien `config user.email`  
~~~ bash
    $ git config user.name
    JRichard-Prado

    $ git config user.email
    jrichip@hotmail.com
~~~

> ¿Cómo obtener ayuda? ejecutando `$ git help config`  

## Obteniendo un repositorio Git

1. Inicializando un repositorio en un directorio existente `git init`

> Si deseas empezar a controlar versiones de archivos existentes debes hacer una confirmación inicial `git add` y `git commit`  

## Clonando un repositorio existente  

* Con una conexion ssh `git clone git@github.com:JRichard-Prado/Git-GitHub.git git_test`

* Utilizando Https `git clone https://github.com/JRichard-Prado/Git-GitHub.git`


`git remote -v show`