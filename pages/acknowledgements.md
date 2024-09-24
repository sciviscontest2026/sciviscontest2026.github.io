---
layout: default
title: Acknowledgements
permalink: /acknowledgements/
sectionid: acknowledgements
---

<div class="container">
    <h1>Acknowledgements</h1>
    <p>We gratefully acknowledge the support and contributions from the following organizations:</p>

    <div class="row">
        <!-- Organization Names -->
        <div class="col-md-4">
            <ul class="acknowledgement-list">
                <li class="hover-link" data-logo="nsdf"><a href="https://nationalsciencedatafabric.org/" target="_blank">National Science Data Fabric (NSDF)</a></li>
                <li class="hover-link" data-logo="nasa"><a href="https://www.nas.nasa.gov/hecc/" target="_blank">NASA ARC</a></li>
                <li class="hover-link" data-logo="nasajpl"><a href="https://www.jpl.nasa.gov/" target="_blank">NASA JPL</a></li>
                <li class="hover-link" data-logo="seal"><a href="https://sealstorage.io/" target="_blank">SEAL Storage</a></li>
                <li class="hover-link" data-logo="osg"><a href="https://osg-htc.org/" target="_blank">OSG Consortium</a></li>
                <li class="hover-link" data-logo="visoar"><a href="https://visoar.net/" target="_blank">ViSOAR</a></li>
                <li class="hover-link" data-logo="wired"><a href="https://resilience.utah.edu/" target="_blank">Wired Global Center</a></li>
                <li class="hover-link" data-logo="nsf"><a href="https://www.nsf.gov/" target="_blank">National Science Foundation</a></li>
            </ul>
        </div>

        <!-- Images -->
        <div class="col-md-8">
            <div class="row floating-images-container">
                <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://nationalsciencedatafabric.org/" target="_blank">
                        <img id="nsdf" src="{{ '/assets/img/nsdf.png' | relative_url }}" alt="NSDF" class="img-fluid logo-img">
                    </a>
                </div>
                <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://www.nas.nasa.gov/hecc/" target="_blank">
                        <img id="nasa" src="{{ '/assets/img/nasa.png' | relative_url }}" alt="NASA" class="img-fluid logo-img">
                    </a>
                </div>
                <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://www.jpl.nasa.gov/" target="_blank">
                        <img id="nasajpl" src="{{ '/assets/img/nasajpl.png' | relative_url }}" alt="NASA JPL" class="img-fluid logo-img">
                    </a>
                </div>
                
            </div>
            
            <div class="row">
            <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://sealstorage.io/" target="_blank">
                        <img id="seal" src="{{ '/assets/img/seal.png' | relative_url }}" alt="SEAL" class="img-fluid logo-img">
                    </a>
                </div>
                <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://osg-htc.org/" target="_blank">
                        <img id="osg" src="{{ '/assets/img/OSG-logo.svg' | relative_url }}" alt="OSG Logo" class="img-fluid logo-img">
                    </a>
                </div>
                <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://visoar.net/" target="_blank">
                        <img id="visoar" src="{{ '/assets/img/visoar.png' | relative_url }}" alt="ViSOAR" class="img-fluid logo-img">
                    </a>
                </div>

            </div>
                <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://resilience.utah.edu/" target="_blank">
                        <div class="logo-container wired-bg">
                            <img id="wired" src="{{ '/assets/img/wired.png' | relative_url }}" alt="Wired" class="img-fluid logo-img">
                        </div>
                    </a>
                </div>
            <div class="row">
                <div class="col-md-4 col-sm-6 text-center">
                    <a href="https://www.nsf.gov/" target="_blank">
                        <img id="nsf" src="{{ '/assets/img/nsf.webp' | relative_url }}" alt="NSF" class="img-fluid logo-img">
                    </a>
                </div>
            </div>
        </div>
    </div>
</div>

<style>
/* General styling for the logos */
.logo-img {
    max-width: 200px;
    margin: 20px auto;
    display: block;
    transition: transform 0.3s ease, filter 0.3s ease;
}

.logo-img:hover {
    transform: scale(1.4);
    filter: brightness(1.02);
}

.img-fluid {
    max-width: 100%;
    height: auto;
}

.wired-bg {
    background-color: #000;
    padding: 20px;
    border-radius: 8px;
}

/* Flexbox for floating images */
.floating-images-container {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
}

/* Acknowledgement list styling */
.acknowledgement-list {
    list-style: none;
    padding-left: 0;
    font-size: 18px;
}

.acknowledgement-list li {
    margin-bottom: 15px;
    background-color: #f8f9fa; /* Light background */
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); /* Subtle shadow */
    transition: background-color 0.3s ease, box-shadow 0.3s ease;
    border-left: 4px solid transparent; /* A colored accent border */
}

.acknowledgement-list a {
    text-decoration: none;
    color: #007bff;
    transition: color 0.3s ease;
    display: block;
}

.acknowledgement-list a:hover {
    color: #0056b3;
    font-weight: bold;
}

.acknowledgement-list li:hover {
    background-color: #e9ecef;
    border-left: 4px solid #007bff; /* Accent color on hover */
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15); /* Deeper shadow on hover */
}

/* Highlighting the logos when the corresponding name is hovered */
.hovered {
    transform: scale(1.2);
    filter: brightness(1.2);
}

</style>

<script>
// JavaScript to handle hover effects for names and corresponding logos
document.querySelectorAll('.hover-link').forEach(function(item) {
    item.addEventListener('mouseenter', function() {
        const logoId = this.getAttribute('data-logo');
        document.getElementById(logoId).classList.add('hovered');
    });
    item.addEventListener('mouseleave', function() {
        const logoId = this.getAttribute('data-logo');
        document.getElementById(logoId).classList.remove('hovered');
    });
});
</script>
