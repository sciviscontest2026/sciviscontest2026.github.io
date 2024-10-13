---
layout: default
title: Tasks
permalink: /tasks/home
redirect_from: /tasks/index.html
sectionid: tasks
---

<div class="container">
    <h1>Contest Tasks</h1>
    <p>Welcome to the tasks page for the 2026 Data Challenge. Select a task to view the details:</p>

    <div class="row">
        <!-- Sidebar Column -->
        <div class="col-md-3">
            <div class="sidebar-box">
                <nav class="nav flex-column">
                    <a class="nav-link active" href="#task0" onclick="showTask('task0')">Task 0: Climate Change Exploration</a>
                    <a class="nav-link" href="#task1" onclick="showTask('task1')">Task 1: Wind Patterns</a>
                    <a class="nav-link" href="#task2" onclick="showTask('task2')">Task 2: Extreme Weather Events</a>
                    <a class="nav-link" href="#task3" onclick="showTask('task3')">Task 3: 3D Ocean Circulation</a>
                    <a class="nav-link" href="#task4" onclick="showTask('task4')">Task 4: Open Exploration </a>
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
                    <p>Visualize how air temperature changes over time from 1950 to 2100 using NEX GDDP CMIP6 data, exploring patterns and variations across different regions.</p>
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
                    <p>Check out the dashboard for more details: <a href="http://chpc3.nationalsciencedatafabric.org:12346/dashboards" target="_blank">Dashboard</a></p>
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
                        <li>Generate vector field visualizations showing wind direction and magnitude.</li>
                        <li>Create a dynamic visualization illustrating atmospheric circulation patterns.</li>
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
                <h2>Task 2: Visualizing the Interaction Between Atmosphere and Ocean During Extreme Weather Events</h2>
                
                <!-- Overview -->
                <div class="task-section">
                    <h3>Overview</h3>
                    <p>Explore the interaction between atmospheric dynamics and ocean conditions during extreme weather events like tropical storms or hurricanes, focusing on wind patterns, temperature, and currents.</p>
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
                        <li>Focus on regions where extreme events occur (e.g., cyclones or monsoons).</li>
                        <li>Visualize the interplay between wind patterns, temperature, and ocean currents.</li>
                        <li>Emphasize interactions between atmospheric wind patterns and sea-surface temperatures or currents.</li>
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
                    <p>Sample use case: <a href="http://chpc3.nationalsciencedatafabric.org:11857/run" target="_blank">Use case</a></p>
                </div>
            </div>

            <!-- Task 3 -->
            <div id="task3" class="task-content" style="display:none;">
                <h2>Task 3: 3D Ocean Circulation Patterns with Depth</h2>
                
                <!-- Overview -->
                <div class="task-section">
                    <h3>Overview</h3>
                    <p>Visualize the complex 3D structure of ocean currents by mapping velocity fields (u, v, w) at different depths, highlighting circulation patterns and their vertical structure.</p>
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
                        <li>Create layered visualizations showing changes in ocean currents with depth.</li>
                        <li>Highlight major circulation systems, such as thermohaline circulation.</li>
                    </ul>
                </div>

                <!-- Variables -->
                <div class="task-section">
                    <h3>Variables</h3>
                    <p>U, V, W, theta (temperature), salinity</p>
                </div>
            </div>

            <!-- Task 4 -->
            <div id="task4" class="task-content" style="display:none;">
                <h2>Task 4: Explore and Innovate (Open-Ended Task)</h2>
                
                <!-- Overview -->
                <div class="task-section">
                    <h3>Overview</h3>
                    <p>Participants are invited to explore any of the provided datasets in creative and innovative ways. The goal is to generate novel visualizations that offer new insights into the data without being restricted to a specific problem or task.</p>
                </div>

                <!-- Instructions -->
                <div class="task-section">
                    <h3>Instructions</h3>
                    <ul>
                        <li>Use any variables, dimensions, or time ranges from the datasets.</li>
                        <li>Combine multiple datasets for a multidisciplinary visualization.</li>
                    </ul>
                </div>

                <!-- Deliverable -->
                <div class="task-section">
                    <h3>Deliverable</h3>
                    <p>A unique and innovative visualization providing fresh insights, along with an explanation of the approach used.</p>
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
