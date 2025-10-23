Sprint 1. Instal·lació i Configuració Base


Virtualització i Muntatge del SO Ubuntu

Aquesta primera fase se centra en la instal·lació i configuració del nostre sistema operatiu principal. Prepararem l'entorn de treball virtualitzant una instal·lació d'Ubuntu 22 mitjançant l'hipervisor VirtualBox. La màquina virtual (VM) que crearem servirà com a imatge "plantilla" que farem servir de punt de partida durant la resta del curs.


Per començar el procés, iniciarem l'assistent de creació de màquines a VirtualBox amb el botó "New". Haurem d'indicar un nom per a la VM i seleccionar la imatge ISO d'Ubuntu 22.

Un detall crucial per a aquesta pràctica és assegurar-nos de desmarcar l'opció "Skip unattended installation" (Ometre la instal·lació desatesa). Aquest pas és fonamental, ja que ens donarà accés a l'instal·lador manual. D'aquesta manera, evitarem l'assistent automàtic i tindrem control total sobre el procés, podent definir nosaltres mateixos l'esquema de particions, la creació de l'usuari i altres paràmetres avançats.

<img width="926" height="1043" alt="instalacio1" src="https://github.com/user-attachments/assets/0bf7a96c-f82d-4113-a397-f3499ffa3a4b" />

<img width="944" height="683" alt="instalacio2" src="https://github.com/user-attachments/assets/f12dea96-b1b1-453f-9890-ac8b9680a7fe" />

<img width="955" height="684" alt="instalacio3" src="https://github.com/user-attachments/assets/6018982e-e521-484b-9710-fce44f9060eb" />

<img width="956" height="672" alt="instalacio4" src="https://github.com/user-attachments/assets/525f5e30-f79f-4ab3-bbb9-7d7bcbb35dcd" />

<img width="963" height="678" alt="instalacio5" src="https://github.com/user-attachments/assets/820a07db-9cf1-47ee-b6ed-a0adebc4246c" />

<img width="961" height="677" alt="instalacio6" src="https://github.com/user-attachments/assets/ebf70931-0ab4-4d05-8c93-550864ab764a" />

<img width="957" height="677" alt="instalacio7" src="https://github.com/user-attachments/assets/e47f3b62-d7e7-43ba-b825-3df9fe68c98d" />

<img width="958" height="676" alt="instalacio8" src="https://github.com/user-attachments/assets/7e1e2338-bdb6-445c-8e7b-80149bea3cba" />

<img width="958" height="676" alt="instalacio9" src="https://github.com/user-attachments/assets/c4771b7a-105a-4a1f-ae40-81608f19a5c6" />

<img width="959" height="677" alt="instalacio10" src="https://github.com/user-attachments/assets/1f314106-463b-4c8d-b21d-112e7210f733" />

<img width="960" height="674" alt="instalacio11" src="https://github.com/user-attachments/assets/8ff3d420-01ec-4aab-9e42-32a216ea7486" />


Per definir l'esquema de particionament manual, s'utilitza l'opció "+" (afegir) disponible a l'eina de gestió de discos de l'instal·lador. Tot i que les configuracions poden ser complexes, una instal·lació robusta requereix diverses particions bàsiques, les quals es detallen a continuació:

/ (Arrel): Aquesta és la partició fonamental que conté la totalitat del sistema operatiu i els fitxers de programari. La mida recomanada sol fluctuar entre 15 i 30 GB, depenent de l'ús previst. Atès que no es preveuen instal·lacions de programari especialment pesades per a aquesta pràctica, s'ha determinat una mida de 20 GB.

/boot: Aquest punt de muntatge és crític, ja que allotja els fitxers essencials per a l'arrencada del sistema, com el nucli (kernel) i l'initrd. Es recomana reservar entre 500 MB i 1 GB. Per garantir prou espai per a futures actualitzacions del nucli i evitar problemes a llarg termini, s'ha optat per assignar 1 GB.

/home: Aquí és on s'emmagatzemen tots els fitxers i configuracions personals dels usuaris (ex: Documents, Descàrregues, Escriptori). És una pràctica estàndard separar /home de l'arrel (/), la qual cosa permet reinstal·lar el sistema operatiu sense perdre les dades personals. Tot i que normalment s'assigna a /home tot l'espai restant del disc, en aquest cas s'ha establert una mida de 15 GB, per complir amb el requisit de l'activitat de mantenir 40 GB d'espai lliure.

