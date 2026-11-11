
DailyHub - Modelul de date și serviciile API

DESCRIERE GENERALĂ

Acest document prezintă modelul preliminar de date al aplicației DailyHub, relațiile dintre entități și principalele endpoint-uri API necesare implementării funcționalităților.

Aplicația va utiliza PostgreSQL pentru stocarea persistentă a datelor și un backend Node.js cu Express pentru accesarea și modificarea acestora.

Modelul este proiectat pentru funcționalitățile esențiale ale aplicației, cu posibilitatea extinderii ulterioare.

ENTITĂȚILE PRINCIPALE

1) USERS - Utilizatori

Stochează informațiile conturilor DailyHub.

Câmpuri principale:

id - BIGINT, cheie primară.
name - VARCHAR(100), obligatoriu.
email - VARCHAR(255), obligatoriu, unic.
password_hash - VARCHAR(255), obligatoriu.
created_at - TIMESTAMP, data creării contului.

Fiecare utilizator poate avea sarcini personale, evenimente, Workspace-uri și invitații.

2) TASKS - Sarcini

Stochează sarcinile personale și colaborative.

Câmpuri principale:

id - BIGINT, cheie primară.
title - VARCHAR(200), obligatoriu.
description - TEXT, opțional.
priority - VARCHAR(20), prioritatea sarcinii.
status - VARCHAR(20), starea sarcinii.
due_date - TIMESTAMP, termen-limită opțional.
owner_id - BIGINT, cheie externă către USERS, opțional.
workspace_id - BIGINT, cheie externă către WORKSPACES, opțional.
assigned_to - BIGINT, cheie externă către USERS, opțional.
created_at - TIMESTAMP, data creării.

O sarcină personală aparține unui utilizator și nu este asociată unui Workspace.

O sarcină colaborativă aparține unui Workspace și poate fi atribuită unui membru al acestuia.

Pentru fiecare sarcină, exact unul dintre câmpurile owner_id și workspace_id trebuie să fie completat.

3) EVENTS - Evenimente personale

Stochează evenimentele și rezervările din calendarul personal.

Câmpuri principale:

id - BIGINT, cheie primară.
user_id - BIGINT, cheie externă către USERS.
title - VARCHAR(200), obligatoriu.
description - TEXT, opțional.
start_time - TIMESTAMP, data și ora începerii.
end_time - TIMESTAMP, data și ora încheierii.
event_type - VARCHAR(30), tipul evenimentului.
created_at - TIMESTAMP, data creării.

Fiecare eveniment aparține unui singur utilizator.

Calendarul comun va fi adăugat într-o etapă ulterioară.

4) WORKSPACES - Spații de lucru

Stochează informațiile spațiilor de lucru colaborative.

Câmpuri principale:

id - BIGINT, cheie primară.
name - VARCHAR(150), obligatoriu.
description - TEXT, opțional.
created_by - BIGINT, cheie externă către USERS.
created_at - TIMESTAMP, data creării.

Fiecare Workspace este creat de un utilizator, care primește inițial rolul de administrator.

5) WORKSPACE_MEMBERS - Membrii Workspace-urilor

Stochează apartenența utilizatorilor la Workspace-uri și rolurile acestora.

Câmpuri principale:

id - BIGINT, cheie primară.
workspace_id - BIGINT, cheie externă către WORKSPACES.
user_id - BIGINT, cheie externă către USERS.
role - VARCHAR(20), administrator sau membru.
joined_at - TIMESTAMP, data aderării.

Perechea workspace_id și user_id trebuie să fie unică.

Un utilizator poate aparține mai multor Workspace-uri, iar un Workspace poate avea mai mulți membri.

6) INVITATIONS - Invitații

Stochează invitațiile de aderare la Workspace-uri.

Câmpuri principale:

id - BIGINT, cheie primară.
workspace_id - BIGINT, cheie externă către WORKSPACES.
invited_user_id - BIGINT, cheie externă către USERS.
invited_by - BIGINT, cheie externă către USERS.
status - VARCHAR(20), pending, accepted sau rejected.
created_at - TIMESTAMP, data trimiterii.
responded_at - TIMESTAMP, data răspunsului, opțional.

Invitațiile pot fi trimise doar către utilizatori care au deja cont DailyHub.

Un utilizator nu poate avea simultan mai multe invitații în așteptare pentru același Workspace.

