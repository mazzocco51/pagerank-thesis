# PageRank: Markov Chains and GPU Computing

Experiments accompanying Marco Mazzocco's bachelor's thesis at Sapienza University of Rome (2026).

[Website](https://mazzocco51.github.io) · [Contact](mailto:mazzocco.dev@gmail.com)

Open **[PageRank_Experiments.ipynb](PageRank_Experiments.ipynb)**. It contains all source code for CPU/GPU power iteration, endpoint Monte Carlo, CUDA sparse kernels, convergence experiments and Flickr contact recommendation. No separate research scripts are needed.

## Quick start

1. Open the notebook in Jupyter or upload it to Google Colab.
2. Install the CPU dependencies if needed (`pip install -r requirements.txt`), or use the optional installation cell.
3. Run all cells with the default flags for historical result summaries and a small CPU check. No dataset download or long GPU job starts by default.
4. To reproduce an experiment, enable its flag in Section 1 and run the notebook in order. Use an NVIDIA GPU and a compatible CuPy installation for GPU sections. GAP-twitter requires Linux, gcc, tar, wget and substantial disk/RAM/VRAM. Full Flickr evaluation may take hours.

The notebook writes included scripts to `_pagerank_runtime/` and new data/results to `pagerank_runs/`. Both directories are ignored by Git. Cached research outputs have been removed; the explicitly labelled historical summaries remain embedded. Do not upload downloaded datasets or generated binary arrays.

## Repository contents

- `PageRank_Experiments.ipynb`: the single, self-contained research notebook.
- `requirements.txt`: CPU/Jupyter dependencies; install CuPy separately for your CUDA runtime.
- `.gitignore`: excludes generated scripts, datasets, outputs and notebook checkpoints.

Recorded results and rerun outputs are separate. The consolidation preserves numerical settings and adds path/setup orchestration; it does not claim that original GPU experiments were rerun during packaging. The notebook documents source provenance and optional exploratory experiments.

For a new, empty GitHub repository, initialise this folder and push its contents. Replace `YOUR_REPOSITORY_URL` with the repository URL:

```bash
git init
git add README.md requirements.txt .gitignore PageRank_Experiments.ipynb
git commit -m "Add PageRank thesis experiments"
git branch -M main
git remote add origin YOUR_REPOSITORY_URL
git push -u origin main
```

For an existing repository, copy these four files into it and use its normal commit/push workflow.

## Packaging validation

All default code cells were executed in order in a clean IPython namespace on Python 3.12. The small CPU power-iteration and Monte Carlo checks passed. The baseline and exploratory Flickr bootstraps were rerun against the archived 5,000-user result files: estimates and confidence intervals matched to an absolute tolerance of 1e-10. Every embedded Python script was syntax-checked. Full GPU experiments and large dataset downloads were not rerun during consolidation.
