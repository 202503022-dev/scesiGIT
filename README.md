# scesiGIT
## clase D1
##titulo: Introduccion
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
### titulo:
## clase D4 
###titulo:
## clase D5
###titulo:
## clase D6
###titulo:
