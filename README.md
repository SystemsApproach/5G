# README

This repository contains source text for *5G Cellular Networks: A
Systems Approach*, available under terms of the
[Creative Commons (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0)
license. The community is invited to contribute corrections,
improvements, updates, and new material under the same terms.

If you make use of this work, the attribution should include the
following information:

> *Title: 5G Cellular Networks: A Systems Approach  
> Authors: Larry Peterson and Oguz Sunay  
> Source: https://github.com/SystemsApproach/5G  
> License: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0)*

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
make 
```

If all goes well, you will be able to view the book in your browser at 
`localhost:4000`. (If all doesn't go well, you might try typing `make`
a second time.) 
