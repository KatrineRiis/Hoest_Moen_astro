# Teknisk Dokumentation: Tema09_Høst Møn

## Om projektet:

MMD - 2. semester, Tema 9
I dette projekt udvikler vi et redesign af festivallen “Høst Møn”s website.
Løsningen udvikles i programmet Astro, der har den fordel at gøre det nemmere at samarbejde om en kode da Astro understøtter “Komponenter” .
I løsningen gøres der også brug af vores eget API, som er udviklet ved hjælp af SupaBase. Her udtrækkes relevant information om artister såsom: Artistnavn, link til SoMe og Spotify, OmArtisten mm.
Disse hentes ind, under program, og sørger for at der nemt og overskueligt kan tilføjes flere artister som tiden mod festivallens start skrider frem.

## Navigationen af vores løsning:

- Forside / program: Her finder man også programmet, klik på en kunstner for at læse mere.
- Menu med punkterne: Program, Bliv frivillig, Praktisk, Om os og Billetter.
- Under praktisk finder man en undermenu med punkterne: Måltidet, Overnatning, Pladsen og Transport, hvor man kan læse om relevant information omkring festivallen.
- Bliv frivillig indeholder en tekst bid om hvordan man bliver frivillig på festivallen og hvem man skal kontakte.
- Yderligere en side med “Om Os” som også indeholder festivallens tideligere plakater.
- Footer med links til SoMe og kontakt oplysning.

## Projekt mappe opsætning

### Tema09_hoest_moen/

Her er standard astro filer udeladt.

```bash
├── dist/
│
├── public/
│   ├── icons/
│   ├── images/
│
├── src/
│   ├── assets/
│   │   └── images/
│   │
│   ├── components/
│   │   ├── ArkivButton.astro
│   │   ├── ArkivPoster.astro
│   │   ├── PraktiskSection.astro
│   │   ├── PraktiskSectionRev.astro
│   │   ├── CircleElement.astro
│   │   └── Heroimg.astro
│   │
│   ├── layout/
│   │   └── Layout.astro
│   │
│   ├── pages/
│   │   ├── index.astro
│   │   ├── blivFrivillig.astro
│   │   ├── praktisk.astro
│   │   └── omOs.astro
│   │
│   └── styles/
│       └── global.css
│
├── .env
├── .gitignore
└── README.md

```

## Installation af Astro Projekt

- Klon repository fra github og indsæt i Vscode.
- Gem mappen i roden af computeren.
- Åben terminalen og kør “npm install”
- Kør sitet ved at skrive “npm run dev” i terminalen.

## Filbeskrivelser:

Alle astro pages:

- index.astro - forsiden med program oversigt.
- blivFrivillig.astro - information og kontakt om frivillig.
- praktisk.astro - Samlet overblik over praktiske informationer.
- omOs.astro - kort beskrivelse om Høst Møn og overblik over tideligere plakater.

## Alle Astro Components filer:

- ArkivButton.astro - knappen der bruges på omOs til at fremvise forrige plakater
- ArkivPoster.astro - Layoutet til plakaterne.
- PraktiskSection.astro - Section layout til Praktisk
- PraktiskSectionRev.astro - Reversed section layout til praktisk.
- CircleElement.astro - Et visuelt element der genbruges på flere sider
- Heroimg.astro - Baggrundsbilledet der skal bruges på flere sider

## .env

Denne fil indeholder en nøgle (“SUPABASE_PUBLISHABLE_KEY”) der skal bruges når man vil tilgå vores SupaBase Api.Derudover indeholder den også URL’en til vores Database.

## .gitignore

Denne fil indeholder forskellige elementer der ikke skal lægges op i github når der publishes en branch. Her i blandt er også .env, da nøglen ikke skal lægges og være public.

## dist

Denne fil fungerer som en building mappe. Når Astro indhenter data fra et Api til en side omhandlende et enkelt produkt, artist, eller event, som skal fungere dynamisk, bygger Astro alle siderne som Html sider og placerer dem i mappen dist. Dette gøres ved i terminalen at skrive. npm run build.

## Sådan fungerer koden:

