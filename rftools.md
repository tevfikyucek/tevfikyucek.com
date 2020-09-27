---
layout: page
title: RF Tools
permalink: /rftools/
---


<p style="color:red">The information on this page is provided on an "as is" basis with no guarantees of completeness, accuracy, and usefulness. Use at your own risk.</p>


<script src='https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML' async></script>
      
<script>
const numInputs = document.querySelectorAll('input[type=number]')

numInputs.forEach(function (input) {
    input.addEventListener('change', function (e) {
    if (e.target.value == '') {
      e.target.value = 0
	}
	})
})

calculatewatts = function()
{
    var dbmvalue = parseFloat(document.getElementById('dBm').value);
    var mwatts = Math.pow(10, dbmvalue/10);
    var watts = mwatts/1000;
    document.getElementById('mwatts').value = mwatts.toFixed(2);
    document.getElementById('watts').value = watts.toFixed(2);
}

calculatedbm1 = function() 
{
    var mw_in = parseFloat(document.getElementById('mw_in').value)
    var dbm = 10*Math.log(mw_in)/Math.log(10)
    document.getElementById('dbm_out1').value = dbm.toFixed(2)
}

calculatedbm2 = function() 
{
    var w_in = parseFloat(document.getElementById('w_in').value)
    var dbm = 10*Math.log(w_in*1000)/Math.log(10)
    document.getElementById('dbm_out2').value = dbm.toFixed(2)
}

		calculatefspl = function() 
		{
    var distance_m = parseFloat(document.getElementById('distance').value);
    var distanceType = document.getElementById('distanceType').value;
    var frequency_mhz = parseFloat(document.getElementById('frequency').value);
    var frequencyType = document.getElementById('frequencyType').value;

    if (distanceType == 1) {
            distance_m = distance_m*1000
    }
    if (frequencyType == 1) {
            frequency_mhz = frequency_mhz*1000
    }
    var pl = 20*Math.log(distance_m)/Math.log(10)+20*Math.log(frequency_mhz)/Math.log(10)-27.55
    pl = pl.toFixed(2)
    document.getElementById('fspl').value = pl
		}

calculateantgain = function() 
		{
    

    var diameter_m = parseFloat(document.getElementById('diameter').value);
    var diameterType = document.getElementById('diameterType').value;
    var ant_frequency_mhz = parseFloat(document.getElementById('ant_frequency').value);
    var ant_frequencyType = document.getElementById('ant_frequencyType').value;
    var efficiency = document.getElementById('efficiency').value;
                                                  

    if (diameterType == 1) {
            diameter_m = diameter_m*0.3048
    }
    if (ant_frequencyType == 1) {
            ant_frequency_mhz = ant_frequency_mhz*1000
    }

    var lambda = 300000000/(ant_frequency_mhz*1000000)
    var A = Math.PI*diameter_m/lambda
    var gmax = 10*Math.log(efficiency/100*A*A)/Math.log(10)
    gmax = gmax.toFixed(2)
    document.getElementById('gmax').value = gmax
		}
                
                
onloadfunc = function() 
{
    calculatefspl()
    calculateantgain()
    calculatewatts()
    calculatedbm1()
    calculatedbm2()
}
</script>

  <body onload="onloadfunc()">



   
<h1>dBm to Watts/mWatts Conversion</h1>

<p>Formula: \(dBm = 10\log_{10} (Watts/1000)\):</p>

<form onsubmit="return false" oninput="calculatewatts()">
    <input name="dBm" id="dBm" type="number" value="0"> dBm = 
		<strong><output name="watts" id="watts">X</output> W </strong> = 
    <strong><output name="mwatts" id="mwatts">X</output> mW </strong>
	</form>
<form onsubmit="return false" oninput="calculatedbm1()">
    <input name="mw_in" id="mw_in" type="number" value="1000"> mW = 
		<strong><output name="dbm_out1" id="dbm_out1">X</output> dBm </strong>
	</form>
<form onsubmit="return false" oninput="calculatedbm2()">
    <input name="w_in" id="w_in" type="number" value="1"> W = 
		<strong><output name="dbm_out2" id="dbm_out2">X</output> dBm </strong>
	</form>
