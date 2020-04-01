# Ventilator

This repository contains design artifacts for several ventilator components that could be mass produced to provide emergency ventilation of COVID-19 patients experiencing acute respiratory distress syndrome (ARDS). The designs target clinically relevant functionality for treatment of ARDS (http://www.ardsnet.org/files/ventilator_protocol_2008-07.pdf). That functionality includes mechanically assisted ventilation of the patient with air having an elevated fraction of inspired oxygen (FiO2) and the provision of controlled positive end expiratory pressure (PEEP). The designs include a pressure relief valve to protect the lungs from damage due to over pressurization (barotrauma).

There are many initiatives developing ventilator solutions to address the acute need presented by the COVID-19 epidemic. This work addresses a concern that these initiatives may be immediately scalable to the degree necessary to materially contribute to patient care during the COVID--19 epidemic.

An objective of this project is to propose solutions that can materially help and that can realistically scale to support hundreds of thousands of patients in a few weeks. Time is by far the most challenging constraint because most high-tech components (brushless DC motors, microcontrollers like the Raspberry pi or Arduino) cannot really be procured in sufficient volume to address the worldwide need in a near instant timeframe. To the degree possible, this project will utilize common materials like aluminum, acetal, wire, screws, and so forth that are available immediately in almost unlimited volume.

## Scenario 1

The unit is being deployed in a field hospital where there are on the order of 1000 patients in proximity. One potential solution includes central oxygenation and distribution of pressurized air with regulated pressure and FiO2 through one or more air plena with local taps for each patient. The patient equipment would provide adjustable regulated inspiration pressure, adjustable PEEP, and a breathing air solenoid with rate controller. In this scenario, we could choose central distribution through wide plena at low pressure or narrow plena at high pressure. If we size the plena for 100 people breathing 10 liters per minute over a 200 foot length, the flow rate is 100 liters per minute or 35 cubic feet per minute. With wide plena, we might use a pressure of 80cm H20 and desire that this not fall below 60cm H20 at the patient tap. A delta of 20cm H20 is equal to 0.79 in H20. Using this calculator (https://www.engineeringtoolbox.com/duct-friction-pressure-loss-d_444.html) we see that a 3 inch plenum has approximately the required capacity. PVC pipe is one possible plenum material that could be used for this purpose. It is available everywhere (Home Depot, Menards, Lowes, etc.) in large quantity. Three-inch PVC pipe has an actual inside diameter of 3 inches. Some other materials with 3 inch nominal size have reduce inside diameter.

Nominal PVC dimensions: https://www.pvcfittingsonline.com/resource-center/pvc-pipe-dimensions-18-through-24/

In the high pressure case we might regulate the input pressure to the plenum at 50 psi and allow it to range between 50 and 25 psi at the patient tap. Using this calculator we see that 200 feet of 0.875 inch pipe provides 35 CFM with roughly 25 psi of loss. https://www.rapidairproducts.com/technical-faq/flow-rate-calculator. One inch PEX plumbing pipe has a nominal interior diameter of 0.875 inches, so this pipe has roughly the desired capacity. PEX tubing is also a ubiquitous material available at the same places that would supply PVC. In the high pressure distribution case, we could also consider a star topology in which the plenum feeds one or more branch plena which in turn branch to individual patients. There are many otther plumbing pipes that could be used as alternatives: polyethylene, PVC, CPVC, copper, iron, etc. PEX can be assembled without glued fittings alleviating concerns about solvent vapor in the piping.

Nominal PEX dimensions: https://www.pexuniverse.com/pex-tubing-technical-specs

If we assume that in either case patients would be tapped off uniformly along the pipe, the capacity of the pipe is improved somewhat so there would be additional margin in those cases.

Of these two, the materials and connections for the high-pressure distribution approach are much easier to manage due to their lower weight and bulk and greater flexibility. We'll assume that the target scenario is served by a one-inch PVC plenum tapped by ten branches to serve 10 patients each. The size of branch tubing can optionally be reduced. For example, a 50 feet branch of half inch nominal PEX loses 5 psi at 10 CFM / 280 liters per minute so could potentially serve on the order of 28 patients.

The provision of pressurized and oxygenated air to the plenum is presently beyond the scope of this project. This problem can presumably be solved using standard compressors appropriate for medical air, pressure regulators, gas analyzers and proportioning valves.

PEX pipe is available in several colors: red, white, and blue. It might be feasible to implement several plena having different FiO2 levels, for example 40, 60, and 100% and corresponding colors like white blue and red to make it easier to find a desired concentration level.

The patient equipment for scenario 1 should provide the following functionality:
* Adjustable inspiration pressure - This pressure regulator should accept oxygenated air with pressures from 25 to 50 PSI and output air at an inspiration pressure that can be adjusted over the range 0 to 45cm H20.
* Breathing valve - In the simplest scenario, this valve is an electrical actuator that integrates both the inspiration function and the non-rebreathing functions. When the valve is activated, it connects the patient airway to the pressurized, oxygenated air while simultaneously blocking connection to the PEEP valve. Otherwise, it connects the patient airway to the PEEP valve.
* PEEP valve - The PEEP valve provides adjustable minimum airway pressure ranging from 0 to 25 cm H20.
* Pressure relief valve. The pressure relief valve is arranged to relieve pressure on the patient airway exceeding 50 cm H20 in order to protect the patient lungs from damage if the system should fail.
* Monitor port - The monitor port provides two small tubing connections on either side of a minor restriction i the airway. The provide the option to monitor airway pressure and to estimate flow/base on the sensed pressure differential between the ports. Sensors like the Bosch BMP 280 could be used to extend the functionality of the basic dumb ventilator in several important ways: including pressure monitoring, tidal monitoring and more advanced breathing modes including patient-initiated breathing.

In the initial most scalable implementation, the actuators from multiple patients will be connected and driven by a single controller such that all patients are breath in unison. This is not therapeutically optimum and may be uncomfortable for the patients, but individualized breathing control comes at the cost of increased complexity and reduced scalability.

List of planned optional improvements for scenario 1:
* Use an Arduino to provide individually adjustable patient breathing rate and expiration / inspiration (E/I) ratio. This can be done using any Arduino controller with MOSFET switches.
* Add a BMP 280 sensor and implement patient-initiated breathing.
* Replace Arduino control with Raspberry PI for more advanced functionality. Add tidal volume estimation & pressure / volume versus time graphics.

## Design notes:
### Pressure Regulator
The pressure regulator is designed to accomodate input pressures from 20 psig to 100 psig while providing regulated output from 0 to 45 cm H20. In order to minimize potential harm if the regulator should fail, the input flows through a 0.060 inch orifice designed to limit flow to 40 liters per minute (1.4 CFM) at 20 psig since this is sufficient to accomodate peak inflow during inspiration. This flow rate estimate and orifice diameter are based on the calculator at https://www.tlv.com/global/US/calculator/air-flow-rate-through-orifice.html. The design uses a simple lever as a diaphragm with atmospheric pressure on one side and regulator output on the other. The force applied to the lever is thus proportional to the output pressure and is effectively applied in the center of the longer lever arm. The lever provides mechanical advantage to close the input valve. Output pressure pushes on the diaphragm / lever to close the input valve. In order to adjust the output pressure to zero, the input valve must be designed so that high input pressure cannot force it open (move the lever). To a first approximation, a sliding gate valve has this property. A spring mechanism exterts pressure on the lever tending to open the input valve, but when sufficient pressure exists to overcome that pressure the lever moves back and closes the input valve. The output pressure is thus proportional to the pressure applied by the adjustment spring. If we design the mechanism to reduce motion at the valve by a factor of 5 and recall that the output pressure is effectively applied at the middle of the long side of the lever, the long side of the lever should be about 10 times the length of the short side where the short side is defined as the distance from the pivot to the orifice. This geometry also requires that the long end move roughly 10 * 0.060 or 0.60 inches to fully open the valve. In order to guard against potential oscillation it is useful to add damping or negative feedback to the control loop.

## Other thoughts:
* In scenario 1, the design should allow a pathogen filter to be inserted between the pressure regulator output and the rest of the device. This is necessary to protect the input plenum from potential contamination.
* Ideally the design will be milled from one inch nominal acetal / delrin stock. It will have a clear polycarbonate cover screwed on with stainless screws. The polycarbonate can be laser cut and marked with pressure gauge gradations.
* It may be desirable to collect the vent air from each pressure gage. It seems like there is some possibility that the gauge vents would emit aerosolized virus leaking past the pistons.
It may be desirable to protect the pressure regulator vent from contamination, and it is important to protect it from blockage since a blocked vent will interfere with pressure regulation.
* Pressure gauges can use coil springs and a square piston for extreme simplicity.
* It may be possible to combine the passive non-rebreathing valve with the voice coil design so that the same hardware can be used with a modulated blower or a fixed pressure source. Of course, a modulated blower will have electronics which could also control the voice coil so this feature might be superfluous.
* A useful enhancement would be to include two pressurized gas ports so that the device could use either a premixed FiO2 cocktail or mix the oxygen and air internally. This would probably entail two pressure regulators to reduce the inlet pressures and a pressure balanced mixing regulator to blend the remaining gases with an adjustable bias on the balancing diaphragm.
* Might be useful to include a switch that gets pressed with each breath. That switch could be routed to a watchdog timer and report an alarm on timeout.
* The force produced by a voice coil actuator is a function of the winding geometry and the current. In principal, the coil doesn't use any power unless it is both applying a force and moving at the same time. In practice, maintaining force while not moving incurs I^2R losses, so designing a voice coil actuator is crudely a matter of first figuring out the required winding geometry, number of turns, and current and then sizing wire so that I^2R losses won't excessively heat the wire or consume more than budgeted power from the source than. Of course the geometry and the wire are linked, so there is feedback required to reconcile the two.


