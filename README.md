# practica_github_is

Quevedo Arreaga José Benito
Lopez Portillo Ireta Sofia Arely
Rivera Torres Juan Angel
Barranco Mendoza Rafael

Prueba para usar comandos de git 

1. Paso: Primer commit (el tuyo)
Tú creas el repositorio y haces el primer commit:
git init
git add index.html
git commit -m "Commit inicial: agrega index.html base"
git branch -M main
git remote add origin https://github.com/usuario/mi-proyecto.git
git push -u origin main
Git log:
* a1b2c3d (HEAD -> main, origin/main) Commit inicial: agrega index.html base
2. Paso: Tu compañero hace un cambio
Tu compañero clona el repositorio y edita index.html, agregando un nuevo <div>:
<body>
 <h1>Bienvenido</h1>
 <div id="info">Información adicional del sitio</div>
</body>
Luego ejecuta:
git add index.html
git commit -m "Agrega un nuevo div con información adicional"
git push origin main
3. Árbol de commits en Git
Si trabajaron uno después del otro (sin conflictos):
* b3c4d5e (HEAD -> main, origin/main) Agrega un nuevo div con información adicional
* a1b2c3d Commit inicial: agrega index.html base
En este caso, el flujo es lineal:
tu compañero hizo pull, actualizó, y luego push con su cambio.
Si ambos trabajaron en paralelo (sin hacer pull antes):
Supón que tú hiciste un cambio local y tu compañero también editó el mismo archivo.
Cuando tu compañero intenta subir, verá:
! [rejected] main -> main (fetch first)
Debe hacer:
git pull origin main
Git fusionará ambos commits, generando un merge commit.
Entonces el árbol se verá así:
* e4f5a6b (HEAD -> main, origin/main) Merge branch 'main' of github.com:usuario/miproyecto
|\
| * b3c4d5e Agrega un nuevo div con información adicional
* | a1b2c3d Commit inicial: agrega index.html base
|/
Aquí, el merge commit (e4f5a6b) combina las dos versiones del index.html.
Si usaron ramas (flujo más profesional)
Tu compañero podría haber hecho su cambio en una rama separada:
git checkout -b feature/agregar-div
git add index.html
git commit -m "Agrega un nuevo div con información adicional"
git push origin feature/agregar-div
Luego, en GitHub hace un Pull Request → main, y tú lo aceptas.
El árbol se vería así:
* f7g8h9i (HEAD -> main, origin/main) Merge pull request #1 from
compañero/feature/agregar-div
|\
| * b3c4d5e Agrega un nuevo div con información adicional
* | a1b2c3d Commit inicial: agrega index.html base
|/
Ventajas de este flujo:
 Historial más limpio.
 Evita conflictos directos en la rama principal.
 Permite revisión de código (pull request review).
Resumen visual (flujo típico)
main
│
├── a1b2c3d (Tú) Commit inicial: agrega index.html base
│
└── b3c4d5e (Compañero) Agrega un nuevo div con información adicional
O, si se trabajó en ramas:
main
│
├── a1b2c3d Commit inicial
│
├── (rama feature/agregar-div)
│ └── b3c4d5e Agrega un nuevo div
│
└── f7g8h9i Merge de feature/agregar-div → main
