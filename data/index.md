---
layout: default
title: Data Page
permalink: /data/home
redirect_from: /data/index.html
sectionid: data
---

<div class="container">
    <h1>Data for 2026 Data Challenge</h1>
    <p>Welcome to the data page for the 2026 Data Challenge. Select a dataset to view the details:</p>

    <div class="row">
        <!-- Sidebar Column -->
        <div class="col-md-3">
            <div class="sidebar-box">
                <nav class="nav flex-column">
                    <a class="nav-link active" href="#data1" onclick="showData('data1')">ECCO LLC4320 Data</a>
                    <a class="nav-link" href="#data2" onclick="showData('data2')">DYAMOND Data</a>
                    <a class="nav-link" href="#data3" onclick="showData('data3')">NEX GDDP CMIP6 Data</a>
                </nav>
            </div>
        </div>

        <!-- Content Column -->
        <div class="col-md-9">
            <div id="data1" class="data-content">
                <h2>ECCO LLC4320 Data</h2>
                <p><strong>Description:</strong> High-resolution ocean data from the ECCO project.</p>
                <ul>
                    <li>Time steps: 10,000+</li>
                    <li>Variables: Sea surface height, temperature, salinity, etc.</li>
                    <li>Resolution: ~1km</li>
                </ul>
                <a href="#" class="btn btn-primary">Download ECCO LLC4320 Data</a>
            </div>

            <div id="data2" class="data-content" style="display:none;">
                <h2>DYAMOND Data</h2>
                <p><strong>Description:</strong> Global storm-resolving atmospheric simulation data.</p>
                <ul>
                    <li>Variables: Wind speed, humidity, precipitation, etc.</li>
                    <li>Models: ICON, NICAM, etc.</li>
                </ul>
                <a href="#" class="btn btn-primary">Download DYAMOND Data</a>
            </div>

            <div id="data3" class="data-content" style="display:none;">
                <h2>NEX GDDP CMIP6 Data</h2>
                <p><strong>Description:</strong> Climate projections data derived from CMIP6 models.</p>
                <ul>
                    <li>Variables: Temperature, precipitation, etc.</li>
                    <li>Time steps: 50,000+</li>
                </ul>
                <a href="#" class="btn btn-primary">Download NEX GDDP CMIP6 Data</a>
            </div>
        </div>
    </div>
</div>

<script>
function showData(dataId) {
    document.querySelectorAll('.data-content').forEach(function(content) {
        content.style.display = 'none';
    });

    document.getElementById(dataId).style.display = 'block';

    document.querySelectorAll('.nav-link').forEach(function(link) {
        link.classList.remove('active');
    });

    document.querySelector('a[href="#' + dataId + '"]').classList.add('active');
}
</script>
