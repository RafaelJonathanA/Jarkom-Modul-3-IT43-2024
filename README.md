# Laporan Resmi Praktikum Modul 3 Jaringan Komputer

### GNS 3

### Kelompok IT43 -

| Name                              |     NRP    |
| ----------------------------------|------------|
| Rafael Jonathan Arnoldus          | 5027231006 | 
| Gandhi Ert Julio                  | 5027231081 |

## Topologi 
![image](https://github.com/user-attachments/assets/5c2c0952-a5fb-4792-a9e6-225b047feda2)

### IP NODE
- Paradis:
    - eth1: 192.238.1.1
    - eth2: 192.238.2.1
    - eth3: 192.238.3.1
    - eth4: 192.238.4.1
- Annie: 192.238.1.2
- Berdholdt: 192.238.1.3
- Reiner: 192.238.1.4
- Armin: 192.238.2.2
- Eren: 192.238.2.3
- Mikasa: 192.238.2.4
- Beast: 192.238.3.2
- Colossal: 192.238.3.3
- Warhammer: 192.238.3.4
- Fritz: 192.238.4.2
- Tybur: 192.238.4.3 

### Konfigurasi 

##### Paradis 
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.238.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.238.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.238.3.1
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 192.238.4.1
	netmask 255.255.255.0
``` 
Di bash 
``` 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.238.0.0/16
apt-get update
apt install isc-dhcp-relay -y
``` 
##### Annie
```
auto eth0
iface eth0 inet static
	address 192.238.1.2
	netmask 255.255.255.0
	gateway 192.238.1.1
```
##### Berdholdt
```
auto eth0
iface eth0 inet static
	address 192.238.1.3
	netmask 255.255.255.0
	gateway 192.238.1.1
```
##### Reiner
```
auto eth0
iface eth0 inet static
	address 192.238.1.4
	netmask 255.255.255.0
	gateway 192.238.1.1
```
##### Zeke 
```
auto eth0
iface eth0 inet dhcp
```
Di Bash 
```
apt update
apt install lynx -y
apt install htop -y
apt install apache2-utils -y
apt-get install jq -y
```
##### Beast 
```
auto eth0
iface eth0 inet static
    address 192.238.3.2
    netmask 255.255.255.0
    gateway 192.238.3.1
```
##### Colossal
```
auto eth0
iface eth0 inet static
    address 192.238.3.3
    netmask 255.255.255.0
    gateway 192.238.3.1
```
Di Bash 
```
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install bind9 -y
apt-get install apache2-utils -y
apt-get install nginx -y
apt-get install lynx -y

service nginx start
```
##### Warhammer 
```
auto eth0
iface eth0 inet static
    address 192.238.3.4
    netmask 255.255.255.0
    gateway 192.238.3.1
```
##### Tybur 
```
auto eth0
iface eth0 inet static
    address 192.238.4.3
    netmask 255.255.255.0
    gateway 192.238.4.1
```
Di Bash
```
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-server -y 
```
##### Fritz 
```
auto eth0
iface eth0 inet static
    address 192.238.4.2
    netmask 255.255.255.0
    gateway 192.238.4.1
```
Di Bash 
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install bind9 -y

echo 'options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        // dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;
        listen-on-v6 { any; };
}; ' >/etc/bind/named.conf.options

service bind9 restart 
```
##### Erwin 
```
auto eth0
iface eth0 inet dhcp
```
Di Bash 
```
apt update
apt install lynx -y
apt install htop -y
apt install apache2-utils -y
apt-get install jq -y
```
##### Armin
```
auto eth0
iface eth0 inet static
    address 192.238.2.2
    netmask 255.255.255.0
    gateway 192.238.2.1
```
Di Bash 
```
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install lynx -y
apt-get install wget -y
apt-get install unzip -y
apt-get install nginx -y
apt install software-properties-common -y
apt install php7.3 -y
apt install php7.3-fpm -y
```
##### Eren 
```
auto eth0
iface eth0 inet static
    address 192.238.2.3
    netmask 255.255.255.0
    gateway 192.238.2.1
```
Di Bash 
```
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install lynx -y
apt-get install wget -y
apt-get install unzip -y
apt-get install nginx -y
apt install software-properties-common -y
apt install php7.3 -y
apt install php7.3-fpm -y
```
##### Mikasa
```
auto eth0
iface eth0 inet static
    address 192.238.2.4
    netmask 255.255.255.0
    gateway 192.238.2.1
```
Di Bash 
```
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install lynx -y
apt-get install wget -y
apt-get install unzip -y
apt-get install nginx -y
apt install software-properties-common -y
apt install php7.3 -y
apt install php7.3-fpm -y
```

### No. 0 
Pulau Paradis telah menjadi tempat yang damai selama 1000 tahun, namun kedamaian tersebut tidak bertahan selamanya. Perang antara kaum Marley dan Eldia telah mencapai puncak. Kaum Marley yang dipimpin oleh Zeke, me-register domain name marley.yyy.com untuk worker Laravel mengarah pada Annie. Namun ternyata tidak hanya kaum Marley saja yang berinisiasi, kaum Eldia ternyata sudah mendaftarkan domain name eldia.yyy.com untuk worker PHP (0) mengarah pada Armin.

Pada Fritz : 
```
#!/bin/bash


cat <<EOL >> /etc/bind/named.conf.local
zone "marley.it43.com" { 
    type master; 
    file "/etc/bind/marley/marley.it43.com";
};

zone "eldia.it43.com" {
    type master;
    file "/etc/bind/eldia/eldia.it43.com";
};
EOL

mkdir -p /etc/bind/marley
mkdir -p /etc/bind/eldia


cat <<EOL > /etc/bind/marley/marley.it43.com
;
; BIND data file for local loopback interface
;
\$TTL    604800
@       IN      SOA     marley.it43.com. root.marley.it43.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      marley.it43.com.
@       IN      A       192.238.1.2     ; IP Annie
EOL


cat <<EOL > /etc/bind/eldia/eldia.it43.com
;
; BIND data file for local loopback interface
;
\$TTL    604800
@       IN      SOA     eldia.it43.com. root.eldia.it43.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      eldia.it43.com.
@       IN      A       192.238.2.2     ; IP Armin
EOL


service bind9 restart

```

### No. 1-5
(1) Lakukan konfigurasi sesuai dengan peta yang sudah diberikan. (Dapat dilihat di Topologi)

Jauh sebelum perang dimulai, ternyata para keluarga bangsawan, Tybur dan Fritz, telah membuat kesepakatan sebagai berikut:
Semua Client harus menggunakan konfigurasi ip address dari keluarga Tybur (dhcp).
Client yang melalui bangsa marley mendapatkan range IP dari [prefix IP].1.05 - [prefix IP].1.25 dan [prefix IP].1.50 - [prefix IP].1.100 (2)
Client yang melalui bangsa eldia mendapatkan range IP dari [prefix IP].2.09 - [prefix IP].2.27 dan [prefix IP].2 .81 - [prefix IP].2.243 (3)
Client mendapatkan DNS dari keluarga Fritz dan dapat terhubung dengan internet melalui DNS tersebut (4)
Dikarenakan keluarga Tybur tidak menyukai kaum eldia, maka mereka hanya meminjamkan ip address ke kaum eldia selama 6 menit. Namun untuk kaum marley, keluarga Tybur meminjamkan ip address selama 30 menit. Waktu maksimal dialokasikan untuk peminjaman alamat IP selama 87 menit. (5)

Di Paradis :
```
#!/bin/bash


cat <<EOL > /etc/default/isc-dhcp-relay
SERVERS="192.238.4.3"
INTERFACES="eth1 eth2 eth3 eth4"
EOL

cat <<EOL > /etc/sysctl.conf
net.ipv4.ip_forward=1
EOL

service isc-dhcp-relay restart
```

Di Tybur :
```
# Pada Tybur konfigurasi DHCP Server (Soal 1)

echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

echo 'subnet 192.238.1.0 netmask 255.255.255.0 {
#Soal 2 Range IP Marley
        range 192.238.1.05 192.238.1.25;
        range 192.238.1.50 192.238.1.100;
        option routers 192.238.1.1;
#Soal 4 DNS Server Fritz
        option broadcast-address 192.238.1.255;
        option domain-name-servers 192.238.4.2;
#Soal 5 Durasi DHCP Marley
        default-lease-time 1800;
        max-lease-time 5220;
}

subnet 192.238.2.0 netmask 255.255.255.0 {
#Soal 3 Range IP Eldia
        range 192.238.2.09 192.238.2.27;
        range 192.238.2.81 192.238.2.243;
        option routers 192.238.2.1;
#Soal 4 DNS Server Fritz
        option broadcast-address 192.238.2.255;
        option domain-name-servers 192.238.4.2;
#Soal 5 Durasi DHCP Eldia
        default-lease-time 360;
        max-lease-time 5220;
}

subnet 192.238.3.0 netmask 255.255.255.0 {
        option routers 192.238.3.1;
}

subnet 192.238.4.0 netmask 255.255.255.0 {
        option routers 192.238.4.1;
} ' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```
Bukti dhcp sudah berhasil : 
![image](https://github.com/user-attachments/assets/bd609361-71bb-4f38-858f-68e0cbd976c4)
![image](https://github.com/user-attachments/assets/29d63436-524e-4689-a061-3696aab15c96)

### No. 6-12
Armin berinisiasi untuk memerintahkan setiap worker PHP untuk melakukan konfigurasi virtual host untuk website berikut https://intip.in/BangsaEldia dengan menggunakan php 7.3 (6)
Dikarenakan Armin sudah mendapatkan kekuatan titan colossal, maka bantulah kaum eldia menggunakan colossal agar dapat bekerja sama dengan baik. Kemudian lakukan testing dengan 6000 request dan 200 request/second. (7)
Karena Erwin meminta “laporan kerja Armin”, maka dari itu buatlah analisis hasil testing dengan 1000 request dan 75 request/second untuk masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut:
Nama Algoritma Load Balancer
Report hasil testing pada Apache Benchmark
Grafik request per second untuk masing masing algoritma. 
Analisis (8)

Dengan menggunakan algoritma Least-Connection, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 1000 request dengan 10 request/second, kemudian tambahkan grafiknya pada “laporan kerja Armin”. (9)
Selanjutnya coba tambahkan keamanan dengan konfigurasi autentikasi di Colossal dengan dengan kombinasi username: “arminannie” dan password: “jrkmyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/supersecret/ (10)
Lalu buat untuk setiap request yang mengandung /titan akan di proxy passing menuju halaman https://attackontitan.fandom.com/wiki/Attack_on_Titan_Wiki (11) 
hint: (proxy_pass)
Selanjutnya Colossal ini hanya boleh diakses oleh client dengan IP [Prefix IP].1.77, [Prefix IP].1.88, [Prefix IP].2.144, dan [Prefix IP].2.156. (12) 
hint: (fixed in dulu clientnya)


- No.6 

Di PHP Worker (Armin, Eren, Mikasa):
```
# Soal 6: Jalankan pada setiap PHP worker (Armin, Eren, Mikasa)
mkdir -p /var/www/eldia.it43.com

wget --no-check-certificate 'https://drive.google.com/uc?export=download&id=1TvebIeMQjRjFURKVtA32lO9aL7U2msd6' -O /root/bangsaEldia.zip
unzip /root/bangsaEldia.zip -d /var/www/eldia.it43.com
rm -rf /root/bangsaEldia.zip

echo '
server {

        listen 80;

        root /var/www/eldia.it43.com;

        index index.php index.html index.htm;
        server_name _;

        location / {
                        try_files $uri $uri/ /index.php?$query_string;
        }

        # pass PHP scripts to FastCGI server
        location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
        }

location ~ /\.ht {
                        deny all;
        }

        error_log /var/log/nginx/jarkom_error.log;
        access_log /var/log/nginx/jarkom_access.log;
 }' > /etc/nginx/sites-available/eldia.it43.com

ln -s /etc/nginx/sites-available/eldia.it43.com /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service php7.3-fpm start
service php7.3-fpm restart
service nginx restart
nginx -t
```

- No 7

Di Fritz :

```
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     eldia.it43.com. root.eldia.it43.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      eldia.it43.com.
@       IN      A       192.238.3.3     ; IP Colossal' > /etc/bind/eldia/eldia.it43.com

service bind9 restart
```

Di Collosal : 
```
echo '
 upstream myweb  {
        server 192.238.2.2; #IP Armin
        server 192.238.2.3; #IP Eren
        server 192.238.2.4; #IP Mikasa
 }

 server {
        listen 80;
        server_name eldia.it43.com;

        location / {
        proxy_pass http://myweb;
        }
 }' > /etc/nginx/sites-available/lb-php

ln -s /etc/nginx/sites-available/lb-php /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service nginx restart
nginx -t
```
Di Client (Erwin):

Jalankan 
    
    ab -n 6000 -c 200 http://eldia.it43.com/  

Hasil : 

![image](https://github.com/user-attachments/assets/4998ece7-a4ab-4a9c-9fae-827ddf093c41)

- No 8 

Pada Collosal : 
```
echo '
 upstream myweb  {
    least_conn; (Untuk Algoritma Least connection)
    ip_hash; (Untuk Algoritma iphash)
    (Tanpa Kedua menjadi Round-robin)
        server 192.238.2.2; #IP Armin
        server 192.238.2.3; #IP Eren
        server 192.238.2.4; #IP Mikasa
 }

 server {
        listen 80;
        server_name eldia.it43.com;

        location / {
        proxy_pass http://myweb;
        }
 }' > /etc/nginx/sites-available/lb-php

ln -s /etc/nginx/sites-available/lb-php /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service nginx restart
nginx -t
```
Di Erwin : 

    ab -n 1000 -c 75 http://eldia.it43.com/

Round-robin :

![image](https://github.com/user-attachments/assets/131135bb-ff5f-4df9-86f3-9a5c003f5efd)

Least-con : 

![image](https://github.com/user-attachments/assets/d3431c8d-ecec-4bb0-8bdb-6b2bc22d1f94)

Ip hash :

![image](https://github.com/user-attachments/assets/626eb370-2291-444f-bf62-144d76ff9148)



- No 9

Di Worker (Armin, Eren,atau Mikasa) :

    service nginx stop

Di Erwin : 

    ab -n 1000 -c 10 http://eldia.it43.com/

3 Worker : 

![image](https://github.com/user-attachments/assets/d1de7896-063f-4573-839b-3284d2734534)

2 Worker : 

![image](https://github.com/user-attachments/assets/369b8e38-3d54-4823-abc6-fec1adb2a180)

1 Woeker :

![image](https://github.com/user-attachments/assets/2cc8bdfe-1b9c-4fa9-9b71-0449192b1873)

- No 10 

Di Collosal :
```
mkdir /etc/nginx/supersecret
htpasswd -b -c /etc/nginx/supersecret/htpasswd arminannie jrkmit43

echo '
 upstream myweb  {
        least_conn;
        server 192.238.2.2; #IP Armin
        server 192.238.2.3; #IP Eren
        server 192.238.2.4; #IP Mikasa
 }

 server {
        listen 80;
        server_name eldia.it43.com;

        location / {
        auth_basic "Restricted Access";
        auth_basic_user_file /etc/nginx/supersecret/htpasswd;
        proxy_pass http://myweb;
        }
 }' > /etc/nginx/sites-available/lb-php

ln -s /etc/nginx/sites-available/lb-php /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service nginx restart
nginx -t
```

Di Erwin : 

    lnyx 192.238.3.3

Tampilan awal 

![image](https://github.com/user-attachments/assets/44ac8db1-f3da-4de8-b001-47f1790604ce)

Tampilan setelah masuk : 

![image](https://github.com/user-attachments/assets/6e9e71ca-70f6-4d8a-9b19-4c2348e117ab)

