<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Det rekommenderas att installera nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) först och sedan `direnv allow` efter att ha gått in i katalogen ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) kommer att köras automatiskt efter att ha gått in i katalogen).

Betydelsen är: kinesisk översättning till japanska, koreanska, engelska, engelsk översättning till alla andra språk. Om du bara vill stödja kinesiska och engelska kan du bara skriva `zh: en` .

Betydelsen är: kinesisk översättning till japanska, koreanska, engelska, engelsk översättning till alla andra språk. Om du bara vill stödja kinesiska och engelska kan du bara skriva `zh: en` .

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

### Instruktioner för automatisering av dokumentöversättning

Se kodförrådet [xxai-art/doc](https://github.com/xxai-art/doc)

Det rekommenderas att installera nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) först och sedan `direnv allow` efter att ha gått in i katalogen ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) kommer att köras automatiskt efter att ha gått in i katalogen).

För att undvika den stora kodbasen översatt till hundratals språk skapade jag en separat kodbas för varje språk och skapade en organisation för att lagra kodbasen

Genom att ställa in miljövariabeln `GITHUB_ACCESS_TOKEN` och sedan köra [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) skapas kodförrådet automatiskt.

Naturligtvis kan du också lägga den i en kodbas.

Översättningsskriptreferens [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Skriptkoden tolkas enligt följande:

[bunx](https://bun.sh/docs/cli/bunx) är en ersättning för npx, vilket är snabbare. Självklart, om du inte har bun installerat kan du använda `npx` istället.

`bunx mdt zh` återger `.mdt` i zh-katalogen som `.md` , se de 2 länkade filerna nedan

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` är kärnkoden för översättning (om du bara har `nodejs` installerade, men `bun` och `direnv` inte är installerade, kan du också köra `npx i18n` för att översätta).

Den kommer att analysera [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , konfigurationen av `i18n.yml` i detta dokument är som följer:

```
en:
zh: ja ko en
```

Betydelsen är: kinesisk översättning till japanska, koreanska, engelska, engelsk översättning till alla andra språk. Om du bara vill stödja kinesiska och engelska kan du bara skriva `zh: en` .

Den sista är [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , som extraherar innehållet mellan huvudtiteln och den första undertiteln i varje språks `README.md` för att generera en post `README.md` . Koden är väldigt enkel, du kan titta på den själv.

Google API används för fri översättning. Om du inte kan komma åt Google, konfigurera och ställ in en proxy, som:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Översättningsskriptet kommer att generera en översatt cache i `.i18n` -katalogen, kontrollera den med `git status` och lägg till den i kodförrådet för att undvika upprepade översättningar.

Kör `bunx i18n` varje gång du ändrar översättningen för att uppdatera cachen.

Om originaltexten och översättningen ändras samtidigt kommer cachen att förväxlas, så om du vill ändra kan du bara ändra en och sedan köra `bunx i18n` för att uppdatera cachen.