Koden fungerer ved at “importe” komponenter ind i omOs-osv. Astro
Komponenterne er stylet i sin egen fil, hvilket er smart hvis farven, størrelsen eller andet, skal ændres alle steder komponenten er brugt.

Alle astro.pages er bygget op i det samme layout. Dette fungerer på samme måde som komponenter. Da alle pages skal indeholde den samme menu, burger menu og footer, mindsker det sandsynligheden for at man kommer til at overwrite en menu style på sin egen html side. Samtidig er det også smart hvis man skal ændre i menuen, da det her kun behøver at gøres 1 sted for at det retter sig på alle sider.

Derudover har vi oprettet en global.css der er linket ind i layout komponenten. Denne fil indeholder styles på elementer der går igen på alle sider:

- Font
- Reset (fjerner browserens default styles)
- Style af Menu og Footer
- farve variable

## Billede behandling:

Astro indeholder et indbygget <Image/> tag der gør det nemmere at optimere og styre billeder. Igennem dette tag er det muligt at komprimere og optimere billeder samt ændre dem til WebP formatet.
Dette er af væsentlig betydning, da ikke-optimerede og komprimerede billeder har flere uhensigtsmæssige konsekvenser:

- Gøre siden langsom at loade
- Bruge unødvendigt meget data på mobil
- Give dårlig brugeroplevelse
- Skade SEO-ranking

Det bruges ved at importere Images tagget i mellem fences: import { Image } from "astro:assets";

Dernæst importeres images fra assets mappen: import food3 from "../assets/praktisk_img/food3.webp";

Dernæst kan det bruges i den ønskede størrelse, filformat, quality osv.

```bash
<Image slot="image" src={food3} width={600} quality={85} format="webP" alt="billede af pladsen omhandlende måltidet" />
```

## Navngivning:

Vi har igennem projektet forsøgt at navngive vores mapper, filer, og branches så tydeligt som muligt.

 

### camelCase:

- Gør koden ensartet
- Gør koden lettere at læse

### Eksempler på kommentarer:

- const id = `pop-${text}`; /_ID til dialog/popover img_/
  {/_ inline JS _/}
- <!--Font-->

### Eksempler på branches:

- Praktisk_styling
- Layout_setup
- Clean_up-Oliver
- omOs_v2

## SupaBase (h2):

Supabase er et program, der giver mulighed for at oprette og arbejde med en database.
Vores data organiseres i tabeller med kolonner, som så kan hentes i projektet ved hjælp af fetch. Det gør det nemt at tilføje nyt indhold, da det blot skal oprettes i databasen og derefter automatisk kan vises på websitet.

### kolonner som vi bruger i denne opgave:

- kunstner
- kunstnerinfo
- spotifylink
- instagramlink
- poster

## Branches og hvordan de bruges:

Hver gang man starter på et nyt element i koden oprettes en branch fra Master. Dette gør det muligt at samarbejde om en kode uden at forstyrre hinandens arbejde og derved undgå merge conflicts.
Eksempler på branches:

- Praktisk_styling
- omOs_v2

Når et element er færdig og virker, commites det og pushes til GitHub hvorefter ens ændringer merges ind i Master. Herefter skifter man, i VsCode, tilbage i Master, synkroniserer (push & pull), laver en ny branch hvorefter punkterne gentages.

## Udfordringer undervejs

Nogle af udfordringerne vi har oplevet undervejs har bl.a. bestået af problemer om “scoped” css fra komponenterne. Altså vi forsøgte at gøre vores cirkel_element til en komponent med <style> kun bestående af visuel styling. Dette betød at når komponenten blev brugt var det ikke muligt at ændre dens layout-styling på siden med (f.eks justify_self:)

### Løsninger

Løsningen på dette problem blev at pakke komponenten ind i en wrapper (div) og style på den i stedet for på selve komponenten

### Mulige forbedringer

Mulige forbedringer undervejs, kunne have været et bedre overblik over hvilke elementer der skulle være komponenter. Det ville have hjulpet os til ikke at lave dobbelt arbejde, ved først at skrive det ind i vores page og derefter flytte det til en komponent.

## Gruppemedlemmer

- Katrine
- Donna
- Mai
- Oliver