Acceptarea unei invitații determină adăugarea utilizatorului în WORKSPACE_MEMBERS.

7) NOTES - Notițe comune

Stochează notițele partajate într-un Workspace.

Câmpuri principale:

id - BIGINT, cheie primară.
workspace_id - BIGINT, cheie externă către WORKSPACES.
created_by - BIGINT, cheie externă către USERS.
title - VARCHAR(200), obligatoriu.
content - TEXT, conținutul notiței.
version - INTEGER, versiunea curentă a notiței.
created_at - TIMESTAMP, data creării.
updated_at - TIMESTAMP, data ultimei modificări.

Toți membrii Workspace-ului pot consulta și modifica notițele.

Câmpul version permite detectarea modificărilor concurente, pentru a evita suprascrierea fără avertizare a unei versiuni mai noi.

Editarea simultană în timp real nu este inclusă în MVP.

8) COLLABORATIVE_LISTS - Liste colaborative

Stochează listele comune din Workspace-uri.

Câmpuri principale:

id - BIGINT, cheie primară.
workspace_id - BIGINT, cheie externă către WORKSPACES.
created_by - BIGINT, cheie externă către USERS.
title - VARCHAR(200), obligatoriu.
created_at - TIMESTAMP, data creării.

Fiecare listă aparține unui Workspace.

9) LIST_ITEMS - Elemente ale listelor

Stochează elementele unei liste colaborative.

Câmpuri principale:

id - BIGINT, cheie primară.
list_id - BIGINT, cheie externă către COLLABORATIVE_LISTS.
content - VARCHAR(300), obligatoriu.
is_completed - BOOLEAN, implicit false.
created_at - TIMESTAMP, data creării.

Fiecare element aparține unei singure liste.

RELAȚIILE DINTRE ENTITĂȚI

USERS - TASKS
Relație 1:N pentru sarcinile personale.

USERS - EVENTS
Relație 1:N. Un utilizator poate avea mai multe evenimente.

USERS - WORKSPACES
Relație 1:N pentru crearea Workspace-urilor.

USERS - WORKSPACE_MEMBERS
Relație 1:N. Un utilizator poate avea mai multe înregistrări de apartenență.

WORKSPACES - WORKSPACE_MEMBERS
Relație 1:N. Un Workspace poate avea mai mulți membri.

USERS - WORKSPACES
Relație N:M pentru apartenență, implementată prin WORKSPACE_MEMBERS.

WORKSPACES - INVITATIONS
Relație 1:N. Un Workspace poate avea mai multe invitații.

USERS - INVITATIONS
Relații 1:N pentru utilizatorii invitați și pentru expeditorii invitațiilor.

WORKSPACES - TASKS
Relație 1:N pentru sarcinile colaborative.

USERS - TASKS
Relație 1:N pentru atribuirea sarcinilor colaborative.

WORKSPACES - NOTES
Relație 1:N. Un Workspace poate avea mai multe notițe.

WORKSPACES - COLLABORATIVE_LISTS
Relație 1:N. Un Workspace poate conține mai multe liste.

COLLABORATIVE_LISTS - LIST_ITEMS
Relație 1:N. O listă poate avea mai multe elemente.

DIAGRAMA ENTITATE-RELAȚIE

Diagrama ERD va prezenta entitățile principale, cheile primare, cheile externe și relațiile dintre acestea.

Diagrama va fi realizată separat și integrată în acest document.

REGULI DE INTEGRITATE

Fiecare tabel va avea o cheie primară.

Cheile externe vor asigura integritatea relațiilor dintre entități.

Adresele de email vor fi unice.

Un utilizator nu va putea fi înregistrat de două ori ca membru al aceluiași Workspace.

O sarcină va aparține fie unui utilizator, fie unui Workspace, nu ambelor simultan.

Utilizatorul căruia i se atribuie o sarcină comună trebuie să fie membru al Workspace-ului respectiv.

Invitațiile vor putea fi acceptate sau refuzate doar de destinatar.

Crearea unui Workspace va include și înregistrarea creatorului ca administrator.

Acceptarea unei invitații și adăugarea membrului vor fi realizate într-o tranzacție.

Data de încheiere a unui eveniment trebuie să fie ulterioară datei de început.

Accesul la datele unui Workspace va fi permis doar membrilor săi.

PRINCIPALELE ENDPOINT-URI API

