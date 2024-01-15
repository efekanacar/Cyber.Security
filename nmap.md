`nmap scanme.nmap.org`

ports/protocol, states, services

`nmap 192.168.8.100-200`  → ıp adres aralığı

`nmap 192.168.8.0/24`  → tüm alt ağları tarama

`nmap 192.168.8.0/24 —exclude 192.168.8.1-10` ->192.168.8.1 ve 192.168.8.10 arasındaki ıpleri hariç tutar

****Agresif Tarama (-A)****

`nmap -A scanme.nmap.org`   

******************Ping Atma******************

`nmap -PN 192.168.8.0/24`  

- -PN →Ağdaki cihazlar detaylı
- -sP  →Sadece ağdaki cihazlar
- -PS  →TCP SYN Ping
- -PA  →TCP ACK Ping
- -PU  →UDP Ping
- -PY  →SCTP INIT Ping
- -PE  →ICMP Echo Ping
- -PR  →ARP Pin

`nmap —traceroute [scanme.nmap.org](http://scanme.nmap.org)`  →Paketin giden ağ rotasını gösterir

`nmap -R 192.168.8.0`  →Ters DNS taraması

**Gelişmiş Tarama**

`nmap -sS scanme.nmap.org`

- -sS → TCP SYN Scan =gizli bilgi kullanır
- -sT → TCP Connect Scan = Doğrudan bağlantı kullanır
- -sU → UDP Scan
- -sN → TCP Null Scan =bayrakları 0 olarak ayarlar
- -sF → TCP FIN Scan =Bağlantı osnlandırma isteği gönderir
- -sA → TCP ACK Scan =filtrelenen portları gösterir
- -sO →Ip Protokol Scan

**Port Tarama**

`nmap -F scanme.nmap.org`

- -F → İlk 100 portu tarar
- -p 80 → sadece 80 numaralı portu tarar
- -p smtp,http,ssh → smtp, http ve ssh hizmetlerini tarar
- -p “*” → Bütün portları tarar (65545)
- —top-ports 10 →En çok kullanılan 10 portu tarar
- -rv → rastgele port tarama

**İşletim Sistemi ve Servis Keşfi**

`nmap -O scanme.nmap.org`

- -O =Sistemin işletim sistemini tanımlar
- -O —fuzzy =Bilinmeyen işletim sistemini tahmin ettirir
- -sV =Sürüm versiyon bul
- -sR =RPC Taraması

`nmap -T4  [localhost](http://localhost)` →Agrasif tarama

T1den T5e kadar 5 en agrasif

**TTL**, Time to Live, yani yaşama süresi anlamına gelir.

`nmap -ttl 200 [scanme.nmap.org](http://scanme.nmap.org)`  ttl değerini 200 yapar

`nmap —host-timeout 1m [localhost](http://localhost)` 1dakika içinde tarama sonucu çıkmaz ise iptal olur

**Firewall Atlama**

- `nmap -f [scanme.nmap.org](http://scanme.nmap.org)` parçalı paketler gönderir
- -**-mtu 16**  →8/16/24  byte sayısını ayarlar güvenlik duvarını atlatmak için
- **-D RND:10**  →Bu tuzak, faaliyetlerin gizlenmesine ve tespitinin zorlanmasına yarar
- `nmap -sI  [zombi_ip] [hedef_ip]`→ zombi taramaya yarar
- **—data-length 25**  → Paketin üzerine 25baytlık yeni bir paket ekler. Güvenlik duvarı bu şekilde şaşırtılır
- **—randomize-host**  → algılanmasını önlemek için rastgele tarar
- **—spoof-mac 0**  →başka bir MAC adresi üretir

**Çıktı Seçenekleri**

`nmap -oN C:\Users\Efekan\Desktop\scan.txt [scanme.nmap.org](http://scanme.nmap.org)` masaüstüne scan.txt adında bir dosya oluşturup çıktıyı içine yazar

**-oX**  →xml dosyası olarak çıktı alır

**-oA**  →alınabilen bütün formatlarda çıktı alır

**—stats-every 5s**  →durumu 5 saniyede bir göster

 **-v**  → ayrıntılı çıktı(-vv de kullanılabilir)

**—reason**  →port durum nedenini gösterir(Ör:SYN_ACK)

**—packet-trace**  →ağ paketlerinin tam ayrıntılarının gösterilmesini sağlar

**—iflist**  → ağ arabirimlerini gösterir

**-e eth0**  →Belirli ağ arabirimini taramaya yarar

zenmap = nmap’in GUI hali

### Nmap Script Motoru (NSE)

scriptler, nmap dosyasında scripts klasörü altında yer alır.

`nmap --script ssl-enum-ciphers 192.168.0.1` Bu skript, hedef sistemdeki SSL/TLS servislerinin desteklediği şifreleme algoritmalarını kontrol eder.

**Hedef Sisteme sızma**

`nmap —script vuln [localhost](http://localhost)` Zaafiyetleri ayrıntılı bir şekilde görebiliriz

metasploit framework’de bulunan açığı arıyoruz. 

*msf5>*search ms17-010 

use exploit…

RHOST [makine_ip]

RPORT 445

exploit

**Çoklu kullanım**

`nmap -sS -sV -O localhost`

`nmap —reason -F —open -T4 localhost`

**Online Port Scan**

[pentest-tools.com](http://pentest-tools.com) 

[nmap.online](http://nmap.online) 

[hackertarget.com](http://hackertarget.com) 

[hidemyna.me](http://hidemyna.me)