swap (Àrea d'intercanvi): Es tracta d'un espai al disc que el sistema utilitza com a memòria virtual (un "coixí") quan la memòria RAM física s'esgota. Tot i que no s'ha implementat en aquest cas, es recomana generalment assignar-hi entre 4 i 8 GB. Cal destacar que per a utilitzar la funció d'hibernació, la mida de la swap ha de ser superior a la quantitat de RAM total del sistema.

Partició del sistema EFI: Aquesta partició és un requisit indispensable per a tots els sistemes que arrenquen mitjançant el microprogramari UEFI. Emmagatzema el gestor d'arrencada. La mida estàndard recomanada per a aquesta partició és d'entre 300 i 600 MB.

<img width="1000" height="696" alt="instalacio12" src="https://github.com/user-attachments/assets/be018922-8414-40ed-aea0-3c77dba82b48" />

<img width="951" height="680" alt="instalacio13" src="https://github.com/user-attachments/assets/b5da9717-2a2e-4c1e-a742-bda9575af626" />

<img width="945" height="676" alt="instalacio14" src="https://github.com/user-attachments/assets/68db8198-62bc-42a6-9e84-9273e53e03db" />


Configuració d'Arrencada Dual (Dual-Boot) amb Windows
Després de la configuració inicial d'Ubuntu, es va procedir a instal·lar un segon sistema operatiu (Windows 10/11) al mateix disc dur virtual. L'objectiu és crear una configuració d'arrencada dual, permetent a l'usuari triar quin sistema operatiu executar en engegar la màquina.

Instal·lació de Windows: Es va muntar la imatge ISO d'instal·lació de Windows a la unitat òptica de la màquina virtual i es va reiniciar, arrencant des d'aquesta ISO.

Selecció de la Partició: Durant l'assistent d'instal·lació de Windows, a la pantalla de selecció d'unitat, es va escollir l'espai lliure (no assignat) per a la instal·lació. Es va permetre a l'instal·lador de Windows crear les seves particions necessàries (NTFS) en aquest espai.

<img width="1020" height="835" alt="instalacio15_w" src="https://github.com/user-attachments/assets/78803df2-2337-4296-b586-3b1393b1f055" />

<img width="861" height="565" alt="instalacio16_w" src="https://github.com/user-attachments/assets/6983a16d-8315-43b9-abe7-7834a815db93" />

<img width="1064" height="599" alt="instalacio17_w" src="https://github.com/user-attachments/assets/559883c3-0da1-427f-a9d0-b9e415705e10" />

<img width="797" height="605" alt="instalacio18_w" src="https://github.com/user-attachments/assets/d20f0e1e-9252-495b-9701-4cb499521121" />

<img width="878" height="640" alt="instalacio19_w" src="https://github.com/user-attachments/assets/7b80f1f2-671f-48b9-9f55-9a55f82c0941" />

<img width="996" height="797" alt="instalacio20_w" src="https://github.com/user-attachments/assets/5f52058d-c3d7-4c38-8b75-9cc7731cea6b" />

<img width="994" height="691" alt="instalacio21_w" src="https://github.com/user-attachments/assets/ef2d6894-c124-4f9d-9217-a2e4c2d477f8" />

<img width="1050" height="833" alt="instalacio22_w" src="https://github.com/user-attachments/assets/27017d62-b6cc-489d-9e9e-b4b4398ae8f0" />

<img width="1259" height="768" alt="instalacio23_w" src="https://github.com/user-attachments/assets/9ff7770a-3872-4d5b-80b2-ef7f42765f5a" />
<img width="758" height="396" alt="instalacio24_w" src="https://github.com/user-attachments/assets/6b56e732-3f0f-4281-a5af-d07590eeb45d" />
<img width="766" height="93" alt="instalacio25_w" src="https://github.com/user-attachments/assets/78923e7b-af62-4e17-8079-40ab0ce13a47" />
<img width="917" height="1009" alt="instalacio26_w" src="https://github.com/user-attachments/assets/fc8b575f-4a23-46f2-aab1-a311114c94e8" />


Conseqüència i Resolució (Corrupció del GRUB):

Un cop finalitzada la instal·lació de Windows, en reiniciar la màquina, el menú d'arrencada GRUB d'Ubuntu ja no apareixia. La màquina arrencava directament a Windows.

Això és un comportament esperat, ja que l'instal·lador de Windows sobreescriu el sector d'arrencada (MBR o la configuració EFI) per prioritzar el seu propi gestor d'arrencada (Windows Boot Manager).

Aquesta situació va fer necessari el procés de reparació del gestor d'arrencada GRUB des d'un Live CD d'Ubuntu, per tal de recuperar l'accés a Ubuntu i afegir l'entrada de Windows al menú de selecció.


TIMESHIFT


Gestió de Punts de Restauració (Snapshots)
Per assegurar la integritat del sistema operatiu i poder revertir canvis no desitjats, s'implementarà un sistema de punts de restauració. L'eina seleccionada per a aquesta tasca és Timeshift, una solució robusta per crear i gestionar instantànies del sistema a Ubuntu.

Lògicament, el punt de partida per a aquesta implementació consisteix a efectuar la instal·lació del paquet de Timeshift dins de la nostra màquina virtual.


<img width="662" height="359" alt="timeshift1" src="https://github.com/user-attachments/assets/ff94ca28-a57a-46a9-b517-a458bfb6ed3b" />

<img width="655" height="476" alt="timeshift2" src="https://github.com/user-attachments/assets/f2879a02-c9c5-4b92-8ca8-7b48cb32ff88" />

<img width="660" height="305" alt="timeshift3" src="https://github.com/user-attachments/assets/1942f7c2-ffcd-4438-8e7f-4ee4e96c8fcb" />

<img width="656" height="366" alt="timeshift4" src="https://github.com/user-attachments/assets/dcd966d6-7e64-4205-a2e2-b90d6ed00da5" />

<img width="656" height="119" alt="timeshift5" src="https://github.com/user-attachments/assets/36bd7624-e1d3-4d47-bb4c-a0dfea97c23f" />

<img width="549" height="114" alt="timeshift6" src="https://github.com/user-attachments/assets/8e158048-6e17-4428-a4f6-9c4a6891fdbe" />

<img width="661" height="514" alt="timeshift7" src="https://github.com/user-attachments/assets/9cc2469c-ce1f-4ca1-a5f4-214fdfca154e" />



Configuració de xarxa bàsica
Per configurar la xarxa en primera instancia podem veure la configuració a través dels paràmetres a l'opció de xarxa. Des d'aquest punt entrem a les opcions del cablejat per comprovar quina IP tenim i amb el mode manual la podem canviar al nostre gust.

<img width="663" height="435" alt="timeshift8" src="https://github.com/user-attachments/assets/ed6aec22-dcf1-4f2b-938c-d701c7fb5875" />

<img width="661" height="366" alt="timeshift9" src="https://github.com/user-attachments/assets/dff23473-999d-4835-b99e-931d0d86ab1a" />

<img width="656" height="466" alt="timeshift10" src="https://github.com/user-attachments/assets/a470a586-c187-4563-a6d1-8456ec0d0f65" />

<img width="660" height="241" alt="timeshift11" src="https://github.com/user-attachments/assets/7d82810e-17fb-4b5f-b40b-b931b7055de6" />


Comandes generals i instal·lacions.
Utilitzarem el pinning packet

Com podem observar tenim 2 versions de VLC disponibles, la 4.0.0 que es la candidata, i la 3.0.16. Mitjançant pinning packet farem que la candidata sigui la 3.0.16.

<img width="830" height="385" alt="pining1" src="https://github.com/user-attachments/assets/9de2e709-7b9d-4016-af9d-af2095c7f82b" />

<img width="824" height="67" alt="pining2" src="https://github.com/user-attachments/assets/1a062490-d1be-465f-8c69-baf36705bae9" />

<img width="815" height="481" alt="pining3" src="https://github.com/user-attachments/assets/b5958445-e3db-470e-8301-13b99dc033ca" />

<img width="766" height="181" alt="pining4" src="https://github.com/user-attachments/assets/41fff7cb-53eb-4dd8-9360-851ede62de15" />

<img width="814" height="268" alt="pining5" src="https://github.com/user-attachments/assets/d485997d-2803-46aa-bd96-b5483f87f80b" />

<img width="824" height="444" alt="pining6" src="https://github.com/user-attachments/assets/40d0109d-0cd2-4121-b744-510c28572965" />

<img width="822" height="249" alt="pining7" src="https://github.com/user-attachments/assets/d4f31b92-3c48-430e-b105-14c28e2beca1" />
































