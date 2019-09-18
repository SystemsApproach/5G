Chapter 1:  Introduction
===========================

Cellular networks, which have a 40-year history that parallels the
Internet’s, have undergone significant change. The first two generations
supported voice and then text, with 3G defining the transition to
broadband access, supporting data rates measured in hundreds of
kilobits-per-second. Today, the industry is at 4G (supporting data rates
typically measured in the few megabits-per-second) and starting the
transition to 5G, with the promise of a tenfold increase in data rates.

But 5G is about much more than increased bandwidth. In the same way 3G
defined the transition from voice to broadband, 5G’s promise is mostly
about the transition from a single access service (broadband
connectivity) to a richer collection of edge services and devices,
including support for immersive user interfaces (e.g., AR/VR),
mission-critical applications (e.g., public safety, autonomous
vehicles), and the Internet-of-Things (IoT). Because these use cases
will include everything from home appliances to industrial robots to
self-driving cars, 5G won’t just support humans accessing the Internet
from their smartphones, but also swarms of autonomous devices working
together on their behalf. All of this requires a fundamentally different
architecture.

This book describes the 5G cellular network, which because it is on an
evolutionary path and not a point solution, includes standardized
specifications, a range of implementation choices, and a long list of
aspirational goals. Because this leaves so much room for interpretation,
our approach to describing 5G is grounded in two mutually-supportive
principles. The first is to apply a *systems lens*, which is to say, we
explain the sequence of design decisions that lead to a solution rather
than fall back on enumerating the overwhelming number of acronyms as a
*fait accompli*. The second is to aggressively disaggregate the system.
Building a disaggregated, virtualized, and software-defined 5G access
network is the direction the industry is already headed (for good
technical and business reasons), but breaking the 5G network down into
its elemental components is also the best way to explain how 5G works.
It also helps to illustrate how 5G might evolve in the future to provide
even more value.

What this all means is that there is no single, comprehensive definition
of 5G, any more than there is for the Internet. It is a complex and
evolving system, constrained by a set of standards that purposely give
all the stakeholders many degrees of freedom. In the chapters that
follow, it should be clear from the context whether we are talking about
*standards* (what everyone must do), *trends* (where the industry seems
to be headed), or *implementation choices* (examples to make the
discussion more concrete). By adopting a systems perspective throughout,
our intent is to describe 5G in a way that helps the reader navigate
this rich and rapidly evolving system.

1.1 Standardization Landscape
-----------------------------

As of 3G, the generational designation corresponds to a standard defined
by the 3GPP (3rd Generation Partnership Project). Even though its name
has “3G” in it, the 3GPP continues to define the standards for 4G and 5G,
each of which corresponds to a sequence of releases of the standard.
Release 15 is considered the demarcation point between 4G and 5G, with
Release 16 expected by the end of 2019. Complicating the terminology, 4G
was on a multi-release evolutionary path referred to as *Long Term
Evolution (LTE)*. 5G is on a similar evolutionary path, with several
expected releases over its lifetime.

While 5G is an ambitious advance beyond 4G, it is also the case that
understanding 4G is the first step to understanding 5G, as several
aspects of the latter can be explained as bringing a new
degree-of-freedom to the former. In the chapters that follow, we often
introduce some architectural feature of 4G as a way of laying the
foundation for the corresponding 5G component.

Like Wi-Fi, cellular networks transmit data at certain bandwidths in the
radio spectrum. Unlike Wi-Fi, which permits anyone to use a channel at
either 2.4 or 5 GHz (these are unlicensed bands), governments have
auctioned off and licensed exclusive use of various frequency bands to
service providers, who in turn sell mobile access service to their
subscribers.

There is also a shared-license band at 3.5-GHz, called *Citizens
Broadband Radio Service (CBRS)*, set aside in North America for cellular
use. Similar spectrum is being set aside in other countries. The CBRS band
allows three tiers of users to share the spectrum: first right of use
goes to the original owners of this spectrum, naval radars and satellite
ground stations; followed by priority users who receive this right over
10MHz bands for three years via regional auctions; and finally the rest
of the population, who can access and utilize a portion of this band as
long as they first check with a central database of registered users.
CBRS, along with standardization efforts to extend cellular networks to
operate in the unlicensed bands, open the door for private cellular
networks similar to Wi-Fi.

The specific frequency bands that are licensed for cellular networks
vary around the world, and are complicated by the fact that network
operators often simultaneously support both old/legacy technologies and
new/next-generation technologies, each of which occupies a different
frequency band. The high-level summary is that traditional cellular
technologies range from 700-MHz to 2400-MHz, with new mid-spectrum
allocations now happening at 6-GHz, and millimeter-wave (mmWave)
allocations opening above 24-GHz.

While the specific frequency band is not directly relevant to
understanding 5G from an architectural perspective, it does impact the
physical-layer components, which in turn has indirect ramifications on
the overall 5G system. We will identify and explain these ramifications
in later chapters.

1.2 Access Networks
-------------------

