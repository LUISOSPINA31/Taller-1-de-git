# Inicializa un repositorio Git en la carpeta TallerGit (si ya existe, lo reinicializa).
git init TallerGit

# Configura el nombre de usuario global para Git.
git config --global user.name "Luis Miguel Ospina"

# Configura el correo electrónico global para Git.
git config --global user.email "luis.miguel.ospina@correounivalle.edu.co"

# Cambia al directorio TallerGit.
cd TallerGit

# Crea una nueva rama llamada 'feature' y cambia a ella.
git checkout -b feature

# Crea un archivo llamado archivo.txt con el contenido "Texto inicial".
echo "Texto inicial" > archivo.txt

# Añade archivo.txt al área de preparación.
git add archivo.txt

# Realiza un commit con el mensaje "Commit inicial".
git commit -m "Commit inicial"

# Agrega texto al archivo archivo.txt y realiza un commit automáticamente (agrega y confirma en un solo paso).
echo "Texto agregado en feature" >> archivo.txt
git commit -am "Segundo commit en feature"

# Agrega más texto y realiza otro commit.
echo "Texto agregado en feature" >> archivo.txt
git commit -am "Tercer commit en feature"

# Cambia a la rama master. (Error, la rama no existe, por lo que se crea en el siguiente paso)
git checkout master

# Crea la rama master y cambia a ella.
git checkout -b master

# Fusiona la rama 'feature' en la rama 'master' (pero no había cambios nuevos, por eso indica 'Already up to date').
git merge feature

# Retrocede al commit anterior, descartando el último commit.
git reset --hard HEAD~1

# Reorganiza la rama 'master' para que siga la rama 'feature'.
git rebase feature

# Crea una nueva rama llamada 'hotfix' y cambia a ella.
git checkout -b hotfix

# Añade texto al archivo archivo.txt y realiza un commit con el mensaje "Hotfix".
echo "Corrección urgente" >> archivo.txt
git commit -am "Hotfix"

# Cambia de nuevo a la rama 'master'.
git checkout master

# Aplica el commit de la rama 'hotfix' en la rama 'master'.
git cherry-pick hotfix

# Muestra el historial de todas las referencias de la rama actual, incluyendo cambios de HEAD.
git reflog

# Cambia a la rama 'feature'.
git checkout feature

# Crea un nuevo archivo llamado conflicto.txt en la rama 'feature'.
echo "Cambio en feature" > conflicto.txt

# Añade el archivo conflicto.txt al área de preparación.
git add conflicto.txt

# Realiza un commit con el mensaje "Cambio en feature".
git commit -am "Cambio en feature"

# Cambia de nuevo a la rama 'master'.
git checkout master

# Crea el archivo conflicto.txt en la rama 'master' con contenido distinto.
echo "Cambio en master" > conflicto.txt

# Añade conflicto.txt al área de preparación.
git add conflicto.txt

# Realiza un commit con el mensaje "Cambio en master".
git commit -am "Cambio en master"

# Intenta fusionar la rama 'feature' en la rama 'master', pero se produce un conflicto en el archivo conflicto.txt.
git merge feature

# Añade el archivo conflicto.txt después de resolver el conflicto.
git add conflicto.txt

# Realiza un commit indicando que se ha resuelto el conflicto.
git commit -am "Solución conflicto"
