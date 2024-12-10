Testowy [link](test/test.md)
# Strona w budowie

# GISday2024
To repozytorium zawiera prezentacje wygłoszoną na wydarzeniu GISday 2024 na Uniwersytecie Łódzkim na wydziale Ekonomiczno - socjologicznym.
Prezentacja została podzielona na 3 części i zawiera informacje odnośnie użytkowania 3 narzędzi do analiz komunikacyjnych w środowisku GIS.
1. Narzędzia wbudowane w QGIS + wtyczki
2. OpenTripPlanner + R
3. Narzędzia symulacyjne VISSIM + TomTomMOVE

# Narzędzia wbudowane w QGIS + wtyczki
W pierwszej części prezentacji zostały omówione bazowe funkcje QGIS, takie jak korzystanie z [bufora](https://youtu.be/n2w32iDwDpw?si=88iRhpI_ni4KyV-j&t=508)
lub polecenia [service area](https://youtu.be/xSHN6FKHApk?si=gvFSLw6LsU4ENThG&t=315) w celu wyznaczenia realnej drogi do przystanku.

Następnie przedstawiona została funkcjonalność wtyczek [OpenRouteService](https://openrouteservice.org/), [Valhalla](https://github.com/valhalla/valhalla) oraz [TravelTime](https://traveltime.com/) 
w zakresie [routingu](https://mapsplatform.google.com/maps-products/routes/), tworzenia analiz sieciowych i izochron. Wszystkie wtyczki oferują wybór różnych rodzajów transportu przy wyznaczaniu izochrony, jednak tylko <ins>TravelTime</ins> daje możliwość wyboru generowania izochron od transportu publicznego. 
Niestety wadą tej wtyczki jest [bardzo mała ilość tokenów](https://docs.traveltime.com/qgis/about/reference-manual), którą możemy wykorzystywać do zapytań serwera. *Each API key has a quota of queries that can be done. Currently, for free keys, this is around 10 searches / minute. Once this quota is reached, all subsequent queries fail for the cooldown period*

Podsumowując, narzędzia wbudowane oraz wtyczki są to narzędzia szybko działające oraz bardzo proste w obsłudze. Ogarniczenia jakie dotyczą tych narzędzi to mała liczba zapytań do API i zależność od danych z zewnętrznego serwera oraz ograniczone możliwości zaawansowanych analiz multimodalnych.
Biorąc pod uwagę zalety oraz wady tych narzędzi znajdują one zastosowanie w prostych analizach oraz przy małym obszarze opracowania.

# OpenTripPlanner + R
W budowie
## Pobieranie danych
Przed przystąpieniem do analiz zostanie omówione w jaki sposób pozyskać dane potrzebne do przeprowadzenia obliczeń.

Potrzebne będą nam dwie podstawowe rzeczy
1. Dane o rozkładach jazdy przewoźników w formacie [GTFS](https://github.com/google/transit)
2. Mapa drogowa w formacie [osm.pbf](https://download.geofabrik.de/)

Dane o przewoźnikach możemy pozyskać z dwóch różnych źródeł
1. [Transitland](https://www.transit.land/)
2. [Mobility Database](https://mobilitydatabase.org/)
Ja swoje dane dla łodzi pobrałem z [tej strony](https://www.transit.land/feeds/f-u3jy-lodz)

Kiedy mamy dane dotyczące rozkładów jazdy następnym krokiem będzie pobranie informacji o sieci drogowej OSM z serwera [Geofabrik](https://download.geofabrik.de/). W tej analizie użyłem danych dla [województwa łódzkiego](https://download.geofabrik.de/europe/poland/lodzkie.html)

## Konfiguracja serwera OTP
Po pobraniu danych przejdziemy do konfiguracji serwera oraz środowiska.
Pierwszy krok to pobranie pliku aplikacji OTP w formacie .jar w wersji [1.5.0](https://github.com/opentripplanner/OpenTripPlanner/releases/tag/v1.5.0).
Do uruchomienia tej aplikacji potrzebne będzie nam środowisko [JAVA w wersji 8](https://www.oracle.com/java/technologies/downloads/#java8-windows)
Następnie potrzebujemy zainstalować język [R](https://cran.rstudio.com/bin/windows/) oraz interfejs [RStudio](https://posit.co/download/rstudio-desktop/)

Kiedy mamy pobrane i zainstalowane wszystkie komponenty przejdzmy do konfiguracji folderu w którym będziemy pracować. Powinniśmy stworzyć folder, do którego będziemy mieli szybki dostęp, bez polskich znaków i spacji w nazwie, ponieważ może to spowodować błąd w ścieżce dostępu. Ja swój folder stworzyłem w lokalizacji: `C:\Users\Michal\otp_data`. To będzie nasz folder główny z plikiem `.jar`, w tym folderze głównym tworzymy nowy folder `graphs`, folder nazwany taką nazwą jest rozpoznawany jako tzw. `router`, będzie nam to potrzebne w dalszej części analizy. W folderze `graphs` tworzymy nowy folder w którym będziemy przechowywać plik `gtfs.zip` i `.osm.pbf`. (**Plik z rozkładami jazdy musi zawierać w nazwie GTFS oraz musi mieć rozszerzenie .zip. Plik z mapą osm również musi być w formacie .osm.pbf**) Folder możemy go nazwać od nazwy analizowanej miejscowości np. `Lodz`, w takim wypadku nazwa `Lodz` stanie się nazwą `routera` i będzię można go w ten sposób wywołać. Struktura folderu powinna wyglądać w taki sposób:
```
/otp_data
    otp.jar
    /graphs
        /lodz
        lodz_gtfs.zip
        lodz.osm.pbf
```
Po skonfigurowaniu struktury folderu przejdziemy do uruchomienia aplikacji z command line, potrzebne będą nam do tego 3 podstawowe komendy
```
java -Xmx4G -jar otp.jar --build C:\Users\Michal\otp_data\graphs\lodz
```
Ta komenda buduje `graph` i zapisuje do pliku `.obj`, przechowywane są tam dane na temat sieci drogowej oraz nałożone trasy środków transportu publicznego

Następnie wpisujemy komende do uruchomienia serwera.
```
java -Xmx2G -jar otp.jar --router lodz --graphs graphs --server
```
Jako router wskazujemy folder `lodz`, parametr `--graphs` wskazuje w jakim folderze aplikacja ma szukać zapisanego graphu

Do dokończenia

## Skrypty w języku R

## Izochorny

## Czas dojazdu do wielu miejsc

## One-to-many analysis

# Narzędzia symulacyjne VISSIM + TomTom MOVE
W budowie

# Źródła
W budowie
Ta prezentacja napewno by nie powstała gdyby nie niesamowita praca wykonana przez użytkownika [marcusyoung](https://github.com/marcusyoung) i jego [bibliotekę do języka R](https://github.com/marcusyoung/otpr) 
oraz [poradnik jak korzystać z OTP](https://github.com/marcusyoung/otp-tutorial)
