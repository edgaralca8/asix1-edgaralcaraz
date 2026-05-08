**Fase 1 - Preparació del sistema**

A l'inici d'aquest Sprint, hem preparat l'entorn afegint un nou disc virtual a la nostra màquina. Mitjançant la Gestió de discs, l'hem inicialitzat i dividit en dues particions independents: una anomenada "Dades" formatada en NTFS, i una altra anomenada "Portable" sota el sistema de fitxers FAT32. L'assignació correcta de lletres s'ha verificat posteriorment amb l'eina de consola diskpart.


<img width="1028" height="609" alt="image" src="https://github.com/user-attachments/assets/60259873-3d02-45f6-b9ef-d96f9aca48df" />



<img width="753" height="606" alt="image" src="https://github.com/user-attachments/assets/2049587f-d585-4a39-98f8-ed47027ffcca" />


<img width="750" height="605" alt="image" src="https://github.com/user-attachments/assets/d470b9bb-8d3e-43b3-82e6-50e73fcaa627" />


<img width="501" height="394" alt="image" src="https://github.com/user-attachments/assets/54b3178e-a406-4be4-af86-01c98b1bf3b7" />



<img width="493" height="392" alt="image" src="https://github.com/user-attachments/assets/ba5975f0-1750-40f3-85de-7a810e21a209" />

<img width="493" height="392" alt="image" src="https://github.com/user-attachments/assets/babc94f1-917e-4880-81b2-a9d7a9462e61" />


<img width="494" height="392" alt="image" src="https://github.com/user-attachments/assets/b90e8687-1293-45a1-82c0-41858141e32e" />


<img width="775" height="624" alt="image" src="https://github.com/user-attachments/assets/39925f71-3681-4090-b5fc-985c7e5e763b" />


<img width="828" height="496" alt="image" src="https://github.com/user-attachments/assets/82b1cc36-22ec-4cc3-bdff-4378bfba3508" />



**Fase 2 - Quotes i usuaris**



Per establir un control d'emmagatzematge, hem activat les quotes de disc sobre la partició "Dades" (NTFS), marcant un límit rígid de 300 MB per a cada usuari i configurant-ne els advertiments. Hem creat els comptes locals edgar1 i edgar2 integrant-los al nou grup Limitats , i hem validat el funcionament de la quota superant el límit intencionadament per fer saltar el bloqueig de còpia del sistema.


<img width="921" height="732" alt="image" src="https://github.com/user-attachments/assets/6a7e2da3-c446-4158-9841-eb3ea20ebb9b" />



<img width="469" height="512" alt="image" src="https://github.com/user-attachments/assets/ce879428-8e99-4ffb-9374-dedeed13154d" />


<img width="924" height="785" alt="image" src="https://github.com/user-attachments/assets/8572204b-c3a0-4a1f-a999-70fced8c3bdd" />


<img width="557" height="556" alt="image" src="https://github.com/user-attachments/assets/6510a4c3-a039-4a81-a6de-81b0a39927f0" />



<img width="492" height="435" alt="image" src="https://github.com/user-attachments/assets/681a8351-0f62-42fa-8c09-d3ff4e7b4758" />


<img width="915" height="732" alt="image" src="https://github.com/user-attachments/assets/dc2a974e-3c59-40a0-aa07-d6e8461ceca8" />


<img width="428" height="391" alt="image" src="https://github.com/user-attachments/assets/8af4f79d-4e18-4d90-b4d4-2b93a42ecb00" />


<img width="451" height="472" alt="image" src="https://github.com/user-attachments/assets/e83f31cd-aad8-44b4-8839-8154acb96a7c" />



<img width="832" height="673" alt="image" src="https://github.com/user-attachments/assets/8db7a874-7cb2-4f04-933f-3492b3b76c7e" />


<img width="589" height="364" alt="image" src="https://github.com/user-attachments/assets/e718009e-7ceb-42e1-b6ca-b9e0d28baf54" />



Fase 3 i 4 - Script de còpia i automatització

Després d'incorporar i formatar en NTFS un tercer disc exclusiu per a Backups , s'ha dissenyat un script en format .bat encarregat de bolcar la carpeta de l'usuari cap a aquest disc. Aquest fitxer s'ha enllaçat a les Directives de Grup (gpedit.msc) perquè s'executi durant l'inici de sessió dels alumnes. Iniciant sessió amb l'usuari edgar1, hem verificat empíricament l'èxit del procés automatitzat de còpia.


<img width="638" height="404" alt="image" src="https://github.com/user-attachments/assets/ca9a2be1-f927-46e6-b45a-96096d29a7b4" />


<img width="758" height="142" alt="image" src="https://github.com/user-attachments/assets/a6bc9296-a81e-4b72-9730-0fafe9351b72" />


<img width="1012" height="746" alt="image" src="https://github.com/user-attachments/assets/40ee4ce5-c5b0-4c14-a801-4d60419319d6" />


<img width="758" height="524" alt="image" src="https://github.com/user-attachments/assets/1a5bc6b6-5af4-44c0-a2f6-fbc1b9507601" />


<img width="873" height="595" alt="image" src="https://github.com/user-attachments/assets/bc8f2a87-d08b-4770-93ef-df9d12eaff06" />


<img width="646" height="176" alt="image" src="https://github.com/user-attachments/assets/fbc8ab94-bd13-4db7-a940-1f8619bbc010" />


<img width="421" height="466" alt="image" src="https://github.com/user-attachments/assets/369748f0-d605-4b5a-a53d-727ca21cec66" />


<img width="962" height="765" alt="image" src="https://github.com/user-attachments/assets/7b84f833-2d6d-4d61-bcc1-6c4d41e36d04" />


<img width="1017" height="832" alt="image" src="https://github.com/user-attachments/assets/090dc53e-f6bf-468e-ba36-3c45febba730" />


**Fase 5 - Gestió de processos i serveis**
