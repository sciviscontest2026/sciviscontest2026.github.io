---
layout: default
title: Examples
permalink: /examples/
sectionid: examples
---

<div class="container">
    <h1>Examples for Data Access and Visualization</h1>

    <div class="row">
        <!-- Sidebar Column -->
        <div class="col-md-3">
            <div class="sidebar-box">
                <nav class="nav flex-column">
                    <a class="nav-link active" href="#prerequisites" onclick="showSection('prerequisites')">Prerequisites</a>
                    <a class="nav-link" href="#access-llc4320" onclick="showSection('access-llc4320')">Access LLC4320 ECCO Data</a>
                    <a class="nav-link" href="#access-dyamond" onclick="showSection('access-dyamond')">Access DYAMOND Data</a>
                    <a class="nav-link" href="#access-nex-gddp-cmip6" onclick="showSection('access-nex-gddp-cmip6')">Access NEX GDDP CMIP6 Data</a>
                    <a class="nav-link" href="#visualization" onclick="showSection('visualization')">Visualization</a>
                </nav>
            </div>
        </div>

        <!-- Content Column -->
        <div class="col-md-9">
            <!-- Prerequisites Section -->
            <div id="prerequisites" class="section-content">
                <h2>Prerequisites</h2>
                <p>To provide progressive streaming capability for large datasets, the data has been converted to <a href="https://github.com/sci-visus/OpenVisus"  target="_blank">OpenVisus IDX format</a>.</p>

                <p>Users can create a new Python environment and install the required libraries with the following steps:</p>
                <strong>Step 1:</strong> Create a new virtual enviroment using python
                <pre>
<code class="language-bash">
# Create a python virtual environment
python -m venv .venv
</code></pre>
<strong>Step 2:</strong> Activate the environment you just created
<pre><code class="language-bash">
# Activate the environment
source .venv/bin/activate
</code></pre>
<strong>Step 3:</strong> Install required libraries
<pre><code class="language-bash">
# Install required libraries
python -m pip install --verbose --no-cache --no-warn-script-location boto3 colorcet fsspec numpy imageio pympler==1.0.1 urllib3 pillow xarray xmltodict plotly requests scikit-image scipy seaborn tifffile pandas tqdm matplotlib zarr altair cartopy dash fastparquet lxml numexpr scikit-learn sqlalchemy  xlrd yfinance pyarrow pydeck netcdf4 nexpy nexusformat nbgitpuller intake ipysheet ipywidgets bokeh ipywidgets-bokeh panel pyvista trame trame-vtk trame-vuetify notebook "jupyterlab==3.6.6" jupyter_bokeh jupyter-server-proxy jupyterlab-system-monitor "pyviz_comms>=2.0.0,<3.0.0" "jupyterlab-pygments>=0.2.0,<0.3.0" 
</code></pre>
<strong>Step 4:</strong> Install OpenVisus
<pre> <code class="language-bash">
# Install OpenVisus
python -m pip install OpenVisus
 </code></pre>

                <h3>Conda Environment File</h3>
                <p>For convenience, here is a conda environment file you can use to create the environment. Save it as a <code>environment.yml</code> file and create the environment using <code>conda env create -f environment.yml</code>.<br /> If you need more instructions on how to manage conda environments, please check the offical documentation <a href= "https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html"  target="_blank">here. </a></p>
                <pre><code class="language-bash">
# environment.yml file
name: scivis2026
channels:
  - conda-forge
