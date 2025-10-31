---
layout: default
title: Examples
permalink: /examples/
sectionid: examples
---

<div class="container">
    <h2>Examples for Data Access and Visualization</h2>

    <div class="row">
        <!-- Sidebar Column -->
        <div class="col-md-3">
            <div class="sidebar-box">
                <nav class="nav flex-column">
                    <a class="nav-link active" href="#prerequisites" onclick="showSection('prerequisites')">Prerequisites</a>
                    <a class="nav-link" href="#pythia-cookbook" onclick="showSection('pythia-cookbook')">Pythia OpenVisus Cookbook</a>
                    <a class="nav-link" href="#access-llc4320" onclick="showSection('access-llc4320')">Access LLC4320 ECCO Data</a>
                    <a class="nav-link" href="#access-dyamond" onclick="showSection('access-dyamond')">Access DYAMOND Data</a>
                    <a class="nav-link" href="#access-nex-gddp-cmip6" onclick="showSection('access-nex-gddp-cmip6')">Access NEX GDDP CMIP6 Data</a>

                </nav>
            </div>
        </div>

        <!-- Content Column -->
        <div class="col-md-9">
            <!-- Prerequisites Section -->
            <div id="prerequisites" class="section-content">
                <h2>Prerequisites</h2>
                <p>To provide progressive streaming capability for large datasets, the data has been converted to <a href="https://github.com/sci-visus/OpenVisus"  target="_blank">OpenVisus IDX format</a>.</p>

                <h3>Option 1: Using Conda</h3>
                <p>Download the <code>environment.yml</code> file from the <a href="https://github.com/ProjectPythia/nsdf-openvisus-cookbook" target="_blank">Pythia OpenVisus Cookbook GitHub repository</a> and use <code>conda</code> to create your environment. This will install all required libraries for data access and visualization.</p>
                <ol>
                    <li><strong>Step 1:</strong> Download <code>environment.yml</code> from <a href="https://github.com/ProjectPythia/nsdf-openvisus-cookbook/blob/main/environment.yml" target="_blank">here</a>.</li>
                    <li><strong>Step 2:</strong> Create the environment using conda:<br>
                        <pre><code class="language-bash">conda env create -f environment.yml</code></pre>
                    </li>
                    <li><strong>Step 3:</strong> Activate the environment:<br>
                        <pre><code class="language-bash">conda activate nsdf-cookbook</code></pre>
                    </li>
                </ol>
                <p>For more instructions on managing conda environments, see the <a href="https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html" target="_blank">official documentation</a>.</p>

                <h3>Option 2: Using pip</h3>
source .venv/bin/activate</code></pre>
                <p>If you prefer to use <code>pip</code>, you can create a Python virtual environment and install the minimal required libraries manually:</p>
                <ol>
                    <li><strong>Step 1:</strong> Create a new virtual environment:<br>
                        <pre><code class="language-bash">python -m venv .venv
source .venv/bin/activate</code></pre>
                    </li>
                    <li><strong>Step 2:</strong> Install the required libraries:<br>
                        <pre><code class="language-bash">python -m pip install jupyterlab matplotlib requests aiohttp bokeh panel xmltodict colorcet boto3 basemap OpenVisus openvisuspy </code></pre>
                    </li>
                </ol>
            </div>

            <!-- Data Access Section -->
            <div id="access-llc4320" class="section-content" style="display:none;">
            <h2>Binder</h2>
<p>You can use the following link to open the binder and try the notebooks. It might take a while if you are launching it for the first time</p>
      <a href="https://mybinder.org/v2/gh/sci-visus/sciviscontest2026/binder" target="_blank" class="btn btn-primary">Launch Binder</a>
                <h2>Access LLC4320 ECCO Data</h2>
                <p>Below are the steps based on the <a href="https://github.com/sci-visus/sciviscontest2026/blob/main/notebooks_examples">GitHub instructions</a>. Check out this <a href="https://github.com/sci-visus/sciviscontest2026/blob/main/notebooks_examples/ieee_scivis_llc4320.ipynb">Github Repo</a> for examples.</p>
                <ol>
                    <ul><strong>Step 1: Importing Libraries</strong></ul>
                    <pre><code class="language-bash">
import numpy as np
import matplotlib.pyplot as plt
import OpenVisus as ov
import openvisuspy as ovp
                    </code></pre>

                    <ul><strong>Step 2: Define the field you want to access</strong></ul>
                    <pre><code class="language-python">
#available options=[salt, theta,  w]; choose one below.. lets say, we select w for now 
variable = 'w'

#or direct links
temperature="pelican://osg-htc.org/nasa/nsdf/climate1/llc4320/idx/theta/theta_llc4320_x_y_depth.idx"

salinity="pelican://osg-htc.org/nasa/nsdf/climate1/llc4320/idx/salt/salt_llc4320_x_y_depth.idx"

