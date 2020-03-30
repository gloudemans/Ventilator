# Ventilator
This repository contains design artifacts for several ventilator components that could be mass produced to provide emergency ventillation of COVID-19 patients experiencing acute respiratory distress syndrome (ARDS). The designs target clinically relevant functionality for treatment of ARDS (http://www.ardsnet.org/files/ventilator_protocol_2008-07.pdf). That functionality includes mechanically assisted ventiallation of the patient with air having an elevated fraction of inspired oxygen (FiO2) and the provision of controlled positive end expiratory pressure (PEEP). The designs include a pressure relief valve to protect the lungs from damage due to overpressurization (barotrauma).

There are many initatives developing ventilator solutions to address the acute need presented by the COVID-19 epidemic. This work addresses a concern that these initiatives may be immediately sclable to the degree necessary to materially contribute to patient care during the COVID--19 epidemic.

An objective of this project is to propose solutions that can materially help and that can realistically scale to support hundreds of thousands of patients in a few weeks. Time is by far the most challenging constraint because most high-tech components (brushless DC motors, microcontrollers like the Raspberry pi or Arduino) cannot really be procured in sufficient volume to address the worlwide need in a near instant timeframe. To the degree possible, this project will utilize common materials like alumimum, acetal, wire, screws, and so forth that are available immeidately in almost unlimited volume.

Scenario 1: The unit is being deployed in a field hospital where there are on the order of 1000 patients in close proximity. One potential solution includes central oxygenation and distribution of pressurized air with regulated pressure and FiO2 through one or more air plena with local taps for each patient. The patient equipment would provide adjustable regulated inspiration pressure, adjustable PEEP, and a breathing air solenoid with rate controller.
In this scenario, we could choose central distribution through wide plena at low pressure or narrow plena at high pressure. If we size the plena for 100 people breating 10 liters per minute over a 200 foot length, the flow rate is 100 liters per minute or 35 cubic feet per minute. With wide plena, we might use a pressure of 80cm H20 and desire that this not fall below 60cm H20 at the patient tap. A delta of 20cm H20 is equal to 0.79 in H20. Using this calculator (https://www.engineeringtoolbox.com/duct-friction-pressure-loss-d_444.html) we see that a 3 inch plenum has approximately the required capacity. PVC pipe is one possible plenum material that could be used for this purpose. It is available everywhere (Home Depot, Menards, Lowes, etc) in large quantity. Three inch PVC pipe has an actual inside diamter of 3 inches. Some other materials with 3 inch nominal size have reduce inside diameter.

Nominal PVC dimensions: https://www.pvcfittingsonline.com/resource-center/pvc-pipe-dimensions-18-through-24/

In the high pressure case we might regulate the input pressure to the plenum at 50 psi and allow it to range between 50 and 25 psi at the patient tap. Using this calaculator we see that 200 feet of 0.875 inch pipe provides 35 CFM with roughly 25 psi of loss. https://www.rapidairproducts.com/technical-faq/flow-rate-calculator. One inch PEX plumbing pipe has a nominal interior diamter of 0.875 inches, so this pipe has roughly the desired capacity. PEX tubing is also a ubiquitous material available at the same places that would supply PVC. In the high pressure distribution case, we could also consider a star topology in which the plenum feeds one or more branch plena which in turn branch to individual patients. There are monay otther plumbing pipes that could be used as alternatives: polyethylene, PVC, CPVC, copper, iron, etc. PEX can be asembled without glued fittings alleviating concerns about solvent vapor in the piping.

Nominal PEX dimensions: https://www.pexuniverse.com/pex-tubing-technical-specs

If we assume that in either case patients would be tapped off uniformly along the pipe, the capacity of the pipe is improved somewhat so there would be additional margin in those cases.

Of these two, the materials and connections for the high pressure distribution aproach are much easier to manage due to their lower weight and bulk and greater flexibility. We'll assume that the target scenario is served by a one inch PVC plenum tapped by ten branches to serve 10 patients each. The size of branch tubing can optionally be reduced. For example, a 50 feet branch of half inch nominal PEX loses 5 psi at 10 CFM / 280 lpm so could potentially serve on the rder of 28 patients.


(a branch with 485 Depending on their length and number of connected patients, smaller half inch nominal) PEX (0.481 inch actual) delivers could be sufficient. 

would be sufficient.

PEX may .

These branches could optionally have further pressure 



in 10 lances 


allow the pressure to fluctuate between


https://www.agorize.com/en/challenges/code-life-challenge

The provision of pressured and oxygenated air is presently beyond the scope of this project. In some circumstances, a shop vac

central air and Central provision and pressure regualtion of the air is Provision 
a breathing air solenoid and conroller,  prressure apparatus would further regulate the pressure to the therapeutic level for the individual. The patient equipment would , provide gating.

to a controlled level  an in

to local patient taps.

,

In this case, a potential solution is to run one or more ~constant pressure air plena from a centralized source. The air plena could be either low pressure (80cm H20) large diameter (several inches) or higher pressure (~5-50 psi) low diameter (~1 inch). Large diameter options might include four inch PVC pipes with glued connections or sewer main with gasketed connections. (I have seen prohibitions against using PVC in ventilator circuits under ordinary circumstances, but whatever the rationale it may not apply in this dire case.) Smaller diameter pipe could be PVC, copper or PEX. The pipe should be size


Aluminum or iron pipe might also be acceptable though less readily sourced. Rapidair provides aluminized shop air tubing that could an alternative.) The pipe should have the capacity to transport breathing air required by hundreds of patients over hundreds of feet without significant pressure loss. Using equipment beyond the scope of this project the main would be centrally pressurized to ~80 cm H20 by medical air and oxygenated to a therapeutic FiO2. The rationale for 80cm H20 is that this pressure level is one suggested level for pressure relief valve setting to prevent barotrauma. If the plenum pressure is below this level, then failure of a patient pressure regulator would be unlikely to cause barotrauma. 

specific  and The main would be pressurized to


with glued or gasthat can readily be procured at building stores.



and there are literally hundreds of patients 

at sufficient scale in 

hundreds of thousand of units be scaled
This project 

to the degree 

The ventilator is 



(valtio while protecting the patient against 

oxygen supplemented air 

for ARDS 

provide s only the bare minimum functionality for treatment of ARDS which includes non-rebreathing  most useful functionality for the ARDSThe design(s) support several potential use cases:

1) Controlled FiO2 air is available at ~60 cm H20. In this case, required ventillator functions include pressure modulation, rebreathing mitigation, and PEEP.

modulation of the 

supplied to the blower unit. In this case, the control unit changes blower speed to control volume and pressure over the breathing cucle

the blower modulates breathingblower modulates breathing by 

Medical air and medical oxygen are combined  

1) The patient 

In order to provide maximum flexibility, these componenmultiple assemblies support 3 basic use cases:

1) The 


the designs  comprise 3 physical assemblies: 

Y-assembly 
* Pressure-relief valve
* Flow and pressure monitor ports
* Non-rebreathing valve ()
* Positive-end-expiratory pressure (PEEP) valve
* Optional




, mixing-valve.



1) 