dependencies:
  - python=3.8
  - boto3
  - colorcet
  - fsspec
  - numpy
  - imageio
  - pympler=1.0.1
  - urllib3
  - pillow
  - xarray
  - xmltodict
  - plotly
  - requests
  - scipy
  - seaborn
  - tifffile
  - pandas
  - matplotlib
  - cartopy
  - fastparquet
  - lxml
  - numexpr
  - sqlalchemy
  - statsmodels
  - xlrd
  - intake
  - ipysheet
  - ipywidgets
  - bokeh
  - ipywidgets-bokeh
  - panel
  - notebook
  - jupyterlab=3.6.6
  - jupyter_bokeh
  - jupyter-server-proxy
  - jupyterlab-system-monitor
  - pyviz_comms>=2.0.0,<3.0.0
  - jupyterlab-pygments>=0.2.0,<0.3.0
  - OpenVisus
                </code></pre>
            </div>

            <!-- Data Access Section -->
            <div id="access-llc4320" class="section-content" style="display:none;">
                <h2>Access LLC4320 ECCO Data</h2>
                <p>Below are the steps based on the <a href="https://github.com/sci-visus/Openvisus-NASA-Dashboard/blob/main/OpenVisus_NASA.ipynb">GitHub instructions</a>:</p>
                <ol>
                    <ul><strong>Step 1: Importing Libraries</strong></ul>
                    <pre><code class="language-bash">
import numpy as np
import matplotlib.pyplot as plt
import OpenVisus as ov
                    </code></pre>

                    <ul><strong>Step 2: Define the field you want to access</strong></ul>
                    <pre><code class="language-python">
#available options=[salt, theta, u, v, w]; choose one below
variable = 'theta'
</code></pre>
<ul><strong>Step 3: Load the IDX metadata:</strong>
In this section, you can select any variables that you can declared in the cells above and replace it inside LoadDataset. We are just reading the metadata for the dataset here. <strong>PUT PERMANENT OSDF LINK... ALSO GENERATE PUBLIC KEYS FOR READ ACCESS</strong> </ul>
<pre><code class="language-bash">
# Step 3: Load the 4320 dataset from OSDF
field= f"https://s3.nsdf.chtc.io/nasa-ecco/llc4320/idx/{variable}/{variable}_llc4320_x_y_depth.idx?access_key=any&secret_key=any&endpoint_url=https://s3.nsdf.chtc.io"

db=ov.LoadDataset(field)
print(f'Dimensions: {db.getLogicBox()[1][0]}*{db.getLogicBox()[1][1]}*{db.getLogicBox()[1][2]}')
print(f'Total Timesteps: {len(db.getTimesteps())}')
print(f'Field: {db.getField().name}')
print('Data Type: float32')
                    </code></pre>

                    <ul><strong>Step 4: Read Data (Since the data is very large, I am only extracting one level. Check <a href="../data/home"> data descriptions </a> for more details.) </strong></ul>
                    <pre><code class="language-python">
# This section shows you how to load the data you want. You can select any timestep, region (x,y,z) you want. You can set the quality or resolution of the data as well. Higher quality means the finer(more) data. Not setting any time means first timestep available. Not setting quality means full data which  takes a while to load because of the higher filesize.

# here you can select the resoution at which you query the data: -15 is very coarse, 0 is full resoltuon (dangerous since you may fetch a lot of data and wait a long time).

data_resolution = -9 # try values among -15, -12, -9, -6, -3, 0
data3D=db.read(time=0,quality=data_resolution, z=[0,1])  # Since the data is very large, I am only extracting one level.
print(data3D.shape)
print(np.min(data3D),np.max(data3D))
                    </code></pre>
                </ol>
            </div>

            <!-- Access DYAMOND Data Section -->
            <div id="access-dyamond" class="section-content" style="display:none;">
                <h2>2. Access DYAMOND Data (Atmospheric - GEOS and Oceanic - LLC2160)</h2>
                <p>You can follow these steps to access the DYAMOND atmospheric (GEOS) and oceanic (LLC2160) data. You can find individual data description and fields description in the <a href="../data/home"> Data Section</a></p>

<h3>2.1 Access DYAMOND Atmospheric Data (GEOS)</h3>
<p>Below are the steps to access the DYAMOND Atmospheric (GEOS) data:</p>

<ol>
    <ul><strong>Step 1: Importing Libraries</strong></ul>
    <pre><code class="language-bash">
