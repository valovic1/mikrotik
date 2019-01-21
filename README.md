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
![nadstavenie schedulera](images/scheduler.png)
scheduler sa dá prípadne nadstavit pomocou terminálu príkazom <br>
/system scheduler <br>
add on-event="iproute" start-time=00:00:00 interval=1h <br>