API-ul va utiliza formatul JSON și metode HTTP standard.

Autentificare

POST /api/auth/register
Creează un cont nou.

POST /api/auth/login
Autentifică utilizatorul.

POST /api/auth/logout
Deconectează utilizatorul.

GET /api/auth/me
Returnează informațiile utilizatorului autentificat.

Sarcini personale

GET /api/tasks
Returnează sarcinile personale.

POST /api/tasks
Creează o sarcină personală.

PATCH /api/tasks/:id
Modifică o sarcină personală.

DELETE /api/tasks/:id
Șterge o sarcină personală.

Calendar personal

GET /api/events
Returnează evenimentele personale.

POST /api/events
Creează un eveniment.

PATCH /api/events/:id
Modifică un eveniment.

DELETE /api/events/:id
Șterge un eveniment.

Workspace-uri

GET /api/workspaces
Returnează Workspace-urile utilizatorului.

POST /api/workspaces
Creează un Workspace.

GET /api/workspaces/:id
Returnează informațiile unui Workspace.

PATCH /api/workspaces/:id
Modifică numele sau descrierea Workspace-ului.

GET /api/workspaces/:id/members
Returnează membrii Workspace-ului.

DELETE /api/workspaces/:id/members/:userId
Elimină un membru din Workspace.

POST /api/workspaces/:id/leave
Permite utilizatorului să părăsească Workspace-ul.

Invitații

POST /api/workspaces/:id/invitations
Trimite o invitație.

GET /api/invitations
Returnează invitațiile primite.

POST /api/invitations/:id/accept
Acceptă o invitație.

POST /api/invitations/:id/reject
Refuză o invitație.

Notițe comune

GET /api/workspaces/:id/notes
Returnează notițele Workspace-ului.

POST /api/workspaces/:id/notes
Creează o notiță.

PATCH /api/workspaces/:id/notes/:noteId
Modifică o notiță.

DELETE /api/workspaces/:id/notes/:noteId
Șterge o notiță.

Sarcini colaborative

GET /api/workspaces/:id/tasks
Returnează sarcinile comune.

POST /api/workspaces/:id/tasks
Creează o sarcină comună.

PATCH /api/workspaces/:id/tasks/:taskId
Modifică o sarcină comună.

DELETE /api/workspaces/:id/tasks/:taskId
Șterge o sarcină comună.

Liste colaborative

GET /api/workspaces/:id/lists
Returnează listele comune.

POST /api/workspaces/:id/lists
Creează o listă.

PATCH /api/workspaces/:id/lists/:listId
Modifică o listă.

DELETE /api/workspaces/:id/lists/:listId
Șterge o listă.

POST /api/workspaces/:id/lists/:listId/items
Adaugă un element într-o listă.

PATCH /api/workspaces/:id/lists/:listId/items/:itemId
Modifică sau finalizează un element.

DELETE /api/workspaces/:id/lists/:listId/items/:itemId
Șterge un element.

SECURITATEA SERVICIILOR API

Endpoint-urile care gestionează date personale sau colaborative vor necesita autentificare.

Backend-ul va verifica drepturile utilizatorului înaintea fiecărei operații protejate.

Utilizatorii vor putea modifica doar propriile date personale.

Operațiile asupra Workspace-urilor vor fi limitate în funcție de apartenență și rol.

Datele primite vor fi validate înainte de procesare.

Interogările SQL vor utiliza parametri pentru prevenirea atacurilor de tip SQL Injection.

Răspunsurile API vor utiliza coduri HTTP corespunzătoare, precum 200, 201, 400, 401, 403, 404 și 409.

EXTINDERI VIITOARE

Modelul de date va putea fi extins pentru:

- Calendare comune și orare recurente.
- Bugete personale, venituri și cheltuieli.
- Documente personale și partajate.
- Activități recurente și planificare avansată.

Aceste funcționalități nu fac parte din modelul esențial al primei versiuni.

CONCLUZIE

Modelul de date DailyHub este organizat în jurul utilizatorilor, activităților personale și Workspace-urilor colaborative.

Relațiile dintre entități permit separarea datelor private de cele comune și controlul accesului în funcție de apartenență și rol.

Serviciile API vor asigura comunicarea dintre frontend și backend și vor permite gestionarea informațiilor stocate în PostgreSQL.

Modelul prezentat este preliminar și poate fi ajustat în timpul implementării.
