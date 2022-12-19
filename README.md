# Aprendiendo Git

## Configuracion
* Git config --global user.name "Jonath"
* Git config --global user.email Jonathangc.dev@gmail.com
* Git config --global init.defaultBranch main
* Git config --global alias.s status --short
* Git config --global alias.lg "log --oneline --decorate --all --graph --abbrev-commit"

## Primeros comandos
* Git init: Inicializa nuestro repositorio.
* Git status: Muestra informacion sobre commits, rama y archivos.
    * Git status --short: Version corta de status.
* Git add: Mueve el archivo seleccionado al Stage.
    * Git add .: Agrega todos los archivos al stage. 
    * Git add *.html: Agrega todos los archivos con la misma extension.
    * Git add css/: Agrega todos los archivos dentro del directorio indicado.
* Git reset 'archivo': Saca el archivo del stage.
* Git commit -m "Nombre commit": Crea un commit con los archivos en el stage, Debe agregarse un comentario significativo.
    * Git commit -am "Mesage": Agrega todos los archivos seguidos al stage y crea un commit.
* Git checkout --.: Reconstruye el proyecto a como estaba en el ultimo commit.
* Git branch: Indica la rama actual.
* Git branch -m master main: Renombra una rama en este caso de 'master' a 'main'.
* Git log: Muestra informacion del commit (Hash, author, date, etc).