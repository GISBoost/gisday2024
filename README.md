# Strona w budowie

# GISday2024
To repozytorium zawiera prezentacje wygłoszoną na wydarzeniu GISday 2024 na Uniwersytecie Łódzkim na wydziale Ekonomiczno - socjologicznym.
Prezentacja została podzielona na 3 części i zawiera informacje odnośnie użytkowania 3 narzędzi do analiz komunikacyjnych w środowisku GIS.
1. Narzędzia wbudowane w QGIS + wtyczki
2. OpenTripPlanner + R
3. Narzędzia symulacyjne VISSIM + TomTomMOVE

# Narzędzia wbudowane w QGIS + wtyczki
W pierwszej części prezentacji zostały omówione bazowe funkcje QGIS, takie jak korzystanie z [bufora](https://docs.qgis.org/3.34/en/docs/gentle_gis_introduction/vector_spatial_analysis_buffers.html)
lub polecenia [service area](https://youtu.be/xSHN6FKHApk?si=gvFSLw6LsU4ENThG&t=315) w celu wyznaczenia realnej drogi do przystanku.

Następnie przedstawiona została funkcjonalność wtyczek [OpenRouteService](https://openrouteservice.org/), [Valhalla](https://github.com/valhalla/valhalla) oraz [TravelTime](https://traveltime.com/) 
w zakresie [routingu](https://mapsplatform.google.com/maps-products/routes/), tworzenia analiz sieciowych i izochron. Wszystkie wtyczki oferują wybór różnych rodzajów transportu przy wyznaczaniu izochrony, jednak tylko <ins>TravelTime</ins> daje możliwość wyboru generowania izochron od transportu publicznego. 
Niestety wadą tej wtyczki jest [bardzo mała ilość tokenów](https://docs.traveltime.com/qgis/about/reference-manual), którą możemy wykorzystywać do zapytań serwera. *Each API key has a quota of queries that can be done. Currently, for free keys, this is around 10 searches / minute. Once this quota is reached, all subsequent queries fail for the cooldown period*

Podsumowując...

# OpenTripPlanner + R
W budowie

# Narzędzia symulacyjne VISSIM + TomTom MOVE
W budowie

# Źródła
W budowie
Ta prezentacja napewno by nie powstała gdyby nie niesamowita praca wykonana przez użytkownika [marcusyoung](https://github.com/marcusyoung) i jego [bibliotekę do języka R](https://github.com/marcusyoung/otpr) 
oraz [poradnik jak korzystać z OTP](https://github.com/marcusyoung/otp-tutorial)
