Chapter 7:  Cloudification of Access
====================================

The previous chapters went step-by-step, first breaking 5G down into its
elemental components and then showing how those components could be put
back together using best practices in cloud design to build a fully
functional, 3GPP-compliant 5G cellular network. In doing so, it is easy
to lose sight of the big picture, which is that the cellular network is
undergoing a dramatic transformation. That’s the whole point of 5G. We
conclude by making some observations about this big picture.

7.1 Multi-Cloud
---------------

To understand the impact of cloud technologies and practices being
applied to the access network, it is helpful to first understand what’s
important about the cloud. The cloud has fundamentally changed the way
we compute, and more importantly, the pace of innovation. It has done
this through a combination of:

-  **Disaggregation:** Breaking vertically integrated systems into
   independent components with open interfaces.

-  **Virtualization:** Being able to run multiple independent copies of
   those components on a common hardware platform.

-  **Commoditization:** Being able to elastically scale those virtual
   components across commodity hardware bricks as workload dictates.

There is an opportunity for the same to happen with the access network,
or from another perspective, for the cloud to essentially expand so far
as to subsume the access network.

.. _fig-cloud:
.. figure:: figures/Slide32.png 
    :width: 700px
    :align: center

    Figure 7.1: A multi-tenant / multi-cloud—including virtualized RAN
    resources alongside conventional compute, storage, and network
    resources—hosting both Telco and Over-the-Top (OTT) services and
    applications.

:ref:`Figure 7.1 <fig-cloud>` gives a high-level overview of how the
transformation might play out, with the global cloud spanning edge
clouds, private Telco clouds, and the familiar public clouds. Each
individual cloud site is potentially owned by a different organization
(this includes the cell towers, as well), and as a consequence, each
site will likely be multi-tenant in that it is able to host (and
isolate) applications on behalf of many other people and organizations.
Those applications, in turn, will include a combination of the RAN and
Core services (as described throughout this book), Over-the-Top (OTT)
applications commonly found today in public clouds (but now also
distributed across edge clouds), and new Telco-managed applications
(also distributed across centralized and edge locations).

Eventually, we can expect common APIs to emerge, lowering the barrier
for anyone (not just today’s network operators or cloud providers) to
deploy applications across multiple sites by acquiring the storage,
compute, networking, and connectivity resources they need.

7.2 Research Opportunities
--------------------------

In order for the scenario depicted in :ref:`Figure 7.1 <fig-cloud>`
to become a reality, a wealth of research problems that need to be
addressed, many of which are a consequence of the blurring line
between access networks and the edge cloud. We refer to this as
the *access-edge*, and we conclude by identifying some example
challenges/opportunities.

- **Multi-Access:** The access-edge will need to support multiple
  access technologies (e.g., WiFi, 5G, fiber), and allow users to
  seamlessly move between them. Research is needed to break down
  existing technology silos, and design converged solutions to common
  problems (e.g., security, mobility, QoS).
   
- **Heterogeneity:** Since the access-edge will be about low-latency
  and high-bandwidth connectivity, much edge functionality will be
  implemented by programming the forwarding pipeline in white-box
  switches, and more generally, will use other domain-specific
  processors (e.g., GPUs, TPUs). Research is needed to tailor edge
  services to take advantage of heterogeneous resources, as well as
  how to construct end-to-end applications from such a collection of
  building blocks.

- **Virtualization:** The access-edge will virtualize the underlying
  hardware using a range of techniques, from VMs to containers to
  lambdas, interconnected by a range of L2, L3, and L4/7 virtual
  networks, some of which will be managed by SDN control
  applications. Research is needed to reconcile the assumptions made
  about by cloud native services and access-oriented Virtualized
  Network Functions (VNFs) about how to virtualize compute, storage,
  and networking resources.
  
- **Multi-Tenancy:** The access-edge will be multi-tenant, with
  potentially different stakeholders (operators, service providers,
  application developers, enterprises) responsible for managing
  different components. It will not be feasible to run the entire
  access-edge in a single trust domain, as different components will
  operate with different levels of autonomy. Research is needed to
  minimize the overhead isolation imposed on tenants.
  
- **Customization:** Monetizing the access-edge will require the
  ability to offer differentiated and customized services to different
  classes of subscribers/applications. Sometimes called network
  slicing, this involves support for performance isolation at the
  granularity of service chains—the sequence of functional elements
  running on behalf of some subscriber. Research is needed to enforce
  performance isolation in support of service guarantees.
  
- **Near-Real Time:** The access-edge will be a highly dynamic
  environment, with functionality constantly adapting in response to
  mobility, workload, and application requirements. Supporting such an
  environment requires tight control loops, with control software
  running at the edge. Research is needed to analyze control loops,
  define analytic-based controllers, and design dynamically adaptable
  mechanisms.
  
- **Data Reduction:** The access-edge will connect an increasing
  number of devices (not just humans and their handsets), all of which
  are capable of generating data. Supporting data reduction will be
  critical, which implies the need for substantial compute capacity
  (likely including domain-specific processors) to be available in the
  access-edge. Research is needed to refactor applications into their
  edge-reduction/backend-analysis subcomponents.
  
- **Distributed Services:** Services will become inherently
  distributed, with some aspects running at the access-edge, some
  aspects running in the datacenter, and some running on premises or
  end device (e.g., on-vehicle). Supporting such an environment
  requires a multi-cloud solution that is decoupled from any single
  infrastructure-based platform, with research needed to develop
  heuristics for function placement.
  
- **Scalability:** The access-edge will potentially span thousands or
  even tens of thousands of edge sites. Scaling up the ability to
  remotely orchestrate that many edge sites (even at just the
  infrastructure level) will be a qualitatively different challenge
  than managing a single datacenter. Research is need to scale both
  the edge platform and widely deployed edge services.
  
.. note::

    To better understand the research opportunity at the access-edge,
    see `Democratizing the Network Edge, ACM SIGCOMM CCR, April 2019
    <https://ccronline.sigcomm.org/wp-content/uploads/2019/05/acmdl19-289.pdf>`__.
