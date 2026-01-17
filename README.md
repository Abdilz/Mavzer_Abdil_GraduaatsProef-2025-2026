# 🦷 AI-Gestuurd Callcenter voor Tandartspraktijken

> **Graduaatsproef Programmeren | HOGENT | Academiejaar 2025-2026**

## 📋 Overzicht

Dit project ontwikkelt een **AI-gestuurd inbound callcenter** voor tandartspraktijken. Het systeem automatiseert telefonische patiëntcommunicatie door gebruik te maken van:

- **Twilio** — Programmeerbare telefonie (spraakherkenning, Text-to-Speech)
- **OpenAI GPT-4o** — Natuurlijke taalverwerking met function calling
- **ASP.NET Core** — Backend API
- **Microsoft Azure** — Hosting en secrets management

### 🎯 Functionaliteiten

| Functie | Beschrijving |
|---------|-------------|
| 🔍 Klant opzoeken | Patiëntgegevens ophalen via telefoonnummer |
| ❌ Afspraak annuleren | Bestaande afspraak annuleren na bevestiging |
| 📅 Afspraak verzetten | Afspraak verplaatsen naar nieuw tijdstip |
| 📝 Wachtlijst | Patiënt toevoegen aan wachtlijst |
| 📞 Doorverbinden | Gesprek doorschakelen naar praktijk |
| 🌍 Meertalig | Nederlands, Engels en Frans |

---

## 📁 Projectstructuur

```
├── gradproef/              # 📄 LaTeX thesis (graduaatsproef)
│   ├── MavzerAbdilBP.tex   #    Hoofddocument
│   ├── inleiding.tex       #    Introductie
│   ├── standvanzaken.tex   #    Literatuurstudie
│   ├── methodologie.tex    #    Onderzoeksmethodiek
│   ├── implementatie.tex   #    Technische implementatie
│   ├── resultaten.tex      #    Resultaten & leerpunten
│   ├── conclusie.tex       #    Conclusie
│   └── gradproef.bib       #    Bibliografie
│
├── voorstel/               # 📝 Onderzoeksvoorstel
│   ├── MavzerAbdil-BPvoorstel.tex
│   └── voorstel-inhoud.tex
│
├── poster/                 # 🖼️ Conferentieposter
│
├── graphics/               # 📊 Afbeeldingen en diagrammen
│
├── fonts/                  # 🔤 Lettertypes (Montserrat, Fira)
│
├── docker/                 # 🐳 Docker build scripts
│
└── output/                 # 📦 Gecompileerde PDF's
```

---

## 🏗️ Architectuur

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Patiënt   │────▶│   Twilio    │────▶│  ASP.NET    │
│  (Telefoon) │◀────│  (Voice)    │◀────│  Core API   │
└─────────────┘     └─────────────┘     └──────┬──────┘
                                               │
                    ┌─────────────┐     ┌──────▼──────┐
                    │  TurnUp     │◀────│   OpenAI    │
                    │    API      │     │   GPT-4o    │
                    └─────────────┘     └─────────────┘
```

**Gespreksflow:**
1. Patiënt belt → Twilio ontvangt oproep
2. Twilio stuurt webhook naar ASP.NET Core
3. Spraak wordt getranscribeerd (Speech-to-Text)
4. OpenAI verwerkt input en bepaalt actie
5. Function calling voert actie uit (bijv. afspraak opzoeken)
6. AI formuleert antwoord → Twilio spreekt uit (Text-to-Speech)

---

## 🛠️ Technologieën

| Technologie | Versie | Doel |
|-------------|--------|------|
| .NET | 8.0 | Backend framework |
| ASP.NET Core | 8.0 | Web API |
| OpenAI API | GPT-4o | Taalverwerking & function calling |
| Twilio | Voice API | Telefonie & spraak |
| Azure App Service | — | Hosting |
| Azure Key Vault | — | Secrets management |
| Azure SQL Database | — | Opslag opnames & transcripties |
| GitHub Actions | — | CI/CD |

---

## 📄 Documenten

| Document | Beschrijving | Build |
|----------|-------------|-------|
| Graduaatsproef | Volledige thesis | `./make_thesis.sh` |
| Onderzoeksvoorstel | Research proposal | `./make_voorstel.sh` |
| Poster | Conferentieposter | `./make_poster.sh` |

---

## 🚀 Bouwen

### Vereisten

- LaTeX distributie (TeX Live of MikTeX)
- XeLaTeX compiler
- Biber voor bibliografie
- Geïnstalleerde fonts: Montserrat, Fira Code, Fira Math

### Lokaal bouwen

```bash
# Thesis compileren
./make_thesis.sh

# Onderzoeksvoorstel compileren
./make_voorstel.sh

# Poster compileren
./make_poster.sh
```

### Via Docker

```bash
docker build -t bpimg ./docker
docker run --rm -v "$PWD":/bp bpimg sh /bp/docker/render_thesis.sh gradproef
```

---

## 👤 Auteur

**Abdil Mavzer**  
📧 [abdil.mavzer@student.hogent.be](mailto:abdil.mavzer@student.hogent.be)  
🎓 Graduaat in het Programmeren — HOGENT

### Begeleiding

- **Co-promotor:** Jona Decubber (TurnUp)

---

## 📚 Bronnen

- [Twilio Voice Documentation](https://www.twilio.com/docs/voice)
- [OpenAI Function Calling](https://platform.openai.com/docs/guides/function-calling)
- [Azure Key Vault](https://docs.microsoft.com/azure/key-vault/)
- [ASP.NET Core Documentation](https://docs.microsoft.com/aspnet/core/)

---

## 📜 Licentie

Dit project is ontwikkeld in het kader van de graduaatsopleiding Programmeren aan HOGENT.

---

<details>
<summary>📖 LaTeX Sjabloon Informatie</summary>

### Lettertypes

Je hebt de volgende lettertypes nodig (meegeleverd in `fonts/`):

- Montserrat (officieel hoofdlettertype HOGENT huisstijl)
- Fira Code (monogespatieerde tekst)
- Fira Math (wiskundige formules)

### LaTeX Editor

Aanbevolen editors:
- [TeXstudio](https://www.texstudio.org/)
- [Visual Studio Code](https://code.visualstudio.com/) met LaTeX Workshop plugin
- [JabRef](https://www.jabref.org/) voor bibliografie

### TeXstudio configureren

- Build > Default compiler: `xelatex`
- Build > Default Bibliography Tool: `Biber`

</details>
