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

The provision of pressurized and oxygenated air to the plenum is presently beyond the scope of this project. This problem can presumably be solved using standard compressors appropriate for medical air, pressure regulators, gas analyzers and proportioning valves.

PEX pipe is available in several colors: red, white, and blue. It might be feasible to implement several plena having different FiO2 levels, for example 40, 60, and 100% and corresponding colors like white blue and red to make it easier to find a desired concentration level.

The patient equipment for scenario 1 should provide the following functionality:

1) Adjustable inspiration pressure - This pressure regulator should accept oxygenated air with pressures from 25 to 50 PSI and output air at an inspiration pressure that can be adjusted over the range 0 to 45cm H20.
2) Breathing valve - In the simplest scenario, this valve is an electrical actuator that integrates both the inspiration function and the non-rebreathing functions. When the valve is activated, it connects the patient airway to the pressurized, oxygenated air while simultaneously blocking connection to the PEEP valve. Otherwise, it connects the patient airway to the PEEP valve.
3) PEEP valve - The PEEP valve provides adjustable minimum airway pressure ranging from 0 to 25 cm H20.
4) Presure relief valve. The pressure relief valve is aranged to relieve pressure on the patient airway exceeding 50 cm H20 in order to protect the patient lungs from damage if the sytem should fail.
5) Monitor port. The monitor port provides a two small tubing connections on either side of a minor restriction i the airway. The provide the option to monitor airway pressure and to estimate flow/base on the sensed pressure differential between the ports. Sensors like the Bosch BMP 280 could be used to extend the functionality of the basic dumb ventallator in several important ways: including pressure monitoring, tidal monitoring and more advanced breathing modes including patient initiated breathing.

In the most scalable implmentation, the actuators from multiple patients will be conected together and driven by a single controller such that all patients are forced to the same breathing rate. 

List of planned improvements for scenario 1:
* Use an Arduino to provide individually adjustable patient breathing rate and exspiration / inspiration (E/I) ratio. This can be done using any Arduino controller with MOSFET switches.
* Add a BMP 280 sensor and implement patient initiated breathing.
* Replace arduino control with Raspberry PI for more advanced functionality. Add tidal volume estimation & pressure / volume versus time graphics.

