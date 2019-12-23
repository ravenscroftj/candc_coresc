# C&C  Tools with CoreSC Super Tagger

This docker container contains a very niche set of tools based on the (now defunct) C&C NLP tools package.

C&C tools is a CCG tagger that was originally developed by James Curran and Stephen Clark at the University of Sydney. In 2016 the original C&C tools project tracker went down and never came back up. The package is now widely considered to be [abandoned](https://chbrown.github.io/candc/).

Our Python-based [Sapienta](http://www.sapientaproject.com/) implementation that enriches biomedical scientific papers with CoreSC scientific discourse information relies on a legacy version of C&C Tools that is no longer available elsewhere. 

I have provided the 'gubbins' that we use to host C&C tools under the MIT open source license. I have included a tarball of C&C source code which comes with its own License which you should follow if possible (although it is difficult to say with abandonware how applicable this license is).



## About the docker image

The docker image is based on `ubuntu:19.04` which is not the most slimline base image but since C&C relies on `glibc` which Alpine linux [does not support out of the box](https://wiki.alpinelinux.org/wiki/Running_glibc_programs) it was the logical choice for a base image.

As with the original C&C tools we run a SOAP server on port `9004` which is exposed by the container.

The application is stored in `/app/candc-1.00/` and the models are hosted in `/app/models` - a bash script called `run_server.sh` which lives in `/app/candc-1.00/bin/` is used to launch the soap server and configure the models.

## About the models

We use C&C tools with a custom super tagger for CoreSC (called super_coresc) as well as the original biomedical models( `pos_bio` and `super_bio`)

There is a tar ball containing all of the models that we use in the main directory of this project.

