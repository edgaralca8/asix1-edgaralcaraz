**Fase 1: Configuració de Xarxa i Sistema Base** 

Establiment d'una adreça de xarxa fixa (10.0.2.15) per assegurar la disponibilitat permanent del servei LDAP.

<img width="582" height="477" alt="1png" src="https://github.com/user-attachments/assets/9cffe83c-0c68-4b95-ae9a-f23e4b699a09" />


Assignació del nom de sistema edgarserver mitjançant l'edició del fitxer /etc/hostname.

<img width="750" height="445" alt="2" src="https://github.com/user-attachments/assets/c4f850f3-8384-4f13-be51-2164afb93121" />


Actualització de la taula de resolució local (/etc/hosts) per associar la IP amb el nom de domini totalment qualificat (FQDN).

<img width="684" height="304" alt="3" src="https://github.com/user-attachments/assets/0893eed3-d61b-40b1-bcff-c0fe2df92967" />


**Fase 2: Instal·lació i Reconfiguració de slapd**

Instal·lació dels binaris del servidor slapd i les utilitats de gestió ldap-utils.

<img width="742" height="295" alt="4" src="https://github.com/user-attachments/assets/1bea228f-82f6-4608-83ea-e864adf7422c" />


Inspecció de l'estat del directori amb slapcat, detectant un domini provisional que requereix correcció.

<img width="726" height="295" alt="5" src="https://github.com/user-attachments/assets/83963644-76b3-4e29-aa1d-57379b088ead" />


Inici del procediment de configuració assistida a través de dpkg-reconfigure slapd.

<img width="1027" height="380" alt="6" src="https://github.com/user-attachments/assets/ed7077c0-60e8-48a3-b7f5-4e8e09f11b33" />


Definició de l'estructura base del directori utilitzant el domini gina.cat.

<img width="1683" height="284" alt="7" src="https://github.com/user-attachments/assets/9d91e425-7684-4340-b4d2-118db754ccc7" />

Creació i verificació de les credencials per al compte d'administració central.

<img width="1144" height="271" alt="8" src="https://github.com/user-attachments/assets/a4a38f47-a4aa-471c-ab87-ab8582f94b5e" />


Configuració de la política d'esborrat de dades en cas de desinstal·lació del programari.

<img width="745" height="280" alt="9" src="https://github.com/user-attachments/assets/7a3a2b29-a698-4dcc-a194-d16c3fedb732" />


Confirmació final del desplegament del nou directori i la seva base de dades associada.

<img width="1021" height="171" alt="10" src="https://github.com/user-attachments/assets/b5752d48-551d-4eed-a0b4-d1e016b425f9" />


**Fase 3: Disseny d'Estructura i Primers Registres (LDIF)**

Definició de la Unitat Organitzativa (OU) destinada als usuaris en un fitxer de text LDIF.

<img width="1194" height="260" alt="11" src="https://github.com/user-attachments/assets/92401d72-9e7d-4ad5-bbb4-79e42c4ed6f1" />


Creació del registre de l'usuari alu1, especificant atributs de sistema com el directori de treball i la shell.

<img width="1163" height="527" alt="12" src="https://github.com/user-attachments/assets/31771014-f22f-4055-849b-1c6ed86e57a6" />


Establiment d'un grup de seguretat anomenat alumnes amb l'ID 1001.

<img width="1020" height="246" alt="13" src="https://github.com/user-attachments/assets/94c0e2f1-3441-4cc9-bb9f-ca9a9e970883" />


Importació de la Unitat Organitzativa al directori actiu mitjançant l'ordre ldapadd.

<img width="1249" height="176" alt="14" src="https://github.com/user-attachments/assets/9e46551b-17ee-4217-bf66-d1d925ec8d43" />

Inclusió del grup i vinculació dels membres dins de l'estructura LDAP.

<img width="1122" height="210" alt="15" src="https://github.com/user-attachments/assets/c1fd722f-2b76-4d35-8244-c1ceacb70d95" />


**Fase 4: Preparació de la Màquina Client**

Validació de la connexió entre màquines mitjançant la traça de paquets ICMP (ping).

