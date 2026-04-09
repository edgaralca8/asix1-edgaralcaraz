**Servidor actualitzacions**



En primer lloc, instal·larem el paquet apache
<img width="754" height="344" alt="1" src="https://github.com/user-attachments/assets/1282f172-fe68-402b-8a8a-1bfd6984840e" />

Segudiament, instal·larem el paquet mirror, que serà el que ens permetrà copiar qualsevol cosa que tinguem en un directori a un altre, com si fos un mirall.

<img width="749" height="277" alt="2" src="https://github.com/user-attachments/assets/d1f46c98-fe48-4f84-9c60-a090651c4cde" />

A continuació, al fitxer /etc/apt/mirror.list configurarem el paquet d'instal·lació de google chrome.

<img width="856" height="783" alt="1edgar" src="https://github.com/user-attachments/assets/8c9401f9-c9f4-4eda-a979-9537a8c523bb" />

<img width="739" height="472" alt="3" src="https://github.com/user-attachments/assets/53f46260-cc09-4203-8fd9-58e710708fa6" />

Un cop tenim aquest fitxer modificat executarem l'apt-mirror

<img width="862" height="619" alt="4" src="https://github.com/user-attachments/assets/1043761f-cb75-4417-a984-c10436869f41" />

Després, ens assegurarem que a la carpeta del mirror hi hagi el paquet d'instal·lació del chrome de la següent manera:

<img width="860" height="259" alt="5" src="https://github.com/user-attachments/assets/5c8d3970-f550-4acd-a4ff-bf25d2afc1b9" />


Si hem seguit tots aquests passos la part de configurar el servidor ja ha finalitzat, ara procedirem a la configuració del client per poder accedir al instal·lador del chrome del client al servidor.


- Client

Configuració del fitxer /etc/apt/sources.list en la màquina client. Es modifica la URL de Google Chrome perquè apunti a la IP del servidor mirror local (10.0.2.5) en lloc dels servidors oficials.

<img width="737" height="480" alt="6" src="https://github.com/user-attachments/assets/e4bb7f94-692e-419c-8db4-0f2cb972ecda" />

Importació de la clau pública GPG de Google. Aquest pas és necessari perquè el client pugui verificar l'autenticitat dels paquets descarregats des del mirror.

<img width="780" height="114" alt="7" src="https://github.com/user-attachments/assets/b9e3ce38-12b1-404d-8ee0-c1734ab009cb" />


Execució de apt install google-chrome-stable. Es confirma que el procés és correcte, ja que la descàrrega es realitza des de la IP local configurada (10.0.2.15 o la del mirror), validant que el mirror funciona correctament.

<img width="854" height="661" alt="8" src="https://github.com/user-attachments/assets/c01502a6-3a16-4e79-bd18-a0af50266231" />


**SERVIDOR **

Instal·lació de l'eina mdadm, necessària per a la gestió i administració de dispositius RAID mitjançant programari a Linux.


<img width="735" height="257" alt="log1" src="https://github.com/user-attachments/assets/3ce667a7-0b61-4dd2-b5ae-5f5e66788855" />

Identificació dels nous discs mitjançant el comandament fdisk -l. S'observen dos discs buits de 2 GiB cadascun (/dev/sdb i /dev/sdc) preparats per ser utilitzats.

<img width="765" height="489" alt="2" src="https://github.com/user-attachments/assets/263d3f0b-c4b5-4ff7-a4e4-29077fd09edd" />

Inicialització del procés de particionament amb fdisk. S'assigna una nova taula de particions de tipus DOS als dispositius per poder treballar-hi.

<img width="819" height="578" alt="3" src="https://github.com/user-attachments/assets/e0539850-874a-498e-b79c-9b63414a68b5" />

Creació d'una partició primària al disc /dev/sdc. Se li assigna tot l'espai disponible (2 GiB) i es guarden els canvis a la taula de particions.

<img width="858" height="572" alt="4" src="https://github.com/user-attachments/assets/6500bc02-2a63-4ed2-8956-aa69a3ed4aad" />

Creació de la partició al disc /dev/sdb. De la mateixa manera que amb l'anterior, es defineix una partició primària que ocuparà la totalitat de la unitat.

<img width="811" height="692" alt="5" src="https://github.com/user-attachments/assets/82931f85-7d8d-423c-b5ff-119cc79cbfe4" />


Verificació final de les particions creades. Es confirma que ara existeixen els dispositius /dev/sdb1 i /dev/sdc1, ambdós de 2G i amb l'identificador de tipus "Linux".

<img width="809" height="680" alt="6" src="https://github.com/user-attachments/assets/e029c7da-5be9-41be-b405-479be79fd746" />


