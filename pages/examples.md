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
                    <a class="nav-link" href="#data-access" onclick="showSection('data-access')">Data Access</a>
                    <a class="nav-link" href="#visualization" onclick="showSection('visualization')">Visualization</a>
                </nav>
            </div>
        </div>

        <!-- Content Column -->
        <div class="col-md-9">
            <!-- Prerequisites Section -->
            <div id="prerequisites" class="section-content">
                <h2>Prerequisites</h2>
                <p>To provide progressive streaming capability for large datasets, the data has been converted to <a href="https://github.com/sci-visus/OpenVisus">OpenVisus IDX format</a>.</p>

                <p>Users can create a new Python environment and install the required libraries with the following steps:</p>
                Step 1: Create a new virtual enviroment using python
                <pre>
<code class="language-bash">
# Create a python virtual environment
python -m venv .venv
</code></pre>
Step 2: Activate the environment you just created
<pre><code class="language-bash">
# Activate the environment
source .venv/bin/activate
</code></pre>
Step 3: Install required libraries
<pre><code class="language-bash">
# Install required libraries
python -m pip install --verbose --no-cache --no-warn-script-location boto3 colorcet fsspec numpy imageio pympler==1.0.1 urllib3 pillow xarray xmltodict plotly requests scikit-image scipy seaborn tifffile pandas tqdm matplotlib zarr altair cartopy dash fastparquet folium geodatasets geopandas geoviews lxml numexpr scikit-learn sqlalchemy statsmodels vega_datasets xlrd yfinance pyarrow pydeck h5py hdf5plugin netcdf4 nexpy nexusformat nbgitpuller intake ipysheet ipywidgets bokeh ipywidgets-bokeh panel holoviews hvplot datashader vtk pyvista trame trame-vtk trame-vuetify notebook "jupyterlab==3.6.6" jupyter_bokeh jupyter-server-proxy jupyterlab-system-monitor "pyviz_comms>=2.0.0,<3.0.0" "jupyterlab-pygments>=0.2.0,<0.3.0" 
</code></pre>
Step 4: Install OpenVisus
<pre> <code class="language-bash">
# Install OpenVisus
python -m pip install OpenVisus
 </code></pre>

                <h3>Conda Environment File</h3>
                <p>For convenience, here is a conda environment file you can use to create the environment. Save it as a <code>environment.yml</code> file and create the environment using <code>conda env create -f environment.yml</code>.<br /> If you need more instructions on how to manage conda environments, please check the offical documentation <a href= "https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html">here. </a></p>
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
            <div id="data-access" class="section-content" style="display:none;">
                <h2>Data Access</h2>
                <p>You can access the datasets using the <code>OpenVisus</code> library:</p>
                <pre><code class="language-python">
import OpenVisus as ov

# Load the dataset
db = ov.LoadDataset("path/to/dataset")
print("Data loaded successfully!")
                </code></pre>
                <p>Make sure to review the dataset documentation for variable descriptions and time steps, as different datasets have different structures.</p>
            </div>

            <!-- Visualization Section -->
            <div id="visualization" class="section-content" style="display:none;">
                <h2>Visualization Example: Using Matplotlib</h2>
                <p>This page will provide resources on how to access the data, give examples of visualizations using <a href="https://matplotlib.org/">matplotlib</a>, and much more. Whether you're new to visualizing scientific data or looking for advanced techniques, you'll find valuable information below.</p>

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
