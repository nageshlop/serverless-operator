# Dockerfile to bootstrap build and test in openshift-ci

FROM docker.io/openshift/origin-release:golang-1.14

# Add kubernetes repository
ADD openshift/ci-operator/build-image/kubernetes.repo /etc/yum.repos.d/

RUN yum install -y kubectl ansible httpd-tools

RUN GO111MODULE=on go get github.com/mikefarah/yq/v3 \
  knative.dev/test-infra/kntest/cmd/kntest

# Allow runtime users to add entries to /etc/passwd
RUN chmod g+rw /etc/passwd

RUN yum install -y https://rpm.nodesource.com/pub_14.x/el/7/x86_64/nodesource-release-el7-1.noarch.rpm
RUN yum install -y gcc-c++ make nodejs