vertical_velocity="pelican://osg-htc.org/nasa/nsdf/climate2/llc4320/idx/w/w_llc4320_x_y_depth.idx"
</code></pre>
<ul><strong>Step 3: Load the IDX metadata:</strong>
In this section, you can select any variables that you can declared in the cells above and replace it inside LoadDataset. We are just reading the metadata for the dataset here. </ul>
<pre><code class="language-bash">
# Step 3: Load the 4320 dataset from OSDF.. if  salt or theta is selected above, change climate2 to climate1 below, or directly use the variable defined above.

field= f"pelican://osg-htc.org/nasa/nsdf/climate2/llc4320/idx/w/w_llc4320_x_y_depth.idx"

db=ovp.LoadDataset(field).   # or replace field with variable defined above like temperature, salinity
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
data3D=db.db.read(time=0,quality=data_resolution, z=[0,1])  # Since the data is very large, I am only extracting one level.
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
<h4>Binder</h4>
<p>You can use the following link to open the binder and try the notebooks. It might take a while if you are launching it for the first time</p>
      <a href="https://mybinder.org/v2/gh/sci-visus/sciviscontest2026/binder" target="_blank" class="btn btn-primary">Launch Binder</a>
<p>Below are the steps to access the DYAMOND Atmospheric (GEOS) data. Check out this <a href="https://github.com/sci-visus/sciviscontest2026/blob/main/notebooks_examples/ieee_scivis_dyamond_geos.ipynb">github repo</a> for more jupyter notebook examples.</p>

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
variable = 'u'
face=0
    </code></pre>

    <ul><strong>Step 3: Load the IDX metadata</strong></ul>
    <p>This step allows you to read the metadata for the selected field. You can replace the variable in the URL to choose the data you want:</p>
    <pre><code class="language-python">
field= f"https://nsdf-climate3-origin.nationalresearchplatform.org:50098/nasa/nsdf/climate3/dyamond/GEOS/GEOS_{variable.upper()}/{variable.lower()}_face_{face}_depth_52_time_0_10269.idx"

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
                <p>Below are the steps based on the <a href="https://github.com/sci-visus/sciviscontest2026/blob/main/notebooks_examples/ieee_scivis_dyamond_ocean.ipynb">GitHub instructions</a>:</p>
                <ol>
                    <ul><strong>Step 1: Importing Libraries</strong></ul>
                    <pre><code class="language-bash">
import numpy as np
import matplotlib.pyplot as plt
import OpenVisus as ov
import openvisuspy as ovp
                    </code></pre>

                    <ul><strong>Step 2: Define the field you want to access</strong></ul>
                    <pre><code class="language-python">
#available options=[salt, theta, u, v, w]; choose one below
variable = 'salt'
</code></pre>
<ul><strong>Step 3: Load the IDX metadata:</strong>
In this section, you can select any variables that you can declared in the cells above and replace it inside LoadDataset. We are just reading the metadata for the dataset here. </ul>
<pre><code class="language-bash">
# Step 3: Load the LLC2160 dataset from OSDF

variable='salt' # options are: u,v,w,salt,theta

base_url= "https://nsdf-climate3-origin.nationalresearchplatform.org:50098/nasa/nsdf/climate3/dyamond/"
if variable=="theta" or variable=="w":
    base_dir=f"mit_output/llc2160_{variable}/llc2160_{variable}.idx"
elif variable=="u":
    base_dir= "mit_output/llc2160_arco/visus.idx"
else:
    base_dir=f"mit_output/llc2160_{variable}/{variable}_llc2160_x_y_depth.idx"

field= base_url+base_dir

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

    <h3>3. Access NEX GDDP CMIP6 Data</h3>
    <p>We demonstrate how to load the data from the NEX-GDDP-CMIP6 dataset using OpenVisus and visualize it with matplotlib. Additionally, you can save the plotted data to a file. In just a few lines of Python code, you can generate a plot as shown in Figure 3.1. Feel feel to try it from binder or quarto(link at the bottom). You can use the following below to open the binder and try the notebooks. It might take a while if you are launching it for the first time</p>

      <a href="https://mybinder.org/v2/gh/sci-visus/sciviscontest2026/binder" target="_blank" class="btn btn-primary">Launch Binder</a>
    <h3>3.1 Table of Contents</h3>
    <ul>
        <li>3.1 <a href="#notebook-code">Notebook Code</a></li>
        <li>3.1.1 <a href="#load-data">Loading the Data</a></li>
        <li>3.1.2 <a href="#plot-data">Plotting and Saving Data</a></li>
    </ul>

    <h3 id="notebook-code">3.1 Notebook Code</h3>
    <p>Below is a sample Jupyter notebook to load one timestep of a selected variable and display it using matplotlib.
    Use this <a href="https://github.com/sci-visus/sciviscontest2026/blob/main/notebooks_examples/ieee_scivis_cmip6.ipynb"> github example </a> as a reference.</p>

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
    <p>Check out this NEX GDDP CMIP6 <a href="https://chpc3.nationalsciencedatafabric.org:12347/dashboards"  target="_blank">Dashboard</a> we deployed for interactive exploration and visualization of the dataset. This dashboard allows users to select variables, timesteps, and generate visualizations interactively.</p>

    <h3 id="quarto">Quarto Documentation</h3>
    <p>Check out this  <a href="https://aashishp.quarto.pub/nex-gddp-cmip6/"  target="_blank">Quarto documentation</a> for more details on accessing the NEX-GDDP-CMIP6 data. The documentation includes step-by-step instructions for loading and visualizing climate model data using Python and OpenVisus.</p>
