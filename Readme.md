### Course Software Setup

In this course, we use **Python** for computational hydrology, water resources modeling, and spatial data visualization. Solution examples and lab exercises are provided as **Jupyter Notebooks (`.ipynb`)** and Python scripts.

We use **Visual Studio Code (VS Code)** as our integrated environment along with **Pixi** for package management. You do **not** need Anaconda, manual Python installations, or administrator rights to install the course packages.

#### Day 1 Setup Instructions:

1. **Install Base Software:**
   * Download and install VS Code: https://code.visualstudio.com/

2. **Open Course Repository:**
   * Clone or download the course workspace repository from GitHub.
   * Open VS Code, go to **File > Open Folder...**, and select the course folder.
   * When prompted in the bottom-right corner, click **"Install Recommended Extensions"** to set up Python and Jupyter support.

3. **Install Pixi & Environment (Inside VS Code Terminal):**
   * Open the VS Code terminal by pressing `Ctrl + ` ` (or going to **Terminal > New Terminal** in the top menu).
   * **Install Pixi:** Copy and paste the command for your operating system into the terminal:

     **Windows:**
     iwr -useb https://pixi.sh/install.ps1 | iex

     **macOS / Linux:**
     curl -fsSL https://pixi.sh/install.sh | bash

   * **Restart the Terminal:** Click the **Trash Can icon** in the top-right corner of the terminal panel to close the session, then press `Ctrl + ` ` to open a fresh terminal window (this enables the newly installed `pixi` command).
   * **Create the Environment:** Run:

     pixi install

   * *Pixi will automatically set up Python and install all spatial packages (`geopandas`, `flopy`, `mikeio`, `pyomo`, `glpk`, etc.) without C-compiler errors or hangs.*
   * *Troubleshooting Note:* If PowerShell says `pixi is not recognized` after installing, either restart VS Code (File > Exit) or run `$env:Path += ";$env:USERPROFILE\.pixi\bin"` in the terminal.

4. **Running Notebooks:**
   * Open any `.ipynb` file in the `notebooks/` folder.
   * Click **Select Kernel** in the top-right corner of the notebook editor.
   * Select **Python Environments...** and choose the **`pixi`** environment (`.pixi/envs/default/bin/python` or `.pixi/envs/default/python.exe`).
   * Run code cells using `Shift + Enter`.