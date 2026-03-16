# Section 2

## Task C - Docker Build fails (no space left om device)

Dôvody, prečo mohol build zlyhať:

### Large build context

Možno sa pri "COPY . /app" zbytočne kopírujú napríklad node-modules, build artefakty, .git atď...

### apt-get update a install

Tieto príkazy vytvoria dodatočné balíky, ktoré zaberajú miesto, pokiaľ ich neodstránime.

### npm install

Priečinok node-modules, ktorý vznikne pri priíkaze "npm install" je príliš veľký.

### Staré artefakty

Staré images, stopnuté konteinery, alebo nazbieraná medzipamäť môžu zaberať miesto na disku. Čiže ak by aj práve tento image nebol príliš veľký, tak build môže padnúť pre nedostatok miesta.


## Dočasné fixy

### Vymazať nepotrebné docker dáta

Teda staré nepoužívane image, kontainere, medzipamäť, atď...

Príkazy

docker system prune -af
docker builder prune -af


### Pridať .dockerignore

Zahrnúť do neho napríklad node-modules, alebo .git, aby sa pri COPY . /app zbytočne nekopírovali.

### Zvážiť použitie CI runnera s vačším úložiskom

Ak už nevieme náš image inak zmenšiť, možno to stojí za zváženie.



## Dlhodobé fixy

### Použiť vhodnejší base image

Namiesto manuálnej inštalácie Node na Ubuntu vieme použiť oficiálny Node image:
"FROM node:verzia"

Vyhneme sa potom apt-get install

### Použiť npm ci

Clean install namiesto obyčajného npm install. Clean install berie iba dependencies z package-lock.json.

### Nastaviť nejaký pravideľný cleanup

Ak vieme nastaviť automatický cleanup raz za čas, ktorý by odstránil staré images, stopnuté kontainery, medzipamäť, atď... Nemuseli by sme to robiť ručne.


## Monitoring

### Monitorovať CI disk

Monitorovať zaplnenie disku. Možno nejaký alert pri určitom zaplnení.


### Monitorovať, koľko priestoru využíva docker

Príkazom

docker system df

vieme zistiť podrobne, koľko priestoru zaberajú images, medzipamäť, atď...
