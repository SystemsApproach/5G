About This Book
===============

This repository contains source for *5G Mobile Networks: A Systems
Approach*, available under terms of the `Creative Commons (CC BY
4.0) <https://creativecommons.org/licenses/by/4.0>`__ license. The
community is invited to contribute corrections, improvements, updates,
and new material under the same terms.

If you make use of this work, the attribution should include the
following information:

| *Title: 5G Mobile Networks: A Systems Approach* 
| *Authors: Larry Peterson and Oguz Sunay* 
| *Source:* https://github.com/SystemsApproach/5G 
| *License:* \ `CC BY 4.0 <https://creativecommons.org/licenses/by/4.0>`__

Read the Book
-------------

An online version of the book is published at
`https://5G.systemsapproach.org <https://5g.systemsapproach.org>`__. You
can also find PDF and eBook versions
`here <https://github.com/SystemsApproach/5G/tree/master/published>`__.

To track progress and receive notices about new versions, you can follow
the project on
`Facebook <https://www.facebook.com/Computer-Networks-A-Systems-Approach-110933578952503/>`__
and `Twitter <https://twitter.com/SystemsAppr>`__. To read a running
commentary on how the Internet is evolving, follow the `Systems Approach
Blog <https://www.systemsapproach.org>`__.

Build the Book
--------------

To build a web-viewable version, you first need to download the source:

.. code:: shell 

   mkdir ~/5G 
   cd ~/5G 
   git clone https://github.com/SystemsApproach/5G.git 
   cd 5G 

The build process is stored in the Makefile and requires Python to be 
installed. The Makefile will create a virtualenv (``doc_venv``) which 
installs the documentation generation toolset. 

To generate HTML in ``_build/html``,  run ``make html``.

To get a live reload in your browser (refreshes on file save), run ``make reload``.

To check the formatting of the book, run ``make lint``.

To see the other available output formats, run ``make``.

Contribute to the Book
----------------------

We hope that if you use this material, you are also willing to
contribute back to it. If you are new to open source, you might check
out this `How to Contribute to Open
Source <https://opensource.guide/how-to-contribute/>`__ guide. Among
other things, you’ll learn about posting *Issues* that you’d like to see
addressed, and issuing *Pull Requests* to merge your improvements back
into GitHub.

If you’d like to contribute and are looking for something that needs
attention, see the `wiki <https://github.com/SystemsApproach/5G/wiki>`__
for the current TODO list.
