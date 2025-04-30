# 📝 FLUJO RESUMIDO TRABAJO EN EQUIPO

## 👉 1. Antes de empezar a trabajar
```bash
git checkout master
git fetch origin
git rebase origin/master

✅ Así actualizás tu master con lo último del remoto.
👉 2. Crear una nueva rama para trabajar

git checkout -b nombre-de-tu-rama

✅ Siempre trabajá en ramas separadas, no directo en master.
👉 3. Hacer cambios, guardar y versionar

git add .
git commit -m "Mensaje claro sobre lo que hiciste"

✅ "Guardar cambios" en Git.
👉 4. Subir tu rama al servidor

git push origin nombre-de-tu-rama

✅ Para que otros puedan ver tu trabajo.
👉 5. (Opcional) Seguir trabajando mientras actualizás

Si alguien más sube cambios al remoto y vos querés traerlos:

git fetch origin
git rebase origin/master

✅ Te mantenés siempre actualizado.
👉 6. Fusionar cambios (Pull Request o Merge)

Normalmente hacés un Pull Request (PR) en GitHub/GitLab para pedir revisar tu rama antes de meterla en master.

O si es local, podés:

git checkout master
git fetch origin
git rebase origin/master
git merge nombre-de-tu-rama

✅ Fusionás tu rama en master.
👉 7. (Problemas) Si te trabás: usar stash

Para guardar cambios sin hacer commit:

git stash
# Luego hacés cambios de rama, pulls, etc.
git stash pop

✅ No perdés nada temporalmente.
🚨 Emergencias:

Si algo sale mal:

git reflog

✅ Te salva casi siempre (para encontrar commits o estados anteriores).