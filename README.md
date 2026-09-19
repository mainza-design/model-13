# model-13
# ICD311 — Deep  Lab

Reproducible project for the Competency-Based Lab (neuron warm-up, XOR MLP,
activation comparison, debugging challenge, Fashion-MNIST MLP).

## Project structure
```
ICD311_Lab_NeuralNetworks/
├── notebooks/        # Jupyter notebook(s) with markdown explanations + outputs
├── src/               # Reusable, runnable Python modules
│   ├── xor_numpy_forward.py     # Task 4.2 — NumPy forward pass (no training)
│   ├── xor_torch.py             # Task 4.3 & 5 — PyTorch XOR model + activation experiment
│   ├── debugging_challenge.py   # Task 6 — deliberate shape error, device mismatch, fixes
│   └── fashion_mnist_mlp.py     # Task 7 — Fashion-MNIST MLP: data, train, evaluate
├── reports/           # Loss curve figure, sample images, error-analysis notes
├── requirements.txt
└── README.md
```

## Exact setup commands (Windows)

```powershell
py -m venv .venv
.venv\Scripts\activate
python --version

pip install numpy matplotlib jupyter
# Install PyTorch using the official selector for your machine at
# https://pytorch.org/get-started/locally/  (choose CPU or your CUDA version)
pip install torch torchvision --index-url <the-url-from-the-selector>

pip freeze > requirements.txt
```

## Exact setup commands (macOS/Linux)

```bash
python3 -m venv .venv
source .venv/bin/activate
python --version

pip install numpy matplotlib jupyter
pip install torch torchvision   # or the CUDA-specific command from pytorch.org

pip freeze > requirements.txt
```

## Verify the environment

```bash
python -c "import torch; print(torch.__version__); print('CUDA available:', torch.cuda.is_available())"
```

## Run order

```bash
# 1. Warm-up NumPy forward pass (no PyTorch needed)
python src/xor_numpy_forward.py

# 2. Train the PyTorch XOR model + activation experiment (Tasks 4.3 and 5)
python src/xor_torch.py

# 3. Debugging challenge (Task 6)
python src/debugging_challenge.py

# 4. Fashion-MNIST MLP: trains 3 epochs, saves reports/loss_curve.png (Task 7)
python src/fashion_mnist_mlp.py

# 5. Or open the full walkthrough notebook
jupyter notebook notebooks/ICD311_Lab.ipynb
```

## Git

```bash
git init
git add .
git commit -m "Initial commit: project structure, README, requirements"
# ... commit again after each milestone, e.g.:
git commit -m "XOR baseline: NumPy forward pass + PyTorch model working"
git commit -m "Fashion-MNIST training and evaluation complete"
```

## Notes on reproducibility

- Random seed used throughout: **42** (set via `torch.manual_seed(42)` and
  `np.random.default_rng(0)` for the NumPy warm-up).
- Device is detected automatically with
  `torch.device("cuda" if torch.cuda.is_available() else "cpu")` and printed
  at the start of every script.
