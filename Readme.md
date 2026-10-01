### Course Software Setup

In this course, we use **Python** for computational hydrology, water resources modeling, and spatial data visualization. Solution examples and lab exercises are provided as **Jupyter Notebooks (`.ipynb`)** and **Python scripts (`.py`)**.

We use **Visual Studio Code (VS Code)** as our integrated environment along with **Pixi** for package management.

---

### Track A: Setup for Personal Laptops (Windows, macOS, Linux)

Follow these instructions if you are working on your own personal computer.

#### Day 1 Setup Instructions:

1. **Install Base Software:**
   Download and install VS Code: https://code.visualstudio.com/

2. **Open Course Repository:**
   * Clone or download the course workspace repository from GitHub: https://github.com/bauergottwein/NIGK21007U-Integrated-Water-Resources-Modelling-python-lab.git
   * **Important:** Ensure the project folder sits on a **local fast drive** (e.g., `C:\Users\...` or `Documents`). Do **not** place it on network drives, USB flash drives, or cloud-synced folders (OneDrive, Dropbox, Google Drive), as file locking will make Python environments extremely slow or unstable.
   * Open VS Code, go to **File > Open Folder...**, and select the course folder.
   * When prompted in the bottom-right corner, click **"Install Recommended Extensions"** to set up Python and Jupyter support.

3. **Install Pixi & Environment (Inside VS Code Terminal):**
   * Open the VS Code terminal by pressing `Ctrl + ` ` (or **Terminal > New Terminal**).
   * **Install Pixi:** Copy and paste the command for your operating system:

     **Windows:**
     ```powershell
     iwr -useb [https://pixi.sh/install.ps1](https://pixi.sh/install.ps1) | iex
     ```

     **macOS / Linux:**
     ```bash
     curl -fsSL [https://pixi.sh/install.sh](https://pixi.sh/install.sh) | bash
     ```

   * **Restart Terminal:** Click the **Trash Can icon** in the top-right of the terminal panel, then press `Ctrl + ` ` to open a new terminal.
   * **Build Environment & Register Kernel:** Run:

     ```bash
     pixi run setup-kernel
     ```

4. **Running Jupyter Notebooks:**
   * Open any `.ipynb` file in the workspace.
   * Click **Select Kernel** in the top-right corner of the notebook editor (or click the active kernel name).
   * Choose **Select Another Kernel...** -> **Jupyter Kernels...**
   * Select **`nigk21007u python lab pixi`**.
   * *Important:* Do **not** select the raw Python path (`.pixi/envs/default`), as running Python directly without `pixi run` will cause kernel crashes when rendering plots.

---
### Track B: Setup for University Lab Computers

Follow these instructions when working on university lab computers. VS Code and Pixi are pre-installed, but user files sit on network drives (`H:`). Because network drives cause Python environments to freeze or crash, the execution workspace is initialized on high-speed local temporary storage (`C:\Temp`).

#### Setup Instructions:

1. **Open Course Repository from Network Drive:**
   * **Day 1 Only:** Clone or download the course repository into your **`H:` Drive** (this ensures your code, notebooks, and changes are saved permanently).
   * Open VS Code, go to **File > Open Folder...**, and select the course folder on your `H:` drive.
   * When prompted in the bottom-right corner, click **"Install Recommended Extensions"** to set up Python and Jupyter support.

2. **Initialize Local Fast Environment & Kernel (Run ONCE per lab session):**
   * Open the VS Code terminal by pressing `Ctrl + ` ` (or **Terminal > New Terminal**).
   * Copy and paste the following command into the terminal and press `Enter`:

     ```powershell
     $local = "C:\Temp\$env:USERNAME\python-lab"; robocopy . $local /MIR /XD .pixi data; cd $local; pixi install; pixi run setup-kernel; code -r .
     ```

   * *How this works:* This clones your code to local fast storage (`C:\Temp`), builds the execution environment, and registers a custom Jupyter kernel spec (`nigk21007u python lab`) that runs Python through `pixi run`. This prevents DLL loading errors and kernel crashes when plotting with Matplotlib.

3. **Running Jupyter Notebooks:**
   * Open any `.ipynb` file in the workspace.
   * Check the kernel name in the top-right corner of the notebook editor:
     * Click **Select Kernel** in the top-right corner (or click the existing kernel name).
     * Choose **Select Another Kernel...** -> **Jupyter Kernels...**
     * Select **`nigk21007u python lab pixi`**.
   * *Important:* Do **not** select the raw `.pixi/envs/default` executable path, as bypassing `pixi run` will cause C-library crashes during plotting.
   * Test your setup by running the first code cell using `Shift + Enter`.

4. **Saving Your Work Before Logging Off (CRITICAL):**
   * Files stored in `C:\Temp` are deleted automatically when you log off or reboot the lab computer.
   * **Before finishing your session**, save all open notebooks in VS Code (`Ctrl + S`), open the VS Code terminal, and run:

     ```powershell
     robocopy . "H:\NIGK21007U-Integrated-Water-Resources-Modelling-python-lab" /MIR /XD .pixi
     ```

   * *Note:* Update `"H:\..."` if your course folder on `H:` uses a different folder name or path.