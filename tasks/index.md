---
layout: default
title: Tasks
permalink: /tasks/home
redirect_from: /tasks/index.html
sectionid: tasks
---

<div class="container">
    <h1>Contest Tasks</h1>
    <p>Welcome to the tasks page for the 2026 SciVis Contest. </p  >

    <div class="task-section">
        <p>To stand out, participants are encouraged to develop <strong>innovative visualization techniques</strong> that go beyond simple maps. Think creatively. </p>
        <p>
        While completion of all tasks is not required, participants are encouraged to tackle at least one or more of Tasks 1-3 alongside interactive tool development to create a competitive submission. Task 0 is foundational exploration to get familiar with the dataset. That said, you do not need to strictly adhere to the defined tasks. If your visualizations are complex and innovative while leveraging the provided datasets, you are encouraged to pursue your own creative direction.</p>
    </div>

    <div class="row">
        <!-- Sidebar Column -->
        <div class="col-md-3">
            <div class="sidebar-box">
                <nav class="nav flex-column">
                    <a class="nav-link active" href="#task0" onclick="showTask('task0')">Task 0: Climate Change Exploration</a>
                    <a class="nav-link" href="#task1" onclick="showTask('task1')">Task 1: Wind Patterns</a>
                    <a class="nav-link" href="#task2" onclick="showTask('task2')">Task 2: Coupled Atmosphere-Ocean Systems</a>
                    <a class="nav-link" href="#task3" onclick="showTask('task3')">Task 3: 3D Ocean Circulation</a>
                </nav>
            </div>
        </div>

        <!-- Content Column -->
        <div class="col-md-9">
            <!-- Task 0 -->
            <div id="task0" class="task-content">
                <h2>Task 0: Exploring Climate Change with NEX GDDP CMIP6 Data</h2>
                
                <!-- Overview -->
                <div class="task-section">
                    <h3>Overview</h3>
                    <p>Visualize how air temperature changes over time from 2015 to 2100 using NEX GDDP CMIP6 data, exploring patterns and variations across different regions.</p>
                </div>


                <!-- Dataset -->
                <div class="task-section">
                    <h3>Dataset</h3>
                    <p>NEX GDDP CMIP6 Data</p>
                </div>

                <!-- Instructions -->
                <div class="task-section">
                    <h3>Instructions</h3>
                    <ul>
                        <li>Create visualizations showing air temperature changes over time.</li>
                        <li>Explore how humidity varies across different regions globally.</li>
                    </ul>
                </div>

                <!-- Variables -->
                <div class="task-section">
                    <h3>Variables</h3>
                    <p>Air temperature, humidity</p>
                </div>

                <!-- Dashboard Example -->
                <div class="task-section">
                    <h3>Dashboard Example</h3>
                    <p>Check out the dashboard for more details: <a href="https://chpc3.nationalsciencedatafabric.org:12347/dashboards" target="_blank">Dashboard</a></p>
                </div>
            </div>

            <!-- Task 1 -->
            <div id="task1" class="task-content" style="display:none;">
                <h2>Task 1: Visualizing Wind Patterns in the Atmosphere (DYAMOND GEOS Data)</h2>
                
                <!-- Overview -->
                <div class="task-section">
                    <h3>Overview</h3>
                    <p>Visualize global atmospheric wind patterns using eastward (U) and northward (V) wind velocities to understand atmospheric circulation at different levels.</p>
                </div>

                <!-- Dataset -->
                <div class="task-section">
                    <h3>Dataset</h3>
                    <p>DYAMOND GEOS Data</p>
                </div>

                <!-- Instructions -->
                <div class="task-section">
                    <h3>Instructions</h3>
                    <ul>
                       
                        <li>Create dynamic visualizations of atmospheric circulations using the U (eastward wind) and V (northward wind) variables. Add other relevant variables as appropriate. Check out the <i>Data</i> tab for more available variables. </li>
                    </ul>
                </div>

                <!-- Variables -->
                <div class="task-section">
                    <h3>Variables</h3>
                    <p>U (eastward wind), V (northward wind), W (vertical velocity)</p>
                </div>
            </div>

            <!-- Task 2 -->
            <div id="task2" class="task-content" style="display:none;">
                <h2>Task 2: Coupled Atmosphere-Ocean Systems</h2>
                
                <!-- Overview -->
                <div class="task-section">
                    <h3>Overview</h3>
                    <p>Visualize the interactions between atmospheric dynamics and ocean conditions, focusing on wind patterns, temperature, and currents.</p>
                </div>

                <!-- Dataset -->
                <div class="task-section">
                    <h3>Dataset</h3>
                    <p>NASA DYAMOND Data</p>
                </div>

                <!-- Instructions -->
                <div class="task-section">
                    <h3>Instructions</h3>
                    <ul>
                        <li>Use atmospheric variables (U, V, P, T) and ocean variables (Theta, u, v, salt) to visualize interactions between atmosphere and ocean. These variables are mentioned for reference only; feel free to use any other variables as appropriate.</li>
                    </ul>
                </div>

                <!-- Variables -->
                <div class="task-section">
                    <h3>Variables</h3>
                    <p>
                        <strong>Atmospheric Data:</strong> U (eastward wind), V (northward wind), P (mid-level pressure), T (air temperature)<br>
                        <strong>Ocean Data:</strong> Theta (sea-surface temperature), u, v (east-west and north-south velocities), salt (salinity)
                    </p>
                </div>

                <!-- Dashboard Example -->
                <div class="task-section">
                    <h3>Dashboard Example</h3>
                    <p>Sample use case: <a href="https://chpc3.nationalsciencedatafabric.org:11857/run" target="_blank">Use case</a></p>
                </div>
            </div>

            <!-- Task 3 -->
            <div id="task3" class="task-content" style="display:none;">
                <h2>Task 3: 3D Ocean Circulation Patterns with Depth</h2>
                
                <!-- Overview -->
                <div class="task-section">
                    <h3>Overview</h3>
                    <p>Visualize the complex 3D structure of thermohaline circulation by mapping ocean temperature and salinity together.</p>
                </div>

                <!-- Dataset -->
                <div class="task-section">
                    <h3>Dataset</h3>
                    <p>ECCO LLC4320 Dataset</p>
                </div>

                <!-- Instructions -->
                <div class="task-section">
                    <h3>Instructions</h3>
                    <ul>
                        <li>Use W, theta (temperature), and salinity variables to visualize 3D ocean circulation patterns.</li>
                        <li>Highlight major circulation systems, such as thermohaline circulation.</li>
                    </ul>
                </div>

                <!-- Variables -->
                <div class="task-section">
                    <h3>Variables</h3>
                    <p> theta (temperature), salinity</p>
                </div>
            </div>

            </div>
        </div>
    </div>
</div>

<script>
function showTask(taskId) {
    // Hide all task contents
    document.querySelectorAll('.task-content').forEach(function(content) {
        content.style.display = 'none';
    });

    // Show the selected task content
    document.getElementById(taskId).style.display = 'block';

    // Remove 'active' class from all links
    document.querySelectorAll('.nav-link').forEach(function(link) {
        link.classList.remove('active');
    });

    // Add 'active' class to clicked link
    document.querySelector('a[href="#' + taskId + '"]').classList.add('active');
}
</script>
