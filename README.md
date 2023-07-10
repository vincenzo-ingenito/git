**ERROR HANDLING**
 
<table>
  <tr>
   <td>Versione
   </td>
   <td>:
   </td>
   <td>ver 1.0
   </td>
  </tr>
</table>




**INDICE**

- [1. Introduzione](#1-introduzione)
- [2.0. Gateway](#20-gateway)
  - [2.1. Errori assistenza](#21-errori-assistenza)
  - [2.2. Errori utente](#22-errori-utente)
- [3.0. Accreditamento](#30-accreditamento)
  - [3.1. Errori assistenza](#31-errori-assistenza)
  - [3.2. Errori utente](#32-errori-utente)
  - [Notes](#notes) 


# 1. Introduzione
Tale documento vuole fornire un manuale sia per permettere all'assistenza di risolvere bug nel modo più veloce possibile, sia per dare supporto ad un utente in difficoltà
 

# <span style="color: red;">2.0. Gateway</span>
Collezione errori che riguardano la saga Gateway

## 2.1. Errori assistenza
<table>
  <tr>
   <td>CATEGORIA</td>
   <td>ID</td>
   <td colspan="2" >DESCRIZIONE ERRORE </td>
  </tr> 
  <tr>
   <td rowspan="13" >VALIDAZIONE</td>
   <td><a href="#schema-not-found">ERRORE SCHEMA NOT FOUND</td>
   <td>Schema with version %s not found on database.</td>
  </tr>
  <tr>
   <td><a href="#schematron-not-found">ERRORE SCHEMATRON NOT FOUND</td>
   <td>Schematron with template id root %s not found on database.</td>
  </tr> 
</table>
 
 _Tabella 1: Categoria,Id, Descrizione Errore_

## 2.2. Errori utente

<table>
  <tr>
   <td>CATEGORIA</td>
   <td>ID</td>
   <td colspan="2" >DESCRIZIONE ERRORE </td>
  </tr> 
  <tr>
   <td rowspan="2" >PUBBLICAZIONE</td>
   <td><a href="#sign-not-found">ERRORE SIGN NOT FOUND</td>
   <td>Il pdf non risulta firmato.</td>
  </tr> 
  <tr> 
   <td><a href="#sign-not-valid">ERRORE SIGN NOT VALID</td>
   <td>La firma del pdf non risulta valida.</td>
  </tr> 
</table>
 
 _Tabella 2: Categoria,Id, Descrizione Errore_


# <span style="color: red;">3.0. Accreditamento</span>
Collezione errori che riguardano il processo di accreditamento

## 3.1. Errori assistenza
<table>
  <tr>
   <td>CATEGORIA</td>
   <td>ID</td>
   <td colspan="2" >DESCRIZIONE ERRORE </td>
  </tr> 
  <tr>
   <td rowspan="1" >TEST</td>
   <td><a href="#test">TEST</td>
   <td>TEST</td>
  </tr>
</table>
 
 _Tabella 3: Categoria,Id, Descrizione Errore_

## 3.2. Errori utente

<table>
  <tr>
   <td>CATEGORIA</td>
   <td>ID</td>
   <td colspan="2" >DESCRIZIONE ERRORE </td>
  </tr> 
  <tr>
   <td rowspan="1" >TEST</td>
   <td><a href="#test1"></td>
   <td>TEST</td>
  </tr>  
</table>
 
 _Tabella 4: Categoria,Id, Descrizione Errore_
    
  
<!-- Footnotes themselves at the bottom. -->
## Notes

[^1]: https://docs.italia.it/media/pdf/lg-modellointeroperabilita-docs/vintra-work/lg-modellointeroperabilita-docs.pdf

[^2]: Par 2.5.1 delle Linee Guida Modello di Interoperabilità 

[^2]: Par. 3.2.1 del documento rif [2]

[^3]: Par. 2.3.2 delle Linee Guida Modello di Interoperabilità

[^5]: Par. 2.5.2 delle Linee Guida Modello di Interoperabilità
 

## SCHEMA NOT FOUND
Assicurarsi che il campo type id del cda sia corretto nel rispetto della versione dello schema del gtw. Qualora invece la collection schema risulti essere vuota è necessario procedere al caricamente dell'item:

Recarsi quindi al seguente url <basePath>/openapi/swagger-ui/index.html, identificare l'api POST /v1/schema e compilare i campi nel seguente modo:

|CAMPO|DESCRIZIONE|VALORE ESEMPIO|
|-----|-----------|--------------|
|root|Nome del file principale dello schema da caricare|CDA.xsd|
|extension|Extension dello schema da caricare|POCD_MT000040UV02|
|files|Tutti i file che compongono lo schema. E' necessario che nei file vi sia anche il root file segnato nel campo root|CDA.xsd,datatypes-base.xsd etc|



## SCHEMATRON NOT FOUND
Assicurarsi che il campo templateId del cda sia corretto nel rispetto del tipo documento da validare.
Assicurarsi inoltre che la collection schematron abbia lo schematron corrispondente, in caso procedere al caricamento dell'item:

Recarsi quindi al seguente url <basePath>/openapi/swagger-ui/index.html, identificare l'api POST /v1/schematron?<system> e compilare i campi nel seguente modo:

|CAMPO|DESCRIZIONE|VALORE ESEMPIO|
|-----|-----------|--------------|
|system|Indica per chi è destinato lo schematron| NONE o TS
|templateIdRoot|E' il template id root del tipo documento da validare|2.16.840.1.113883.2.9.10.1.1|
|version|Version dello schematron|1.0|
|file|Content dello schematron|Lab_1.0.sch|

## SIGN NOT FOUND
Il pdf fornito in input all'ep di creazione non risulta firmato. Il GTW impone che i file che arrivino in pubblicazione siano firmati mentre in validazione no.

## SIGN NOT VALID
Il pdf fornito in input all'ep di creazione risulta firmato, ma la sua firma non risulta essere valida.