import numpy as np
import matplotlib.pyplot as plt
import OpenVisus as ov
    </code></pre>

    <ul><strong>Step 2: Define the field and face you want to access. Remember that the GEOS data is projected to a cubed sphere, so it has 6 faces. </strong></ul>
    <p>Available options are: CO, CO2, DELP, DTHDT, DTHDTCN, FCLD, H, P, P_TAVG, QI, QL, QV, RI, RL, T, U, V, W. Set the variable based on your selection:</p>
    <pre><code class="language-python">
# Example available options: CO, CO2, DELP, DTHDT, DTHDTCN, FCLD, H, P, P_TAVG, QI, QL, QV, RI, RL, T, U, V, W
variable = 'CO'
face=0
    </code></pre>

    <ul><strong>Step 3: Load the IDX metadata</strong></ul>
    <p>This step allows you to read the metadata for the selected field. You can replace the variable in the URL to choose the data you want:</p>
    <pre><code class="language-python">
field= f"https://maritime.sealstorage.io/api/v0/s3/utah/nasa/dyamond/GEOS/GEOS_{variable}/{variable}_face_{face}_depth_52_time_0_10269.idx?access_key=any&secret_key=any&endpoint_url=https://maritime.sealstorage.io/api/v0/s3&cached=arco"

db = ov.LoadDataset(field)
print(f'Dimensions: {db.getLogicBox()[1][0]}*{db.getLogicBox()[1][1]}*{db.getLogicBox()[1][2]}')
print(f'Total Timesteps: {len(db.getTimesteps())}')
print(f'Field: {db.getField().name}')
print('Data Type: float32')
    </code></pre>

    <ul><strong>Step 4: Read Data</strong></ul>
    <p>This section shows how to load the data for the specified field. You can select any timestep and region (face number) or resolution you want:</p>
    <pre><code class="language-python">
# This selects the resolution for querying the data. -15 is very coarse, 0 is full resolution.
# Be cautious: full resolution (0) may take longer to load because of the file size.

data_resolution = -6  # Try values among -15, -12, -9, -6, -3, 0
data3D = db.read(time=0, quality=data_resolution)
print(data3D.shape)
print(np.min(data3D), np.max(data3D))
    </code></pre>
</ol>


                <h3>2.2 Access DYAMOND Oceanic Data (LLC2160)</h3>
                <p>Below are the steps based on the <a href="https://github.com/sci-visus/Openvisus-NASA-Dashboard/blob/main/OpenVisus_NASA.ipynb">GitHub instructions</a>:</p>
                <ol>
                    <ul><strong>Step 1: Importing Libraries</strong></ul>
                    <pre><code class="language-bash">
import numpy as np
import matplotlib.pyplot as plt
import OpenVisus as ov
                    </code></pre>

                    <ul><strong>Step 2: Define the field you want to access</strong></ul>
                    <pre><code class="language-python">
#available options=[salt, theta, u, v, w]; choose one below
variable = 'salt'
</code></pre>
<ul><strong>Step 3: Load the IDX metadata:</strong>
In this section, you can select any variables that you can declared in the cells above and replace it inside LoadDataset. We are just reading the metadata for the dataset here. </ul>
<pre><code class="language-bash">
# Step 3: Load the LLC2160 dataset from Sealstorage
field= "https://maritime.sealstorage.io/api/v0/s3/utah/nasa/dyamond/mit_output/llc2160_arco/visus.idx?access_key=any&secret_key=any&endpoint_url=https://maritime.sealstorage.io/api/v0/s3&cached=arco" if variable=="salt" else  f"https://maritime.sealstorage.io/api/v0/s3/utah/nasa/dyamond/mit_output/llc2160_{variable}/{variable}_llc2160_x_y_depth.idx?access_key=any&secret_key=any&endpoint_url=https://maritime.sealstorage.io/api/v0/s3&cached=arco"

db=ov.LoadDataset(field)
print(f'Dimensions: {db.getLogicBox()[1][0]}*{db.getLogicBox()[1][1]}*{db.getLogicBox()[1][2]}')
print(f'Total Timesteps: {len(db.getTimesteps())}')
print(f'Field: {db.getField().name}')
print('Data Type: float32')
                    </code></pre>

                    <ul><strong>Step 4: Read Data</strong></ul>
                    <pre><code class="language-python">
