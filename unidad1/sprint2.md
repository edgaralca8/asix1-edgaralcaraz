1.Sistemes de fitxer i particions
Fonaments de l'estructura física
Quan parlem de l'estructura física, ens referim exclusivament al maquinari o suport material que permet l'emmagatzematge de la informació. Això engloba dispositius com els discs durs mecànics (HDD), les unitats d'estat sòlid (SSD) o les memòries tipus flash.

En els HDD: La informació s'organitza magnèticament en pistes, sectors i cilindres.

En els SSD: L'emmagatzematge es realitza mitjançant cel·les de memòria. Aquests components físics són els fonaments sobre els quals s'edifiquen els mecanismes posteriors de lectura i escriptura de dades.

Organització lògica
Aquesta capa fa de pont entre el maquinari i l'usuari. L'estructura lògica és la forma en què el sistema operatiu interpreta i administra els bits del disc per convertir-los en elements recognoscibles, com ara carpetes, fitxers i enllaços simbòlics. El component clau aquí és el sistema de fitxers (ex: ext4, NTFS, FAT32), que actua com un protocol per definir la ubicació, l'escriptura i la recuperació de les dades, fent que l'accés a la informació sigui transparent i eficient per a l'usuari final.

Jerarquia de la informació i unitats d'assignació
L'estructura de la informació combina els aspectes físics i lògics per optimitzar com es desen les dades. Dins d'aquest àmbit, és crucial entendre la diferència entre com el disc veu les dades i com les veu el sistema operatiu:

El Sector (Nivell Físic): És la "casella" mínima d'emmagatzematge que ve definida de fàbrica pel maquinari. Tradicionalment era de 512 bytes, encara que els discs moderns (format avançat) utilitzen sovint sectors de 4 KB (4096 bytes). Aquesta unitat és fixa i immutable.

El Bloc (Nivell Lògic): El sistema operatiu no sol treballar sector a sector, sinó que agrupa diversos sectors en "blocs" per gestionar la informació de manera més àgil.

Eina d'anàlisi: Per obtenir una radiografia detallada de les unitats connectades, l'ordre fdisk -l és fonamental. Ens permet visualitzar paràmetres com la ruta del dispositiu (/dev/sda), la capacitat total, el tipus de taula de particions (MBR o GPT) i la geometria dels sectors.

sudo fdisk -l
<img width="839" height="654" alt="image" src="https://github.com/user-attachments/assets/721bd91b-aedc-4906-b4ab-772c026dd918" />
<img width="790" height="551" alt="image" src="https://github.com/user-attachments/assets/1c1ab286-64f5-449e-aae6-9d3a7adcee88" />


