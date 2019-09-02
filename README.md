# React-Tutorial
Nauka React.js

## Lekcja 1 - EcmaScript

Wersje JavaScript i Kompatybilność przeglądarek

JavaScript jest językiem rozwijanym przez specjalną grupę ludzi, ale wiele nowych rzeczy pochodzi bezpośrednio od użytowników (deweloperów).

W zależnośc od przeglądarki lub innej aplikacji, która korzysta z JavaScript do wykonania jakiś rzeczy wersja JS może się różnić i wiele rzeczy może nie być dostępne.

Dla przykładu:

```javascript
const foo = () => {};
```

Które jest równoznaczne z:

```javascript 1.8
function foo() {}
```

Może nie być dostępne. Wszystkie nowe właściwości często są oznaczane jako `es8+` lub `esnext`.

Skrót ten pochodzi od `EcmaScript`, hipotetycznego języka, kórego JavaScript jest wersja. Jest to coś w rodzaju "komunikatora internetowego", którego implementacją jest Messenger albo Slack.

Ze względu na ogólnie przyjęte podejście wspierania najpopularniejszych nowoczesnych przeglądarek wspiera się tzw 99% rynku które stanowi:

* Firefox
* Google Chrome
* Safari
* Internet Explorer 9+

Safari jest w tej chwili najbardziej opóźnioną przeglądarką i wiele najnowocześniejszych rozwiązań tam nie znajdziesz.

Jest to przy okazji najczęściej wybierana przeglądarka użytkowników Mac'ów, więc świat frontendowy jest zmuszony się dostosować.


## Lekcja 2 - docker & extrenal drive system

### Docker

Prawie nikt w biznesie nie korzysta z Windows. Jest to tak daleko posunięte, że wiele rzeczy zwyczajnie nie jest dostępnych na Windows.

Nie znajdziesz wiele paczek z gotowym kodem (tzw. biblioteki), a czasem jesteś zmuszony kozystać z zastępników.
W biznesie jest to jednak nieakceptowane ponieważ produkcyjna aplikacja (taka widziana już przez użytkowików) musi być stabilna i przetestowana.

Nikt nie będzie kupował Windows tylko po to żeby sprawdzić czy mu coś działa albo żeby postawić serwer skoro Linux jest darmowy.

Jakimś rozwiązaniem jest Docker. Jest to aplikacja, która w pewnym stopniu instaluje Linux na maszynie i uruchamia wewnątrz już działającego systemu operacyjnego.

[Instalacja docker'a](https://docs.docker.com/docker-for-windows/install/) 

Niestety mimo, że Docker jest już standardem w świecie programistów jego wsparcie jest ograniczone na Linux.

### External Drive

Niemal na pewno nikt nie uzna Cię za dobrego kandydata bez znajomości systemu Unix (czy to iOS, czy Linux).
Jest to bardzo ważne wymaganie ponieważ zakres narzędzi koniecznych do stworzenia działającego systemu jest nieporównany.

Windows jest oparty na aplikacjach okienkowych, które są zbyt ciężkie i zbyt wolne dla odpowiedzi w czasie rzeczywistym. 

Dlatego bardzo ważne jest posiadanie systemu, na którym przynajmniej da się ćwiczyć. Lnux można bez problemów postawić jako "sąsiada" Windows na tym samym dysku, tej samej maszynie.

Można alternatywnie zainstalować go na dysku zewnętrznym, podłączać się kiedy jest potrzeny i restartować komputer.

Proponuje Ubuntu ponieważ jest obecnie uważany za najbardziej User-friendly. W obecnym stanie użytkownik nie powinien odczuć żadnej różnicy jeśli nie gra w najnowsze gry i nie używa Steam żeby je odpalić.
MS Office jest dostępny z poziomu przeglądarki [ms office 365](https://www.office.com/) w ramach już posiadanej licencji.

Nie głupim pomysłem jest też zakupienie pendrive'a o pojemności 128GB i więcej, zainstalowanie na nim Ubuntu i traktowanie tego jako środowisko do nauki.

[Instalacja Ubuntu na USB](https://linuxhint.com/run-ubuntu-18-04-from-usb-stick/) 

## Lekcja 3 - babeljs, webpack, yarn

* Budowanie aplikacji

Jak już masz świeżo zainstalowany Linux możesz spokojnie przejść do pracy.

Zacznijmy od zainstalowania podstawowych programów.

Wciśnij: `Ctrl + Alt + T`

Powinien pojawić się terminal, jest to okienko z czarnym tłem w którym możesz pisać.
To okienko samo w sobie posiada wbudowany język programowania `Bash`.
Nie jest on bardzo zaawansowany, ale z pomocą dodatkowych aplikacji jesteś w stanie zautomatyzować prawie wszystko.

`Bash` lub jego podobne języki zawsze są dostępne z w twoim systemie i służą jako podstaowe narzędzie.

Teraz z pomocą narzędzia zwanego `apt-get` zainstalujemy aplikacje, które przydadzą się później

```bash
sudo apt-get update
sudo apt-get install git build-essential libssl-dev libcurl4-gnutls-dev libexpat1-dev gettext unzip curl nodejs
```

Rzeczy które zostaną zainstalowane:

* `git` - narzędzie do śledzenia zmian w kodzie
* `unzip` - narzędzie do rozpadkowywania plików zip bez okienek, `zip` (do tworzenia plików zip) zostanie zainstalowane przy okazji
* `curl` - narzędzie do pobierania zawartości z internetu i "wydrukowania" go w postaci tekstu
* `libXXXXXX` - szereg wielu bibliotek niezbędnych do pracy, w tym szyfrowanie itd
* `nodejs` - javascript w systemie operacyjnym

Dla wygodnej pracy ze środowiskiem JS zainstalujemy `yarn`. Jest to narzędzie którym będziemy odpalać kod w systemie i instalowaniać biblioteki używane przez twoją przyszłą aplikację.
Żeby jednak nie było za łatwo zrobisz to sam.

Przejdź do [https://yarnpkg.com/lang/en/docs/install/#debian-stable](https://yarnpkg.com/lang/en/docs/install/#debian-stable)
i postępuj zgodnie z poleceniami. Dokładnie czytaj wszystkie komunikaty.

## Klucz publiczny

Klucz publiczny i prywatny do specjalny ciąg znaków, które umożliwiają potwierdzenie twojej tożsamości.
Złamanie zabezpieczeń takiego mechanizmu jest niezwykle trudne i nieopłacalne. 

Utwórz klucz publiczny, hasła pozostaw puste. Większość rzeczy

```
ssh-keygen -o
```

Właśnie powstały 2 pliki `id_rsa` i `id_rsa.pub`.
Pierwszy jest tajnym plikiem do którego dostęp powinieneś mieć tylko ty i **NIGDY** go nikomu nie udostępniać, drugi może zostać udostępniony każdemu.
Skrót `pub` oznacza `public`, to jest twój klucz publiczny. 

Teraz możesz dodać swój klucz publiczny do github'a i przestać się przejmować logowaniem z poziomu terminala.

```
cat ~/.ssh/id_rsa.pub
```

`cat` weźmie zawartość pliku i wydrukuje ją w terminalu, skopiuj to i wklej tutaj:

[https://github.com/settings/keys](https://github.com/settings/keys).
Github automatycznie sprawdzi wklejone dane i doda nowy klucz publiczny.

Pisz jeśli będziesz miał problemy lub pytania