# This section shows you how to load the data you want. You can select any timestep, region (x,y,z) you want. You can set the quality or resolution of the data as well. Higher quality means the finer(more) data. Not setting any time means first timestep available. Not setting quality means full data which  takes a while to load because of the higher filesize.

# here you can select the resoution at which you query the data: -15 is very coarse, 0 is full resoltuon (dangerous since you may fetch a lot of data and wait a long time).

data_resolution = -9 # try values among -15, -12, -9, -6, -3, 0
data3D=db.read(time=0,quality=data_resolution)
print(data3D.shape)
print(np.min(data3D),np.max(data3D))
                    </code></pre>
                </ol>
            </div>

            <!-- Access NEX GDDP CMIP6 Data Section -->
<!-- Access NEX GDDP CMIP6 Data Section -->
<div id="access-nex-gddp-cmip6" class="section-content" style="display:none;">
    <h2>3. Access NEX GDDP CMIP6 Data</h2>
    <p>We demonstrate how to load the data from the NEX-GDDP-CMIP6 dataset using OpenVisus and visualize it with matplotlib. Additionally, you can save the plotted data to a file. In just a few lines of Python code, you can generate a plot as shown in Figure 3.1.</p>

    <h3>3.1 Table of Contents</h3>
    <ul>
        <li>3.1 <a href="#notebook-code">Notebook Code</a></li>
        <li>3.1.1 <a href="#load-data">Loading the Data</a></li>
        <li>3.1.2 <a href="#plot-data">Plotting and Saving Data</a></li>
    </ul>

    <h3 id="notebook-code">3.1 Notebook Code</h3>
    <p>Below is a sample Jupyter notebook to load one timestep of a selected variable and display it using matplotlib.</p>

    <pre><code class="language-python">
# import libraries
import numpy as np
import OpenVisus as ov

# Set climate variables
model     = "ACCESS-CM2"
variable  = "huss" 
year      = 2020
scenario  = "ssp585"
field = f"{variable}_day_{model}_{scenario}_r1i1p1f1_gn"

# Open remote dataset to variable db
db = ov.LoadDataset(f"http://atlantis.sci.utah.edu/mod_visus?dataset=nex-gddp-cmip6&cached=arco")
print("Dataset loaded successfully!")
print(f"Available fields: {db.getFields()}")
    </code></pre>

    <h3 id="load-data">3.1.1 Loading the Data</h3>
    <p>We load a specific timestep (for July 21, 2020) and print the information about the data.</p>

    <pre><code class="language-python">
# Set the timestep for July 21. See https://nsidc.org/data/user-resources/help-center/day-year-doy-calendar
day_of_the_year = 202 
timestep = year * 365 + day_of_the_year

# Load the data into a numpy array
data = db.read(field=field, time=timestep)
print(f"Data shape: {data.shape}")
print(f"Min value: {np.min(data)}, Max value: {np.max(data)}")
    </code></pre>

    <h3 id="plot-data">3.1.2 Plotting and Saving Data</h3>
    <p>Below, we use matplotlib to plot the data and save it as a PNG image.</p>

    <pre><code class="language-python">
import matplotlib.pyplot as plt

