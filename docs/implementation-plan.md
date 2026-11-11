
DailyHub - Plan de implementare

DESCRIERE GENERALĂ

Acest document prezintă tehnologiile alese pentru dezvoltarea aplicației DailyHub, motivele alegerii acestora, strategia de versionare, etapele de implementare și distribuirea responsabilităților în echipă.

Proiectul este realizat de o echipă formată din doi membri, care vor contribui atât la dezvoltarea frontend-ului, cât și a backend-ului.

1. TEHNOLOGII UTILIZATE ȘI JUSTIFICAREA ALEGERII

Frontend

HTML5
Utilizat pentru definirea structurii paginilor aplicației.

CSS3
Utilizat pentru stilizarea interfeței și adaptarea acesteia la diferite dimensiuni ale ecranului.

JavaScript
Utilizat pentru interactivitatea paginilor, validarea formularelor și comunicarea cu backend-ul.

Aceste tehnologii au fost alese deoarece permit realizarea unei aplicații web fără utilizarea unui framework frontend suplimentar.

Backend

Node.js
Utilizat pentru executarea codului JavaScript pe server.

Express.js
Utilizat pentru implementarea serverului web, definirea endpoint-urilor REST și procesarea cererilor HTTP.

Alegerea permite utilizarea limbajului JavaScript atât pe frontend, cât și pe backend.

Baza de date

PostgreSQL
Utilizat pentru stocarea utilizatorilor, sarcinilor, evenimentelor, Workspace-urilor și datelor colaborative.

PostgreSQL a fost ales deoarece este un sistem relațional care oferă suport pentru chei primare, chei externe, constrângeri și tranzacții.

Versionare și colaborare

Git
Utilizat pentru urmărirea modificărilor și gestionarea versiunilor proiectului.

GitHub
Utilizat pentru găzduirea repository-ului, colaborarea între membrii echipei și verificarea modificărilor prin Pull Requests.

2. STRATEGIA DE VERSIONARE

Codul sursă și documentația vor fi păstrate într-un repository GitHub comun.

Branch-ul main va conține versiunea principală a proiectului.

Pentru dezvoltarea funcționalităților și modificarea documentației vor fi create branch-uri separate.

Fiecare membru va realiza modificările pe propriul branch și va salva progresul prin commit-uri cu mesaje descriptive.

După finalizarea unei funcționalități, modificările vor fi propuse pentru integrare în main printr-un Pull Request.

Înainte de integrare, modificările vor fi verificate pentru a reduce riscul introducerii erorilor.

Exemple de branch-uri:

docs-initial-setup
feature-authentication
feature-personal-tasks
feature-calendar
feature-workspaces
feature-collaboration

3. PLANUL DE IMPLEMENTARE

Etapa 1 - Configurarea proiectului

Crearea structurii frontend și backend.
Configurarea proiectului Node.js și Express.
Configurarea conexiunii la PostgreSQL.
Stabilirea structurii folderelor și a convențiilor de dezvoltare.

Etapa 2 - Autentificare și utilizatori

Implementarea înregistrării utilizatorilor.
Implementarea autentificării și deconectării.
Protejarea endpoint-urilor care necesită autentificare.

Etapa 3 - Funcționalități personale

Implementarea dashboard-ului.
Implementarea gestionării sarcinilor personale.
Implementarea calendarului personal și a evenimentelor.

Etapa 4 - Workspace-uri

Implementarea creării și afișării Workspace-urilor.
Implementarea invitațiilor între utilizatori înregistrați.
Implementarea acceptării și refuzării invitațiilor.
Implementarea gestionării membrilor și rolurilor.

Etapa 5 - Funcționalități colaborative

Implementarea sarcinilor comune.
Implementarea notițelor partajate.
Implementarea listelor colaborative.

Etapa 6 - Integrare și testare

Conectarea interfeței frontend la endpoint-urile backend.
Verificarea operațiilor asupra bazei de date.
Testarea autentificării și a drepturilor de acces.
Testarea scenariilor de utilizare documentate.
Corectarea erorilor identificate.

4. ÎMPĂRȚIREA RESPONSABILITĂȚILOR

Echipa este formată din doi membri.

Ambii membri vor contribui la frontend și backend, prin împărțirea funcționalităților în module.

Membrul 1

Responsabilități principale:

- Implementarea autentificării și gestionării conturilor.
- Implementarea sarcinilor personale.
- Implementarea calendarului personal.
- Dezvoltarea interfețelor pentru modulele atribuite.
- Implementarea endpoint-urilor backend aferente.
- Testarea funcționalităților implementate.

Membrul 2

Responsabilități principale:

- Implementarea creării și gestionării Workspace-urilor.
- Implementarea invitațiilor și a rolurilor membrilor.
- Implementarea sarcinilor colaborative.
- Implementarea notițelor și listelor comune.
- Dezvoltarea interfețelor pentru modulele atribuite.
- Implementarea endpoint-urilor backend aferente.
- Testarea funcționalităților implementate.

Responsabilități comune

- Proiectarea și actualizarea documentației.
- Stabilirea structurii bazei de date.
- Integrarea modulelor frontend și backend.
- Revizuirea Pull Request-urilor.
- Testarea finală a aplicației.
- Pregătirea prezentării proiectului.

Distribuirea responsabilităților poate fi ajustată de comun acord în timpul dezvoltării.

5. REZULTATUL AȘTEPTAT

La finalul implementării, aplicația DailyHub va permite utilizatorilor să își organizeze activitățile personale și să colaboreze în Workspace-uri.

Funcționalitățile principale vor include autentificarea, gestionarea sarcinilor și evenimentelor personale, crearea Workspace-urilor, invitațiile și administrarea sarcinilor, notițelor și listelor comune.

Aplicația va utiliza o arhitectură frontend-backend-bază de date și va fi dezvoltată colaborativ prin GitHub.