<img width="751" height="410" alt="16c" src="https://github.com/user-attachments/assets/7278bbd7-83cc-404a-9f49-e83312278444" />


Instal·lació dels mòduls d'interfície libnss-ldap i libpam-ldap per habilitar l'accés remot.

<img width="1071" height="86" alt="17c" src="https://github.com/user-attachments/assets/67cc67bd-e8d0-46e2-80af-f78e7bcc6d48" />


Apuntament del client cap a l'URI del servidor: ldap://10.0.2.15.

<img width="1191" height="404" alt="18c" src="https://github.com/user-attachments/assets/16967bd4-da0d-45f4-8c47-e9683c39a950" />


Especificació de la base de dades de cerca (dc=gina,dc=cat) per a les consultes d'usuari.

<img width="1193" height="383" alt="19c" src="https://github.com/user-attachments/assets/2bd46981-6c28-4162-8f8b-1028dd337f93" />


Selecció de la versió actualitzada del protocol (v3) per a la comunicació.

<img width="1196" height="425" alt="20c" src="https://github.com/user-attachments/assets/a6bb42a9-8452-40e0-a492-64c97d056859" />


Designació de l'administrador com a encarregat de la gestió de privilegis al client.

<img width="809" height="380" alt="21c" src="https://github.com/user-attachments/assets/dac18b8f-895a-45e7-9d1f-473c8a40b59b" />

Emmagatzematge xifrat de la clau d'accés en el fitxer de sistema /etc/ldap.secret.

<img width="1157" height="392" alt="22c" src="https://github.com/user-attachments/assets/add3973d-1b9c-4ce3-8694-095bdd1d99c8" />


Confirmació del compte d'usuari per a consultes de base de dades.

<img width="1157" height="376" alt="23c" src="https://github.com/user-attachments/assets/62aebe4e-3096-4b5e-951e-c2e778e03e6b" />


**Fase 5: Integració d'Autenticació i Entorn Gràfic**

Modificació del servei de noms (/etc/nsswitch.conf) per prioritzar les consultes LDAP.

<img width="1268" height="686" alt="24c" src="https://github.com/user-attachments/assets/2630b292-5235-4907-8831-85186c92a976" />


Programació del mòdul PAM per a la generació automàtica del directori Home en el primer accés.

<img width="1232" height="647" alt="25c" src="https://github.com/user-attachments/assets/f53f893d-1727-4449-b12f-008f348d3e17" />


Configuració de la política de contrasenyes compartides entre el sistema local i el directori.

<img width="1220" height="724" alt="26" src="https://github.com/user-attachments/assets/9710639e-386c-4ce9-acff-3fcd09cdc376" />


Ajust de la pantalla de benvinguda per permetre la introducció manual de noms d'usuari.

<img width="1199" height="273" alt="27c" src="https://github.com/user-attachments/assets/256fc7a2-901e-4e42-bc5b-cf662591036a" />


Comprovació de visibilitat de l'usuari mitjançant l'eina getent.

<img width="822" height="105" alt="28c" src="https://github.com/user-attachments/assets/540f8cf5-aec9-4fd5-bbd5-c044f8b0d683" />


Demostració d'inici de sessió efectiu en una sessió de terminal de client.

<img width="819" height="215" alt="29c" src="https://github.com/user-attachments/assets/830aa215-7f32-4a3e-b7d3-7f350e7637c4" />


**Fase 6: Panell de Control Web (LAM)**

Implementació de l'eina LDAP Account Manager per facilitar la gestió visual.

<img width="833" height="582" alt="30" src="https://github.com/user-attachments/assets/ffc0cece-2020-4e86-8077-79317254390f" />


Accés a la interfície de gestió a través del navegador web local.

<img width="832" height="694" alt="31" src="https://github.com/user-attachments/assets/f3ebfb3a-21e4-4ffc-b3e2-c501c95a6ffd" />


Personalització de les opcions de seguretat i sufixos del directori al LAM.

<img width="825" height="758" alt="32" src="https://github.com/user-attachments/assets/c9a87eb0-c3d6-4acd-a078-6b5973fd6466" />


