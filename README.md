# README

This repository contains source for *Cellular Networks: A Systems
Approach*, available under terms of the
[Creative Commons (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0)
license. The community is invited to contribute corrections,
improvements, updates, and new material under the same terms.

If you make use of this work, the attribution should include the
following information:

> *Title: Cellular Networks: A Systems Approach  
> Authors: Larry Peterson and Oguz Sunay  
> Source: https://github.com/SystemsApproach/5G  
> License: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0)*

## Read the Book

An online version of the book is published at
[https://cellular.systemsapproach.org](https://cellular.systemsapproach.org).
You can also find PDF and eBook versions
[here](https://github.com/SystemsApproach/5G/tree/master/published).

To track progress and receive notices about new versions, you can follow
the project on
[Facebook](https://www.facebook.com/Computer-Networks-A-Systems-Approach-110933578952503/)
and [Twitter](https://twitter.com/SystemsAppr).
To read a running commentary on how the Internet is evolving, follow
the [Systems Approach Blog](https://www.systemsapproach.org).

## Build the Book 

To build a web-viewable version, you first need to install a couple
packages:

* [Gitbook Toolchain](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md)
* [Node.js Package Manager](https://www.npmjs.com/get-npm) 

Then do the following to download the source:

```shell 
mkdir ~/5G
cd ~/5G
git clone https://github.com/SystemsApproach/5G.git 
cd 5G
```

To build a web version of the book, simply type:

```shell 
undo
make 
```

If all goes well, you will be able to view the book in your browser at 
`localhost:4000`. (If all doesn't go well, you might try typing `make`
a second time.)

## Contribute to the Book

We hope that if you use this material, you are also willing to
contribute back to it. If you are new to open source, you might check
out this [How to Contribute to Open
Source](https://opensource.guide/how-to-contribute/) guide.
Among other things, you'll learn about posting *Issues* that you'd
like to see addressed, and issuing *Pull Requests* to merge your
improvements back into GitHub.

If you'd like to contribute and are looking for something that needs
attention, see the
[wiki](https://github.com/SystemsApproach/5G/wiki)
for the current TODO list.