<br>

	<h1>Free-Space Path Loss (FSPL) Calculation</h1>

	<p>Formula: \(FSPL = 20\log_{10}(d) + 20\log_{10}(f) + 20\log_{10}({4\pi \over c}) \):</p>

	
	<form onsubmit="return false" oninput="calculatefspl()">

    Distance:  <input name="distance" id="distance" type="number" min="0" value="1">    
		<select id="distanceType">
			<option value="0">Meters</option>
			<option value="1" selected="selected">Kilometers</option>
		</select>
		<br/>
    Frequency: <input name="frequency" id="frequency" type="number" min="0" value="6"> 
		<select id="frequencyType">
			<option value="0">MHz</option>
			<option value="1" selected="selected">GHz</option>
		</select>
		<br/>
		FSPL = <strong><output name="fspl" id="fspl">X</output> dB </strong>
	</form>
<br>

	<h1>Parabolic Antenna Gain Calculation</h1>

	<p>Formula: \(G_{max} = 10\log_{10}\big( ({\pi*D \over \lambda})^2 * e \big) \):</p>

	<form onsubmit="return false" oninput="calculateantgain()">

    Diameter:  <input name="diameter" id="diameter" type="number" min="0" value="8">    
		<select id="diameterType">
        <option value="0">Meters</option>
			<option value="1" selected="selected">Feet</option>
		</select>
		<br/>
    Frequency: <input name="ant_frequency" id="ant_frequency" type="number" min="0" value="6"> 
		<select id="ant_frequencyType">
			<option value="0">MHz</option>
			<option value="1" selected="selected">GHz</option>
		</select>
		<br/>
    Efficiency: <input name="efficiency" id="efficiency" type="number" min="1" max="100" value="55"> %
		<br/>
		Antenna Gain = <strong><output name="gmax" id="gmax">X</output> dB </strong>
	</form>
<br>

<h1>Links to ITU Recommendations:</h1>
<ol>
    <li><a href="https://www.itu.int/dms_pubrec/itu-r/rec/p/R-REC-P.2109-0-201706-I!!PDF-E.pdf">ITU-R P.2109-0</a>, Prediction of <u>building entry loss</u></li>
    <li><a href="https://www.itu.int/dms_pubrec/itu-r/rec/p/R-REC-P.2108-0-201706-I!!PDF-E.pdf">ITU-R P.2108-0</a>, Prediction of <u>clutter loss</u></li>
    <li><a href="https://www.itu.int/dms_pubrec/itu-r/rec/p/R-REC-P.530-17-201712-I!!PDF-E.pdf">ITU-R P.530-17</a>, Propagation data and <u>prediction methods</u> required for the design of terrestrial line-of-sight systems</li>
    <li><a href="https://www.itu.int/dms_pubrec/itu-r/rec/f/R-REC-F.699-8-201801-I!!PDF-E.pdf">ITU-R F.699-8</a>, Reference radiation <u>patterns for fixed wireless system antennas</u> for use in coordination studies and interference assessment in the frequency range from 100 MHz to 86 GHz</li>
    <li><a href="https://www.itu.int/dms_pubrec/itu-r/rec/f/R-REC-F.1245-3-201901-I!!PDF-E.pdf">ITU-R F.1245-3</a>, Mathematical model of average and related <u>radiation patterns for point-to-point fixed wireless system antennas</u> for use in interference assessment in the frequency range from 1 GHz to 86 GHz</li>

</ol>

<h1>Frequency Allocation Tables:</h1>
<ol>
    <li><a href="https://transition.fcc.gov/oet/spectrum/ituregions.pdf">ITU Regions</a></li>
    <li><a href="https://transition.fcc.gov/oet/spectrum/table/fcctable.pdf">FCC</a></li>
    <li><a href="https://www.efis.dk/reports/ReportDownloader?reportid=1">Europe</a></li>
</ol>

<h1>6 GHz Related Links:</h1>
<ol>
    <li><a href="https://docs.fcc.gov/public/attachments/FCC-18-147A1.pdf">FCC 18-147</a>, FCC Notice of Proposed Rulemaking (NPRM), 2019-10-24</li>
    <li><a href="https://www.fcc.gov/ecfs/search/filings?proceedings_name=18-295&q=(proceedings.name:((6%20gh*))%20OR%20proceedings.description:((6%20gh*)))&sort=date_disseminated,DESC">FCC OET Docket 18-295</a>, Unlicensed Use of the 6 GHz Band</li>
    <li><a href="https://www.ecodocdb.dk/download/cc03c766-35f8/ECC%20Report%20302.pdf">CEPT ECC Report 302</a>, Sharing and compatibility studies related to Wireless Access Systems including Radio Local Area Networks (WAS/RLAN) in the 5925-6425 MHz, 2019-03-29</li>
</ol>

<img src="https://hitcounter.pythonanywhere.com/count/tag.svg" alt="Hits">