Preparació del punt de muntatge. Es crea el directori /mnt/raid1 i se li assignen permisos totals (777) per permetre l'accés i les proves posteriors.

<img width="660" height="137" alt="7" src="https://github.com/user-attachments/assets/bf77a66b-4663-4205-b78c-417cb003c8b4" />


Creació del dispositiu RAID amb el comandament mdadm --create. Es defineix el nivell RAID 1 (mirall) amb dos dispositius actius (/dev/sdb1 i /dev/sdc1).

<img width="845" height="211" alt="8" src="https://github.com/user-attachments/assets/1f8c3630-ead8-4952-9de4-7e2188e15a1a" />


Formatació del nou volum RAID /dev/md0 amb el sistema de fitxers ext4. Això permet que el volum sigui utilitzable per a l'emmagatzematge de dades.


<img width="844" height="250" alt="9" src="https://github.com/user-attachments/assets/bcf9a7a2-8fe5-4515-80cc-3537868ed9e0" />


Verificació del detall del RAID amb mdadm --detail /dev/md0. Es confirma que l'estat és "clean", que ambdós dispositius estan en sincronia ("active sync") i que la redundància funciona correctament.


<img width="839" height="514" alt="10" src="https://github.com/user-attachments/assets/b017fd79-31ad-4d35-bbc2-e2a16274846e" />

Escaneig de la configuració actual del RAID amb mdadm --detail --scan. El resultat es bolca al fitxer /etc/mdadm/mdadm.conf per assegurar que el sistema reconegui el volum automàticament en arrencar.


<img width="840" height="106" alt="11" src="https://github.com/user-attachments/assets/25ff4434-a28c-4f42-b65c-a21e2a8ea63b" />


Edició manual del fitxer /etc/mdadm/mdadm.conf. S'afegeix la línia DEVICE especificant les particions que formen part de l'array per donar més context al sistema.

<img width="843" height="322" alt="12" src="https://github.com/user-attachments/assets/eafdac56-355d-4cad-a399-e2ed60c579e7" />


Configuració del muntatge automàtic al fitxer /etc/fstab. S'afegeix la línia corresponent a /dev/md0 amb el punt de muntatge /mnt/raid1, assegurant que el RAID estigui disponible després de cada reinici.


<img width="859" height="531" alt="13" src="https://github.com/user-attachments/assets/4a6d169b-c99a-4b2e-993c-02b0a32fcae7" />

Execució de update-initramfs -u. Aquest pas actualitza el sistema d'arrencada per incloure la nova configuració del RAID i garantir que es munti correctament des de l'inici.

<img width="725" height="90" alt="14" src="https://github.com/user-attachments/assets/1982eb6f-96da-472b-bcb4-1018f2e7459f" />


Reinici del sistema amb el comandament reboot per verificar que tota la configuració de persistència aplicada anteriorment funciona correctament.


<img width="599" height="77" alt="15" src="https://github.com/user-attachments/assets/a79ac9a7-38c7-4a46-8f78-ba37310d56fc" />


Verificació post-reinici. S'executa mdadm --detail /dev/md0 per confirmar que el RAID ha arrencat automàticament i es manté en estat "clean" amb els dos discs actius.


<img width="796" height="551" alt="16" src="https://github.com/user-attachments/assets/f1e4a86b-3ad8-4ac7-8658-3f341e1e2a20" />


Prova d'ús del RAID. Es navega fins al directori muntat i es creen elements de prova (touch dijous, mkdir divendres) per confirmar que el sistema de fitxers és totalment funcional.


<img width="672" height="256" alt="17" src="https://github.com/user-attachments/assets/4d623cda-2628-416b-82a8-61904627edeb" />


Es marca el disc /dev/sdb1 com a defectuós (-f) i posteriorment s'extreu del RAID (-r). L'estat del RAID canvia a "degraded", però les dades segueixen accessibles.


<img width="848" height="604" alt="18" src="https://github.com/user-attachments/assets/e6021fb4-11d2-45ab-9eda-ab070863391d" />


Verificació de la integritat de les dades durant la fallada. Es crea un nou fitxer (novainfosol1disk) i es comprova que, tot i tenir un disc menys, el sistema permet seguir treballant sense pèrdua d'informació.


<img width="709" height="70" alt="19" src="https://github.com/user-attachments/assets/07ebc0f0-6388-45b5-a704-49acaba07e6d" />


Recuperació del RAID. Després d'aturar i tornar a muntar l'array, s'afegeix de nou el disc /dev/sdb1. El sistema inicia automàticament el procés de "spare rebuilding" (reconstrucció) per tornar a sincronitzar les dades i recuperar la redundància.


