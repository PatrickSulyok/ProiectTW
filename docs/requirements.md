
DailyHub - Cerințele aplicației
DESCRIERE GENERALĂ

DailyHub este o aplicație web pentru organizarea activităților cotidiene, individuale și colaborative. Aplicația propune gestionarea sarcinilor, evenimentelor și rezervărilor personale, listelor comune, notițelor, bugetelor și documentelor.

Fiecare utilizator are un spațiu personal (My Space) și poate crea sau participa la spații de lucru comune (Workspace-uri). Accesul la un Workspace se obține printr-o invitație acceptată de utilizator. Datele personale rămân separate de datele partajate.

UTILIZATORI ȘI ROLURI

Utilizator: persoană care deține un cont și își gestionează activitățile personale.

Administrator Workspace: utilizatorul care creează spațiul comun, invită membri și gestionează apartenența la grup.

Membru Workspace: utilizatorul care a acceptat invitația și poate contribui la conținutul comun, fără a administra membrii.

CERINȚE FUNCȚIONALE

Conturi și spațiu personal

Cerința 1 - Utilizatorul poate crea un cont folosind o adresă de email și o parolă.
Prioritate: Esențială (MVP)

Cerința 2 - Utilizatorul se poate autentifica și deconecta.
Prioritate: Esențială (MVP)

Cerința 3 - Utilizatorul poate vizualiza într-un Dashboard un rezumat al activităților sale.
Prioritate: Esențială (MVP)

Sarcini și calendar personal

Cerința 4 - Utilizatorul poate crea, vizualiza, modifica și șterge sarcini personale.
Prioritate: Esențială (MVP)

Cerința 5 - Utilizatorul poate stabili termene-limită și priorități pentru sarcini și le poate marca drept finalizate.
Prioritate: Esențială (MVP)

Cerința 6 - Utilizatorul poate crea, vizualiza, modifica și șterge evenimente și rezervări personale în calendar, cu dată și oră.
Prioritate: Esențială (MVP)

Workspace-uri și invitații

Cerința 7 - Utilizatorul poate crea un Workspace și îi poate modifica numele și descrierea.
Prioritate: Esențială (MVP)

Cerința 8 - Administratorul poate invita prin adresa de email utilizatori care au deja cont DailyHub.
Prioritate: Esențială (MVP)

Cerința 9 - Utilizatorul invitat poate vedea invitația în aplicație și o poate accepta sau refuza.
Prioritate: Esențială (MVP)

Cerința 10 - Administratorul poate elimina membri, iar un membru poate părăsi un Workspace.
Prioritate: Esențială (MVP)

Notițe, sarcini și liste comune

Cerința 11 - Membrii pot crea, vizualiza, modifica și șterge notițe comune în Workspace. Modificările se salvează și devin vizibile la redeschiderea sau reîncărcarea notiței; nu se solicită editare simultană în timp real.
Prioritate: Esențială (MVP)

Cerința 12 - Membrii pot crea, modifica și șterge sarcini comune și le pot atribui unui membru al Workspace-ului.
Prioritate: Esențială (MVP)

Cerința 13 - Membrii pot crea liste colaborative, adăuga sau elimina elemente și marca elementele drept finalizate.
Prioritate: Esențială (MVP)

Extinderi planificate

Cerința 14 - Membrii pot adăuga evenimente într-un calendar comun și pot partaja un orar introdus manual, inclusiv activități săptămânale recurente.
Prioritate: Importantă (Etapa 2)

Cerința 15 - Utilizatorul poate înregistra venituri și cheltuieli, le poate organiza pe categorii și poate consulta soldul personal.
Prioritate: Importantă (Etapa 2)

Cerința 16 - Utilizatorul poate încărca, organiza și descărca documente personale sau partajate într-un Workspace, în funcție de permisiuni.
Prioritate: Opțională (Etapa 3)

Cerința 17 - Membrii pot organiza activități de grup extinse, precum planificarea în familie sau distribuirea responsabilităților recurente.
Prioritate: Opțională (Etapa 3)

CERINȚE NEFUNCȚIONALE

Cerința 1 - Interfața trebuie să fie clară și ușor de utilizat, cu navigare consecventă între module.
Prioritate: Esențială

Cerința 2 - Interfața trebuie să se adapteze la ecrane de calculator, tabletă și telefon.
Prioritate: Esențială

Cerința 3 - Parolele trebuie stocate sub formă de hash securizat, nu în text simplu.
Prioritate: Esențială

Cerința 4 - Backend-ul trebuie să verifice autentificarea și drepturile de acces la fiecare operație asupra datelor private sau partajate.
Prioritate: Esențială

Cerința 5 - Datele primite de la utilizatori trebuie validate pe server, iar erorile trebuie comunicate clar.
Prioritate: Esențială

Cerința 6 - Informațiile salvate trebuie să persiste în baza de date și să fie disponibile la autentificări ulterioare.
Prioritate: Esențială

Cerința 7 - Modificarea unei notițe comune nu trebuie să suprascrie fără avertizare o versiune mai nouă salvată între timp de alt membru.
Prioritate: Importantă

Cerința 8 - Operațiile uzuale, precum afișarea sarcinilor sau salvarea unei notițe, ar trebui să răspundă în cel mult 3 secunde în condiții normale de testare.
Prioritate: Importantă

Cerința 9 - Aplicația trebuie să funcționeze în versiunile moderne ale browserelor Chrome, Firefox, Safari și Edge.
Prioritate: Importantă

Cerința 10 - Codul trebuie organizat în module separate, pentru a permite dezvoltarea și testarea independentă a funcționalităților.
Prioritate: Importantă

Cerința 11 - Modificările proiectului trebuie urmărite prin Git și GitHub, folosind branch-uri și Pull Requests.
Prioritate: Importantă

Cerința 12 - Arhitectura trebuie să permită adăugarea ulterioară de module fără rescrierea completă a aplicației.
Prioritate: Importantă

PRIORITIZAREA IMPLEMENTĂRII

Esențială (MVP): funcționalitățile necesare primei versiuni utilizabile, incluzând conturile, sarcinile, calendarul personal și colaborarea de bază în Workspace-uri.

Importantă (Etapa 2): calendarul comun, partajarea orarului și bugetele personale.

Opțională (Etapa 3): gestionarea documentelor și planificarea avansată a activităților în grup.

Etapele sunt propuneri de implementare și pot fi ajustate în funcție de timpul disponibil și de cerințele ulterioare ale profesorului.

TEHNOLOGII PROPUSE

Frontend: HTML, CSS și JavaScript simplu.
Backend: Node.js și Express.
Bază de date: PostgreSQL.
Versionare și colaborare: Git și GitHub.

Aceste tehnologii vor fi detaliate și justificate în documentele de arhitectură și de planificare a implementării.
