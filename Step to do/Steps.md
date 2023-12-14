# Running Jupyter Notebook as a Web App Using Jupyter Dashboard and Flask

## Objective
This guide aims to illustrate the process of running a Jupyter Notebook as a web app by integrating Jupyter Dashboard into a Flask application.

### Prerequisites
Before proceeding, ensure the following prerequisites are met:
1. Installation of Jupyter Notebook, Flask, and necessary supporting modules.
2. A Jupyter Notebook file (`file.ipynb`) that you want to run as a web app.

## Implementation Steps

### Step 1: Convert Jupyter Notebook to Jupyter Dashboard

1. **Install Jupyter Dashboard (voila)**
   - Install `voila` if not already installed:
     ```bash
     pip install voila
     ```

2. **Convert the Notebook**
   - Use the following command to convert the Jupyter Notebook (`file.ipynb`) into a dashboard:
     ```bash
     voila file.ipynb
     ```
   This command initiates a local server and opens the notebook as a web app.

### Step 2: Integrate Dashboard into Flask Web App

1. **Create Flask App (`app.py`)**
   - Create a Flask application (`app.py`) to host the Jupyter Dashboard:
     ```python
     from flask import Flask, render_template

     app = Flask(__name__)

     @app.route('/dashboard')
     def show_dashboard():
         return render_template('dashboard.html')

     if __name__ == '__main__':
         app.run(debug=True)
     ```

2. **Create HTML Template for Dashboard (`dashboard.html`)**
   - Inside a `templates` folder, create a file named `dashboard.html`:
     ```html
     <!DOCTYPE html>
     <html>
     <head>
         <title>Jupyter Dashboard</title>
     </head>
     <body>
         <h1>Jupyter Dashboard</h1>
         <iframe src="http://localhost:8866/" width="100%" height="800px" frameborder="0"></iframe>
     </body>
     </html>
     ```

### Step 3: Run Flask App and Access Dashboard

1. **Run Flask App**
   - Execute the Flask application (`app.py`) by running the following command:
     ```bash
     python app.py
     ```

2. **Access the Dashboard**
   - Open a web browser and visit `http://localhost:5000/dashboard` to access the Jupyter Dashboard.
   
   Utilizing Jupyter Dashboard in conjunction with Flask facilitates an interactive experience to run Jupyter Notebooks as web applications. Ensure all necessary dependencies and configurations are set in the notebook for proper execution within the Jupyter Dashboard.
