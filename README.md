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

admin tool:
<img width="382" height="531" alt="image" src="https://github.com/user-attachments/assets/d29c7fde-a51b-4663-9cb3-9e0d3307ea1d" />
<img width="447" height="691" alt="image" src="https://github.com/user-attachments/assets/f5b5e991-09bc-4230-8999-274933fad73d" />
Ohne HWID login nur per Website
<img width="939" height="859" alt="image" src="https://github.com/user-attachments/assets/3d2a3727-e2a4-4df3-8d39-cc8e8039ed7d" />
Mit Login über das Tool
<img width="930" height="765" alt="image" src="https://github.com/user-attachments/assets/8c28ccf9-62d4-4a69-aba0-8f46cbcaf6d6" />
HWID
<img width="997" height="1075" alt="image" src="https://github.com/user-attachments/assets/0b5d3db8-7f28-49ba-816d-6996febae1f8" />
HWID Reset
<img width="1018" height="908" alt="image" src="https://github.com/user-attachments/assets/931e37e8-9452-4bf7-84f1-6ed4c3ddd145" />
<img width="522" height="147" alt="image" src="https://github.com/user-attachments/assets/09658131-0f48-4fb9-ad9a-a2fe7c458009" />
Tool Login first Time
<img width="1116" height="628" alt="image" src="https://github.com/user-attachments/assets/19a0837d-81b8-4d82-91f6-e75c88e3abce" />