Configuració dels tipus de comptes definint els sufixos LDAP on es realitzaran les cerques d'usuaris i grups.

<img width="845" height="324" alt="33" src="https://github.com/user-attachments/assets/6e868590-1b75-426e-9c61-568159da4f8b" />


Vinculació de les Unitats Organitzatives d'usuaris i grups amb les vistes del panell.

<img width="839" height="563" alt="34" src="https://github.com/user-attachments/assets/6370c8fc-1300-4dc4-b592-ee2a180ffe70" />


Inventari visual dels comptes existents al sistema.

<img width="829" height="655" alt="35" src="https://github.com/user-attachments/assets/224a2069-b359-44fc-886c-fc2504126b75" />


Exploració de l'arquitectura de branques del directori des de la interfície web.

<img width="833" height="250" alt="36" src="https://github.com/user-attachments/assets/f02cab0c-dea3-4987-b154-ebfe64c8809c" />


Ús del menú contextual per afegir noves entrades de forma assistida.

<img width="653" height="426" alt="37" src="https://github.com/user-attachments/assets/9368af64-72fd-42bc-87b6-33d20cd59eb0" />


Inici del tràmit d'alta d'un nou perfil d'usuari.

<img width="860" height="496" alt="38" src="https://github.com/user-attachments/assets/1fbc3932-c4b3-4393-9859-72431f81ae15" />


Registre de les dades d'identitat (Nom i Cognoms) al formulari.

<img width="1069" height="809" alt="39" src="https://github.com/user-attachments/assets/5efded24-fe13-47f9-8edd-804a08000da3" />


Definició dels atributs Unix pel nou usuari edgaralu.

<img width="1061" height="489" alt="40" src="https://github.com/user-attachments/assets/fa2c8ed6-a21b-4c90-a31b-426c251280e4" />


Verificació de la incorporació de l'usuari a la base de dades central.

<img width="1058" height="523" alt="41" src="https://github.com/user-attachments/assets/97628251-a3cb-4215-80fe-800d246489ba" />

Prova de reconeixement al client: l'usuari creat via web ja és accessible pel sistema.

<img width="818" height="89" alt="42" src="https://github.com/user-attachments/assets/7eedc466-1c3d-4e2a-8cb4-19e113bd22cd" />


**Fase 7: Explotació de Dades i Operacions Avançades**

Validació de la identitat d'usuari actiu en l'entorn de treball mitjançant l'ordre whoami.

<img width="860" height="292" alt="43" src="https://github.com/user-attachments/assets/1877f4b9-7077-4830-b637-9024334a7306" />


Redacció d'una estructura corporativa complexa mitjançant un script LDIF que inclou múltiples unitats organitzatives i grups.

<img width="1201" height="707" alt="44" src="https://github.com/user-attachments/assets/336ac547-2a02-4268-bb5e-f226b26cd417" />


Processament en lot d'usuaris, grups i departaments per completar l'arquitectura del directori.

<img width="876" height="400" alt="45" src="https://github.com/user-attachments/assets/f0c920f0-bc68-4880-81e9-ac5bef6957d9" />


Consulta exhaustiva de tot el directori per verificar la consistència de les dades inserides.

<img width="1604" height="869" alt="46" src="https://github.com/user-attachments/assets/18d3643f-9c6c-488c-9f4c-a47440fe16ec" />


Filtratge selectiu per obtenir exclusivament comptes d'usuari de la classe posixAccount.

<img width="1546" height="829" alt="47" src="https://github.com/user-attachments/assets/3c38d903-e292-493c-8f76-c09a4f83637e" />


Extracció detallada de la fitxa d'un usuari específic utilitzant el filtre d'identificador d'usuari (uid=mgarcia).

<img width="876" height="301" alt="48" src="https://github.com/user-attachments/assets/ade62461-90d0-45df-9ff8-6dfcbf928172" />


Recerca i visualització de l'estat dels grups de treball de tipus posixGroup.

<img width="1379" height="775" alt="49" src="https://github.com/user-attachments/assets/e6690d7b-008f-4dda-b06d-4a42d02fdf62" />


