

Fase 1 - Instal·lació del sistema operatiu


En aquesta primera fase hem configurat una màquina virtual amb VirtualBox, assignant-li els recursos mínims sol·licitats (4 GB de RAM i 50 GB d'emmagatzematge) i carregant la imatge ISO. Després de completar l'assistent d'instal·lació, configurant l'usuari i l'idioma, hem validat que el sistema operatiu s'inicia i arriba a l'escriptori correctament.

<img width="1050" height="833" alt="image" src="https://github.com/user-attachments/assets/048d7550-8ca5-4245-bc48-7cadfeb42d5c" />


<img width="776" height="395" alt="image" src="https://github.com/user-attachments/assets/80cc27fc-2f77-444b-bae5-63e3003fbb15" />


<img width="1098" height="899" alt="image" src="https://github.com/user-attachments/assets/c97e1111-1434-47a1-871f-85020a4edf75" />


Fase 2 - Punts de restauració

Hem accedit a les eines del sistema per cercar i configurar els punts de restauració. Després d'activar la protecció per a la unitat C: i generar un punt de restauració manual, hem aplicat un petit canvi al sistema per, posteriorment, restaurar-lo i verificar que l'eina compleix la seva funció correctament


<img width="763" height="642" alt="image" src="https://github.com/user-attachments/assets/d77c9c18-2b95-4386-8c29-229968d11801" />

<img width="796" height="511" alt="image" src="https://github.com/user-attachments/assets/49be845b-730c-4236-b573-c0129858efa3" />


<img width="531" height="514" alt="image" src="https://github.com/user-attachments/assets/16c8a67d-a2be-4898-8df2-7925f115f349" />

Un cop generat el nostre punt de restauració manual, hem realitzat un canvi visible al sistema (crear una carpeta/canviar configuració). Acte seguit, hem executat la restauració per verificar que l'equip torna a l'estat exacte en què es trobava, desfent el canvi.


<img width="472" height="304" alt="image" src="https://github.com/user-attachments/assets/91031052-b6b5-45ed-adac-3988fecbdf8e" />


<img width="403" height="148" alt="image" src="https://github.com/user-attachments/assets/341947c2-4741-48a6-9cba-12bbf3a504e9" />

<img width="768" height="608" alt="image" src="https://github.com/user-attachments/assets/083715ca-05c3-4251-8a18-f159398b08df" />

<img width="492" height="516" alt="image" src="https://github.com/user-attachments/assets/bc27991e-7305-4375-8b0b-b8140618fd4d" />


<img width="568" height="462" alt="image" src="https://github.com/user-attachments/assets/a5312997-15fa-4ada-bfeb-303148e5d4a2" />



<img width="470" height="231" alt="image" src="https://github.com/user-attachments/assets/1e548e06-bb9d-4916-bb11-e3cd9201520c" />



Fase 3 - Llicències de Windows


Per comprovar l'estat legal del nostre sistema operatiu, hem accedit a l'apartat Configuració i posteriorment a Sistema i Activació. Aquesta pantalla ens indica si la nostra còpia de Windows es troba actualment activada o no.


<img width="1023" height="787" alt="image" src="https://github.com/user-attachments/assets/08676ddb-9739-435f-90ad-5f0a21c14334" />

Hem executat la comanda slmgr /xpr a través del cmd per esbrinar el tipus de llicenciament de l'equip, el qual hem detallat a l'informe. A més, consultant botigues oficials, hem determinat el preu aproximat d'una llicència original.  

La lletra "N" significa que és una versió especial per al mercat europeu que ve sense el Windows Media Player preinstal·lat (per complir amb lleis antimonopoli), i la part d'Educació indica que és una variant de la versió Pro dissenyada per a entorns acadèmics. El "modo de notificación" (mode de notificació) vol dir que el Windows no està activat. El període de prova ha caducat o no s'ha introduït cap clau de producte vàlida i, per tant, el sistema començarà a llançar avisos i marques d'aigua demanant que l'activis.

<img width="836" height="340" alt="image" src="https://github.com/user-attachments/assets/fab579c2-1b15-48ef-a1d7-388c8cfb8719" />


Pel que fa als preus oficials a la botiga de Microsoft per a Espanya actualment:

Una llicència oficial de Windows 11 Pro (o Pro N) costa 259,00 €.

Una llicència oficial de Windows 11 Home (o Home N) costa 145,00 €.



Fase 4 - Gestor d'arrencada

Executant bcdedit amb permisos d'administrador, hem visualitzat els blocs del gestor d'arrencada. El Boot Manager decideix el temps d'espera (timeout) i quin sistema arrenca per defecte, mentre que el Boot Loader indica a quina partició (C:) i amb quin fitxer (winload.efi) es carrega el Windows 11 .  


<img width="846" height="647" alt="image" src="https://github.com/user-attachments/assets/f06fc076-b045-407d-87c9-c78318609658" />


**Quin sistema s'està arrencant?** S'està arrencant el Windows 10 (tal com indica l'apartat description del Cargador d'arrencada).

**A quin disc o partició està instal·lat?** Està instal·lat a la partició C: (com indica el paràmetre device).

**Quant temps espera abans d'arrencar?** Espera 30 segons (determinat pel paràmetre timeout a l'Administrador d'arrencada).

**Quin fitxer inicia Windows?** El fitxer encarregat d'iniciar-lo és \Windows\system32\winload.exe (indicat al paràmetre path).


**Qui decideix l'arrencada (Boot Manager):** L'"Administrador de arranque de Windows" és qui controla el menú de selecció, el temps d'espera (timeout) i estableix quin sistema s'inicia per defecte.

**Qui carrega el sistema (Boot Loader):** El "Cargador de arranque de Windows" és qui pren el relleu, busca a la partició corresponent (C:) el fitxer exacte d'inici (winload.exe) i carrega el sistema operatiu a la memòria.


Guia Pràctica: Fase 5 - Xarxa bàsica


Per iniciar la configuració de xarxa, el primer pas ha estat obrir la configuració del sistema i paral·lelament consultar l'estat actual de la nostra connexió. Executant la comanda ipconfig al Símbol del sistema, hem obtingut les dades bàsiques assignades a la nostra màquina virtual (adreça IP, màscara i porta d'enllaç).  

