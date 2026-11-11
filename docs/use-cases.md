
DailyHub - Scenarii de utilizare

1) Introducere

Acest document prezintă principalele scenarii de utilizare ale aplicației DailyHub. Scopul său este de a descrie modul în care utilizatorii interacționează cu aplicația pentru a organiza activități personale și pentru a colabora în spații de lucru comune, numite Workspace-uri.

Fiecare scenariu include actorii implicați, condițiile inițiale, pașii principali, situațiile alternative și rezultatele așteptate. Scenariile pot fi utilizate ulterior pentru verificarea funcționalităților implementate.

2) Scenariul 1 - Crearea și gestionarea unei sarcini personale

Scop:
Utilizatorul dorește să creeze o sarcină personală, să îi stabilească prioritatea și să o marcheze drept finalizată.

Actor principal:
Utilizator autentificat.

Condiții inițiale:
Utilizatorul are un cont DailyHub și este autentificat în aplicație.

Pașii principali:

Pasul 1: Utilizatorul accesează secțiunea Sarcini din spațiul personal.

Pasul 2: Apasă butonul pentru adăugarea unei sarcini noi.

Pasul 3: Introduce titlul sarcinii, o descriere opțională, termenul-limită și prioritatea.

Pasul 4: Apasă butonul Salvează.

Pasul 5: Aplicația verifică datele introduse și salvează sarcina în baza de date.

Pasul 6: Noua sarcină apare în lista personală a utilizatorului.

Pasul 7: Utilizatorul poate modifica informațiile sarcinii sau o poate marca drept finalizată.

Pasul 8: Aplicația actualizează starea sarcinii și salvează modificările.

Situații alternative:

Dacă utilizatorul nu introduce titlul sarcinii, aplicația afișează un mesaj de eroare și solicită completarea acestuia.

Dacă termenul-limită introdus este invalid, aplicația solicită corectarea datei.

Dacă salvarea eșuează, aplicația informează utilizatorul și nu confirmă operația.

Rezultat așteptat:
Sarcina este salvată în baza de date și poate fi vizualizată, modificată, finalizată sau ștearsă de utilizator.

Verificare:
Se creează o sarcină de test, se verifică apariția acesteia în listă, apoi se modifică prioritatea și se marchează drept finalizată. După reîncărcarea paginii, modificările trebuie să fie păstrate.


3) Scenariul 2 - Crearea unui Workspace și invitarea unui utilizator

Scop:
Un utilizator dorește să creeze un spațiu de lucru comun și să invite o altă persoană pentru a colabora.

Actori:
Administratorul Workspace-ului și utilizatorul invitat.

Condiții inițiale:
Ambii utilizatori au conturi DailyHub. Administratorul este autentificat în aplicație.

Pașii principali:

Pasul 1: Administratorul accesează secțiunea Workspaces.

Pasul 2: Apasă butonul pentru crearea unui Workspace nou.

Pasul 3: Introduce numele spațiului și, opțional, o descriere.

Pasul 4: Apasă butonul Creează.

Pasul 5: Aplicația salvează Workspace-ul și îl desemnează automat pe creator drept administrator.

Pasul 6: Administratorul accesează secțiunea Membri și selectează opțiunea Invită utilizator.

Pasul 7: Introduce adresa de email asociată contului persoanei invitate.

Pasul 8: Aplicația verifică existența utilizatorului și înregistrează invitația.

Pasul 9: Utilizatorul invitat se autentifică și accesează secțiunea Invitații.

Pasul 10: Utilizatorul acceptă invitația.

Pasul 11: Aplicația îl adaugă în lista membrilor Workspace-ului.

Pasul 12: Noul membru poate accesa informațiile comune și poate contribui la activitățile spațiului.

Situații alternative:

Dacă adresa de email nu aparține unui cont existent, aplicația afișează un mesaj corespunzător.

Dacă utilizatorul este deja membru, aplicația nu permite trimiterea unei invitații duplicate.

Dacă există deja o invitație în așteptare pentru acel utilizator, aplicația informează administratorul.

Dacă utilizatorul refuză invitația, acesta nu este adăugat în Workspace.

Rezultat așteptat:
Workspace-ul este creat, iar utilizatorul care acceptă invitația devine membru și primește acces la resursele comune.

Verificare:
Se folosesc două conturi de test. Primul creează Workspace-ul și trimite invitația. Al doilea acceptă invitația. Se verifică dacă Workspace-ul apare în contul celui de-al doilea utilizator și dacă acesta poate accesa conținutul comun.


