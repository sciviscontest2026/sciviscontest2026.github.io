---
layout: default
title: Data Page
permalink: /data/home
redirect_from: /data/index.html
sectionid: data
---

<div class="container">
    <h1>Data for 2026 SciVis Contest</h1>
    <p>Select a dataset to view the details:</p>

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
        <!-- ECCO LLC4320 Data -->
        <div id="data1" class="data-content">
            <h2>ECCO LLC4320 Data</h2>
            <p><strong>Overview:</strong> This page provides access to hourly data from the Estimating the Circulation and Climate of the Ocean (ECCO, <a href="https://ecco-group.org"> https://ecco-group.org</a>) Project's 1/48° Massachusetts Institute of Technology general circulation model (MITgcm, <a href="https://mitgcm.org"> https://mitgcm.org</a>) simulation, a 14-month global simulation of the ocean (September 2011 to November 2012) that resolves internal tides and admits submesoscale and internal-gravity-wave variability.</p>
            <h3>Significance</h3>
            <p></p>


        <h3>Data</h3>
        <p><strong>Variables:</strong> The dataset includes various oceanographic variables, each available at 90 different depth levels. These depths represent model layers from the sea surface down to deeper ocean levels. Select the level below to get its corresponding depth from the sea surface in meters:</p>

<!-- Dropdown for depth levels -->
<select id="depth-level" onchange="showDepth()" style="width:15%;">
    <option value="">Select a level</option>
    <!-- Generate options for levels 1-90 -->
    <option value="0.5">Level 1</option>
    <option value="1.6">Level 2</option>
    <option value="2.8">Level 3</option>
    <option value="4.2">Level 4</option>
    <option value="5.8">Level 5</option>
    <option value="7.6">Level 6</option>
    <option value="9.7">Level 7</option>
    <option value="12">Level 8</option>
    <option value="14.7">Level 9</option>
    <option value="17.7">Level 10</option>
    <option value="21.1">Level 11</option>
    <option value="25">Level 12</option>
    <option value="29.3">Level 13</option>
    <option value="34.2">Level 14</option>
    <option value="39.7">Level 15</option>
    <option value="45.8">Level 16</option>
    <option value="52.7">Level 17</option>
    <option value="60.3">Level 18</option>
    <option value="68.7">Level 19</option>
    <option value="78">Level 20</option>
    <option value="88.2">Level 21</option>
    <option value="99.4">Level 22</option>
    <option value="112">Level 23</option>
    <option value="125">Level 24</option>
    <option value="139">Level 25</option>
    <option value="155">Level 26</option>
    <option value="172">Level 27</option>
    <option value="190">Level 28</option>
    <option value="209">Level 29</option>
    <option value="230">Level 30</option>
    <option value="252">Level 31</option>
    <option value="275">Level 32</option>
    <option value="300">Level 33</option>
    <option value="325">Level 34</option>
    <option value="352">Level 35</option>
    <option value="381">Level 36</option>
    <option value="410">Level 37</option>
    <option value="441">Level 38</option>
    <option value="473">Level 39</option>
    <option value="507">Level 40</option>
    <option value="541">Level 41</option>
    <option value="576">Level 42</option>
    <option value="613">Level 43</option>
    <option value="651">Level 44</option>
    <option value="690">Level 45</option>
    <option value="730">Level 46</option>
    <option value="771">Level 47</option>
    <option value="813">Level 48</option>
    <option value="856">Level 49</option>
    <option value="900">Level 50</option>
    <option value="946">Level 51</option>
    <option value="992">Level 52</option>
    <option value="1040">Level 53</option>
    <option value="1089">Level 54</option>
    <option value="1140">Level 55</option>
    <option value="1192">Level 56</option>
    <option value="1246">Level 57</option>
    <option value="1302">Level 58</option>
    <option value="1359">Level 59</option>
    <option value="1418">Level 60</option>
    <option value="1480">Level 61</option>
    <option value="1544">Level 62</option>
    <option value="1611">Level 63</option>
    <option value="1681">Level 64</option>
    <option value="1754">Level 65</option>
    <option value="1830">Level 66</option>
    <option value="1911">Level 67</option>
    <option value="1996">Level 68</option>
    <option value="2086">Level 69</option>
    <option value="2181">Level 70</option>
    <option value="2281">Level 71</option>
    <option value="2389">Level 72</option>
    <option value="2503">Level 73</option>
    <option value="2626">Level 74</option>
    <option value="2757">Level 75</option>
    <option value="2898">Level 76</option>
    <option value="3050">Level 77</option>
    <option value="3215">Level 78</option>
    <option value="3392">Level 79</option>
    <option value="3584">Level 80</option>
    <option value="3792">Level 81</option>
    <option value="4019">Level 82</option>
    <option value="4266">Level 83</option>
    <option value="4535">Level 84</option>
    <option value="4828">Level 85</option>
    <option value="5148">Level 86</option>
    <option value="5499">Level 87</option>
    <option value="5882">Level 88</option>
    <option value="6301">Level 89</option>
    <option value="6760">Level 90</option>
</select>
    <p id="depth-display"></p>

        <p>The depths are distributed to capture surface processes more finely while still representing the deeper ocean layers, ensuring both near-surface and deep ocean dynamics are well resolved.</p>

            <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>Field Name</th>
                        <th>Data Type</th>
                        <th>Unit</th>
                        <th>Standard Name</th>
                        <th>Shape</th>
                        <th>Dimensions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>u</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>Sea-surface east-west velocity</td>
                        <td>(17280, 12960, 90)</td>
                        <td> Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>v</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>Sea-surface north-south velocity</td>
                        <td>(17280, 12960, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>w</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>Sea-surface vertical velocity</td>
                        <td>(17280, 12960, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>theta</td>
                        <td>float32</td>
                        <td>°C</td>
                        <td>Sea-surface Temperature</td>
                        <td>(17280, 12960, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>salt</td>
                        <td>float32</td>
                        <td>g kg-1</td>
                        <td>Sea Water Salinity</td>
                        <td>(17280, 12960, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                </tbody>
            </table>
            <p><strong>Resolution:</strong> 1/48° horizontal grid (~2 km), 90 vertical levels</p>
            <p><strong>How to Access:</strong> Access via <a href="#">ECCO Data Portal</a></p>
            <h3>Jupyter Notebook</h3>
            <p>Use the <a href="#">ECCO LLC4320 Jupyter Notebook</a> for interactive exploration and analysis of the dataset.</p>
        </div>

        <div id="data2" class="data-content" style="display:none;">
            <h2>DYAMOND Data</h2>
            <p><strong>Overview:</strong> The DYnamics of the Atmospheric general circulation Modeled On Non-hydrostatic Domains (DYAMOND)  data provides high resolution ocean circulation models, offering unprecedented detail. This dataset comprises a C1440 configuration of the Goddard Earth Observing System (GEOS) atmospheric model, with 7-km horizontal grid spacing and 72 vertical layers, coupled to a LLC2160 configuration of the Massachusetts Institute of Technology general circulation model (MITgcm) with 2–4-km grid spacing and 90 vertical levels. The C1440-LLC2160 simulation has been integrated for 14 months, starting from prescribed initial conditions on January 20, 2020.   </p>
            <h3>Significance</h3>
            <p>This "nature" simulation provides a unique synthetic dataset for atmospheric and oceanic boundary layer studies and for satellite and in-situ observing system design.</p>
            <h3>Data</h3>
            <p><strong>Variables:</strong> The dataset includes the combination of LLC2160 configuration of MITgcm ocean model and  c1440 configuration of GEOS model. These variables are shown below separately.</p>
            GEOS Atmospheric Data:
             The GEOS model uses cubed-sphere grid that helps improve the representation of the polar regions compared to traditional latitude-longitude grids. Thus, there are 6 faces available for each of its fields below.
            <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>Field Name</th>
                        <th>Data Type</th>
                        <th>Unit</th>
                        <th>Standard Name</th>
                        <th>Shape</th>
                        <th>Dimensions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>P</td>
                        <td>float32</td>
                        <td>Pa</td>
                        <td>mid level pressure</td>
                        <td>(1440, 1440, 51)</td>
                        <td> Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>U</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>eastward wind from level closest to surface</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>V</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>northward wind from level closest to surface</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                        <tr>
                        <td>W</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>vertical velocity from level closest to surface</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>T</td>
                        <td>float32</td>
                        <td>K</td>
                        <td>air temperature from level closest to surface</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>H</td>
                        <td>float32</td>
                        <td>m</td>
                        <td>mid layer heights from level closest to surface</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>CO</td>
                        <td>float32</td>
                        <td>mol mol-1</td>
                        <td>Carbon Monoxide (All Sources)</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>CO2</td>
                        <td>float32</td>
                        <td>mol mol-1</td>
                        <td>Carbon Dioxide (All Sources)</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>QI</td>
                        <td>float32</td>
                        <td>kg kg-1</td>
                        <td>mass fraction of cloud ice water from level closest to surface</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>QL</td>
                        <td>float32</td>
                        <td>kg kg-1</td>
                        <td>mass fraction of cloud liquid water from level closest to surface</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>RI</td>
                        <td>float32</td>
                        <td>m</td>
                        <td>ice phase cloud particle effective radius</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                                        <tr>
                        <td>RL</td>
                        <td>float32</td>
                        <td>m</td>
                        <td>liquid cloud particle effective radius</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>DELP</td>
                        <td>float32</td>
                        <td>Pa</td>
                        <td>pressure thickness</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>DTHDT</td>
                        <td>float32</td>
                        <td>Pa K s-1</td>
                        <td>pressure weighted potential temperature tendency due to moist</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>DTHDTCN</td>
                        <td>float32</td>
                        <td>K s-1</td>
                        <td>potential temperature tendency due to convection</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>FCLD</td>
                        <td>float32</td>
                        <td>1</td>
                        <td>cloud fraction for radiation</td>
                        <td>(1440, 1440, 51)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                </tbody>
            </table>
            LLC2160 Ocean Data:
             <table class="table table-bordered">
                <thead>
                    <tr>
                        <th>Field Name</th>
                        <th>Data Type</th>
                        <th>Unit</th>
                        <th>Standard Name</th>
                        <th>Shape</th>
                        <th>Dimensions</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>U</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>Sea-surface east-west velocity</td>
                        <td>(8640, 6480, 90)</td>
                        <td> Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>V</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>Sea-surface north-south velocity</td>
                        <td>(8640, 6480, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>W</td>
                        <td>float32</td>
                        <td>m s-1</td>
                        <td>Sea-surface vertical velocity</td>
                        <td>(8640, 6480, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>Theta</td>
                        <td>float32</td>
                        <td>°C</td>
                        <td>Sea-surface Temperature</td>
                        <td>(8640, 6480, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                    <tr>
                        <td>Salt</td>
                        <td>float32</td>
                        <td>g kg-1</td>
                        <td>Sea Water Salinity</td>
                        <td>(8640, 6480, 90)</td>
                        <td>Latitude, Longitude, Depth</td>
                    </tr>
                </tbody>
            </table>
            <p><strong>Resolution:</strong> 1/24° horizontal grid (~4 km), 90 vertical levels</p>
            <p><strong>How to Access:</strong> Access via <a href="https://github.com/aashishpanta0/IEEE_SciVis_Notebooks_Examples">Notebooks</a> or see <a href='{{ site.baseurl }}/examples/'>Examples<a> Tab.</p>
            <h3>Jupyter Notebook</h3>
            <p>Use the <a href="https://github.com/aashishpanta0/IEEE_SciVis_Notebooks_Examples/blob/main/ieee_scivis_dyamond_ocean-Copy1.ipynb">DYAMOND Jupyter Notebook</a> for interactive exploration and analysis of the dataset.</p>
        </div>


<!-- NEX GDDP CMIP6 Data -->
<div id="data3" class="data-content" style="display:none;">
    <h2>NEX GDDP CMIP6 Data</h2>
    <p><strong>Overview:</strong> The NEX-GDDP CMIP6 dataset consists of downscaled climate projections derived from the Coupled Model Intercomparison Project Phase 6 (CMIP6) and downscaled to a 0.25° x 0.25° grid (~25 km), providing finer spatial details suitable for regional climate impact studies. The dataset includes historical simulations (1950-2014) and future projections (2015-2100) based on different Shared Socioeconomic Pathways (SSPs), including SSP2-4.5, and SSP5-8.5, which represent different climate futures depending on societal responses to climate change.</p>

    <h3>Significance</h3>
    <p>The purpose of this dataset is to provide a set of global, high resolution, bias-corrected climate change projections that can be used to evaluate climate change impacts on processes that are sensitive to finer-scale climate gradients and the effects of local topography on climate conditions.</p>

    <h3>Models</h3>
    <p>The NEX-GDDP CMIP6 dataset integrates projections from multiple global climate models (GCMs) included in CMIP6, including models such as GFDL-ESM4, IPSL-CM6A-LR, and MRI-ESM2-0. These models represent a range of climate system behaviors and help provide a more robust assessment of future climate conditions.</p>

    <h3>Data</h3>
    <p><strong>Variables:</strong> The dataset includes key variables that capture changes in temperature, precipitation, and other climate phenomena. These variables are available for different time periods (historical and future projections) and under various SSPs.</p>

    <table class="table table-bordered">
        <thead>
            <tr>
                <th>Field Name</th>
                <th>Data Type</th>
                <th>Unit</th>
                <th>Standard Name</th>
                <th>Shape</th>
                <th>Dimensions</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>tas</td>
                <td>float32</td>
                <td>K</td>
                <td>Near-Surface Air Temperature</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
            <tr>
                <td>pr</td>
                <td>float32</td>
                <td>kg m-2 s-1</td>
                <td>Precipitation</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
            <tr>
                <td>rsds</td>
                <td>float32</td>
                <td>W/m²</td>
                <td>Surface Downwelling Shortwave Radiation</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
            <tr>
                <td>hurs</td>
                <td>float32</td>
                <td>%</td>
                <td>Near-Surface Relative Humidity</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
            <tr>
                <td>rlds</td>
                <td>float32</td>
                <td>W/m²</td>
                <td>Surface Downwelling Longwave Radiation</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
                <tr>
                <td>sfcWind</td>
                <td>float32</td>
                <td>m s-1</td>
                <td>Daily-Mean Near-Surface Wind Speed</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
            <tr>
                <td>tasmin</td>
                <td>float32</td>
                <td>K</td>
                <td>Daily Minimum Near-Surface Air Temperature</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
            <tr>
                <td>tasmax</td>
                <td>float32</td>
                <td>K</td>
                <td>Daily Maximum Near-Surface Air Temperature</td>
                <td>(600, 1440)</td>
                <td>Latitude, Longitude</td>
            </tr>
        </tbody>
    </table>
    <p> Currently Available Models: ACCESS-CM2, CanESM5, CESM2, CMCC-CM2-SR5, EC-Earth3, GFDL-ESM4, INM-CM5-0, IPSL-CM6A-LR, MIROC6, MPI-ESM1-2-HR, and MRI-ESM2-0</p>
    <p><strong>Resolution:</strong> 0.25° x 0.25° horizontal grid (~25 km)</p>
    <p><strong>More information about the dataset can be found in </strong><a href="https://planetarycomputer.microsoft.com/dataset/nasa-nex-gddp-cmip6#overview"  target="_blank">Microsoft Planetary Computer.</a></p>

    <h3>Dashboard</h3>
    <p>Check out this  <a href="http://chpc3.nationalsciencedatafabric.org:12345/dashboards"  target="_blank">NEX GDDP CMIP6 Dashboard</a> we deployed for interactive exploration and visualization of the dataset.</p>
    <h3>Jupyter Notebook</h3>
    <p>Check out this  <a href="https://aashishp.quarto.pub/nex-gddp-cmip6/"  target="_blank">Quarto documentation</a> for more details on accessing the data.</p>
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





function showDepth() {
    var depthValue = document.getElementById("depth-level").value;
    if (depthValue) {
        document.getElementById("depth-display").innerHTML = "Selected Depth: " + depthValue + " meters";
    } else {
        document.getElementById("depth-display").innerHTML = "";
    }
}
</script>
