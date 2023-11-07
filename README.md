# A bio-inspired hardware implementation of a analog spike-based hippocampus memory model

<h2 name="Description">Description</h2>
<p align="justify">
Code on which the paper entitled "A bio-inspired hardware implementation of a analog spike-based hippocampus memory modely" is based, sent to a journal and awaiting review.
</p>
<p align="justify">
A fully functional analog spike-based implementation of a memory model bio-inspired on the hippocampus implemented on the <a href="https://ieeexplore.ieee.org/document/8094868">DYNAPSE1</a> hardware platform using the technology of the Spiking Neuronal Network (SNN) is presented. The code is written in Python and makes use of the Samna library and their adaptation for DYNAPSE1 called <a href="https://code.ini.uzh.ch/ncs/libs/dynap-se1">dynap-se1</a>. In addition, the necessary scripts to replicate the tests and plots carried out in the paper are included, together with data and plots of the tests.
</p>
<p align="justify">
Please go to section <a href="#CiteThisWork">cite this work</a> to learn how to properly reference the works cited here.
</p>


<h2>Table of contents</h2>
<p align="justify">
<ul>
<li><a href="#Description">Description</a></li>
<li><a href="#Article">Article</a></li>
<li><a href="#Instalation">Instalation</a></li>
<li><a href="#Usage">Usage</a></li>
<li><a href="#RepositoryContent">Repository content</a></li>
<li><a href="#CiteThisWork">Cite this work</a></li>
<li><a href="#Credits">Credits</a></li>
<li><a href="#License">License</a></li>
</ul>
</p>


<h2 name="Article">Article</h2>
<p align="justify">
<strong>Title</strong>: A bio-inspired hardware implementation of a analog spike-based hippocampus memory model

<strong>Abstract</strong>: The growing need for data has led to the demand for better computational systems by exploring alternative technologies. Neuromorphic engineering addresses this problem by developing computational systems that mimic biology to achieve the superior capabilities of the brain. However, neuromorphic memory systems remain a challenge with much work to be done. Among all brain regions, the hippocampus stands out as an alternative to attack this problem as an autoassociative memory capable of learning large amounts of information quickly and recalling it efficiently. In this work, we propose a computational spike-based memory model bio-inspired on the hippocampus that takes advantage of the benefits of an analog design: energy efficiency, robustness to noise and better real-time operation. This model is able to learn memories, recall them from a fragment and forget them. This model has been implemented on DYNAPSE1 using Spiking Neural Networks and a series of experiments have demonstrated its correct operation. This work presents the first hardware implementation on a special-purpose hardware platform for Spiking Neural Networks of a fully functional analog spike-based hippocampal bio-inspired memory model, paving the road for the development of future more complex neuromorphic systems.

<strong>Keywords</strong>: Hippocampus model, analogic memory model, spiking neural networks, Neuromorphic engineering, DYNAPSE

<strong>Author</strong>: Daniel Casanueva-Morato

<strong>Contact</strong>: dcasanueva@us.es
</p>


<h2 name="Instalation">Instalation</h2>
<p align="justify">
<ol>
	<li>Have or have access to the DYNAPSE1 hardware platform
	<li>Python version 3.8.10</li>
	<li>Python libraries:</li>
	<ul>
		<li><strong>samna</strong> 0.18.0.0</li>
		<li><strong>dynap-se1</strong> available in the <a href="https://code.ini.uzh.ch/ncs/libs/dynap-se1">gitlab repository</a></li>
		<li><strong>ctxctl_contrib</strong> available in the <a href="https://gitlab.com/neuroinf/ctxctl_contrib">gitlab repository</a></li>
		<li><strong>numpy</strong> 1.21.4</li>
		<li><strong>matplotlib</strong> 3.5.0</li>
	</ul>
</ol>
</p>

