# Ćwiczenia 51 -- GP0, wdrażanie oprogramowania + pulpit zdalny

1. Zaloguj się na konto administrator.
1. W AD utwórz nową jednostkę organizacyjną o nazwie **addapp**.
1. Dołącz stację do domeny.
1. Po dołączeniu stacji, przenieś komputer w AD do jednostki organizacyjnej addapp.
1. Przenieś konto, na które logujesz się na stacji do jednostki
    organizacyjnej addapp.

   ![image1](media/image1.png)

1. Na dysku udostępnij folder o nazwie apps (udostępnianie
    zaawansowane) jako ukryty,  
    obie zakładki: udostępnianie i zabezpieczenia.

    - administratorzy domeny - pełna kontrola,

    - użytkownicy uwierzytelnieni -- odczyt,

    - wszyscy -zmiana(change).

    ![image2](media/image2.png)

1. Na stacji wybierz: Ten komputer - \> Mapuj dysk sieciowy (
    [\\\\10.9.8.1\\apps\$](../../../../../../apps$) ) pod literę R:

1. Ściągnąć instalkę teams ze strony:

    <https://learn.microsoft.com/en-us/microsoftteams/msi-deployment>  

    <https://go.microsoft.com/fwlink/?linkid=2243204&clcid=0x409>

    <https://go.microsoft.com/fwlink/?linkid=2196106>

1. Pobrane pliki installerów zapisz na zmapowanym dysku R.

1. Utwórz skrypt bat o zawartości:

   ```bash
    \\10.9.8.1\apps$\teamsbootstrapper.exe -p -o "\\10.9.8.1\apps$\MSTeams-x64.msix"
   ```

1. Skrypt dodać w

   ```text
   Computer configuration -> Policies -> Windows settings -> Scripts -> Startup.
   ```

   i przycisk add

1. Ściągnąć instalkę putty:

    <https://the.earth.li/~sgtatham/putty/latest/w64/putty-64bit-0.83-installer.msi>

1. Ściągnąć plik dla 7-zip:

    <https://7-zip.org/a/7z2600-x64.msi>

1. Również zapisz plik msi na zmapowanym dysku R.

1. Możesz zaktualizować te pliki na nośnikach pendrive.

1. Otwórz przystawkę GPO Zarządzanie zasadami grupy.

   ![image3](media/image3.png)

1. Dla jednostki **addapp** utwórz nowy obiekt zasad grup.
1. Podać nazwę instalacja oprogramowania. OK.
1. Po utworzeniu obiektu wybierz Edytuj.

   ![image4](media/image4.png)

1. W nowo otwartym oknie:  

   ```text
   Konfiguracja komputera -> Zasady -> Ustawienia oprogramowania ->Instalacja oprogramowania.
   ```

1. Następnie prawym klawiszem myszki i z rozwiniętego menu
    kontekstowego wybieramy:

   ```text
   Nowy -> Pakiet.
   ```

1. Nazwa pliku, podajemy
    `\\10.9.8.1\apps$` i wybieramy plik teams \...msi .

   ![image5](media/image5.png)

1. Rozmieszczenie oprogramowania: przypisany.

   ![image6](media/image6.png)

1. Analogicznie dla drugiego pakietu msi.

   ![image7](media/image7.png)

1. Finalnie:

   ![image8](media/image8.png)

1. Wybierz:

   ```text
   Szablony administracyjne -> System -> Wyświetlaj bardzo szczegółowe komunikaty o stanie. Włącz.
   ```

   ![image9](media/image9.png)

1. Zamykamy okno edycji zasad.

1. Zapisz raport na pulpicie z utworzonych
    zasad. Prawy klawisz myszy po prawej stronie na Settings.

   ![image10](media/image10.png)

1. Na stacji w cmd wpisujemy polecenie: gpupdate /force
   Serwer:

   ![image11](media/image11.png)

   Stacja:

   ![image12](media/image12.png)

1. Po restarcie stacji sprawdzić czy oprogramowanie zostało
    zainstalowane.

   ![image13](media/image13.png)

1. Sprawdzenie oprogramowania:

   ![image14](media/image14.png)

1. Sprawdź poleceniem

   ```bash
    gpresult /r
   ```

   oraz

   ```bash
    gpresult /h raport.html
   ```

1. Jeśli po restarcie stacji oprogramowanie nie pojawiło się w systemie, wykonaj poniższe kroki na stacji roboczej:
    Naciśnij <kbd>Win</kbd> + <kbd>R</kbd>, wpisz `eventvwr.msc` i enter.

    Rozwiń sekcję:
    Dzienniki systemu Windows (Windows Logs) -> Aplikacja (Application).  
    Szukaj: `App Mgmt`

1. Odłącz stację od domeny.

1. Przenieś komputer w AD z jednostki organizacyjnej **addapp** do
    kontenera Computers.

1. Zatrzymaj udostępnianie katalogu apps, następnie usuń ten folder.

1. Usunąć raport z pulpitu.

1. Opróżnij kosz.

1. W przystawce _`GPO Group Policy Management`_ usunąć obiekt „instalacja
    oprogramowania".

---

1. Dodatkowe ćwiczenie -- **pulpit zdalny**.

2. Konfiguracja pulpitu zdalnego:

   ```text
   Server Manager -> Local Server -> Remote Desktop
   ```

   , klikamy na disabled

   ![image15](media/image15.png)

3. Na stacji windows. Po kliknięciu Podłącz podać hasło i odpowiedzieć
    twierdzącą w nowym oknie.

   ![image16](media/image16.png)

   ![image17](media/image17.png)

4. Wyłączyć pulpit zdalny.

5. KONIEC.🔚
