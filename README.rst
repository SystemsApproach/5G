About The Book
===============

Source for *5G Mobile Networks: A Systems Approach* is available on
GitHub under
terms of the `Creative Commons (CC BY-NC-ND 4.0)
<https://creativecommons.org/licenses/by-nc-nd/4.0>`__ license. The
community is invited to contribute corrections, improvements, updates,
and new material under the same terms. While this license does not
automatically grant the right to make derivative works, we are keen to
discuss derivative works (such as translations) with interested
parties. Please reach out to discuss@systemsapproach.org.

If you make use of this work, the attribution should include the
following information:

| *Title: 5G Mobile Networks: A Systems Approach* 
| *Authors: Larry Peterson and Oguz Sunay* 
| *Source:* https://github.com/SystemsApproach/5G 
| *License:* \ `CC BY-NC-ND 4.0 <https://creativecommons.org/licenses/by-nc-nd/4.0>`__

Read the Book
-------------

This book is part of the `Systems Approach Series
<https://www.systemsapproach.org>`__, with an online version published at
`https://5G.systemsapproach.org <https://5g.systemsapproach.org>`__.

To track progress and receive notices about new versions, you can follow
the project on
`Facebook <https://www.facebook.com/Computer-Networks-A-Systems-Approach-110933578952503/>`__
and `Mastodon <https://discuss.systems/@SystemsAppr>`__. To read a running
commentary on how the Internet is evolving, follow the `Systems Approach
on Substack <https://systemsapproach.substack.com>`__.

Build the Book
--------------

To build a web-viewable version, you first need to download the source:

.. literalinclude:: code/build.sh

The build process is stored in the Makefile and requires Python be
installed. The Makefile will create a virtualenv (``venv-docs``) which
installs the documentation generation toolset. You may also need to
install the ``enchant`` C library using your system’s package manager
for the spelling checker to function properly.

To generate HTML in ``_build/html``,  run ``make html``.

To check the formatting of the book, run ``make lint``.

To check spelling, run ``make spelling``. If there are additional
words, names, or acronyms that are correctly spelled but not in the dictionary,
please add them to the ``dict.txt`` file.

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
