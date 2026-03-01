# Installation Instructions

## Prerequisites
- Ensure you have Python 3.x installed.
- A package manager such as `pip` or `conda`.

## Environment Setup
1. Create a virtual environment:
   - For `venv`:  
     ```bash
     python -m venv myenv
     ```  
   - For `conda`:  
     ```bash
     conda create --name myenv python=3.x
     ```
2. Activate the virtual environment:
   - For `venv`:  
     - On Windows:  
       ```bash
       myenv\Scripts\activate
       ```  
     - On macOS/Linux:  
       ```bash
       source myenv/bin/activate
       ```  
   - For `conda`:  
     ```bash
     conda activate myenv
     ```

## Required Libraries
Install the required libraries by running:
```bash
pip install -r requirements.txt
```

## Running the Notebooks and Dash Application
To run the Jupyter notebooks:
1. Start Jupyter:
   ```bash
   jupyter notebook
   ```
2. Open your notebook in your web browser.

To run the Dash application:
1. Navigate to the directory containing the Dash app.
2. Execute the following command:
   ```bash
   python app.py
   ```
3. Open your web browser and go to `http://127.0.0.1:8050/` to view the app.