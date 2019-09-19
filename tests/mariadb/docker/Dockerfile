FROM ubuntu:16.04

RUN apt-get update -y && apt-get install libpath-tiny-perl 
RUN cpan install File::Find

COPY mysql /opt
CMD ["/bin/bash"]