The cellular network is part of the access network that implements the
Internet’s so-called *last mile*. Other access technologies include
*Passive Optical Networks (PON)*, colloquially known as
Fiber-to-the-Home. These access networks are provided by both big and
small network operators. Global network operators like AT&T run access
networks at thousands of aggregation points-of-presence across a
country like the US, along with a national backbone that interconnects
those sites. Small regional and municipal network operators might run
an access network with one or two points-of-presence, and then connect
to the rest of the Internet through some large operator’s backbone.

In either case, access networks are physically anchored at thousands of
aggregation points-of-presence within close proximity to end users,
each of which serves anywhere from 1,000 to 100,000 subscribers,
depending on population density. In practice, the physical deployment
of these ”edge” locations vary from operator to operator, but one
possible scenario is to anchor both the cellular and wireline access
networks in Telco *Central Offices*.

Historically, the Central Office—officially known as the *PSTN
(Packet-Switched Telephone Network) Central Office*—anchored wired
access (both telephony and broadband), while the cellular network
evolved independently by deploying a parallel set of *Mobile Telephone
Switching Offices (MTSO)*. Each MTSO serves as a *mobile aggregation*
point for the set of cell towers in a given geographic area. For our
purposes, the important idea is that such aggregation points exist, and
it is reasonable to think of them as defining the edge of the
operator-managed access network. For simplicity, we sometimes use the
term “Central Office” as a synonym for both types of edge sites.

1.3 Edge Cloud
--------------

Because of their wide distribution and close proximity to end users,
Central Offices are also an ideal place to host the edge cloud. But this
begs the question: What exactly is the edge cloud?

In a nutshell, the cloud began as a collection of warehouse-sized
datacenters, each of which provided a cost-effective way to power, cool,
and operate a scalable number of servers. Over time, this shared
infrastructure lowered the barrier to deploying scalable Internet
services, but today, there is increasing pressure to offer
low-latency/high-bandwidth cloud applications that cannot be effectively
implemented in centralized datacenters. Augmented Reality (AR), Virtual
Reality (VR), Internet-of-Things (IoT), Autonomous Vehicles are all
examples of this kind of application. This has resulted in a trend to
move some functionality out of the datacenter and towards the edge of
the network, closer to end users.

Where this edge is *physically* located depends on who you ask. If you
ask a network operator that already owns and operates thousands of
Central Offices, then their Central Offices are an obvious answer.
Others might claim the edge is located at the 14,000 Starbucks across
the US, and still others might point to the tens-of-thousands of cell
towers spread across the globe.

Our approach is to be location agnostic, but it is worth pointing out
that the cloud’s migration to the edge coincides with a second trend,
which is that network operators are re-architecting the access network
to use the same commodity hardware and best practices in building
scalable software as the cloud providers. Such a design, which is
sometimes referred to as *CORD (Central Office Re-architected as a
Datacenter)*, supports both the access network and edge services
co-located on a shared cloud platform. This platform is then replicated
across hundreds or thousands of sites (including, but not limited to,
Central Offices). So while we shouldn’t limit ourselves to the Central
Office as the only answer to the question of where the edge cloud is
located, it is becoming a viable option.

.. note::

    To learn about the technical origins of CORD, which was first 
    applied to fiber-based access networks (PON), see `Central Office 
    Re-architected as a Datacenter, IEEE Communications, October 2016 
    <https:wiki.opencord.org/download/attachments/1278027/PETERSON_CORD.pdf>`__. 

    To understand the business case for CORD (and CORD-inspired
    technologies), see the A.D. Little report `Who Dares Win!
    How Access Transformation Can Fast-Track Evolution of
    Operator Production Platforms, September 2019
    <https://www.adlittle.com/en/who-dares-wins>`__.

When we get into the details of how 5G can be implemented in practice,
we use CORD as our exemplar. For now, the important thing to understand
is that 5G is being implemented as software running on commodity
hardware, rather than embedded in the special-purpose proprietary
hardware used in past generations. This has a significant impact on how
we think about 5G (and how we describes 5G), which will increasingly
become yet another software-based component in the cloud, as opposed to
an isolated and specialized technology attached to the periphery of the
cloud.

Keep in mind that our use of CORD as an exemplar is not to imply that
the edge cloud is limited to Central Offices. CORD is a good exemplar
because it is designed to host both edge services and access
technologies like 5G on a common platform, where the Telco Central
Office is one possible location to deploy such a platform.

An important takeaway from this discussion is that to understand how 5G
is being implemented, it is helpful to have a working understanding of
how clouds are built. This includes the use of *commodity hardware*
(both servers and white-box switches), horizontally scalable
*microservices* (also referred to as *cloud native*), and
*Software-Defined Networks (SDN)*. is also helpful to have an
appreciation for how cloud software is developed, tested, deployed and
operated, including practices like *DevOps* and *Continuous Integration
/ Continuous Deployment (CI/CD)*.

One final note about terminology. Anyone that has been paying attention
to the discussion surrounding 5G will have undoubtedly heard about
*Network Function Virtualization (NFV)*, which involves moving
functionality that was once embedded in hardware appliances into VMs
running on commodity servers. In our experience, NFV is a stepping
stone towards the fully disaggregated solution we describe, and so we do
not dwell on it. You can think of NFV as an alternative to the cloud
native exemplar presented here.
