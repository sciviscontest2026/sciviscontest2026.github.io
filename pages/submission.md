---
layout: default
title: Submission
permalink: /submission/
sectionid: submission
---

<div class="container">
    <h1>Data Submission</h1>
    <p>Submit your results and models below. Make sure your submission follows the format outlined in the contest guidelines.</p>

    <form action="http://sci-visus.github.io/sciviscontest2026" method="post" enctype="multipart/form-data" class="submission-form">
        <div class="form-group">
            <label for="teamname">Team Name:</label>
            <input type="text" id="teamname" name="teamname" class="form-control" placeholder="Enter your team name" required>
        </div>

        <div class="form-group">
            <label for="task">Select Task:</label>
            <select id="task" name="task" class="form-control" required>
                <option value="" disabled selected>Select a task</option>
                <option value="1">Task 1: Predicting Ocean Currents</option>
                <option value="2">Task 2: Storm Prediction</option>
                <option value="3">Task 3: Climate Change Impact Analysis</option>
            </select>
        </div>

        <!-- Team Members -->
        <div class="form-group">
            <label for="members">Team Members:</label>
            <div id="team-members">
                <div class="team-member" id="member1">
                    <input type="text" name="member1" class="form-control" placeholder="Team Member 1" required>
                    <button type="button" class="btn remove-member-btn" onclick="removeMember(1)">Remove</button>
                </div>
            </div>
            <button type="button" id="add-member" class="btn btn-secondary">+ Add Member</button>
        </div>

        <div class="form-group">
            <label for="submission">Upload your file:</label>
            <input type="file" id="submission" name="submission" class="form-control file-input" required>
        </div>

        <div class="form-group text-center">
            <input type="submit" value="Submit" class="btn btn-primary">
        </div>
    </form>
</div>

<script>
let memberCount = 1;

document.getElementById('add-member').addEventListener('click', function() {
    if (memberCount < 6) {
        memberCount++;
        let newMemberField = document.createElement('div');
        newMemberField.classList.add('team-member');
        newMemberField.setAttribute('id', `member${memberCount}`);
        newMemberField.innerHTML = `
            <input type="text" name="member${memberCount}" class="form-control" placeholder="Team Member ${memberCount}" required>
            <button type="button" class="btn remove-member-btn" onclick="removeMember(${memberCount})">Remove</button>`;
        document.getElementById('team-members').appendChild(newMemberField);
    }

    if (memberCount === 6) {
        document.getElementById('add-member').style.display = 'none';
    }
});

function removeMember(id) {
    if (memberCount > 1) {
        document.getElementById(`member${id}`).remove();
        memberCount--;
        document.getElementById('add-member').style.display = 'inline-block'; 
    }
}
</script>
