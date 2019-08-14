# Chapter 2: Wireless Transmission Primer

For anyone familiar with wireless access technologies like Wi-Fi, the cellular network is most unique due to its approach to sharing the available radio spectrum among its many users, all the while allowing those users to remain connected while moving. This has resulted in a highly dynamic and adaptive approach, in which coding/modulation and scheduling play a central role.

We start by giving short primer on wireless transmission as a way of laying a foundation for understanding the rest of the 5G architecture. The following is not a substitute for a theoretical treatment of the topic, but is instead intended as a way of grounding the systems-oriented description of 5G that follows in the reality of wireless communication.

## Coding and Modulation

At its core, coding inserts extra bits into the data to account for environmental factors that interfere with signal propagation, and modulation translates those bits into electromagnetic signals by varying the signal’s amplitude and phase. This relationship is depicted in Figure 1, where coding typically implies some form of Forward Error Correction (e.g., turbo codes) and modulation is done relative to an assigned carrier signal.

Figure 1. The role of coding and modulation in wireless communication.

When we’re dealing with radio signals propagating through the air, the opportunities for interference are plentiful. As illustrated in Figure 2, the signal bounces off various stationary and moving objects, following multiple paths from the transmitter to the receiver, who may also be moving.

Figure 2. Signals propagate along multiple paths from transmitter to receiver.

As a consequence of these multiple paths, the original signal arrives at the receiver spread over time, as illustrated in Figure 3. Empirical evidence shows that the Multipath Spread—the time between the first and last signals of one transmission arriving at the receiver—is 1 to 10us in urban environments and 10 to 30us in suburban environments. Theoretical bounds for the time duration for which the channel may be assumed to be time invariant, known as the Coherence Time and denoted $$T_c$$ , is given by

$$
T_c = c/v \times 1/f
$$

where $$c$$ is the velocity of the signal, $$v$$ is the velocity of the receiver (e.g., moving car or train), and $$f$$  is the frequency of the carrier signal being modulated. This says the coherence time is inversely proportional to the frequency of the signal and the speed of movement, which makes intuitive sense: The higher the frequency (shorter the wave) the shorter the coherence time, and likewise, the faster the receiver is moving the longer the coherence time. Based on the target parameters to this model (selected according to the physical environment), it is possible to calculate Tc  which in turn bounds the rate at which symbols can be transmitted without undue risk of interference.

Figure 3. Received data spread over time due to multipath variation.

To complicate matters further, Figures 2 and 3 imply the transmission originates from a single antenna, but cell towers are equipped with an array of antennas, each transmitting in a different (but overlapping) direction. This technology, called Multiple-Input-Multiple-Output (MIMO), opens the door to purposely transmitting data from multiple antennas in an effort to reach each user, adding even more paths to the environment-imposed multipath propagation.

One of the most important consequences of these factors is that the transmitter must receive feedback from every receiver to judge how to best utilize the wireless medium on their behalf. 3GPP specifies a Channel Quality Indicator (CQI) for this purpose, where in practice a CQI status report is sent every 1ms. Knowing the details of these CQI messages is not critical to recognizing that they play a central role in scheduling transmissions, but in essence this feedback is about the observed signal-to-noise ratio, which impacts the receiver’s ability to recover the data bits.

The state-of-the-art in coding and modulation for such environments is called Orthogonal Frequency-Division Multiple Access (OFDMA), where “Orthogonal” is the operative word. The idea is to multiplex data over a set of 12 orthogonal subcarrier frequencies, each of which is modulated independently. The “Multiple Access” in OFDMA implies that data can simultaneously be sent on behalf of multiple users, each on a different subcarrier frequency and for a different duration of time. The subbands are narrow (e.g., 15kHz), but the coding of user data into OFDMA symbols is designed to minimize the risk of data loss due to interference between adjacent bands.

## Scheduling

The use of OFDMA naturally leads to conceptualizing the radio spectrum as a two-dimensional resource, as shown in Figure 4. The minimal schedulable unit, called a Resource Element (RE), corresponds to a 15kHz-wide band around one subcarrier frequency and the time it takes to transmit one OFDMA symbol. The number of bits that can be encoded in each symbol depends on the modulation rate, so for example using Quadrature Amplitude Modulation (QAM), 16-QAM yields 4 bits per symbol and 64-QAM yields 16 bits per symbol.

A scheduler allocates some number of REs to each user that has data to transmit during each 1ms Transmission Time Interval (TTI), where users are depicted by different colored blocks in Figure 4. The only constraint on the scheduler is that it must make its allocation decisions on blocks of 7x12=84 resource elements, called a Physical Resource Block (PRB). Figure 4 shows two back-to-back PRBs. Of course time continues to flow along one axis, and depending on the size of the available frequency band, there may be many more subcarrier slots (and hence PRBs) available along the other axis, so the scheduler is essentially preparing and transmitting a sequence of PRBs. (Even though resources are technically allocated at the granularity of individual REs, RAN scheduling is often described in terms of allocating PRBs, so we will adopt that terminology in future sections.)

Figure 4. Spectrum abstractly represented by a 2-D grid of schedulable Resource Elements.

Note that OFDMA is not a coding/modulation algorithm, per se, but instead provides a framework for selecting a specific coding and modulator for each subcarrier frequency. QAM is one common example modulator. It is the scheduler’s responsibility to select the modulation to use for each PRB, based on the CQI feedback it has received. The scheduler also selects the coding on a per-PRB basis (again based on the observed CQI), for example, by how it sets the parameters to the turbo code algorithm.

The 1ms TTI corresponds to the time frame in which the scheduler receives feedback from users about the quality of the signal they are experiencing. This is the CQI mentioned earlier, where once every millisecond, each user sends a set of metrics, which the scheduler uses to make its decision as to how to allocate PRBs during the subsequent TTI. 

Figure 5. Scheduler allocates Resource Elements to user data streams based on CQI feedback from receivers and the QCI parameters associated with each class of service.

As shown in Figure 5, the other input to the scheduling decision is the QoS Class Identifier (QCI), which indicates the quality-of-service each class of users expects to receive. The set of QCI values has changed between 4G and 5G, reflecting the increasing differentiation being supported. For 5G, each class includes the following attributes:

* Resource Type: Guaranteed Bit Rate (GBR), Delay-Critical GBR, Non-GBR
* Priority Level	
* Packet Delay Budget	
* Packet Error Rate	
* Averaging Window	
* Maximum Data Burst

Keep in mind that Figures 4 and 5 focus on scheduling transmissions from a single antenna, but the MIMO technology described above means the scheduler also has to determine which antenna (or more generally, what subset of antennas) will most effectively reach each receiver. But again, in the abstract, the scheduler is charged with allocating a sequence of PRBs.

Finally, 5G allows one more degree of freedom: the ability to adjust the TTI from 1ms down to 0.25ms, depending on the target latency requirements.

This all begs the question: How does the scheduler decide which set of users to service during any TTI, how many Resource Elements to allocate to each such user, how to select the coding and modulation levels, and which antenna to transmit their data on? This is an optimization problem that, fortunately, we are not trying to solve here. Our goal is to describe an architecture that allows someone else to design and plug in an effective scheduler. Keeping the 5G architecture open to innovations like this is one of our highest priorities in the sections that follow.
