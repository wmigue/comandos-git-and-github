
# GIT AND GITHUB (COMANDOS BASICOS DEL DIA A DIA)

##### borrando cache cuando no se actualiza el repositorio remoto al hacer push, por ejemplo cuando agregamos archivos al .gitignore y no persisten los cambios en github.  
```git
git rm -r --cached .
git add .
git commit -m "nombre del comit"
git push
```
##### borrar todos los commits de una branch.
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
##### cambiar la rama por default en github
 ir a settings > branches > default branch y seleccionar.