<h2 name="RepositoryContent">Repository content</h3>
<p align="justify">
<ul>
	<li><p align="justify"><a href="decoder_CA1.ipynb">decoder_CA1.ipynb</a>, <a href="encoder_DG_cascade.ipynb">encoder_DG_cascade.ipynb</a>, <a href="ca3_cascade_dg.ipynb">ca3_cascade_dg.ipynb</a> and <a href="ca3_cascade_dg_opt_time.ipynb">ca3_cascade_dg_opt_time.ipynb</a>: python notebooks containing the definition of the CA1, DG and the complete hippocampal memory models respectively. For the case of the hippocampal memory, two different models are attached, a base model (ca3_cascade_dg_opt_time.ipynb) and a model with the parameters configured in such a way as to optimise the operations carried out in time (ca3_cascade_dg_opt_time.ipynb). In addition, each notebook contains the tests that are carried out on each model.</p></li>
	<li><p align="justify"><a href="triplet_stdp_params.json">triplet_stdp_params.json</a> and <a href="triplet_stdp_params_opt.json">triplet_stdp_params_opt.json</a>: json file with the configuration parameters of the STDP learning mechanism for the base model (<a href="ca3_cascade_dg.ipynb">ca3_cascade_dg.ipynb</a>) and the time-optimised model (<a href="ca3_cascade_dg_opt_time.ipynb">ca3_cascade_dg_opt_time.ipynb</a>).</p></li>
	<li><p align="justify"><a href="results/">results</a> folder: contains the figures (.png) generated by all the tests of the different models, as well as files with the trace of modifications in the synaptic weight of CA3 during the operations performed (trace_.txt) and spikes generated by the network (events_.txt) during these tests. In the event file, the following can be found for each spike generated in the network: the time instant at which it occurred (timestamp_ms), the id of the neuron that generated it at the global level of the network (neuron_ids) as formatted at the local level of the population to which it belongs (neuron_ids_formated) and the tag associated with said neuron (event_tag) formed by the population to which the neuron that produces the spike belongs plus its local id.</li>
</ul>
</p>


<h2 name="Usage">Usage</h2>
<p align="justify">
To run the different experiments, it is necessary to install all the libraries indicated in the <a href="#Instalation">instalation</a> section, to have a local or online tool for running notebooks and to have access to a DYNAPSE1 board. Each cell of each notebook comments to a greater or lesser extent on what is happening in it. In general terms: connecting to the board, declaring the functions to be used during the definition of the network, defining the neural network itself, defining the learning mechanism, configuring the parameters of neurons and synapses per core of the board, elaborating and applying the tests to the model, taking and formatting the results network data and creating the figures with the data taken as a result of the test.
</p>

<p align="justify">
For this code to work, it is necessary to modify the local path to the "ctxctl_contrib" library in the first cell and the path to the STDP triplet mechanism parameter file in the configuration cell of this mechanism. If you want to modify between the different network sizes that have been tested for each model, modify the variable "exp_id" indicating which of all of them you want to test (immediately before the variable it is explained for each number which net size will be used). Finally, if you want to apply different tests on the network, modify the variable "experiment" indicating which of all the tests you want to apply.
</p>


<h2 name="CiteThisWork">Cite this work</h2>
<p align="justify">
Work in progress...
</p>


<h2 name="Credits">Credits</h2>
<p align="justify">
The author of the original idea is Daniel Casanueva-Morato while working on a research project of the <a href="http://www.rtc.us.es/">RTC Group</a>.

Daniel Casanueva-Morato would like to thank Giacomo Indiveri and his group for hosting him during a three-months internship between 1st June 2023 and 31th August 2023, during which this idea was originated and most of the results presented in this work were obtained.

This research was partially supported by project TED2021-130825B-I00. 

D. C.-M. was supported by a "Formación de Profesor Universitario" Scholarship and by "Ayuda complementarias de movilidad" from the Spanish Ministry of Education, Culture and Sport.
</p>


<h2 name="License">License</h2>
<p align="justify">
This project is licensed under the GPL License - see the <a href="https://github.com/dancasmor/A-bio-inspired-hardware-implementation-of-a-analog-spike-based-hippocampus-memory-model/blob/main/LICENSE">LICENSE.md</a> file for details.
</p>
<p align="justify">
Copyright © 2023 Daniel Casanueva-Morato<br>  
<a href="mailto:dcasanueva@us.es">dcasanueva@us.es</a>
</p>

[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](http://www.gnu.org/licenses/gpl-3.0)
