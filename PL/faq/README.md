---
name: Frequently Asked Questions
---

# Często zadawane pytania

Tutaj możesz znaleźć odpowiedzi na najczęściej zadawane pytania. Jeśli nie możesz znaleźć tutaj odpowiedzi na swoje pytanie, możesz poprosić o pomoc na serwerze. [Oficjalny Serwer Discord Quaver](https://discord.gg/quaver).

## Głowne

### Czym jest Quaver?

Quaver to napędzana przez społeczność gra rytmiczna open-source.Inspirowana jest różnymi klasycznymi grami rytmicznymi z pionowym przewijaniem i planuje je rozwinąć, koncentrując się na zdrowej rywalizacji w czasie rzeczywistym.

### Jak Quaver różni się od innych gier?

Gra jest w pełni open-source, co pozwala każdemu pomagać i ulepszać grę. Co więcej, naszym celem jest zapewnienie nowego doświadczenia VSRG poprzez wprowadzenie koncepcji rywalizacji, takich jak konkurencyjny matchmaking.

### Na jakich platformach dostępny jest Quaver?

Quaver dostępny jest na Windows, Mac oraz Linux.

## Rozgrywka

### Jakie tryby gry wspiera Quaver?

Quaver obsługuje obecnie 4 klawisze (4k) i 7 klawiszy (7k). Obsługiwane są również mapy 7k z dodatkowym scratch lane (7k+1), ale wyniki na nich pozostają nierankingowane.

### Gdzię mogę znaleźć więcej?

Więcej map można pobrać za pomocą narzędzia do pobierania w grze lub z [Oficjalnej Strony Quaver](https://quavergame.com/maps).

### Czy mogę zaimportować więcej map z innych gier?

Tak, Quaver obsługuje obecnie pliki .osz, .sm i .mcz. Aby je zaimportować, przeciągnij pliki do okna gry.

### Mam wiele map w innej grze, czy mogę zaimportować je wszystkie naraz?

Możliwe jest jednoczesne zaimportowanie wszystkich map z innych gier. W Quaver przejdź do Opcje > Różne, włącz "Wczytaj utwory z innych zainstalowanych gier" i kliknij "Wykryj utwory z innych zainstalowanych gier".

### Czy mogę zaimportować skiny z innych gier?

Gra nie wspiera konwersji skinów bezpośrednio, choć możliwe jest pobranie konwertera plików .osk [tutaj](https://rhythmgamers.net/QBC/) razem z[poradnikiem](https://www.youtube.com/watch?v=pWeLbx48NVI).

### Znalazłem błąd, gdzie mogę go zgłosić?

Każdy błąd powinien być zgłoszony na naszej stronie zgłaszania [Github](https://github.com/Quaver/Quaver/issues). Możesz publikować wszystko, co znajdziesz, ale sprawdź, czy problem nie został już zgłoszony, aby uniknąć powielania.

### Mam prośbę o dodanie funkcji, gdzie mogę ją opublikować?

Podobnie jak błędy, prośby o dodanie nowych funkcji powinny być zgłaszane na naszej stronie zgłaszania [GitHub](https://github.com/Quaver/Quaver/issues). Wybierz po prostu "Feature Request", aby zgłosić prośbę o dodanie nowej funkcji.

### Czy mogę zmienić moją nazwę użytkownika?

Zmiana nazwy użytkownika jest funkcją dostępną tylko dla wspierających. Jeśli wspierasz Quaver, możesz zmienić nazwę użytkownika raz na 30 dni.

### Jak zmniejszyć opóźnienie dźwięku hitsound w systemie Linux??

Opóźnienie dźwięku powinno być w porządku od razu po uruchomieniu. Nadal możliwe jest dostosowanie zmiennych, jeśli pojawią się nietypowe problemy.

Jeśli opóźnienie dźwięku wzrasta w czasie odtwarzania, otwórz aplikację `/etc/pulse/default.pa`, znajdź linię:

```
load-module module-udev-detect
```

i zmień na:

```
load-module module-udev-detect fixed_latency_range=yes
```

Następnie uruchom ponownie system. Należy pamiętać, że może to spowodować poważne zakłócenia dźwięku w niektórych aplikacjach (obecnie powoduje to otwarcie Discorda w Firefoksie, chociaż odpowiedzialny za to komponent ma już wdrożoną poprawkę).

Można również dostosować opóźnienie, którego Quaver żąda od systemu. W pliku `quaver.cfg` należy znaleźć następujące ustawienia:

```
DevicePeriod = 2
DeviceBufferLengthMultiplier = 4
```

Kontrolują one okres (domyślnie 2 ms, jak często system odpytywał Quaver o nowy dźwięk) i długość bufora (domyślnie 4, jak duży jest bufor audio, jako wielokrotność okresu). Zmniejszenie okresu zmniejszy opóźnienie dźwięku przy jednoczesnym zwiększeniu obciążenia procesora, a zmniejszenie mnożnika długości bufora zmniejszy opóźnienie dźwięku przy potencjalnym wprowadzeniu "trzasków" dźwięku i innych artefaktów. Zwiększenie tych wartości doprowadzi do większego opóźnienia przy jednoczesnym zmniejszeniu obciążenia procesora i prawdopodobieństwa wystąpienia zakłóceń dźwięku.

### Jak użyć Wayland VSync?

Aby korzystać z Wayland VSync, należy uruchomić system Linux z kompozytorem Wayland, takim jak obecny w nowszych wersjach GNOME i KDE (upewnij się, że nie używasz trybu "Xorg") lub samodzielnym, takim jak Weston lub sway.

Włącz opcję "Preferuj Wayland" w Video/Linux i zrestartuj Quaver. Teraz włącz Wayland VSync. Możesz upewnić się, że działa, używając licznika FPS. Liczba klatek na sekundę powinna być równa częstotliwości odświeżania monitora, a UPS powinna być wyższa.

Aby uzyskać najniższe opóźnienie (poniżej 1 klatki) podczas uruchamiania sway, ustaw `max_render_time` na wyjściu i w oknie Quaver. Zobacz `man 5 sway` po instrukcje.

## Interfejs

### Jak działają filtry map?

Obecnie mamy takie filtrys:

| Filtr        | Skrótowiec | Pełna nazwa | Argument                                                   |
| ------------ | ---------- | ----------- | -----------------------------------------------------------|
| BPM          | b          | bpm         | numer                                                      |
| Trudność     | d          | difficulty  | numer                                                      |
| Gra          | g          | game        | quaver/q, osu/o, stepmania/sm/s/etterna/e                  |
| Tryb         | k          | keys        | numer                                                      |
| Długość      | l          | length      | numer in seconds                                           |
| LNs          | ln         | lns         | liczba naturalna (452) lub pełny procent (57%)             |
| KPS          | n          | nps         | numer                                                      |
| Status       | s          | status      | ranked/r, notsubmitted/n, unranked/u, (dan/d)              |
| Ilość zagrań | t          | timesplayed | numer                                                      |

Wszystkie filtry mogą używać operatora `=` (równa się) i `!=` (nie równa się), porównania liczb mogą dodatkowo używać `>= > <= <`.

Filtru używa się poprzez wpisanie skrótu, operatora i argumentu w pasku wyszukiwania, wszystko bez spacji. Przykładem może być `difficulty>30`. Dowolny ciąg od krótkiej do pełnej nazwy zostanie dopasowany, `diff>30` będzie prawidłowym filtrem.

Jeśli nie zostanie podany żaden argument ani operator, zostanie ona potraktowana jako zwykłe słowo kluczowe i wyświetli wszystkie zestawy map, które zawierają to słowo kluczowe w metadanych (artysta, tytuł, mapper, tagi).

Wszystkie warunki wyszukiwania muszą być spełnione, aby zestaw map został wyświetlony (AND). Nie ma jeszcze opcji dla bramek OR.

## Rozwiązywanie problemów

### Gra nie uruchamia sie

Upewnij się, że Steam jest uruchomiony, ponieważ jest wymagany do uruchomienia Quaver.

#### Linux, build offline lub lokalny

Uruchomienie kompilacji offline lub opublikowanej samodzielnej kompilacji (np. z `dotnet publish -c Release -r linux-x64`) musi zostać wykonane przez środowisko wykonawcze Steam. Uruchom to polecenie z folderu repozytorium Quaver:

``hell
~/.steam/bin/steam-runtime/run.sh Quaver/bin/Release/netcoreapp2.1/linux-x64/publish/Quaver
```

Uruchomienie zwykłej, samodzielnej kompilacji (np. z `dotnet build -p Quaver -c Debug`) wymaga poprawnej ścieżki biblioteki. Można to zrobić za pomocą skryptu uruchamiania Steam i własnego skryptu uruchamiania Quaver:

``hell
~/.steam/bin/steam-runtime/run.sh Quaver/bin/Debug/netcoreapp2.1/quaver.sh
```

### Otrzymuję komunikat "Content File Locked" podczas próby pobrania Quaver na Steam.

Wydaje się, że jest to problem związany ze Steam.

Kilka rzeczy, które mogą pomóc rozwiązać ten problem, to uruchomienie Steam jako administrator, ponowne uruchomienie komputera i sprawdzenie integralności plików gry Quaver.

Jeśli żaden z tych sposobów nie zadziała, możesz znaleźć odpowiedź w jednym z tych wątków na forum:

- [Wątek pierwszy (SteamCommunity)](https://steamcommunity.com/app/346110/discussions/0/333656722964822410/)
- [Wątek drugi (Reddit)](https://www.reddit.com/r/Steam/comments/5cnjzf/content_file_locked/)

### Gra uruchomiła się z rozdzielczością większą niż rozdzielczość mojego monitora, przez co stała się niegrywalna.

Jeśli gra uruchomiła się z tym problemem, zamknij Quaver i przejdź do plików lokalnych steam gry.

Otwórz plik `quaver.cfg` i poszukaj opcji konfiguracyjnych `WindowHeight`, `WindowWidth` i `WindowFullScreen`. Kontynuuj, aby ustawić żądaną rozdzielczość okna. Następny krok jest opcjonalny, dobrym pomysłem byłoby ustawienie `WindowFullScreen` na False do czasu ponownego uruchomienia klienta, aby uniknąć dalszych problemów.

### Mój program antywirusowy wykrył Quaver jako złośliwe oprogramowanie

Wynika to z faktu, że pliki gry nie są podpisane cyfrowo w celu zapewnienia ich autentyczności, ponieważ wymaga to zakupu i utrzymania kosztów certyfikatu cyfrowego.

Aby uniknąć wykrycia gry Quaver przez program antywirusowy, należy dodać plik `Quaver.exe` lub katalog plików lokalnych do białej listy programu antywirusowego.