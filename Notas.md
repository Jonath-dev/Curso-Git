# Aprendiendo Git

## Configuracion
* Git config --global user.name "Jonath"
* Git config --global user.email Jonathangc.dev@gmail.com
* Git config --global init.defaultBranch main
* Git config --global pull.ff only
* Git config --global pull.rebase true
* Git config --global alias.s "status --short"
* Git config --global alias.lg "log --oneline --decorate --all --graph --abbrev-commit"

## Fundamentos de Git
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
* Git checkout file: Restablece el archivo conforme el ultimo commit.
    * Git checkout --.: Reconstruye el proyecto a como estaba en el ultimo commit.
    * Git chechout nombre-rama: Cambia a la rama ingresada.
    * Git cheackout HASH file: Restablece el archivo al punto en el tiempo ingresado.
* Git branch: Indica la rama actual.
    Git branch 'nueva-rama': Crea una nueva rama.
* Git branch -m master main: Renombra una rama en este caso de 'master' a 'main'.
* Git log: Muestra informacion del commit (Hash, author, date, etc).

## Profundizando en Git
* Git diff: Muestra las diferencias de un archivo como fue capturado en el ultimo commit contra los nuevos cambios.
    * Git diff --stage: Muestra los cambios de nuestros archivos en el stage con los actuales.
* Git commit --amend -m "Correccion de mensaje": Corrige el mensaje del ultimo commit.
* Git reflog: Historial de todos los commits.
* Git mv 'archivo.md' nuevo-nombre.md: Cambiamos el nombre de un archivo. Tambien sirve para mover, si no indicamos el directorio, solo cambia el nombre.
* Git rm 'archivo.md': Elimina un archivo.
* Git tag nombre-etiqueta: Crea una etiqueta en el HEAD.
    * Git tag -d nombre-etiqueta: Elimina la etiqueta. 
    * Git tag -a v1.0.0 -m "Version 1.0.0 Lista" : Nota con mensaje.
    * Git tag -a v1.0.0 Hash -m "Version 1.0.0 Lista": Crea la etiqueta en el commit correspondiente al hash.
* Git show v0.1.0: Muestra informacion detallada del tag.

## Git reset
* Git reset --soft HEAD^: Regresa los archivos a como estaban en el ultimo commit pero deshace el mismo.
    * Puedes sustituir HEAD por un hash del commit deseado. 
    * No destructivo. 
* Git reset --mix 345d7de: Regresa los archivos a como estaban en el commit.
    * No destructivo. 
* Git reset --hard 4e809d4: Regresa los archivos a como estaban en el ultimo commit pero destruyelos cambios.
    * Destructivo. 
    * Viajes al futuro

## Ramas y Uniones 
* Git merge rama-a-unir: Trae los cambios de la rama selecciona y los une con la rama actual.
* Git branch -d rama-a-eliminar: Elimina una rama.
    * -f: Forzar eliminacion.
* Git cheackout -b nueva-rama: Crea y posiciona en una nueva rama.

## Stash
* Git stash: Guarda los cambios no guardados para recuperarlos mas tarde.
    * Git stash list: Muestra la lista de stash.
        * Git stash list --stat: Muestra mas informacion de la lista.
    * Git stash pop: Recupera los archivos guardado y mantiene los cambios realizados hasta antes de recuperarlos.
    * Git stash clear: Elimina todo el stash.
    * Git stash drop n: Elimina el stash ingresado.
    * Git stash apply 'n': Regresa los archivos del numero de stash ingresado.
    * Git stash show n: Muestra informacion de los cambios en el stash deseado.
    * Git stash save "Agregamos un mensaje": crea un stash y un mensaje que sera mostrado en stash list.

## Rebase
* Git rebase: Separa los commits de una rama (generalmente la secundaria) para reordenarlos en un punto y rama diferente de donde fueron creados (rama principal).
    * Git rebase -i HEAD~4:
        * Squash (s): Junta el commit seleccionado con el anterior inmediato.
        * Reword (r): Cambia el mensaje de nuestro commit.
        * Edit: Sirve para separar commits.
        * Git rebase --continue: Al resolver los problemas, se utiliza este codigo para finalizar el rabese.
NOTAS: Sirve para reiniciar el punto inicial de nuestra rama. Se recomienda el uso si los los cambios a realizar no han sido subidos a github, ya que generara problemas a los demas.

# Aprendiendo GitHub
## Git remote
* Git remote add origin 'https://github.com/Jonath-dev/Curso-Git.git': Creamos la direccion remota de nuestro repositorio.
    * add: Agrega un nuevo remote. 
    * 'origin' nombre estandar del remoto.
    * 'https://github.com/Jonath-dev/Curso-Git.git': Direccion del remote, en este caso a nuestro repositorio llamado Curso-Git.git.
* Git remote -v: Vista de nuestros repositorios remotos.
* Git remote prune origin: limpia las ramas remotas que ya han sido eliminadas. 

## Push and Pull
* Git push -u origin master:Envia nuestros cambios al repositorio remoto.
    * origin: Nombre del repositorio que queremos subir.
    * master: Rama que deseamos enviar.
* Git push --tag: Envia los tags al origen remoto.
* git push --set-upstream origin rama-nombre: Sube una rama secundaria a nuestro repositorio.
* Git push origin :rama-nombre: Elimina una rama en github desde linea de comando.
* Git pull: Trae los cambios del repositorio remoto a nuestro repositorio local. 
    * Git pull origin main (En caso de no tener predefinido el origen -u).
    * Git config pull.rebase true: En caso de no ser posible un fastforward, podemos hacer un rebase en el pull con este codigo.

## Clone
* Git clone 'https://github.com/Jonath-dev/Curso-Git.git': Clona es repositorio remoto al directorio donde nos encontremos, al clonar un repositorio es posible ver los commits anteriores y viajar en el tiempo como si fuera nuestro repositorio local.

## Fetch
* Git fetch: Trae los commits del repositorio remoto al repositorio local pero sin hacer un merge con muestra rama principal.

## Forks 
Los forks son una copia de un repositorio ajeno, al que tendremos acceso como si fuera nuestro, con un git clone podemos enlazarlo con un repositorio local.