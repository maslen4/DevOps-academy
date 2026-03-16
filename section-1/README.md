# Section 1

V tejto úlohe som vytvoril malú pythonovskú webovú aplikáciu a zabalil som ju do docker image. Aplikácia vyžíva Flask framework, ako bolo v zadaní. Použil som WSGI server Gunicorn. Docker image je vytvorený pomocou multi stage build, ako bolo v zadaní. V prvej fáze sa nainštalujú závislosti a v druhej fáze sa do výsledného image skopírujú iba potrebné balíky a samotná aplikácia. 

V docker file sa nachádzajú všetky kroky potrebné pre vznik image. V yaml súbore sa nachádza konfigurácia orchestrácie, v tomto prípade je tam ale len jeden service.

V docker file som vystavil port 5000 a v yaml file ho namapoval, takže aplikácia je po spustení dostupná  na adrese http://localhost:5000. 
Tatiež som nastavil, aby sa pri samovoľnom vypnutí kontainer reštartoval - teda pokiaľ ho nevypnem ja sám.
