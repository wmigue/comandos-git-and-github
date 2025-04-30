git merge

    Fusiona dos ramas creando un nuevo commit de "merge".

    Preserva el historial real (tal cual fue).

    Puede generar commits de tipo "Merge branch..." (ruidoso).

Ejemplo:

A---B---C (main)
\
 D---E (feature)

Si haces git checkout main y luego git merge feature, el historial será:

A---B---C---M (main)
\ /
D--E

    M es un commit especial que junta las dos historias.

Ventajas: Se ve claro cuándo hubo un trabajo paralelo.
Desventajas: El historial puede volverse feo y lleno de merges.
⚡ git rebase

    Mueve tus commits locales para que parezca que vinieron después de la rama remota.

    Reescribe el historial para que quede lineal y limpio.

Ejemplo:

Mismo escenario inicial:

A---B---C (main)
\
 D---E (feature)

Si haces git checkout feature y luego git rebase main, Git reescribe la historia así:

A---B---C---D'---E' (feature)

(D' y E' son copias reescritas de D y E, ahora "después de C").

Ventajas: Historial muy limpio, parece que todo pasó en orden.
Desventajas: No debes hacer rebase de commits que ya compartiste (porque cambia los IDs de commits y rompe ramas compartidas).
🧠 Resumen rápido:
Tema merge rebase
¿Cómo combina? Junta ramas con un commit de merge Reescribe historia
¿Resultado? Árbol con ramas Línea recta
¿Es seguro? Sí, siempre Sí, pero solo si trabajas local o solo
¿Historial? Puede ser desordenado Muy limpio
¿Cuándo usar? En proyectos colaborativos, para no reescribir historia compartida Para mantener historia limpia antes de compartir
🎯 Frase para recordar:

        merge es "honesto": muestra toda la historia tal cual.

        rebase es "elegante": limpia la historia como si no hubiera ramas.
