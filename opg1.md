# Guide til lansering av egen npm-pakke 📦

1. [Opprett npm bruker](https://www.npmjs.com/signup)
2. Test brukeren din med `npm login`: [dokumentasjon](https://docs.npmjs.com/creating-a-new-npm-user-account#testing-your-new-account-with-npm-login)
3. I terminalen navigerer du til mappen du har lyst til å ha repoet. Nå skal du et viktig navn, nemlig navnet på hva pakken din skal hete på npmjs. Det er derfor litt viktig å ta en titt på disse små [retningslinjene](https://docs.npmjs.com/package-name-guidelines) før du skriver `mkdir ditt-unike-pakkenavn`.
4. Opprett en `package.json` med kommandoen `npm init` og fyll ut valgfritt.
5. I `package.json` kan du legge til `“main”: “./dist/index.ts”`. Dette forteller hvilken bygd TypeScript-fil som er startpunktet når noen importerer pakken din. Legg deretter til `"types": "./dist/index.d.ts"`. Dette gjør du får å fortelle hva som er typedefinisjonene.
   </br>📚: Les mer om `.d.ts`-filer her i [TypeScript sin egen dokumentasjon](https://www.typescriptlang.org/docs/handbook/2/type-declarations.html#:~:text=.-,d.,our%20own%20declaration%20files%20later.).
   Dist-mappen inneholder kompilerte filer og genereres i byggeprosessen. Enda mer lesestoff om [declaration-files](https://www.typescriptlang.org/docs/handbook/declaration-files/dts-from-js.html)
6. I `package.json` kan du legge på nøkkelord som `author`, `license`, `keywords`, `bugs`, `homepage`, `repository`. Dette blir referanser som brukere kan se på npm-siden til pakken din. Prøv å fylle ut disse og sjekk ut senere 😁.
7. `npm install -D typescript` for å kunne skrive TypeScript. Dette gjør vi for å kunne konvertere `.ts`-filer til `.js`-filer. Det er for å kunne sjekke typer under utvikling og generering av `.d.ts` filer som vi så på i steg 5.
8. Opprett en `.gitignore` og legg til `node_modules` og `dist` ettersom disse ikke er vits å versjonskontrollere genererte filer.
9. For å kompilere koden til JavaScrip trenger vi en `tsconfig.json`-fil. Dette gjør vi med kommandoen `npx tsc --init`. Hvis du har TypeScript globalt på maskinen trenger du ikke ha med `npx`. `tsc` er et TypeScript cli som lar deg kompilere fra TypeScript til JavaScript.
   </br>a. Legg til `"include": ["src"]` som forteller `tsc` hvilken kode du skal kompilere.
   </br>b. `"exclude": ["node_modules", "dist"]` på utsiden av compilerOptions. Dette er paths som du ikke vil kompilere. Legg til `"outDir": "./dist"`, i compilerOptions. Det er her koden blir plassert.
10. TypeScript kompilerer seg ikke selv, så nå kan du kjøre `npm run build`. Inne i `package.json` skal du ha `tsc` som kompilerer koden med de innstillingene du nettopp konfigurerte.
11. `git init` på rot-nivå i pakken etterfulgt av `git remote add origin git://git-remote-url`.
12. `npm publish` og sjekk at du har publisert pakken din på npmjs.com!
13. Gjør en endring og gjør en npm publish igjen, se hva som skjer! Kan `npm version patch` hjelpe?
14. Kan dere dokumentere hvordan man bruker pakken i readme-en og få sidemannen til å ta den i bruk? 😎

Gratulerer, nå har du laget og publisert en unscoped public package! 🎉🥳🍾

## 📚[Scopes](https://docs.npmjs.com/about-scopes)

Her er det litt mer lesestoff for de som vil se hva de ulike pakke-scopsene er 🤓

- [unscoped public packages](https://docs.npmjs.com/creating-and-publishing-unscoped-public-packages)
- [scoped public packages](https://docs.npmjs.com/creating-and-publishing-scoped-public-packages)
- [private packages](https://docs.npmjs.com/creating-and-publishing-private-packages)