Segmentació de la cerca per branques departamentals específiques com la unitat d'Informàtica.

<img width="1277" height="573" alt="50" src="https://github.com/user-attachments/assets/cf08cbee-c1ed-4a85-9f03-e1f6dccb7944" />


Localització de contactes basada en el format del correu electrònic institucional del domini @gina.cat.

<img width="1153" height="273" alt="51" src="https://github.com/user-attachments/assets/78fdac78-7265-41ff-9169-ab64c02d49c3" />


Creació de la branca de Recursos Humans (RRHH) definida com una unitat organitzativa en format LDIF.

<img width="662" height="182" alt="52" src="https://github.com/user-attachments/assets/0167fe58-4b5c-400b-a95c-a5ab6177b6de" />


Extensió del directori amb la incorporació efectiva de la nova Unitat Organitzativa de RRHH.

<img width="1053" height="67" alt="53" src="https://github.com/user-attachments/assets/02f7b5a0-afe8-4f60-81ac-75fd4364d738" />


Auditoria de la nova entrada per comprovar-ne la correcta inserció a l'arbre del directori.

<img width="866" height="138" alt="54" src="https://github.com/user-attachments/assets/47371af4-745d-4316-aa68-d558e00b6272" />


Preparació d'una ordre de modificació d'atributs per actualitzar el número de telèfon d'un registre existent.

<img width="630" height="104" alt="55" src="https://github.com/user-attachments/assets/22cb0618-c254-4fec-b24f-af6d96794586" />


Aplicació de canvis en calent sobre el registre de l'usuari pmarti mitjançant l'eina ldapmodify.

<img width="887" height="108" alt="56" src="https://github.com/user-attachments/assets/c4a453c6-d499-4b2c-b9d2-f21473902e30" />


Actualització de metadades addicionals per al perfil de l'usuari lsanchez.

<img width="882" height="117" alt="57" src="https://github.com/user-attachments/assets/2c25086a-ff8a-406c-ba84-3149b3d458cc" />


Verificació de l'atribució de descripcions personalitzades als usuaris després de les modificacions.

<img width="889" height="118" alt="58" src="https://github.com/user-attachments/assets/ce4c8ad7-aaca-44d0-8def-e6dadf167976" />


Comprovació de la integritat de les dades d'atributs específics com el telèfon després de les actualitzacions.

<img width="878" height="91" alt="59" src="https://github.com/user-attachments/assets/bb6ca07b-de5e-4715-9e25-bc91a998afba" />


Procediment d'eliminació de registres obsolets del directori utilitzant l'ordre ldapdelete.

<img width="888" height="405" alt="60" src="https://github.com/user-attachments/assets/0ae68946-a393-47cb-8afc-4faeacd3ab76" />


Prova d'esborrat de grups organitzatius i validació de la seva desaparició definitiva de l'arbre del directori.

<img width="881" height="259" alt="61" src="https://github.com/user-attachments/assets/d528e835-ab8f-40c7-a183-47bf2a80d869" />


Aquí tens la documentació detallada de la configuració del servidor de fitxers Samba a Ubuntu, ordenada del pas 1 al 10 en català, amb els enllaços corresponents i la separació de dos salts de línia:

Instal·lació del servei Samba mitjançant l'ordre apt install samba, descarregant tots els paquets i dependències necessaris per a la gestió de fitxers compartits en xarxa.

<img width="738" height="383" alt="SAMBA1" src="https://github.com/user-attachments/assets/2c127009-ccee-4b56-b7dd-cd20b5bd8838" />

Creació del directori de compartició anomenat "asixa" a l'arrel del sistema, assignació de permisos totals (777) i canvi del propietari al grup "nobody" per permetre l'accés correcte.

<img width="748" height="242" alt="SAMBA2" src="https://github.com/user-attachments/assets/845aff0b-951a-4ff0-b980-8dfa8608d984" />

Creació dels usuaris locals (edgar, naim, eros) amb el paràmetre -s /sbin/nologin per seguretat, creació del grup "madrid" i addició dels usuaris corresponents a aquest grup.

