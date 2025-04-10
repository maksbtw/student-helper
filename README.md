# Instrukcja uzywanie Git

# Wazne
Nigdy nie uzywac <b>git init</b> dla folder-u korzeniowego systemu. Inczej GIT bedzie obserowal zmiany w calym systemie i trudno potem to usunac. <br>

Roznica miedzy GIT i Github jest wazna: <br>
<b>GIT</b> - jest LOKALNYM systemem kontoli wersji <br>
<b>GitHub</b> - online serwis ktory umozliwia przechowywania wersji w chmurze <br>

Wszystko co bedziesz sobie robil w terminalu na komputerze bedzie odbywac sie na twojej lokalnej kopii repozytorium. Jesli nie widzisz czegos co jest na Github stronie, prawdopodobnie nie zaktualizowales danych lokalnych (pull)

### Fajne linki
[CheatSheet](https://education.github.com/git-cheat-sheet-education.pdf) <br>
[Файлик с курсов (укр версия)](https://docs.google.com/document/d/1lCt8y3kz62z5dAlMvJ7kQRWouHJRkr991cBHc1bhSbU/edit?tab=t.0#heading=h.w1hy05o1ju5m) где много чего написано полезного но сразу все читать не советую (утонете в инфе)

# Pobieranie projektu

GIT ma juz byc pobrany i zasinstalowany, komenda do sprawdzenia:
```
git -v
```

1. Otworzenie w bash-u folderu gdzie bedzie zamieszczony projekt
2. Klonowanie repo na swoj komputer:
```
git clone https://github.com/maksbtw/student-helper.git
```
3. Otworzenie folderu projektu w VSCode jak korzeniowego
```
code student-helper
```
Dalej dzialamy z wbudowanego terminala w VSCode (Ctrl + `) <br>
4. Sprawdzenie czy projekt zostal poprawnie pobrany
```
git status
```
Musi wyskoczyc podobny napis
```
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

# Dodawanie zmian do nowego commit-u
1. Zaznaczmy pliki/foldery w ktorych byly dokonane jakies zmiany (te zmiany trafia tylko do index-u, na danym etapie jeszcze nie zostaly zapisane, wiec mozna zmieniac wybrane elementy)
```
git add plik-jakis.txt
git add folder-jakis
git add . //dla wybrania wszystkich nie dodanych elementow do index-u
```
W przypadku otrzymnia linii:
```
warning: in the working copy of 'index.html', LF will be replaced by CRLF the next time Git touches it
```
mozna to zignorowac 
2. Gdy wszystkie zmienione pliki zostaly dodane do index-u robimy commit:
```
git commit -m "opis zmian"
```
flaga -m oznacza ze dla commit-u bedzie przyisany opis (robimy to zawsze)
3. Podczas pierwszego commit-u GIT bedzie chcial dowiedziec sie kto wprowadza zmiany lokalne i zapyta o mail-a i username:
```
Author identity unknown
*** Please tell me who you are.
Run
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.
fatal: unable to auto-detect email address (got 'maks2@mAx.(none)')
```
nalezy skorzystac z polecen podanych w bledzie i wpisac dane na ktore jest zarejestrowane konto Github (username jest napisany w URL na glownej stronie Github twojego profilu), dalej jescze raz probujemy wpisac linijke z punktu 2
4. Zeby commit wrzucic do Github robimy push:
```
git push origin main
```
w tym poleceniu <b>origin</b> oznacza nazwe galezi w repozytorium zdalnym na ktory chcemy wrzucic zmiany (bedzie on zawsze taki sam), <b>main</b> galaz lokalna Git z ktorej dane beda wrzucone do chmury
5. Wchodzimy na strone repozytorium i obserwujemy dodane pliki

# Zarzadzanie galezmi
Tworzenie nowej galezi
```
git checkout -b nazwa-galezi
```
Wysylanie zmian (push) w danej galezi do Github
```
git push origin nazwa-galezi
```
Pobieranie (pull) zmian z Github w danej galezi
```
git pull origin nazwa-galezi
```
Przelaczanie sie miedzy galeziami
```
git checkout nazwa-galezi
```
Wyswitlanie wszystkich galezi <br>
```
git branch
```

# Merge

Uzywamy merge, gdy chce zmiany z jednej galezi wrzucic do innej.
Z nich bedziemy korzystac pozniej, na razie skupiamy sie na materialu wyzej

```
git merge nazwa-galezi
```
na moment wywolania komendy musi byc wybrana DO KTOREJ chcemy dolaczyc zmiany z galezie wpisanej w poleceniu

Gdy podczas merge beda konfikty (np. w tym samym miejscu kodu w roznych galeziach beda rozne zmiany) w VSCode otworzy sie edytor konfiltow. W nim trzeba recznie wskazac jakie zmiany musza byc dodane do koncowego commit-u. Po rozwiazaniu wszystkiech konfliktow klikamy "Complete" i VSCode sam dokonczy merge i stworzy commit w ktorym beda polacze dwie galezie. WAZNE: push automaytcznie nie odbedzie sie, trzeba recznie go zrobic w razie potrzeby
