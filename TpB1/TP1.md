# I. Récolte d'informations

### Rendu PowerShell:

```powershell
PS C:\Users\lucve> ipconfig

Configuration IP de Windows


Carte Ethernet Ethernet 3 :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :

Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :

Carte Ethernet Ethernet 2 :

   Suffixe DNS propre à la connexion. . . :
   Adresse d’autoconfiguration IPv4 . . . : 169.254.240.21
   Masque de sous-réseau. . . . . . . . . : 255.255.0.0
   Passerelle par défaut. . . . . . . . . :

Carte réseau sans fil Connexion au réseau local* 1 :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :

Carte réseau sans fil Connexion au réseau local* 10 :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.72.214
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
```

#### Bonus:

```powershell
PS C:\Users\lucve> Get-NetFirewallProfile | ft Name,Enabled

Name    Enabled
----    -------
Domain     True
Private    True
Public     True
```

# II. ***PING !!***

```powershell
PS C:\Users\lucve> ping 10.33.72.214

Envoi d’une requête 'Ping'  10.33.72.214 avec 32 octets de données :
Réponse de 10.33.72.214 : octets=32 temps<1ms TTL=128
Réponse de 10.33.72.214 : octets=32 temps=1 ms TTL=128
Réponse de 10.33.72.214 : octets=32 temps<1ms TTL=128
Réponse de 10.33.72.214 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 10.33.72.214:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 1ms, Moyenne = 0ms
PS C:\Users\lucve> ping 127.0.0.1

Envoi d’une requête 'Ping'  127.0.0.1 avec 32 octets de données :
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128
Réponse de 127.0.0.1 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 127.0.0.1:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms
```

```powershell
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
   Serveur DHCP . . . . . . . . . . . . . : 10.33.79.254
   Serveurs DNS. . .  . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
PS C:\Users\lucve> ping 10.33.79.254

Envoi d’une requête 'Ping'  10.33.79.254 avec 32 octets de données :
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.
Délai d’attente de la demande dépassé.

Statistiques Ping pour 10.33.79.254:
    Paquets : envoyés = 4, reçus = 0, perdus = 4 (perte 100%),
PS C:\Users\lucve> ping 10.33.73.111

Envoi d’une requête 'Ping'  10.33.73.111 avec 32 octets de données :
Réponse de 10.33.73.111 : octets=32 temps=12 ms TTL=128
Réponse de 10.33.73.111 : octets=32 temps=7 ms TTL=128
Réponse de 10.33.73.111 : octets=32 temps=5 ms TTL=128
Réponse de 10.33.73.111 : octets=32 temps=7 ms TTL=128

Statistiques Ping pour 10.33.73.111:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 5ms, Maximum = 12ms, Moyenne = 7ms
PS C:\Users\lucve> ping www.thinkerview.com

Envoi d’une requête 'ping' sur www.thinkerview.com [188.114.97.7] avec 32 octets de données :
Réponse de 188.114.97.7 : octets=32 temps=17 ms TTL=55
Réponse de 188.114.97.7 : octets=32 temps=17 ms TTL=55
Réponse de 188.114.97.7 : octets=32 temps=17 ms TTL=55
Réponse de 188.114.97.7 : octets=32 temps=16 ms TTL=55

Statistiques Ping pour 188.114.97.7:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 16ms, Maximum = 17ms, Moyenne = 16ms
```

#### DNS:

```powershell
PS C:\Users\lucve> nslookup ls www.thinkerview.com
DNS request timed out.
    timeout was 2 seconds.
Serveur :   UnKnown
Address:  188.114.96.7

DNS request timed out.
    timeout was 2 seconds.
DNS request timed out.
    timeout was 2 seconds.
*** Le délai de la requête sur UnKnown est dépassé.
PS C:\Users\lucve> nslookup ls www.wikileaks.org
Serveur :   UnKnown
Address:  51.159.197.136

*** UnKnown ne parvient pas à trouver ls : No response from server
PS C:\Users\lucve> nslookup ls www.torproject.org
Serveur :   UnKnown
Address:  204.8.99.146

*** UnKnown ne parvient pas à trouver ls : No response from server
```

# III. **SNIFFFF..!**
### ***Voir les fichiers correspondants***

# IV. *Scanning in progress...*

```powershell
MAC Address: 52:B6:7E:93:33:84 (Unknown)
Nmap scan report for 10.33.68.212
Host is up (0.73s latency).
MAC Address: 92:69:C3:7D:28:00 (Unknown)
Nmap scan report for 10.33.68.213
Host is up (0.089s latency).
MAC Address: FA:13:45:34:BA:CF (Unknown)
Nmap scan report for 10.33.68.221
```

```powershell
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . :
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.68.218
   Masque de sous-réseau. . . . . . . . . : 255.255.240.0
   Passerelle par défaut. . . . . . . . . : 10.33.79.254
```