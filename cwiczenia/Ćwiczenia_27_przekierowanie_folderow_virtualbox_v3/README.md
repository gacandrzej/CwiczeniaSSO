# Ćwiczenia 27 -- Przekierowanie folderów

💡Założenia: stacja windows + serwer standard

1. Zaloguj się na konto administrator na serwerze.

1. Utwórz jednostkę organizacyjną w AD dla domeny zsmeie.abcd, o ile
    nie istnieje, o nazwie: ***3x***, gdzie ***x*** oznacza
    literę twojej klasy.

1. Utwórz w jednostce ***3x*** podjednostkę o nazwie ***grx***, gdzie
    ***x*** oznacza numer twojej grupy.

1. Utwórz na dysku c: katalog do przechowywania twoich plików z pulpitu
    o nazwie: pulpity_3x_grX, gdzie x
   oznacza literę twojej klasy, a X numer twojej grupy.

1. W przystawce zarządzanie komputerem ( compmgmt.msc ) udostępnij
   folder pulpity_3x_grX jako ukryty,
   dodając na końcu znak dolara. Pamiętaj o kliknięciu w przycisk Dostosuj
   (Patrz punkt 8).

1. Udostępnij folder dla wszystkich pełna kontrola, oraz na zakładce
    \'zabezpieczenia\' dodaj grupę Wszyscy i dla niej
   również włącz opcję pełna kontrola.

   ![image1](media/image1.png)

   ![image2](media/image2.png)

1. Utwórz grupę zabezpieczeń na poziomie swojego konta o nazwie:
   pulpity_3x_grX, gdzie x oznacza literę twojej
   klasy, a X numer twojej grupy.

   ![image3](media/image3.png)

   ![image4](media/image4.png)

1. We właściwościach swojego konta przejdź na zakładkę Członek grupy,
   następnie przycisk Dodaj i wybierz z listy
   utworzoną w poprzednim punkcie grupę, poprzez kliknięcie w przyciski
   zaawansowane i znajdź teraz. W efekcie
   zostałeś dodany do tej grupy zabezpieczeń.

   ![image5](media/image5.png)

1. Otwórz przystawkę Zarządzanie zasadami grupy i przejdź do jednostki
   organizacyjnej do której należysz, np.
   zsmeie.abcd/2k/gr2.

   ![image6](media/image6.png)

1. Prawym klawiszem myszy wybierz pozycję 'utwórz obiekt zasad grup
   ...' , następnie nadaj mu nazwę, np.
   przekierowanie folderów. Prawym klawiszem myszy na obiekcie wybierz
   pozycję edytuj

   ![image7](media/image7.png)

1. , otworzy się okno \'Edytor zarządzania zasadami
   grupy\', następnie \'konfiguracja użytkownika\' → zasady → ustawienia
   systemu windows → przekierowania
   folderów → Dokumenty ( prawym klawiszem myszy wybrać właściwości) i
   skonfigurować przekierowanie dla
   grupy zabezpieczeń i folderu udostępnionego.

   ![image8](media/image8.png)

1. Ustawienia: Zaawansowane -- określaj lokalizację dla różnych grup
    użytkowników, następnie Dodaj.

1. Otworzy się okno \'Określenie grupy i lokalizacji\' , członkostwo
   grupy zabezpieczeń: wybrać swoją grupę,
   lokalizacja folderu docelowego: utwórz folder dla każdego użytkownika w
   ścieżce,
   ścieżka katalogu głównego: np.

   [\\\\serverx\\](file:///\\serverx\)pulpity\$ i OK.

   ![image9](media/image9.png)

   ![image10](media/image10.png)

1. Na zakładce ustawienia zaznacz 4 pierwsze pozycje.

1. Zamknij okno edytora zasad grup !!!

1. Zaloguj się na swoje konto w AD na stacji roboczej i sprawdź, czy
   pliki z pulpitu zostaną przeniesione na
   serwer do katalogu np.

   c:\\pulpity_3k_gr2\\nazwa_twojego_konta\\Dokumenty.

   Na serwerze:

   ![image11](media/image11.png)

   ![image12](media/image12.png)

1. Zapisz plik raportu z GPO na pulpicie, pozycja Save Report.

   ![image13](media/image13.png)

1. Na wypadek, gdyby nie działało przelogowanie

   ![image14](media/image14.png)

1. Wszystkie czynności powtórz dla katalogu dokumenty.

1. Wszystkie czynności powtórz dla katalogu Obrazy( bez patrzenia na kartkę).

1. Wybierz inne foldery do przećwiczenia.

1. Usuń wszystkie obiekty, konta, grupy, które utworzyłeś/aś.

1. KONIEC.🔚
