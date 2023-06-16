<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

En del av webbplatskoden är öppen källkod, välkommen att hjälpa till att optimera översättningen.

## front-end-kod

* [front-end-kod](https://github.com/xxai-art/web)
* [Språkpaket för webbplatsen som helhet](https://github.com/xxai-art/web/tree/main/i18n)
* [Språkpaket för inloggningsmoduler](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Webbplats flerspråkig dokumentation](https://github.com/xxai-doc)

Front-end-programmeringsspråket är [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , vilket lägger till några funktioner baserat på coffeescript-syntaxen, se [./coffee_plus.md](./coffee_plus.md) .

## Internationalisering av webbplatser och dokument

Bygg på följande 3 projekt

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Suffixet är `.mdt` , du kan använda syntaxen som liknar `<+ ./coffee_plus/import.js>` för att referera till externa filer, och generera markdown med suffixet `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Markdown-översättning kommer inte att översätta koder och länkar och cachelagrar översatta meningar. Om översättningen modifieras men originaltexten inte ändras, kommer inte modifieringen av översättningen att skrivas över om den körs igen.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Språkfiler för att översätta `yaml` genererade webbplatser.