<img width="847" height="780" alt="20" src="https://github.com/user-attachments/assets/29323f83-f1b7-4a4c-b69a-a189571c02c1" />


Finalització de la sincronització i verificació final. Un cop acabat el procés de reconstrucció, s'executa mount -a i es llista el contingut de la unitat per confirmar que tots els fitxers de prova continuen intactes. El detall de mdadm mostra que el RAID ha tornat a l'estat "clean" amb els 2 dispositius actius i sincronitzats, completant amb èxit el cicle de manteniment i recuperació davant fallades.


<img width="828" height="565" alt="21" src="https://github.com/user-attachments/assets/b36ed3ea-5808-47b0-91bc-1de6eaa51f13" />



**RAIDS**


Accés al directori /var/log i llistat del seu contingut. S'observen els diferents fitxers de registre del sistema (syslog, auth.log, kern.log) i com alguns ja presenten numeració (.1, .2.gz), indicant que han estat rotats prèviament.

<img width="854" height="423" alt="1" src="https://github.com/user-attachments/assets/2addd161-06a9-4f95-8d11-2c1f544798d4" />


Visualització del fitxer de configuració principal /etc/logrotate.conf. S'hi defineixen els paràmetres globals de rotació, com la freqüència setmanal (weekly), el manteniment de 4 còpies de seguretat (rotate 4) i la creació de nous fitxers buits després de la rotació (create).

<img width="844" height="642" alt="2" src="https://github.com/user-attachments/assets/25e1c4a1-b6c8-4080-8526-c080e2818ccf" />


Exploració del directori /etc/logrotate.d/. Aquest directori conté configuracions específiques per a diferents serveis instal·lats al sistema, com apache2, apt, mysql o ufw, permetent una gestió personalitzada per a cada aplicació.


<img width="851" height="154" alt="3" src="https://github.com/user-attachments/assets/dfa6def5-8677-4380-a0f5-9fede3d3cfde" />



Per provar com configurar la rotació d'un log en concret escollirem els logs de dpkg en aquest cas. lA configuració ens mostra que els arxius rotaran cada mes que d'aquests es conservaran els últims 12 arxius de logs antics abans d'eliminar-los, que els antics es comprimiràn, i que la compressió es farà després de la rotació. Finalment es donaran els permisos.

<img width="858" height="414" alt="dpkg" src="https://github.com/user-attachments/assets/79571862-14a4-4438-9bf0-2b235b225f05" />


Ús del comandament journalctl amb filtres temporals. Es demana el registre d'esdeveniments del sistema compresos entre les 12:00 i les 14:00 del dia 5 de març, mostrant informació detallada sobre l'arrencada del nucli (kernel).


<img width="857" height="848" alt="4" src="https://github.com/user-attachments/assets/b9705c15-9fee-45f6-a849-40f6ad798a5b" />


Filtratge de logs per dispositiu de maquinari. S'executa journalctl /dev/sda per visualitzar exclusivament els missatges relacionats amb el disc principal, on es detallen paràmetres com el model de disc, la mida del sector i l'estat de la memòria cau d'escriptura.


<img width="854" height="412" alt="5" src="https://github.com/user-attachments/assets/e55a01e5-2ee2-4b41-b87f-5afaad3c71c9" />

Proves de funcionament.

Ara veurem els logs del sistema al fitxer /etc/rsyslog.d/50-defaul.conf, en aquest fitxer podem configurar quins logs es mostren i quins no al fitxer al qual estan assignats. Després de modificar-lo s'ha de reiniciar el servei.


<img width="1224" height="798" alt="7" src="https://github.com/user-attachments/assets/7dfdf9b1-e4aa-4e55-9e55-7fec33953151" />


Per fer una prova enviarem una alerta al servei de mail i després farem un cat al arxiu on es guarden els logs del mail per veure si ha registrat l'alerta.

<img width="836" height="128" alt="8" src="https://github.com/user-attachments/assets/2f6aa665-dde7-44af-9da3-19adf0e67fec" />

Ara, el que volem es que TOTES les alertes de nivell critic quedin registrades a una nova carpeta, on podrem analitzar tots els logs d'alerta critica. Com hem dit abans si modifiquem aquest arxiu s'ha de reiniciar el sistema.


<img width="840" height="714" alt="9" src="https://github.com/user-attachments/assets/79f2bf11-80af-4d13-9705-14f2fbfe0de4" />


A continuació, per comprovar que els canvis funcionen crearem una alerta critica anomenada Alerta critica edgar, i llavors consultarem la carpeta dels logs que hem creat per comprovar si realment apareix l'alerta.

<img width="843" height="115" alt="10" src="https://github.com/user-attachments/assets/569fa203-8f61-4d75-973c-9eff0c88ddad" />