<img width="837" height="295" alt="image" src="https://github.com/user-attachments/assets/e7b440b5-848a-453a-8f85-ed441b9e55ac" />




Hem accedit a les propietats de l'adaptador de xarxa per modificar l'assignació d'IP del protocol IPv4. Després de verificar que el sistema utilitzava una assignació dinàmica (DHCP automàtic) , ho hem canviat a una configuració d'IP fixa, introduint manualment la nova adreça, la màscara de subxarxa, la porta d'enllaç i els servidors DNS.  


<img width="439" height="467" alt="image" src="https://github.com/user-attachments/assets/dd025666-6127-4c85-a74d-3a31c70c5f54" />



<img width="420" height="469" alt="image" src="https://github.com/user-attachments/assets/a139c67a-44fc-4d55-aff5-00e555c24b28" />



<img width="718" height="268" alt="image" src="https://github.com/user-attachments/assets/29eae587-1c53-4ff9-9553-9e988115c13e" />


Guia Pràctica: Fase 6 - Comandes generals


Hem iniciat l'entorn PowerShell. A diferència del cmd clàssic, PowerShell és molt més potent, ja que permet treballar amb objectes i automatitzar tasques complexes . En aquesta primera part, hem provat les comandes bàsiques de gestió de fitxers creant un directori (mkdir), desplaçant-nos-hi (cd), creant un fitxer (echo), llistant el contingut (dir) i finalment eliminant l'arxiu creat (del) .

<img width="861" height="562" alt="image" src="https://github.com/user-attachments/assets/0bbe6ffd-77ea-4c93-ae3b-86f8815a5889" />

Hem procedit a l'execució de comandes d'administració del sistema. Hem identificat l'equip i l'usuari amb hostname i whoami, hem consultat les característiques del maquinari amb systeminfo, i hem gestionat aplicacions actives llistant-les amb tasklist i forçant el seu tancament amb taskkill . Addicionalment, hem provat les comandes de xarxa per comprovar l'estat d'IP (ipconfig), connexió exterior (ping) i ports oberts (netstat -an) .  

<img width="915" height="725" alt="image" src="https://github.com/user-attachments/assets/5caa6a52-741b-4ce4-b5a3-24ac9c10e2fd" />



<img width="709" height="639" alt="image" src="https://github.com/user-attachments/assets/5d136568-1936-43d3-9d17-ed4d1045d5d6" />



<img width="500" height="115" alt="image" src="https://github.com/user-attachments/assets/009ed395-fed7-44d6-825f-76ecd4619a91" />


<img width="474" height="174" alt="image" src="https://github.com/user-attachments/assets/ac5ebff6-53b2-4c9c-99f5-c09747550900" />



<img width="924" height="679" alt="image" src="https://github.com/user-attachments/assets/abf31e87-8be7-4056-8f22-fe1712155362" />



<img width="636" height="258" alt="image" src="https://github.com/user-attachments/assets/63925cfb-b37a-4446-b957-6b303da6d58a" />



<img width="916" height="679" alt="image" src="https://github.com/user-attachments/assets/df9e6080-e9cf-4310-8873-23b5916688cb" />


