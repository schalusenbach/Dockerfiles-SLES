FROM registry.suse.com/suse/sles12sp4:latest
LABEL maintainer="seppo"
ARG repo
ARG cert
RUN echo "$cert" > /etc/pki/trust/anchors/RHN-ORG-TRUSTED-SSL-CERT.pem
RUN update-ca-certificates
RUN echo "$repo" > /etc/zypp/repos.d/susemanager:dockerbuild.repo
## Add the package script
ADD add_packages.sh /root/add_packages.sh

# Run the package script
RUN /root/add_packages.sh

# After building remove the repository path from image
#RUN rm -f /etc/zypp/repos.d/susemanager:dockerbuild.repo