# Plot and save data
my_cmap = 'gist_rainbow'
plt.subplots(figsize=(18, 9))
plt.imshow(data, cmap=my_cmap, origin='lower')
plt.colorbar(label=f'{variable} values')
plt.title(f'{model} {variable} {scenario} on Day {day_of_the_year}, {year}')
plt.savefig("NEX-GDDP-CMIP6_ACCESS-CM2_huss_ssp585_2020_day202.png")
plt.show()
    </code></pre>

    <h4>Figure 3.1: Plot of NEX-GDDP-CMIP6 data (huss, ACCESS-CM2, ssp585)</h4>

    <h3 id="dashboard">Dashboard</h3>
    <p>Check out this NEX GDDP CMIP6 <a href="http://chpc3.nationalsciencedatafabric.org:12345/dashboards"  target="_blank">Dashboard</a> we deployed for interactive exploration and visualization of the dataset. This dashboard allows users to select variables, timesteps, and generate visualizations interactively.</p>

    <h3 id="quarto">Quarto Documentation</h3>
    <p>Check out this  <a href="https://aashishp.quarto.pub/nex-gddp-cmip6/"  target="_blank">Quarto documentation</a> for more details on accessing the NEX-GDDP-CMIP6 data. The documentation includes step-by-step instructions for loading and visualizing climate model data using Python and OpenVisus.</p>
</div>


            <!-- Visualization Section -->

            <!-- Visualization Section -->
            <div id="visualization" class="section-content" style="display:none;">
                <h2>Visualization Example: Using Matplotlib</h2>
                <p>This page will provide resources on generating visualizations using <a href="https://matplotlib.org/">matplotlib</a>, and much more. Whether you're new to visualizing scientific data or looking for advanced techniques, you'll find valuable information below.</p>

                <p>Below is a basic example of how you can visualize some of the ocean data using Python and <code>matplotlib</code>:</p>
                <pre><code class="language-python">
import numpy as np
import matplotlib.pyplot as plt

# Example data (simulated sea surface temperature)
x = np.linspace(0, 10, 100)
y = np.linspace(0, 10, 100)
X, Y = np.meshgrid(x, y)
Z = np.sin(X) * np.cos(Y)

# Create the plot
plt.figure(figsize=(10, 6))
plt.contourf(X, Z, cmap='coolwarm')
plt.colorbar(label='Sea Surface Temperature (C)')
plt.title('Sea Surface Temperature Visualization')
plt.xlabel('Longitude')
plt.ylabel('Latitude')
plt.show()
                </code></pre>

                <p>This is a simple example of visualizing 2D data. You can modify the code to work with the real dataset, adding more complexity and details as needed.</p>

                <h3>Other Visualization Tools</h3>
                <ul>
                    <li><a href="https://seaborn.pydata.org/">Seaborn</a> – An advanced Python library for statistical data visualization.</li>
                    <li><a href="https://www.paraview.org/">ParaView</a> – For handling large datasets and creating 3D visualizations.</li>
                    <li><a href="https://bokeh.org/">Bokeh</a> – Interactive visualization in modern web browsers.</li>
                </ul>

                <h2>Data Analysis Resources</h2>
                <p>For advanced data analysis techniques, we recommend using libraries like <a href="https://numpy.org/">NumPy</a>, <a href="https://pandas.pydata.org/">Pandas</a>, and <a href="https://xarray.pydata.org/en/stable/">Xarray</a>. These libraries allow you to handle multi-dimensional arrays and efficiently work with large-scale scientific data.</p>

                <h2>Learning Resources</h2>
                <p>If you're new to scientific computing and visualization, the following resources may be helpful:</p>
                <ul>
                    <li><a href="https://matplotlib.org/stable/tutorials/index.html">Matplotlib Tutorials</a></li>
                    <li><a href="https://numpy.org/learn/">NumPy Learning Resources</a></li>
                    <li><a href="https://tutorial.xarray.dev/intro.html">Xarray Tutorials</a></li>
                    <li><a href="https://scipy.org/">SciPy Documentation</a></li>
                </ul>
            </div>
        </div>
    </div>
</div>

<script>
function showSection(sectionId) {
    // Hide all sections
    document.querySelectorAll('.section-content').forEach(function(content) {
        content.style.display = 'none';
    });

    // Show the selected section
    document.getElementById(sectionId).style.display = 'block';

    // Remove 'active' class from all links
    document.querySelectorAll('.nav-link').forEach(function(link) {
        link.classList.remove('active');
    });

    // Add 'active' class to clicked link
    document.querySelector('a[href="#' + sectionId + '"]').classList.add('active');
}
</script>
