Obre l'eina "Directivas de seguridad local" (escrivint secpol.msc al cercador). Navega cap a Directivas locales > Directiva de auditoría. Fes doble clic a "Auditar eventos de inicio de sesión" i marca les caselles de "Correcto" i "Erróneo".


Fes el mateix per a la política "Auditar el acceso a objetos".



<img width="796" height="569" alt="image" src="https://github.com/user-attachments/assets/8b71d984-c665-4a20-b63d-8e45dabac20d" />

Ho hem validat tancant i obrint sessió amb el nostre usuari administrador , comprovant posteriorment al Visor d'esdeveniments la generació exitosa de l'ID 4624 corresponent a un inici de sessió correcte.

<img width="931" height="910" alt="image" src="https://github.com/user-attachments/assets/936c154d-b100-44f3-8df9-1f10d0ab34af" />


Hem afegit una capa de traçabilitat sobre la carpeta Edgar configurant-ne les opcions avançades de seguretat per auditar les accions del compte . En interactuar amb el contingut del directori, el sistema ha generat l'esdeveniment 4663, confirmant que som capaços de monitorar qui accedeix als nostres fitxers de forma efectiva.  


<img width="799" height="636" alt="image" src="https://github.com/user-attachments/assets/834a5af6-afda-4b44-91ca-85f58a55c497" />



<img width="788" height="583" alt="image" src="https://github.com/user-attachments/assets/31f8f8cc-15c6-4d3a-a500-2bcb60628b9f" />


<img width="809" height="629" alt="image" src="https://github.com/user-attachments/assets/370e7d69-d47e-4ab6-a2c6-b1720ca7a481" />



<img width="929" height="928" alt="image" src="https://github.com/user-attachments/assets/8ff7bbba-0e00-445f-8efb-2c4912fbd158" />



Per mantenir un registre estricte de la càrrega de programari, s'ha habilitat la directiva de seguiment de processos. L'efectivitat d'aquesta mesura s'ha demostrat executant un navegador, la qual cosa ha registrat un esdeveniment 4688 d'arrencada. L'aturada forçada del mateix programa ha deixat el corresponent registre 4689 d'acabament de tasca al visor.  


<img width="779" height="562" alt="image" src="https://github.com/user-attachments/assets/cda6ffbf-25b9-4b42-bf78-5162862874b0" />



<img width="929" height="905" alt="image" src="https://github.com/user-attachments/assets/420795d7-dffa-44b7-8b3a-82c5c7964c72" />



<img width="906" height="920" alt="image" src="https://github.com/user-attachments/assets/831682e2-3015-408f-a0f8-11b6ef44f4ed" />




<img width="362" height="370" alt="image" src="https://github.com/user-attachments/assets/f0d787ea-c48a-45a4-ba10-03496ffa61a8" />



<img width="936" height="877" alt="image" src="https://github.com/user-attachments/assets/f76be395-2cc3-4a31-9d97-fcb616efab5a" />



La darrera validació ha consistit en activar l'auditoria d'administració de comptes per tenir coneixement sobre qualsevol modificació en els usuaris. Realitzant un cicle de vida complet d'un compte secundari (creació, deshabilitació i eliminació), hem constatat que Windows genera fidelment els identificadors d'esdeveniment 4720, 4725 i 4726 respectivament, garantint un registre complet d'aquestes operacions administratives.  


<img width="557" height="116" alt="image" src="https://github.com/user-attachments/assets/743acb94-e710-432f-aedf-e633608ff53d" />

Creacio
<img width="420" height="392" alt="image" src="https://github.com/user-attachments/assets/ab650d0e-89e3-4602-a92d-a723ebdfa239" />



<img width="925" height="920" alt="image" src="https://github.com/user-attachments/assets/def19044-d56e-4926-93c6-a1a47c2ca29a" />


Deshabilitada

<img width="446" height="520" alt="image" src="https://github.com/user-attachments/assets/cacebea6-cb94-4ad5-aeee-dcbe74bd4109" />



<img width="930" height="898" alt="image" src="https://github.com/user-attachments/assets/7f71e6e0-f8ec-4c45-a657-ea295edcc325" />



Eliminada


<img width="515" height="284" alt="image" src="https://github.com/user-attachments/assets/e13b9f05-b682-4d6c-a045-1d51fda9d990" />





<img width="930" height="925" alt="image" src="https://github.com/user-attachments/assets/afeff410-e05a-4a96-81df-6b2dc208fec0" />
