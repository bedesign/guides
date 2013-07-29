# Huusufgoobe Büechli

## 1. Terminal öffnen:

* Mac OS X: Öffne Spotlight, tippe Terminal und klicke auf die Terminal Applikation.
* Windows: Klicke Start und tippe im Suchfeld „Command Prompt“, klicke danach auf „Command Prompt with Ruby on Rails“ um das Terminal zu öffnen.
* Linux (Ubuntu): Suche nach dem  Terminal in der dash und klicke auf Terminal.

Als nächstes tippe folgende Befehle im Terminal:

```
mkdir projects
cd projects
rails new ferienpass
cd ferienpass
rails server
```

Geh in den Browser deiner Wahl und öffne `http://localhost:3000`.
Nun solltest du die “Welcome aboard” Seite sehen, was bedeutet, dass dein neues Projekt korrekt funktioniert.

Drücke **CTRL-C** im terminal um den Server zu beenden.

## 2. Erstelle das Task Gerüst

Nun werden wir die Rails `scaffold` Funktion nutzen um deine erste Applikation zu erstellen.
Diese erlaubt dir eine Task Liste zu erstellen in welcher zu Tasks hinzufügen, ändern, ansehen und entfernen kannst.

```
rails generate scaffold task title:string description:text due_date:date status:boolean
rake db:migrate
rails server
```

Öffne `http://localhost:3000/tasks` in deinem Browser.
Klicke ein wenig herum und teste was du mit den wenigen Befehlen im Terminal erstellt hast.

Klicke **CTRL-C**  um den Server wieder zu beenden.

## 3. Design

Um das Design ein wenige schöner zu gestalten werden wir das Twitter Bootstrap Projekt verwenden. Dies tun wir folgendermassen:

Öffne `app/views/layouts/application.html.erb` in deinem text editor füge oberhalb dieser Zeile

    <%= stylesheet_link_tag "application", media: "all", "data-turbolinks-track" => true %>

folgende Zeile ein

    <link href="//netdna.bootstrapcdn.com/twitter-bootstrap/2.3.2/css/bootstrap-combined.min.css" rel="stylesheet">

und ersetze:

    <%= yield %>

mit

```ruby
<div class="container">
  <%= yield %>
</div>
```

Nun fügen wir eine Navigation zum Layout hinzu. Dafür fügen wir unter <body> folgendes hinzu:

```html
<div class="navbar navbar-fixed-top">
  <div class="navbar-inner">
    <div class="container">
      <a class="brand" href="/">Husufgoobe Büechli</a>
      <ul class="nav">
        <li class="active"><a href="/tasks">Tasks</a></li>
      </ul>
    </div>
  </div>
</div>
```

und füge vor `</body>` folgendes ein

```html
<footer>
  <div class="container">
    Ferienpass 2013
  </div>
</footer>
```

Nun wollen wir das Design der Tasks Tabelle ändern. Öffne `app/assets/stylesheets/application.css` und füge folgendes ein:

```css
body { padding-top: 100px; }
footer { margin-top: 100px; }
table, td, th { vertical-align: middle !important; border: none !important; }
th { border-bottom: 1px solid #DDD !important; }
```

Refresh deinen Browser und sehe was sich geändert hat. Nun kannst du auch gerne noch weitere Änderungen am CSS vornehmen um zu sehen wie die Seite reagiert.

Eine Übersicht über die CSS Funktionen findest du auf dieser Seite: http://de.selfhtml.org/css/

## 4. Routes

Wenn du `http://localhost:3000` öffnest wird dort immer noch die  “Welcome aboard” Seite angezeigt.
Um dort direkt diene Husufgoobe Büechli Seite anzuzeigen machen wir folgendes:

Öffne `config/routes.rb` und füge nach der ersten Zeile folgendes hinzu:

    root :to => "tasks#index"

Teste die Änderungen indem du `http://localhost:3000` in deinem Browser öffnest.
Anstelle der "Welcome aboard" Seite solltest du nun die Indexseite aller deiner Hausaufgaben sehen.