<img width="805" height="344" alt="SAMBA3" src="https://github.com/user-attachments/assets/9f560b9d-7ef9-48ce-943e-4de1286dedee" />

Configuració del recurs compartit al fitxer smb.conf, definint la ruta, els permisos d'escriptura, l'accés de convidats i les llistes d'usuaris permesos i invàlids (edgar).

<img width="668" height="257" alt="SAMBA4" src="https://github.com/user-attachments/assets/fc400df2-a577-494f-84f7-3ea397f2e4a8" />

Reinici dels serveis smbd i nmbd per aplicar els canvis, i verificació de l'estat dels dimonis per confirmar que el servidor Samba està actiu i funcionant correctament.

<img width="719" height="243" alt="SAMBA5 5" src="https://github.com/user-attachments/assets/7c0548b4-e5c5-4220-874f-4b27c88e6785" />

Instal·lació de l'eina smbclient al terminal per poder realitzar proves de connexió i llistar els recursos compartits disponibles des del propi client.

<img width="814" height="67" alt="SAMBA6" src="https://github.com/user-attachments/assets/2f4cd7f0-e1c0-4dfd-b9c2-b378075aac77" />

Connexió al recurs compartit des de l'explorador de fitxers d'Ubuntu mitjançant el protocol smb://10.0.2.15/asixa, localitzant el servidor anomenat "EDGARSERVER".

<img width="885" height="554" alt="SAMBA7" src="https://github.com/user-attachments/assets/c7a18cd7-945a-422f-a3b5-0b1c28d0f365" />

Accés satisfactori al directori "asixa", confirmant que la carpeta es troba inicialment buida i que el lligam amb el servidor s'ha establert de forma correcta.

<img width="890" height="547" alt="SAMBA8" src="https://github.com/user-attachments/assets/f56ffe79-4429-4305-9222-f093c83cee55" />

Prova d'escriptura al recurs compartit creant una nova carpeta anomenada "ANONIM" per verificar que els permisos de creació definits a la configuració funcionen.

<img width="885" height="545" alt="SAMBA9" src="https://github.com/user-attachments/assets/b910bdd2-360a-4bf4-ac8d-36591dffa1fb" />

Verificació final de l'estructura de fitxers al servidor Samba, mostrant la carpeta "ANONIM" creada des del client, el que valida tota la configuració del servei.

<img width="886" height="547" alt="SAMBA10" src="https://github.com/user-attachments/assets/eb856adc-7647-4bc7-b40d-93f467a640c5" />
Assignació de contrasenyes de Samba per als usuaris edgar, naim i eros mitjançant l'ordre smbpasswd -a, permetent així la seva autenticació des de clients externs.

<img width="888" height="551" alt="SAMBA11" src="https://github.com/user-attachments/assets/d27a753f-197d-4efb-8411-63d911a0b7d8" />

Inici de sessió al recurs compartit amb l'usuari "naim", introduint les credencials configurades prèviament per accedir als privilegis d'escriptura definits al fitxer smb.conf.

<img width="893" height="550" alt="SAMBA12" src="https://github.com/user-attachments/assets/b97d7333-7ee5-4929-a0f5-5fb694947093" />

Creació d'una nova carpeta anomenada "NAIM" dins del recurs compartit, acció permesa ja que l'usuari "naim" es troba a la write list de la configuració de Samba.

<img width="890" height="558" alt="SAMBA13" src="https://github.com/user-attachments/assets/3b30386b-78ec-43c4-b1e8-f18eec08810b" />

Canvi d'usuari al client per accedir com a "eros", qui forma part del grup "madrid" i té permisos de lectura al recurs, però no d'escriptura individual.

<img width="893" height="549" alt="SAMBA14" src="https://github.com/user-attachments/assets/07d9d7bd-003e-42be-8f30-612cf4628b23" />

Comprovació de la denegació de permisos: en intentar crear el directori "EROS", el sistema mostra un error ja que l'usuari no té privilegis d'escriptura, validant així la configuració de seguretat.

<img width="886" height="546" alt="SAMBA15" src="https://github.com/user-attachments/assets/58723c1b-3866-4923-bf5d-44fb5bafedfd" />
