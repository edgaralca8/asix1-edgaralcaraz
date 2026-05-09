Per implementar el nostre sistema RAID 5, hem afegit tres discos físics independents de la mateixa capacitat a la màquina virtual, ja que aquest és el nombre mínim requerit per a aquesta arquitectura. Un cop dins del sistema operatiu, mitjançant el Gestor de discos, els hem inicialitzat sense aplicar-los cap format de partició previ


<img width="1056" height="611" alt="image" src="https://github.com/user-attachments/assets/ba87a209-a4f9-42f0-a919-19d299389895" />



<img width="921" height="842" alt="image" src="https://github.com/user-attachments/assets/41470a7e-34a1-49eb-a8d0-f3533593e9aa" />


A través de les eines d'administració de programari del sistema, hem vinculat els tres discos en un únic volum RAID 5 lògic. Aquesta configuració distribueix les dades i la informació de paritat entre totes les unitats. Hem assignat la lletra R:, l'hem formatat en NTFS amb l'etiqueta "RAID5-Test" i n'hem verificat la seva correcta sincronització i estabilitat.

<img width="926" height="380" alt="image" src="https://github.com/user-attachments/assets/d080a3a7-f528-496f-a895-736b86ab326b" />



<img width="503" height="404" alt="image" src="https://github.com/user-attachments/assets/143613aa-3b48-4fe0-8b09-d76f323c77fb" />


<img width="500" height="407" alt="image" src="https://github.com/user-attachments/assets/00d3e884-238b-4d51-80e0-5460e07907a3" />


<img width="503" height="413" alt="image" src="https://github.com/user-attachments/assets/82706458-8df9-4362-a536-92649ebcba56" />


<img width="924" height="344" alt="image" src="https://github.com/user-attachments/assets/fc0af635-f038-4c58-b28c-cf988f5a0444" />

**Proves de funcionalitat i tolerància a fallades**


Després d'emmagatzemar fitxers de prova al volum, hem simulat la fallada d'un disc físic desconnectant-lo manualment (Offline). Hem pogut constatar que el sistema RAID 5 tolera aquesta pèrdua gràcies a la paritat: l'estat passa a ser "Degradat", però el sistema continua funcionant i les dades segueixen sent completament accessibles.  

<img width="913" height="596" alt="image" src="https://github.com/user-attachments/assets/8650d6f0-468c-484d-978f-e28408103c80" />



<img width="854" height="806" alt="image" src="https://github.com/user-attachments/assets/6da39d4d-438b-4e66-a5c1-8d16d7173783" />



<img width="808" height="114" alt="image" src="https://github.com/user-attachments/assets/1b311da2-a3c3-4513-bc18-2fad6e70b344" />


<img width="898" height="643" alt="image" src="https://github.com/user-attachments/assets/050fe328-e509-4c12-851f-99e08560bda3" />


**Límit de tolerància i pèrdua de dades**


Hem forçat la simulació d'una segona fallada consecutiva desconnectant un altre disc. Com que l'arquitectura RAID 5 només està dissenyada per tolerar la pèrdua d'un únic disc físic simultàniament, el volum ha col·lapsat de manera crítica, resultant en la pèrdua d'accés i bloquejant completament qualsevol lectura de les nostres dades. Inclus, el disc que ens hauria de sortir, "R", directament ja deixa de sortir

<img width="908" height="812" alt="image" src="https://github.com/user-attachments/assets/aa8c08a2-cdba-4bc8-95b6-02483f31d3e8" />


<img width="918" height="421" alt="image" src="https://github.com/user-attachments/assets/f03865cd-2470-4dd4-9393-c8141fcd1dab" />



<img width="1633" height="905" alt="image" src="https://github.com/user-attachments/assets/f27bd2b2-0d78-4433-8057-41b753623ef8" />



**Recuperació del sistema**

Finalment, hem procedit a la recuperació del volum tornant a posar en línia la unitat fallida. El sistema operatiu ha detectat el retorn del disc i ha iniciat automàticament el procés de reconstrucció (Resynching) basat en la informació de paritat. Un cop recuperat l'estat degradat/operatiu, hem comprovat que la integritat dels fitxers inicials s'ha mantingut inalterada.


<img width="1633" height="897" alt="image" src="https://github.com/user-attachments/assets/207204b3-e510-49af-bbfd-be0ba5d7f168" />



<img width="1658" height="925" alt="image" src="https://github.com/user-attachments/assets/a9e09709-53ed-493b-9e4b-b032eacbbb9e" />


