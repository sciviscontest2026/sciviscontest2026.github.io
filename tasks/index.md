---
layout: default
title: Welcome
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
                    <a class="nav-link active" href="#task1" onclick="showTask('task1')">Task 1: Predicting Ocean Currents</a>
                    <a class="nav-link" href="#task2" onclick="showTask('task2')">Task 2: Storm Prediction</a>
                    <a class="nav-link" href="#task3" onclick="showTask('task3')">Task 3: Climate Change Impact</a>
                </nav>
            </div>
        </div>

        <!-- Content Column -->
        <div class="col-md-9">
            <div id="task1" class="task-content">
                <h2>Task 1: Predicting Ocean Currents (ECCO LLC4320 Data)</h2>
                <ul>
                    <li>Objective: Use ECCO LLC4320 data to forecast ocean current patterns.</li>
                    <li>Required Variables: Sea surface height, temperature, salinity.</li>
                    <li>Evaluation: RMSE between predicted and actual data.</li>
                </ul>
            </div>

            <div id="task2" class="task-content" style="display:none;">
                <h2>Task 2: Storm Prediction (DYAMOND Data)</h2>
                <ul>
                    <li>Objective: Predict upcoming storm events using DYAMOND Data.</li>
                    <li>Required Variables: Wind speed, precipitation.</li>
                    <li>Evaluation: Accuracy of storm predictions.</li>
                </ul>
            </div>

            <div id="task3" class="task-content" style="display:none;">
                <h2>Task 3: Climate Change Impact Analysis (NEX GDDP CMIP6 Data)</h2>
                <ul>
                    <li>Objective: Analyze climate model predictions for the year 2100.</li>
                    <li>Required Variables: Temperature, precipitation.</li>
                    <li>Evaluation: Percentage deviation from baseline projections.</li>
                </ul>
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
