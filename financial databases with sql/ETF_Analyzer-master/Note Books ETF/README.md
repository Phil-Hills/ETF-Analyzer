# Financial Database
This financial database application will analyze ETFs and its cumulative returns, annualized returns, daily returns and ultimately extract data to review the assets' performance. With this analysis a user can reduce financial exposure and have a predictable earnings while investing in a diversified ETF.


---

## Technologies

This application runs on Jupyter Notebook, as it uses the Pandas/Python language. 



**Systems**

[conda 4.10.3](https://docs.anaconda.com/anaconda/install/index.html) - Package manager, Environment Manager

python 3.10 - included in Anaconda

JupyterLab - included in Python 

Pandas - included in Python

**Other Installations**

[Numpy](https://numpy.org/doc/stable/) - included in Python

[PyViz](https://pyviz.org/) - tools for data visualizations

[SQLAlchemy](https://docs.sqlalchemy.org/en/14/core/engines.html) - helps communicate with and create databases

[Voila](https://github.com/voila-dashboards/voila)-turns Jupyter Notebook into a web application

---

## Installation Guide 
install in terminal, in a dev environment:

```JupyterLab
conda activate dev
python -m ipykernel install --user --name dev
conda install -c conda-forge nodejs


```
open Jupyter Notebook:

```
conda activate dev
jupyter notebook
```


Install Pandas:

```Pandas
conda activate dev
conda install pandas -y
conda deactive
```
Numpy:
```
pip install numpy
```

PyViz will help build interactive visual modules that will showcase our data:

```
conda install -c plotly plotly=4.13.
conda install -c pyviz hvplot
conda install -c conda-forge nodejs=12
```
install Jupyterlab dependencies:

```
conda install -c conda-forge jupyterlab=2
jupyter labextension install jupyterlab-plotly@4.13.0 --no-build
jupyter labextension install @jupyter-widgets/jupyterlab-manager plotlywidget@4.13.0 --no-build
jupyter labextension install @pyviz/jupyterlab_pyviz --no-build
jupyter lab build
```
SQLAlchemy will assist in building SQL databases that will host the data that's needed:
```
pip install sqlalchemy
```
Lastly create a web application from the Jupyter Notebook:
```
conda install -c conda-forge voila -y
```
---

## Usage and Examples

To Use, clone GIT repository.

Enter into the dev environment: 

```
 conda activate dev
```

'financial_database' folder using Jupyter Notebook, and use the code:

```
jupyter notebook
```


Open the 'etf_analyzer.ipynb' file.



start analyzing ETFs, pull in the 'etf.db' as a temporary database using SQLite to interact with the database.

```
database_connection_string = 'sqlite:///etf.db'
engine = sqlalchemy.create_engine(database_connection_string)
```

PayPal (PYPL) data:
```
query = """
SELECT * FROM PYPL
"""

pypl_dataframe = pd.read_sql_query(query,con=engine)
```

View the data by creating an interactive visualization showcasing the PYPL daily returns.


Creat a visualization to show the cumulative returns for this asset.
 

**Optimize Data Access**

Test the data two ways using SQL.

First access the closing prices for PYPL that are greater than 200.


Second is to find the top 10 daily returns for PYPL.



**Analyzing the ETF Portfolio**

To analyze the entire portfolio arrange each of the four assets in the ETF portfolio into one DataFrame by the column 'time': 

```
query = """
SELECT * FROM GDOT
INNER JOIN GS ON GDOT.time = GS.time
INNER JOIN PYPL ON GDOT.time = PYPL.time
INNER JOIN SQ ON GDOT.time = SQ.time
"""
```
Next analyze the cumulative returns of the portfolio by using hvPlot to visualize the cumulative return values.
 


**Deploying a Web Application**

Open Voilà to deploy the notebook as a web application. 


When the code runs, it will open the notebook as a web application.



---

## Contributors

Phil Hills

## License

MIT License
