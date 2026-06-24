# Odessa City-Centre Evacuation DSS
## Overview
The Odessa Model is an agent-based Decision Support System pilot adapted to civilian-evacuation mobility during geopolitical-conflict disruptions to critical infrastructure. Unlike the other three AntifragiCity pilots, Odessa is the framework's unique application to mobility needs during current geopolitical conflicts, where disruptions extend beyond environmental hazards to include systemic threats to civilian safety .
The model serves one operative purpose: mobility related to the evacuation of the city centre following an attack on the adjacent port area. Specifically, the developed scenario involves the second phase of an evacuation plan, where civilians already gathered at the shelters are instructed to proceed with their evacuation from the area .
The model's distinctive design twist is the introduction of a dynamic transformation rule: civilians start in shelters as residents and transform into the corresponding agent — a pedestrian or a car — only after selecting their transport mode towards the evacuation point . This delayed-agent-instantiation rule lets the same model represent a shelter-confined population and a road-network-active population in a single coherent simulation.
________________________________________
## Key Features
🗺️ City-Centre Topology with Building Passages
The model integrates the entire road network of the city centre, including building passages and pathways in parks, sourced from OpenStreetMaps and processed in QGIS 3.40 .
This is a finer-grained graph than the other pilots: building passages and park pathways serve as critical escape corridors when the primary road network is partially disrupted .

🏢 Bomb-Shelter Capacity Layer
The model also integrates the locations and capacities of the bomb shelters currently available in the city of Odessa, as mapped by the local municipality (reference 54) .
The city evacuation plans were not publicly available; therefore, the rendered evacuation points were assumed for modelling purposes .

🚶 Mode-Switching Civilians (Residents → Pedestrian / Car)
Dynamic agents entail the civilians in the shelters, identified as 'residents'. These agents can then select their transport mode towards the evacuation point and transform accordingly into the corresponding agent — a 'pedestrian' or a 'car' .
This rule preserves the resemblance of the model to the underlying real-world conditions by treating shelter-confined occupants and on-the-move evacuees as fully fungible through mode choice, while keeping the stay-in-shelter agents (those who cannot or choose not to evacuate) part of the same simulation.

🛡️ Autonomous Responders Agent Class
A new agent breed — responders — is introduced in the response strategies. Responders are autonomous agents that locate and collect vulnerable population to facilitate their safe transit through secured corridors, thereby mitigating the exposure of high-risk individuals .

🔁 Real-Time Pathfinding with A*
The simulation employs the A algorithm to continuously re-evaluate these trajectories*, ensuring agents adapt to real-time road accessibility shifts such as path obstructions or saturation .

📊 Configurable Parameters & Scenarios
Parameter	Description
Modal share (pedestrian / car)	Distribution of evacuees' choice to evacuate on foot or by car 

Response delay	Time elapsed between receiving evacuation instruction and beginning movement 

Traffic pattern	User-defined traffic intensity during evacuation 

Vulnerability share	Fraction of evacuees flagged with lower transit velocity 

🎯 Response Strategies
The model implements intervention strategies through the introduction of 'responders' as autonomous agents that locate and collect vulnerable population:
R1 — Base responder deployment: standard prioritization of vulnerable extraction through secured corridors.
R2 — Enhanced responder routing: extends the responder coverage subset with adaptive repositioning.
R3 — Pairs high-capacity responder routing with a corridor-prioritization scheme to safeguard escape routes.
Exact formulation should be cross-checked against Section 5.3.4.2 in the parent deliverable .

📈 Built-In KPI Dashboard
The model tracks the KPIs defined in Deliverable D2.3 :
KPI	Measures
Throughput (M)	Number of evacuees reached the evacuation points in the forecast horizon
Efficiency (S)	Performance of the evacuation network under real-time perturbations
Redundancy (R)	Availability of alternative escape pathways given corridor saturation
Entropy (Q)	Satisfaction / psychological-stress level of the evacuees and vulnerable subgroup
Equity indices	Serviceability stratifications across the vulnerable group
________________________________________
## Empirical Foundation
Road and pathway network — OpenStreetMaps + QGIS 3.40 geolocation pipeline .
Bomb-shelter locations and capacities — local municipality mapping (reference 54) .
Evacuation-point locations — assumed for modelling purposes because published city evacuation plans were not available .
Modelling approach — relied on similar work on evacuation scenarios in urban contexts (references 55–57), including the A* pathfinding formulation 
Vulnerability taxonomy — people with disabilities, mobility impairments, age extremes, disadvantaged and socio-economic backgrounds are flagged and assigned lower transit velocities, so that without intervention they require exponentially longer time to reach the evacuation points .
________________________________________
## Demo Pilots in Context
Dimension	Odessa
Mobility function examined	Civilian evacuation during geopolitical-conflict disruptions 

Topology scope	City centre + building passages + park pathways 

Modes in the model	Pedestrians, cars — resident agents transform into one of these on mode choice 

Disruption typology	Attack on the adjacent port area; phase-2 evacuation from shelters 

Response strategies	R1 / R2 / R3 — all involve responder agents collecting vulnerable through secured corridors 

Pathfinding algorithm	A*, continuously re-evaluated 

Vulnerability layer	People with disabilities / mobility impairments / age extremes / disadvantaged / socio-economic backgrounds → lower transit velocity 

KPIs	Throughput (M), Efficiency (S), Redundancy (R), Entropy (Q) — D2.3 framework
________________________________________
## Sample Insights
The model's design highlights emphasise four points:
Vulnerability has exponential rather than linear effects. Without intervention, vulnerable groups (people with disabilities, mobility impairments, age extremes, disadvantaged and socio-economic backgrounds) require exponentially longer time to reach the evacuation points . This is the operational rationale for prioritised extraction by responder agents.
Topology disproportionately shapes outcomes. By integrating building passages and pathways in parks into the network, the model extends the set of viable evacuation corridors beyond primary roads. This matters because, in the second evacuation phase, primary road segments are likely to be at capacity or partially obstructed.
Mode choice is the decisive behavioural step. The resident-to-(pedestrian-or-car) transformation rule lets agents self-organise the modal mix dynamically; it also creates the realistic stochastic head-start condition that pathfinding and responder extraction have to address.
The responder class is the model's most distinctive response lever. Unlike floating ferry vehicles or shuttle services, the responder agent is a personnel relocation class — it locates and physically collects vulnerable persons to transport them through secured corridors, de-risking high-friction segments of the route .
________________________________________
## Citation
If you use this model in academic work, please cite the parent deliverable:
Tzioutziou, A., Tsami, M., Xenidis, Y., et al.. D3.4 Mobility Triage Analysis DSS. AntifragiCity Project, 2026. Section 5.3.4 — Odessa .
________________________________________
## References
Source document: D3.4 Mobility Triage Analysis DSS — Section 5.3.4 Odessa, including subsections 5.3.4.1 Model Development, .3.4.2 Definition of Parameters and Scenarios 
OpenStreetMaps — Source of the road network, building passages, and park pathways in the city centre.
