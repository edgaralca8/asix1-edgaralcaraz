

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


<img width="1019" height="842" alt="image" src="https://github.com/user-attachments/assets/1e00a120-45d6-452c-bbee-9261396c24e4" />

<img width="470" height="231" alt="image" src="https://github.com/user-attachments/assets/1e548e06-bb9d-4916-bb11-e3cd9201520c" />



Fase 3 - Llicències de Windows


Per comprovar l'estat legal del nostre sistema operatiu, hem accedit a l'apartat Configuració i posteriorment a Sistema i Activació. Aquesta pantalla ens indica si la nostra còpia de Windows es troba actualment activada o no.


<img width="1023" height="787" alt="image" src="https://github.com/user-attachments/assets/08676ddb-9739-435f-90ad-5f0a21c14334" />

Hem executat la comanda slmgr /xpr a través del cmd per esbrinar el tipus de llicenciament de l'equip, el qual hem detallat a l'informe. A més, consultant botigues oficials, hem determinat el preu aproximat d'una llicència original.  

<img width="851" height="525" alt="image" src="https://github.com/user-attachments/assets/0d14bda0-db37-4158-a3a6-801df6117023" />

