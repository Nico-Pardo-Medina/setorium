# Setorium — Mushroom Species Identifier

A web application that identifies mushroom species from a photo and tells you whether they are edible, toxic, or deadly. Upload an image, get the top-2 predictions with confidence scores, and detailed information about each species — habitat, season, and edibility.

Built as a team project by three people: Sheila Santos Rosell (model training), Nico Pardo Medina (backend & data pipeline), and Héctor Martínez (frontend & deployment). The app was live on Heroku until 2022, when Heroku discontinued its free tier.

---

## How it was built

The project covers the full ML pipeline from data collection to production deployment:

1. **Data collection** — a Selenium scraper downloaded labelled mushroom images from the web to build the training dataset
2. **Model training** — transfer learning on MobileNetV2, fine-tuned and evaluated across multiple iterations on 15 mushroom species
3. **Backend** — Flask app serving predictions with a `Mushroom` data class and confidence-based UX logic (low confidence → hedged response, ambiguous top-2 → both shown, clear result → definitive answer)
4. **Frontend** — image upload UI, styled results cards with species details, toxicity colour-coding (green/orange/red)
5. **Deployment** — deployed to Heroku via `gunicorn` + `Procfile`

---

## Species covered (15)

| Species | Common name | Edibility |
|---|---|---|
| Agaricus campestris | Champiñón silvestre | Edible |
| Amanita bisporigera | Ángel de la muerte | **Deadly** |
| Amanita caesarea | Huevo del rey | Edible |
| Amanita muscaria | Matamoscas | Toxic |
| Boletus edulis | Boleto de calabaza | Edible |
| Boletus satanas | Corvall del demoni | Toxic |
| Cantharellus cibarius | Rebozuelo | Edible |
| Cortinarius orellanus | Cortinario de montaña | **Deadly** |
| Gyromitra esculenta | Falsa colmenilla | Toxic |
| Hygrophorus russula | Rovellón escarlata | Edible |
| Lactarius deliciosus | Níscalo | Edible |
| Lycoperdon perlatum | Pedo de lobo | Edible (with care) |
| Omphalotus olearius | Seta del olivo | Toxic |
| Pleurotus eryngii | Seta de cardo | Edible |
| Russula mariae | — | Edible |

---

## Running locally

**Requirements:** Python 3.9+, pip

```bash
git clone https://github.com/Nico-Pardo-Medina/webapp.git
cd webapp
pip install -r requirements.txt
python main.py
```

Then open `http://localhost:5000` in your browser.

---

## Limitations

- **15 species only** — the model will attempt a prediction on any mushroom image but accuracy drops significantly outside the trained species.
- **Not a safety tool** — do not use this to decide whether to eat a wild mushroom. It is a demonstration project.
- **Heroku demo no longer live** — the free Heroku tier was discontinued in November 2022.
