# scesiGIT
## clase D1
## titulo: Introduccion
git es un sistema de controles de verssion distribuidio
   permite guardar versones de un proyeto y permite contribuciones
   fue creado por Linux Torbax 
## clase D2
## titulo:Flujo de trabajo
consta de 4 fases :
### WORKING DIRECTORY
es la carpeta donde estás trabajando normal
git solo observa, no guarda todavía
los archivos pueden estar así:

untracked → archivo nuevo, git aún no lo sigue
modified → archivo que ya existía pero lo cambiaste
cuando está modified significa que ya no coincide con lo último guardado
STAGE AREA
es una especie de filtro, decides qué cambios sí van al commit
### COMANDOS:
git add archivo.txt
git add .
(el punto agrega todo)
quitar del stage:
git restore --staged archivo.txt
si usas restore sin --staged, el archivo vuelve a la versión anterior (pierdes cambios)

### REPOSITORIO LOCAL
aquí ya se guarda todo en el historial con un commit
git commit -m "mensaje"
para retroceder un commit:
git reset --soft HEAD~1
mantiene los cambios pero quita el commit
ver estado
git status
si aparece:working tree clean
todo está igual que el último commit
cosas típicas en status:
untracked files → archivos nuevos
changes not staged → cambios que aún no agregaste
ejemplo: README.md modificado pero no añadido → todavía no entra al commit
.gitignore
archivo donde pones cosas que git no debe seguir
sirve para evitar subir archivos innecesarios
restaurar archivo
git restore archivo.txt
vuelve a la última versión guardada
commits
mejor hacer commits pequeños, cada uno con un cambio específico
mensajes:
usar verbos claros:
add → agregar
fix → corregir
change → modificar
remove → eliminar
ejemplo:
git commit -m "feat: add login"
prefijos comunes:
feat → nueva funcionalidad
fix → error
docs → documentación
refactor → mejora interna
## clase D3
### titulo: github 
que es? 
GitHub es una plataforma en internet donde los desarrolladores pueden guardar sus proyectos de programación, organizarlos y trabajar en equipo con otras personas. Funciona como una especie de red social para programadores

Diferebcia con git:
Git = herramienta para guardar cambios
GitHub = plataforma para subir y compartir esos cambios

para conectar con un repositorio con https cada vez nos pide una clave o keys, para lo cual usaremos un ssh, que configiramos en la laptop desde el repositorio de github

## clase D4 
### titulo:
Git remote es el comando que se usa para manejar las conexiones entre tu repositorio local (el de tu computadora) y los repositorios remotos (como los que están en la nube). Básicamente, le indica a Git de dónde traer información o a dónde enviarla.

Comandos importantes:

git remote -v
Muestra las direcciones (URLs) de los repositorios remotos vinculados.

git remote add <apodo> "url"
Sirve para conectar tu repositorio local con uno remoto. El apodo suele ser “origin”.

git remote set-url <apodo> "url"
Permite cambiar la dirección del repositorio remoto al que estás conectado.


## clase D5
### titulo: Git Flow
¿Qué son las ramas en Git?
Las ramas son una herramienta que permite trabajar en diferentes versiones de un mismo proyecto al mismo tiempo

Ramas principales
### Main (o master)
Es la rama más importante.
Contiene el código listo, estable y terminado (el que ya se puede usar o entregar)
 Nunca debería tener errores.
### Develop
Es la rama donde se juntan todos los cambios antes de pasar a main.
Aquí se prueba y se integra todo lo nuevo.
 Es como una “zona de preparación”.
### Ramas de apoyo
Feature (feature/...)
Se usan para crear nuevas funciones.
Nacen desde develop
Cuando terminas, vuelven a develop
 Ejemplo: feature/login

Release (release/...)
Se usan para preparar una versión final.
Nacen desde develop
Se ajustan detalles finales (bugs pequeños, config)
Luego pasan a main y también a develop
 Ejemplo: release/v1.0

Hotfix (hotfix/...)
Se usan para arreglar errores urgentes en producción.
Nacen desde main
Se corrige rápido
Luego vuelve a main y también a develop
 Ejemplo: hotfix/error-login
## clase D6
### titulo:Flujo de trabajo de Git
¿Qué es git merge?
Es para juntar ramas osea unes tu rama con otra y se combinan los cambios.
El --no-ff sirve para que no se pierda el historial, o sea deja marcado que hubo una unión de ramas con un commit.
¿Qué es git fetch?
Es como revisar si hay cambios en el repo remoto.
Los trae, pero no los aplica todavía.

¿Qué es git pull?
Trae los cambios del repo remoto y los aplica de una vez.
Ejemplo:
git pull origin rama

¿Qué es git push?
Sirve para subir tus cambios al repositorio.
Ejemplo:
git push origin rama
Si no es tu repo, la primera vez usas -u para que ya no moleste después:

git push -u origin rama
Flujo de trabajo sin PR (más directo)
Primero te actualizas:

git checkout develop
git fetch
git pull origin develop
Te vas a tu rama:

git checkout -b rama
Si hubo cambios:

git merge develop
Trabajas normal y subes:

git push origin rama
Luego vuelves a develop:

git checkout develop
git fetch
git pull origin develop
Fusionas tu rama:

git merge --no-ff rama
Si hay conflictos, los arreglas y haces:

git add .
git commit
Borras la rama:

git branch -D rama
Y subes todo:

git push origin develop
## clase D7
### titulo: ¿Qué son los Pull Request (PR)?
Los Pull Request son como una solicitud para unir tu trabajo con el código principal.
O sea, no subes directo, sino que dices: “hey, quiero agregar esto” y los demás lo revisan antes.
¿Para qué sirven?
Sirven más que todo para:
ver si el código está bien
evitar errores
que el equipo opine
no arruinar el proyecto
básicamente es como pedir permiso antes de mezclar tu código
¿Cómo se hace un PR?
Primero haces tus cambios en una rama y luego:

git push origin rama
Después vas a GitHub y ahí te sale la opción de crear el PR para unir tu rama con develop o main.
Flujo más o menos (simplificado)
Primero te actualizas:

git checkout develop
git fetch
git pull origin develop
Luego creas o usas tu rama:

git checkout -b rama
Trabajas normal y luego subes:

git push origin rama
Si hubo cambios en develop, haces merge:

git merge develop
Si hay errores los arreglas, haces commit y vuelves a subir:

git add .
git commit
git push origin rama
Y recién haces el PR en GitHub
¿Por qué usar PR?
Porque si no cualquiera puede subir lo que sea y romper todo xd
Con PR:
revisan tu código
opinan
se evita meter cosas mal hechas
es más seguro trabajar así

Y aunque haya PR, igual alguien podría hacer merge sin revisar, entonces se ponen reglas
tipo que sí o sí alguien revise antes
