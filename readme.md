
# GIT AND GITHUB (COMANDOS BASICOS DEL DIA A DIA)

##### Borrando cache cuando no se actualiza el repositorio remoto al hacer push, por ejemplo cuando agregamos archivos al .gitignore y no persisten los cambios en github.  
```git
git rm -r --cached .
git add .
git commit -m "nombre del comit"
git push
```
##### Borrar todos los commits de una branch. dejar solo el ultimo. forzar push.
```git
1. Checkout
  git checkout --orphan latest_branch
2. Add all the files
  git add -A
3. Commit the changes
  git commit -am "commit message"
4. Delete the branch
  git branch -D main
5. Rename the current branch to main
  git branch -m main
6. Finally, force update your repository
  git push -f origin main
```
##### Cambiar la rama por default en github
 ir a settings > branches > default branch y seleccionar.

##### Eliminar una rama remota
 git push origin --delete nombre_rama

##### Traer cambios de una rama remota a rama local.
git pull origin nombre_rama

##### Traer commits de rama remota para luego aplicar los cambios de rama local en un commit nuevo.
```git
git fetch origin
git rebase origin/nombre_rama_en_uso
git add .
git rebase --continue
git push --set-upstream origin nombre_rama_en_uso
```