MIDA DEL BLOC (Unitat d'assignació)
Mentre que el sector és una limitació física, el bloc és la unitat lògica fonamental que utilitza el sistema operatiu per gestionar l'espai. Aquest paràmetre no ve imposat pel fabricant, sinó que es defineix quan donem format a la partició.

La tria de la mida del bloc és un factor clau d'optimització que implica un compromís:

Blocs grans: Milloren la velocitat de lectura i escriptura, però si guardem fitxers molt petits, es perd espai real de disc (l'anomenada fragmentació interna), ja que un fitxer de 1KB ocuparà un bloc sencer de 4KB.

Blocs petits: Aprofiten millor l'espai, però el sistema ha de gestionar molts més fragments, la qual cosa pot afectar lleugerament el rendiment.


<img width="789" height="139" alt="image" src="https://github.com/user-attachments/assets/de422f8a-61bf-4e3e-b911-6f2729e8fa90" />



FRAGMENTACIÓ INTERNA
La fragmentació interna es produeix quan un fitxer no omple completament un bloc assignat, deixant espai sense utilitzar. Aquest espai es considera desaprofitat. La mida del bloc és clau per minimitzar aquest tipus de fragmentació. Si reduïm la mida dels blocs, es pot disminuir la fragmentació interna, però això pot impactar negativament el rendiment, ja que el sistema haurà de gestionar més blocs.

Seguidament, crearem un fitxer nou anomenat hola, en el que escriurem "bon dia". Després comprovarem que existeix amb un "ls" i mostrarem el contingut per terminal amb "cat". Per demostrar la fragmentació interna executarem la comanda "du -b hola" i "du -sh hola". Podem comprovar que en la primera comanda mostra un 15 que vol dir que el fitxer ocupa 15 Bytes, en la segona comanda mostra la mida real que ocupa el fitxer, aquesta és 4Kb.


echo "bon dia" > hola

ls

cat hola

du -b hola

du -sh hola


<img width="798" height="359" alt="image" src="https://github.com/user-attachments/assets/3ca79d66-d908-46ac-94d1-deda905d7b2b" />


Per últim, si revisem per GUI els paràmetres del fitxers, ens mostra 15 Bytes.

<img width="515" height="651" alt="image" src="https://github.com/user-attachments/assets/c2e2dd84-8a10-475b-9b22-fa169c8d1e36" />


<img width="880" height="406" alt="image" src="https://github.com/user-attachments/assets/4934e8e4-5745-40b8-a528-4838cd4b5687" />

PARTICIONS:
<img width="783" height="545" alt="image" src="https://github.com/user-attachments/assets/1794796a-737a-4ed4-90cc-e596eb923d97" />




2. Gestió de processos.

El control del flux d'execució, o gestió de processos, és una de les tasques vitals del sistema operatiu (SO). Podem definir un procés com una instància d'un programa en execució, a la qual se li han assignat recursos específics (temps de CPU i espai en memòria RAM).

La responsabilitat del SO és orquestrar el cicle de vida d'aquests processos: des del seu naixement (creació) i execució, fins a la seva pausa o finalització (mort). L'objectiu és garantir la multitasca, permetent que diferents aplicacions coexisteixin i comparteixin els recursos disponibles sense conflictes.

Per supervisar aquesta activitat, disposem de diverses eines, però per entendre les dependències entre processos, la comanda pstree és la més il·lustrativa.

Aquesta ordre representa els processos actius com un arbre genealògic.

Permet veure clarament quin procés ha generat a quin altre (relació pare-fill).

La sortida variarà segons l'usuari que l'executi, mostrant només els processos rellevants per a aquell context.


pstree
<img width="1067" height="727" alt="image" src="https://github.com/user-attachments/assets/a6afb8cc-39f9-479b-a3d7-fa3eafa11329" />
<img width="1064" height="730" alt="image" src="https://github.com/user-attachments/assets/14035065-418a-4ebe-8988-241db7a6e0f4" />






3.Gestio d'usuaris, grups i permisos

En sistemes GNU/Linux, la gestió d’usuaris i grups es pot fer tant des de terminal com gràficament (en entorns com GNOME o KDE). Per obtenir ajuda sobre qualsevol comanda podem utilitzar:

man comanda
# o
comanda --help
Exercis
Crear usuari amb useradd
Com podem crear un usuari completament amb useradd, lo maxim possible?

Amb la comanda:

sudo useradd -m -s /bin/bash -c "Merda que s'actualitza cada dia i peta" -p $(openssl passwd -6) windows10
Paràmetres importants:

-m: Crea el directori personal
-s: Defineix l’intèrpret (ex: /bin/bash)
-c: Afegeix informació GECOS
-g: Defineix grup principal
-G: Defineix grups addicionals
-p : Defineix la contrasenya xifrada de l'usuari
openssl passwd -6: Genera el hash SHA-512 compatible amb /etc/shadow


<img width="1150" height="69" alt="image" src="https://github.com/user-attachments/assets/a6e22e28-6542-45fd-8c5e-0d362afcf3a4" />



<img width="803" height="209" alt="image" src="https://github.com/user-attachments/assets/061f960c-1001-4a2c-ac52-dc4a5ae18842" />



4. Copies de seguretat i auomatització de tasques
5.Quotes d'usuari
