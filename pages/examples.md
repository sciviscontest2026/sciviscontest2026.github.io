---
layout: default
title: Examples
permalink: /examples/
sectionid: examples
---

<div class="container">
    <h1>Example Resources for Data Access and Visualization</h1>

    <p>This page will provide resources on how to access the data, give examples of visualizations using <a href="https://matplotlib.org/">matplotlib</a>, and much more. Whether you're new to visualizing scientific data or looking for advanced techniques, you'll find valuable information below.</p>

    <h2>Data Access</h2>
    <p>To access the data provided for the SciVis contest, you can use the following steps:</p>
    <ol>
        <li>Go to the <a href="/sciviscontest2026/data/">Data Page</a> where you will find links to datasets like <strong>NASA ECCO LLC4320</strong> and <strong>DYAMOND</strong>.</li>
        <li>Use the provided download links to access specific datasets.</li>
        <li>Make sure to review the variable descriptions and time steps for each dataset, as they vary significantly in scale and detail.</li>
    </ol>

    <h2>Visualization Example: Using Matplotlib</h2>
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
