# GIT AND GITHUB (COMANDOS BASICOS DEL DIA A DIA) 🤘



# GH AUTO LOGIN

#### Si ya tienes la GitHub CLI instalada y estás logueado
##### Loguearse desde consola
```git
gh auth login

```
##### cambiar rama por default donde "main" es la que queremos setear como default.

```git
gh repo edit --default-branch main

```
##### Eliminar una rama remota

git push origin --delete nombre_rama



# PUSH

##### hacer commit --amend en local y luego subir al remoto (Usá --force solo si sabés que nadie más está trabajando en esa rama, porque reescribe el historial remoto.)


```git
git push --force

```

##### hacer commit --amend en local (sobreecribe ultimo commit) y luego subir al remoto (si realmente necesitás usar amend, pero te preocupa romper cambios de otras personas en el remoto. Este comando solo fuerza el push si el remoto no cambió desde tu último pull, lo cual protege contra sobrescribir trabajo de otros sin darte cuenta.)


```git
git push origin main --force-with-lease
```



# DIFF

##### ver ediciones en todos los archivos del proyecto que no fueron commiteados. (Cambios no añadidos al staging lo que aún no hiciste git add)

```git
git diff

```

##### Cambios que ya hiciste git add (comparar staging con el último commit):


```git
git diff --cached

```

#####  Comparar dos commits específicos:


```git
git diff commit1 commit2


```

#####  Ver qué cambió en un archivo:


```git
git diff HEAD archivo.txt


```






# RESET

##### git reset --hard esto elimina los commits posteriores al indicado en el comando HEAD. con hard nos aseguramos de eliminar todos los archivos que habian en el staged area y ultimo commit, y volver a un estado anterior limpio de commits posteriores. en el ejemplo volveremos atras 1 commit anterior al ultimo:

```git
git reset --hard HEAD~1

```

##### git reset --soft nos trae todos los archivos del ultimo commit al staged area, inclusive con el estado del ultimo commit. todo trackeado listo para hacer los commits.

```git
git reset --soft HEAD~6

```

##### git reset --mixed lo mismo que soft pero con la diferencia de que trae todos los archivos y estados sin trackear, es decir hay que hacer los ADD archivo por archivo antes de commitear.

```git
git reset --mixed HEAD~3

```

##### git reset --hard HEAD@{1} tambien podemos usarlo de esta manera para recuperar los commits y estados eliminados con reset hard, mixed o soft.

```git
git reset --hard HEAD@{1}

```

##### Eliminar directorios untracked, por ejemplo cuando hacemos reset mixed y queremos limpiar o eliminar archivos sin trackear.

```git
git clean -f

```

##### si al hacer reset me trae el estado del ultimo commit, puedo volver al estado que tenia el commit en donde estoy ahora (head) referenciando el commit en cuestion. con esto mantendria el estado, es algo como reset hard en algun sentido.

```git
 git restore --source=f6f8c95 .

```

# REBASE

##### para abortar un rebase con

```git
 git rebase --abort

```

##### ir al primer commit

```git
 git rebase -i --root

```

##### traer un archivo o varios desde otro commit a nuestro commit HEAD.

```git
 git checkout abc1234 -- src/app.js
 git add . 
 git commit --amend

```

##### Modificar un commit en nuestra historia de rama, ir a un commit especifico siempre le indicamos el anterior al que necesitamos.

```git
git log --oneline 

#OUTPUT 
f8458c1 (HEAD -> master2) 3  (este queremos editar.)
e5cd873 1 (anterior)
e03a60e 2

git rebase -i e5cd873
# se nos abre el editor, modificamos pick por edit en el commit que queremos editar. cerramos editor.
# git add .
# git rebase --continue
# se nos abre editor, cambiamos el label del commit si queremos y cerramos editor.


```

##### cambiar de lugar un commit dentro de la historia de nuestra branch.

```git
git rebase -i head~4
# con esto se nos abre el editor, cambiamos de posicion los commits simplemente, arriba o abajo nanteniendo el pick. luego hacemos git add . y resolvemos problemas si los hubiese. luego hacemos git rebase --continue para finalizar.

```

# CHERRY PICK

##### traer un commit de otra branch y ponerlo en mi master. si se combina luego con rebase se puede cambiar la posicion en la historia de nuesta branch.

```git
 git checkout mi-rama
 git cherry-pick <hash-del-commit>
 git add .
 # (acepamos los incomming changes)
 git cherry-pick --continue
 # (le cambiamos el nombre si es necesario)
 # (hacemos el rebase solo si queremos cambiar de posicion este nuevo commit)
```

##### recuperar commit perdido

```git
 # nos abre historico de cambios
 git reflog
 # buscamos en reflog el commit y lo traemos
 git cherry-pick <commit>
 git add .
 git cherry-pick --continue

```

#### Eliminar un commit específico o varios dentro de mi rama. Si deseas eliminar un commit, usa rebase con la opción drop.

```
git rebase -i 9e5f072

OUTPUT:
pick 30133c0 (master) tres
drop 974f17b (HEAD) dos
pick 9e5f072 uno

# Cambiar "pick" por "drop" en el commit que deseas eliminar, guardar y luego continuar con:

git rebase --continue
```

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

##### eliminar ultimo commit.

git reset --hard HEAD~1

##### integrar los cambios al último commit sin crear un nuevo commit para ello.

```git
git add .
git commit --amend  //se abrira un editor, entonces guardar los cambios.
git push origin nombre-de-tu-rama --force //forzar sobreescritura del ultimo commit remoto.

```
