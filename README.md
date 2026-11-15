# Intro to ML: tutoring sessions

These are the notebooks for the Intro to ML tutoring sessions. Each session has its own folder, and new sessions are added as we go through the course material.

## Session 1: coding foundations (`session01/`)

Python basics, git, conda, numpy, pandas and matplotlib: the foundations underneath the recitation notebooks you've already worked through. The session ends with a kNN prediction you build by hand, and then check against sklearn.

| Notebook | Topic |
|---|---|
| `session01/00_setup_check.ipynb` | Is everything installed? |
| `session01/01_python_basics.ipynb` | Variables, types, errors, lists, dictionaries |
| `session01/02_functions.ipynb` | `if`, `for`, functions, testing with `assert` |
| `session01/03_numpy.ipynb` | Arrays, shapes, vectorised maths, masks, distances |
| `session01/04_pandas.ipynb` | Loading, auditing, filtering and grouping real data |
| `session01/05_matplotlib.ipynb` | Histograms, scatter plots, and a mini kNN by hand |

**Slides** (why git, why conda): open `session01/slides/index.html` in your browser by double-clicking it in your file explorer. Use ← / → to move between slides. No clone? On GitHub, open the file and use **Download raw file**.

**Can't install anything, or your setup broke?** Click the "Open in Colab" badge at the top of any notebook. It runs in your browser, so you can keep following along.

---

## 1. Before the session: install the tools (≈ 20 minutes)

You need three tools:
- **Git**: tracks versions of your code and downloads updates.
- **Miniforge**: gives you `conda`, which installs Python and its libraries into a separate *environment*.
- **VS Code**: the editor we'll use for writing and running notebooks.

### Windows

1. **Git**: download from <https://git-scm.com/download/win> and run the installer. Keep the default answer on every screen, except one: on the *"Choosing the default editor"* screen, pick **Visual Studio Code**.
2. **Miniforge**: download `Miniforge3-Windows-x86_64.exe` from <https://github.com/conda-forge/miniforge/releases/latest> and run it. Choose **"Just Me"** and keep the defaults.
3. **VS Code**: install it from <https://code.visualstudio.com>. Open it, go to the Extensions tab on the left, and install **Python** and **Jupyter** (both are published by Microsoft).

👉 On Windows, run **every command** in this README in the **Miniforge Prompt**. Find it in the Start menu by typing "Miniforge". Don't use the regular Command Prompt or PowerShell, because `conda` won't work there.

### Mac

1. **Git**: open **Terminal** and run `git --version`. If git isn't installed yet, macOS will offer to install it, so click *Install*.
2. **Miniforge**: in Terminal, run:
   ```bash
   curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
   bash Miniforge3-$(uname)-$(uname -m).sh
   ```
   Press Enter or type `yes` at each question. When the installer finishes, **close Terminal and open it again**.
3. **VS Code**: install it from <https://code.visualstudio.com>, then install the **Python** and **Jupyter** extensions from its Extensions tab.

### Check that it worked (Windows and Mac)

```bash
git --version
conda --version
```

If both commands print a version number, you're done ✅. Then tell git who you are. This name appears on your commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global pull.rebase false
```

---

## 2. Get the repo and create the environment

Run these commands in the Miniforge Prompt (Windows) or Terminal (Mac):

```bash
git clone https://github.com/abuchnick/intro-to-ml-tutoring.git
cd intro-to-ml-tutoring
conda env create -f environment.yml
```

The last command downloads Python and the course libraries into an environment called `intro-ml`. It takes a few minutes. You only need to do it **once**.

Next, open the repo in VS Code: **File → Open Folder…** and select the `intro-to-ml-tutoring` folder. Open `session01/00_setup_check.ipynb`, click **Select Kernel** (top right), then **Python Environments**, then **intro-ml**. Run the cell.

---

## 3. git cheat sheet

| Command | What it does |
|---|---|
| `git status` | Shows what has changed since your last commit. Run it whenever you're unsure. |
| `git add session01/01_python_basics.ipynb` | Marks that file to be saved in the next commit |
| `git commit -m "finished exercise 1"` | Saves a snapshot of the marked files, with a message |
| `git log --oneline` | Lists your past snapshots |
| `git pull --no-edit` | Downloads updates from the course repo (for example, new solutions) |

**Fell behind during the session?** Run `git pull --no-edit`, then open the matching notebook in that session's `solutions/` folder (for example `session01/solutions/`). Your own work is safe, because solutions always arrive as **new files** and never overwrite your notebooks.

## 4. conda cheat sheet

| Command | What it does |
|---|---|
| `conda activate intro-ml` | Switch to the course environment (needed before running `jupyter lab`) |
| `conda env list` | List your environments. The active one has a `*`. |
| `conda env update -f environment.yml` | Install anything that was added to `environment.yml` |
| `jupyter lab` | An alternative to VS Code: opens notebooks in your browser |
