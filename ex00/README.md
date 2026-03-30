# Python Virtual Environments & Jupyter Notebooks

## The Core Ideas

A **virtual environment** is just a folder containing its own Python binary and its own package directory.
When you activate it, your terminal redirects `python` and `pip` to point inside that folder — that's the whole trick.

A **Jupyter notebook** is a local web server. It serves `.ipynb` files — documents where some cells are runnable Python and others are Markdown text.

---

## Virtual Environment Commands

```bash
# Create a virtual environment (creates a folder named ex00/)
python3 -m venv ex00

# See what's inside
ls ex00/
# bin/   ← the Python + pip executables used when env is active
# lib/   ← where installed packages (numpy etc.) get dropped
# include/
# pyvenv.cfg   ← records which Python version built this

# Activate (redirects python/pip to use the ones in ex00/bin/)
source ex00/bin/activate

# Your prompt will change to show: (ex00) $

# Install packages while active (goes into ex00/lib/, not globally)
pip install numpy matplotlib jupyter

# Deactivate (go back to global Python)
deactivate
```

---

## Jupyter Commands

```bash
# Start the notebook server (run this with your env active)
jupyter notebook --port 8891

# Jupyter opens your browser automatically at:
# http://localhost:8891
```

---

## Creating a Notebook (Step by Step)

1. Run the Jupyter command above — browser opens to a file explorer
2. Click **New** → **Python 3** to create a new notebook
3. Click the title ("Untitled") at the top → rename to `Notebook_ex00`
4. **Cell 1 — Markdown:**
   - Click the cell type dropdown (says "Code") → switch to **Markdown**
   - Type:
     ```
     # H1 TITLE
     ## H2 TITLE
     ```
   - Press `Shift + Enter` to render it
5. **Cell 2 — Code:**
   - Leave as **Code**
   - Type: `print("Buy the dip ?")`
   - Press `Shift + Enter` to run it

---

## Key Shortcuts Inside Jupyter

| Action | Shortcut |
|---|---|
| Run cell | `Shift + Enter` |
| Add cell below | `B` (in command mode) |
| Switch to Markdown | `M` (in command mode) |
| Switch to Code | `Y` (in command mode) |
| Enter command mode | `Esc` |
| Enter edit mode | `Enter` |

---

## Mental Model

```
ex00/
├── bin/python      ← used instead of /usr/bin/python when env is active
├── bin/pip         ← installs into THIS folder, not globally
├── lib/            ← numpy, jupyter, etc. land here
└── pyvenv.cfg      ← metadata (Python version, base prefix)
```

Everything is self-contained. Delete the folder = delete the environment. No uninstall needed.
