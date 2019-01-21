# MikroTik - monitoring RIP 
monitorovanie siete RIP a zasielanie informácii na e-mail
## Nadstavenie smerovačov
### nadstavenie rozhraní
Je treba priradiť jednotlivým rozhraniam IP adresy. <br>
Takéto nadstavenie je vo Winboxe v záložke IP>addresses <br>
![nadstavenie rozhraní](images/nadstavenie_IP.png)
### nadstavenie RIP
Je treba spustiť dynamické smerovanie protokolom RIP <br>
Takéto nadstavenie je vo Winboxe v záložke routing>RIP <br>
![nadstavenie RIP](images/nadstavenie_RIP.png)
### nadstavenie e-mail
následne je vo Winboxe treba nadstavit emailovu adresu pre zasielanie emailov <br>
![nadstavenie email](images/nadstavenie_email.png)
## Konfigurácia skriptov
skript na skopírovanie smerovacej tabulky a zaslanie na email
![skript na kopírovanie smerovacej tabulky](images/skripty.png)
## Konfigurácia schedulera
nadstavíme scheduler ktorý bude volať skript v pravidelných intervaloch <br>
![nadstavenie schedulera](images/scheduler.png) <br>
scheduler sa dá prípadne nadstavit pomocou terminálu príkazom <br>
/system scheduler <br>
add on-event="iproute" start-time=00:00:00 interval=1h <br>
## Konfigurácia netwatch
nadstavíme netwatch ktorý bude kontrolovat stav linky a v prípade zmeny stavu zavolá príslušný skript <br>
![nadstavenie netwatchu](images/netwatch.png) <br>
netwatch sa dá prípadne nadstavit pomocou terminálu príkazom <br>
system netwatch> add host=10.0.0.2 timeout=999ms interval=20s up-script=e-up down-script=e-down <br>
**skript ktorý netwatch zavolá** <br>
system script> add name=e-down source={/tool e-mail send toto=mimikro14@gmail.com subject="stav linky" body="linka dolu"} <br>
