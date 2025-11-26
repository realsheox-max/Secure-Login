# Secure-Login
HWID Basierter Login mit Restzeit Funktion für Tools mit beschränkter Nutzungsdauer.

========================================================
HWID Basierter Login mit Restzeit Funktion für Tools
mit beschränkter Nutzungsdauer.

Frontend, Backend + API, Datenbank, Admintool via Terminal
und ein VS22 Projekt ( c# / Konsole ) für ein sicheren Login.

Das ist ein Langeweile Projekt … keine ernsthafte Nutzung
vorgesehen von meiner Seite aus.

Es muss angepasst werden:
Security Keys in der .env
IPs in allen Dateien.

Frontend:
Login Funktion ( nur Nutzername / Passwort )
News Funktion, Interface, Status Seite und zeit Counter
+ Session wird gehalten .. somit muss sich der Nutzer nicht
jedes mal von neuem einloggen.

Admin Tool:
Nutzer erstellen, HWIDs verwalten, Zeit Verlängern,
 News Verwalten usw … 

das VS22 projekt 
sollte auch eine update Funktion bekommen … war zu faul XD
Minimal enthalten ??

Viel spaß, würde mich freuen wenn man mich verlinkt wenn
man es nutzt .. bzw das Projekt verlinkt =)

Lg
Sheox

========================================================

benötigt: npm, pm2, node, admin rechte


bash# 1. Projekt-Ordner hochladen
Ordner OPT / VAR / ETC hochladen ( schauen das man keine index.html hat im var/WWW/html ordner !!! )


# 2. nginx.conf bearbeiten und das so einfügen bzw nachtragen
http {
	## das muss rein !!!
	limit_req_zone $binary_remote_addr zone=api_limit:10m rate=10r/s;

}

sudo ln -s /etc/nginx/sites-available/secure-backend /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx


# 3. Dependencies installieren
im Ordner /opt/secure-backend folgendes ausführen via Terminal
npm install

# 4. .env anpassen
nano .env
# ADMIN_KEY ändern!!!

# 5. Server starten
node server.js

oder dauerhaft

# 5. Server starten (PM2 empfohlen!)
pm2 start server.js --name secure-backend
pm2 startup
pm2 save

# Die SQLite Datei wird automatisch erstellt!
# Du siehst dann: secure_login.db


Per Admin Tool ( putty / terminal )
👤 User erstellen:
Option 1: Admin Tools CLI (empfohlen)
bashnode admin-tools.js
oder node admin-tools.js

Rest ist selbsterklärend.


## Login Tool 
Visual Studio 22
c# Konsolen anwendnung
einfach ip bearbeiten.
Login zuerst mit Daten, dann werden HWID abgegriffen danach login automaitsch mit hwid.


############################################################################
# . Firewall konfigurieren
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw allow 22/tcp
sudo ufw allow 3000/tcp
sudo ufw enable
