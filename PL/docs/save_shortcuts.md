# Kopie przez Skróty
Aplikacja Skróty może kopiować twoje zapisy w wybrane przez ciebie miejsce, na przykład na iCloud Drive, za każdym razem, gdy wychodzisz z gry. Robi to sama, bez pytania. To część pełnej wersji gry.

## Konfiguracja
1. W aplikacji **Skróty** stuknij +, aby utworzyć nowy skrót, stuknij **Edycja** w prawym górnym rogu i dodaj czynność gry **Pobierz ostatni zapis**.
2. Dodaj **Zachowaj plik** i stuknij jego strzałkę. Wyłącz **Pytaj, gdzie zachować**, wybierz folder i włącz **Nadpisz plik, jeśli istnieje**.
3. Stuknij **Szukaj** na dole, potem **Automatyzacja**, a w sekcji **Aplikacje** wybierz **Aplikacja**.
4. W wierszu, który się pojawi, stuknij **Aplikacja** i wybierz grę, potem stuknij **Otwarto** i wybierz **Zamknięto**.

Przed iOS 27 utwórz automatyzację zamiast tego na karcie **Automatyzacja**: wybierz **Aplikacja**, grę, tylko **Jest zamknięta** i **Uruchom od razu**, a potem dodaj do niej czynności z kroków 1 i 2. W iOS 16 wyłącz zamiast tego **Pytaj przed uruchomieniem**.

Każda kopia to zip nazwany tak jak jej zapis, więc z każdego zapisu masz jedną aktualną kopię.

## Starsze kopie
Wstaw zmienną **Bieżąca data** do ścieżki folderu w czynności **Zachowaj plik**. Kopie z innej daty trafią wtedy do osobnego folderu, a starsze zostaną.

## Inne czynności
**Pobierz zapis** pobiera jeden zapis po jego nazwie. **Pobierz zapisy** pobiera wszystkie zapisy albo tylko te zmienione od jakiejś daty.

## Przywracanie kopii
Te czynności tylko kopiują twoje zapisy na zewnątrz. Aby przywrócić kopię, naciśnij „Import” na ekranie wczytywania i wybierz jej zip.

Zapis w chmurze utrzymuje twoje urządzenia na tym samym postępie. Kopia ze Skrótów to twój własny plik, trzymany tam, gdzie chcesz, jako historia albo dla gry na PC.