4) Scenariul 3 - Crearea și modificarea unei notițe comune

Scop:
Membrii unui Workspace doresc să creeze și să actualizeze o notiță accesibilă tuturor membrilor.

Actori:
Doi utilizatori care aparțin aceluiași Workspace.

Condiții inițiale:
Workspace-ul există, iar ambii utilizatori sunt membri și au acces la secțiunea Notițe.

Pașii principali:

Pasul 1: Primul utilizator accesează Workspace-ul.

Pasul 2: Deschide secțiunea Notițe.

Pasul 3: Apasă butonul Adaugă notiță.

Pasul 4: Introduce titlul și conținutul notiței.

Pasul 5: Apasă butonul Salvează.

Pasul 6: Aplicația salvează notița în baza de date și o asociază Workspace-ului.

Pasul 7: Al doilea utilizator accesează același Workspace.

Pasul 8: Deschide secțiunea Notițe și selectează notița creată.

Pasul 9: Citește conținutul și efectuează modificări.

Pasul 10: Apasă butonul Salvează.

Pasul 11: Aplicația actualizează notița în baza de date.

Pasul 12: Primul utilizator redeschide sau reîncarcă notița și vede conținutul actualizat.

Situații alternative:

Dacă titlul notiței lipsește, aplicația solicită completarea acestuia.

Dacă un utilizator care nu aparține Workspace-ului încearcă să acceseze notița, aplicația refuză accesul.

Dacă un membru încearcă să salveze o versiune veche a unei notițe care a fost modificată între timp, aplicația îl avertizează și nu suprascrie automat versiunea mai recentă.

Dacă salvarea eșuează, aplicația afișează un mesaj de eroare.

Rezultat așteptat:
Notița este disponibilă tuturor membrilor Workspace-ului, iar modificările salvate pot fi vizualizate de aceștia.

Verificare:
Primul utilizator creează o notiță. Al doilea o deschide, modifică textul și salvează. Primul utilizator reîncarcă notița și verifică dacă modificările sunt vizibile.

Editarea simultană în timp real nu este inclusă în prima versiune a aplicației.


5) Scenariul 4 - Crearea și actualizarea unei liste colaborative

Scop:
Mai mulți membri ai unui Workspace doresc să gestioneze împreună o listă de activități sau cumpărături.

Actori:
Doi membri ai aceluiași Workspace.

Condiții inițiale:
Ambii utilizatori sunt autentificați și aparțin aceluiași Workspace.

Pașii principali:

Pasul 1: Primul utilizator accesează Workspace-ul și deschide secțiunea Liste.

Pasul 2: Apasă butonul Creează listă.

Pasul 3: Introduce numele listei, de exemplu Cumpărături pentru weekend.

Pasul 4: Salvează lista.

Pasul 5: Adaugă elemente precum lapte, pâine și fructe.

Pasul 6: Aplicația salvează elementele și le afișează în lista comună.

Pasul 7: Al doilea utilizator accesează același Workspace și deschide lista.

Pasul 8: Adaugă un element nou sau marchează un element existent drept finalizat.

Pasul 9: Aplicația salvează modificările.

Pasul 10: Primul utilizator reîncarcă lista și vede elementele actualizate.

Situații alternative:

Dacă utilizatorul încearcă să creeze o listă fără nume, aplicația solicită introducerea acestuia.

Dacă un utilizator nu este membru al Workspace-ului, accesul la listă este refuzat.

Dacă salvarea unui element eșuează, aplicația afișează un mesaj de eroare.

Rezultat așteptat:
Lista și elementele sale sunt stocate în baza de date și pot fi actualizate de membrii Workspace-ului.

Verificare:
Se creează o listă folosind primul cont. Al doilea cont adaugă un element și marchează altul drept finalizat. După reîncărcare, ambii utilizatori trebuie să vadă modificările salvate.


6) Concluzie

Scenariile prezentate descriu funcționalitățile principale ale primei versiuni DailyHub și modul în care utilizatorii pot organiza activități personale sau pot colabora în Workspace-uri.

Fiecare scenariu conține condiții inițiale, pași de executare, situații alternative și rezultate verificabile.

Aceste scenarii vor fi utilizate ca referință pentru proiectarea interfeței, implementarea funcționalităților și testarea aplicației.

