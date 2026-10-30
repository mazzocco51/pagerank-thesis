# PageRank: Markov Chains and GPU Computing

Bachelor's thesis in Computer and Control Engineering, Sapienza University of Rome (2026), with the code and experiments behind it.

📄 **[Read the thesis (PDF)](thesis/PageRank_Markov_Chains_and_GPU_Computing.pdf)** · 📓 **[Open the notebook](PageRank_Experiments.ipynb)** · [Website](https://mazzocco51.github.io) · [Contact](mailto:mazzocco.dev@gmail.com)

## What this is about

PageRank ranks the nodes of a graph by the long-run behaviour of a random walk on it, which makes it the stationary distribution of a Markov chain. The thesis studies this from both the mathematical and the computational side: why the iteration converges, and how to compute it fast on large sparse graphs, on CPU and on GPU.

## What the notebook covers

| Section | Dataset | What it does |
|---|---|---|
| Power iteration, CPU vs GPU | web-Google | Convergence behaviour and run times of the classic iterative method |
| Endpoint Monte Carlo | twitter_combined | Estimates PageRank with random walks and measures accuracy against the exact values |
| Sparse kernels at scale | GAP-twitter | Graph preparation, power iteration and custom CUDA sparse matrix-vector kernels |
| Contact recommendation | Flickr | Personalised PageRank to predict future contacts, evaluated with a paired bootstrap |

## Quick start

1. Open `PageRank_Experiments.ipynb` in Jupyter or upload it to Google Colab.
2. Install the dependencies: `pip install -r requirements.txt`. For the GPU sections, also install the CuPy build that matches your CUDA version.
3. Run all cells. With the default settings the notebook only shows the recorded results and runs a small CPU check. It downloads nothing and starts no long GPU job.
4. To rerun an experiment, turn on its flag in Section 1 and run the notebook in order.

Some experiments are heavy. The GAP-twitter part needs Linux, an NVIDIA GPU and a lot of disk, RAM and GPU memory. The full Flickr evaluation can take hours.

## Repository contents

- `thesis/PageRank_Markov_Chains_and_GPU_Computing.pdf`: the full thesis.
- `PageRank_Experiments.ipynb`: a single, self-contained notebook with all the code (CPU/GPU power iteration, Monte Carlo, CUDA kernels, the Flickr evaluation).
- `requirements.txt`: CPU and Jupyter dependencies.
- `.gitignore`: keeps datasets and generated outputs out of the repository.

When run, the notebook writes its helper scripts to `_pagerank_runtime/` and new data and results to `pagerank_runs/`. Both folders are ignored by Git.

## A note on the results

The results shown in the notebook are the ones recorded for the thesis and are clearly labelled as such. When the code was gathered into this notebook, the default cells and the small CPU checks were rerun on Python 3.12, and the Flickr statistics were recomputed from the saved results and matched. The full GPU experiments were not rerun.