</div>


            <!-- Pythia Cookbook Section -->
            <div id="pythia-cookbook" class="section-content" style="display:none;">
                <h2><b>Pythia OpenVisus Cookbook</b></h2>

                <div style="display:flex;align-items:center;margin-bottom:16px;">
                    <img src="../assets/img/projectpythia.svg" alt="Project Pythia Logo" style="height:60px;">
                    <a href="https://projectpythia.org/nsdf-openvisus-cookbook/" target="_blank" style="margin-left:20px; background-color:#007bff; color:#fff; padding:10px 20px; border-radius:5px; text-decoration:none; font-weight:600; font-size:16px;">Open Pythia Cookbook</a>
                </div>
                <p>
                    The <a href="https://projectpythia.org/nsdf-openvisus-cookbook/" target="_blank">Pythia OpenVisus Cookbook</a> provides a comprehensive guide to working with large-scale scientific data using OpenViSUS. It includes working Jupyter notebooks, conda environment setup, and practical workflows for data access, analysis, and visualization.
                </p>
                <h4>Motivation</h4>
                <p>OpenViSUS enables interactive analysis and visualization of petabyte-scale scientific datasets on any device. The cookbook teaches efficient storage, querying, and visualization using hierarchical Z-order data layouts.</p>
                <h4>Main Sections</h4>
                <ul>
                    <li><strong>Preamble:</strong> How to cite the NSDF-OpenViSUS Cookbook.</li>
                    <li><strong>Introduction:</strong> Overview of the NSDF-OpenViSUS framework and its role in scientific data visualization.</li>
                    <li><strong>NASA DYAMOND Datasets (C1440–LLC2160):</strong> Workflows for visualizing and analyzing NASA DYAMOND atmospheric and ocean datasets.</li>
                    <li><strong>ECCO LLC4320 Datasets:</strong> Visualization and analysis of the ECCO LLC4320 ocean dataset, including data access and interactive exploration.</li>
                </ul>
                <h4>Running the Notebooks</h4>
                <ul>
                    <li><strong>On Binder:</strong> Click the rocket icon in any chapter to launch an interactive Jupyter notebook in the cloud. No installation required.</li>
                    <li><strong>Locally:</strong> Clone the <a href="https://github.com/ProjectPythia/nsdf-openvisus-cookbook" target="_blank">GitHub repository</a>, create and activate the conda environment from <code>environment.yml</code>, and start JupyterLab in the <code>notebooks</code> directory.</li>
                </ul>
                <pre><code class="language-bash">
# Clone the repository
$ git clone https://github.com/ProjectPythia/nsdf-openvisus-cookbook
$ cd nsdf-openvisus-cookbook
# Create and activate the environment
$ conda env create -f environment.yml
$ conda activate nsdf-cookbook
# Start JupyterLab
$ cd notebooks
$ jupyter lab
</code></pre>
                <h4>References & Further Reading</h4>
                <ul>
                    <li><a href="https://nationalsciencedatafabric.org/" target="_blank">National Science Data Fabric</a></li>
                    <li><a href="https://github.com/sci-visus/OpenVisus" target="_blank">OpenVisus</a></li>
                    <li><a href="https://github.com/sci-visus/OpenVisuspy" target="_blank">OpenVisuspy</a></li>
                    <li><a href="https://arxiv.org/abs/2408.11831v1" target="_blank">Web-based Visualization and Analytics of Petascale data</a></li>
                    <li><a href="https://arxiv.org/abs/2009.03254" target="_blank">Interactive Visualization of Terascale Data in the Browser</a></li>
                    <li><a href="https://sci.utah.edu/publications/Kum2014a/KumarISC2014.pdf" target="_blank">Fast Multiresolution Reads of Massive Simulation Datasets</a></li>
                </ul>
                <p>For questions, contact Aashish Panta, Giorgio Scorzelli, or Valerio Pascucci.</p>
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
