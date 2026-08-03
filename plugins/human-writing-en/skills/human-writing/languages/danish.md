# Danish writing guide

Brug denne guide til dansk prosa, der skal lyde skrevet af et menneske – ikke som engelske instrukser oversat ord for ord. Dansk arbejdspladssprog er direkte, uformelt, lavt i hierarki og praktisk.

## Grundprincipper

- **Skriv konkret:** Brug navne, datoer, tal, eksempler og klare handlinger.
- **Vælg hverdagsord:** Skriv "brug" før "anvend", og "er" før "fungerer som".
- **Brug uformelt "du" som standard:** Dansk arbejdspladssprog er lavt i hierarki. Vælg ikke "De", ceremoniel høflighed eller overformel distance, medmindre brugeren beder om det.
- **Brug verber før navneord:** Skriv "Vi optimerer koden" frem for "Vi foretager en optimering af koden".
- **Undgå engelsk syntaks:** Dansk tåler længere hovedsætninger, men tunge indskud, passiver og dash-tung rytme (—) får teksten til at lyde oversat.

## Ord, vendinger og mønstre med høj risiko

### Fjern i færdig prosa

- **Tomme overgange:** "Det er vigtigt at bemærke, at", "Som nævnt tidligere", "I en verden hvor", "Ydermere", "Desuden".
- **Buzzwords og metaforer:** dybdegående, robust, sømløs, synergi, rejsen, landskab, økosystem, transformation, afgørende, essentiel.
- **Engelske talemåder oversat direkte:** "på den samme side" (brug *enige* eller *afstemt*), "i slutningen af dagen" (brug *når alt kommer til alt*), "gå den ekstra mil" (brug *gøre lidt ekstra*).
- **Stablede forbehold:** "Det kunne potentielt muligvis..." -> Skriv det direkte: "Det kan...".

### Substantiveringer
AI på dansk skjuler ofte handlinger i tunge navneord. Find mønstre som "foretage en", "gennemføre en", "udføre en" og "ske en", og skriv handlingen som et verbum.

- `foretage en optimering af` -> **optimere**
- `gennemføre en implementering af` -> **implementere**
- `foretage en vurdering af` -> **vurdere**
- `der sker en forbedring af svartiden` -> **svartiden bliver bedre** eller **svartiden falder**

### Direkte erstatninger

- `fungerer som` / `agerer som` / `tjener som` -> **er**
- `med henblik på` -> **for at**
- `i forhold til` -> **om** / **for** / **når det gælder**
- `det anbefales, at man` -> **vi anbefaler** (eller direkte bydeform)
- `implementere en løsning, der muliggør` -> skriv hvad løsningen gør

## Partikler og naturlig stemme

Brug modalpartikler som *lige*, *bare*, *jo* og *vel* til at skabe naturlig mundtlighed i uformelle formater:

- "Kan du **lige** kigge på PR'en?"
- "Vi sender den **bare** i morgen."

*Bemærk:* Undlad partikler i formelle dokumenter, READMEs, arkitekturnotater og beskeder til eksterne.

## Kontekst og register

Vælg først relation og format. Start med *du* i intern og almindelig ekstern kommunikation. Skift kun til mere formel tone, hvis teksten er juridisk, myndighedsrettet, meget ceremoniel eller brugeren eksplicit beder om det.

### 1. Team-beskeder og mails (uformel og direkte)

Gå direkte til sagen. Afslut med en konkret handling, ikke en tom høflighedsfrase.

- ❌ *"Kære team. Jeg håber, I har det godt. Det er vigtigt at bemærke, at vi står over for en potentiel udfordring..."*
- ✅ *"Deployment fejler i staging, fordi migreringen mangler rettigheden `ALTER`. Lars kigger på det. Kan en af jer genstarte pipelinen bagefter?"*

### 2. Wiki, README og dokumentation (præcis og struktureret)

Skriv for en læser, der skal løse et problem nu.

- ❌ *"Denne guide giver et dybdegående overblik over, hvordan man nemt og effektivt navigerer i opsætningen."*
- ✅ *"Denne guide viser, hvordan du kører projektet lokalt og opretter en testbruger."*

### 3. Rapporter og blog (rytme og fakta)

Vis resultat og fremdrift med tal og eksempler frem for adjektiver.

- ❌ *"Dette banebrydende initiativ viser, hvordan samarbejde kan skabe markante resultater."*
- ✅ *"Tre teams brugte samme release-tjekliste i juni. Antallet af rollbacks faldt fra fem til én."*

## Dansk self-check

1. Lyder det som en dansk kollega, der taler, eller som en engelsk oversættelse?
2. Er verbale handlinger gemt væk i lange navneord (substantivering)?
3. Er "det er vigtigt at bemærke" eller andre tomme fyldord fjernet?
4. Er tonen direkte og tilpasset modtageren uden stiv formelhed?
5. Er modalpartikler (*jo, lige, bare*) brugt rigtigt – og kun hvor det giver mening?