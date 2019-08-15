# Chapter 3: Architecture

<figure>
	<a id="cellular"></a>
	<img src="figures/Slide01.png" width="600px"/>
	<figcaption>Cellular networks consists of a Radio Access Network
	(RAN) and a Mobile Core.</figcaption>
</figure>

<figure>
	<a id="cups"></a>
	<img src="figures/Slide02.png" width="400px"/>
	<figcaption>Mobile Core divided into a Control Plan and a User
	Plane, an architectural feature known as CUPS: Control and User
	Plane Separation</figcaption>
</figure>

<figure>
	<a id="active-ue"></a>
	<img src="figures/Slide03.png" width="500px"/>
	<figcaption>Base Station detects (and connects to) active UEs.</figcaption>
</figure>

<figure>
	<a id="control-plane"></a>
	<img src="figures/Slide04.png" width="500px"/>
	<figcaption>Base Station establishes control plane connectivity
	between each UE and the Mobile Core.</figcaption>
</figure>

<figure>
	<a id="user-plane"></a>
	<img src="figures/Slide05.png" width="500px"/>
	<figcaption>Base station establishes one or more tunnels between
	each UE and the Mobile Core's User Plane.</figcaption>
</figure>

<figure>
	<a id="tunnels"></a>
	<img src="figures/Slide06.png" width="500px"/>
	<figcaption>Base Station to Mobile Core (and Base Station to Base
	Station) control plane tunneled over SCTP/IP and user plane
	tunneled over GTP/UDP/IP.</figcaption>
</figure>

<figure>
	<a id="handover"></a>
	<img src="figures/Slide07.png" width="500px"/>
	<figcaption>Base Stations cooperate to implement UE hand over.</figcaption>
</figure>

<figure>
	<a id="link-aggregation"></a>
	<img src="figures/Slide08.png" width="500px"/>
	<figcaption>Base Stations cooperate to implement multipath
	transmission (link aggregation) to UEs.</figcaption>
</figure>

<figure>
	<a id="mobile-core"></a>
	<img src="figures/Slide20.png" width="700px"/>
	<figcaption>Mobile Core disaggregated into a Service Mesh.</figcaption>
</figure>
