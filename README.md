# NER — Named Entity Recognition (simple version)

Same flat style as the POS notebook: plain Keras `Sequential` models, no extras.

**Task:** give every word a BIO entity tag (`B-per`/`I-per`, `B-geo`, `B-org`, ..., `O`).

**Data:** `data/NER.zip` — CSV with columns `Sentence #`, `Word`, `POS`, `Tag`.

**Notebook:** `simple_ner.ipynb` trains and compares three models:

| model | layer |
|---|---|
| `model1` | `LSTM` (baseline, left → right only) |
| `model2` | `Bidirectional(LSTM)` |
| `model3` | `Bidirectional(GRU)` |

Test accuracy, training time and parameter counts are compared with bar charts
(saved to `images/ner_comparison.png`).

## Install dependencies

This project uses [`uv`](https://docs.astral.sh/uv/). Install it first if you don't have it:

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# or with pip / pipx
pip install uv
```

Then install the dependencies (from `pyproject.toml` / `uv.lock`):

```bash
git clone <repo-url>
cd POSTagging
uv sync
```

`uv sync` creates a `.venv/` and installs everything, including:

- `tensorflow` — Keras models
- `numpy`, `pandas` — data handling
- `matplotlib` — figures
- `scikit-learn`, `tqdm` — helpers
- `ipykernel` — to run the notebook

## Run

```bash
uv run jupyter lab simple_ner.ipynb
```

(or open `simple_ner.ipynb` in VS Code / PyCharm and select the `.venv` interpreter)
