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
Aquí tens la continuació amb el text reescrit i la comanda que faltava per completar l'explicació:

MIDA DEL BLOC (Unitat d'assignació)
Mentre que el sector és una limitació física, el bloc és la unitat lògica fonamental que utilitza el sistema operatiu per gestionar l'espai. Aquest paràmetre no ve imposat pel fabricant, sinó que es defineix quan donem format a la partició.

La tria de la mida del bloc és un factor clau d'optimització que implica un compromís:

Blocs grans: Milloren la velocitat de lectura i escriptura, però si guardem fitxers molt petits, es perd espai real de disc (l'anomenada fragmentació interna), ja que un fitxer de 1KB ocuparà un bloc sencer de 4KB.

Blocs petits: Aprofiten millor l'espai, però el sistema ha de gestionar molts més fragments, la qual cosa pot afectar lleugerament el rendiment.



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
4. Copies de seguretat i auomatització de tasques
5.Quotes d'usuari
