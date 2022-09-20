# mb-eye-jenkins-master-build

This is a fairly simple set of procedures which will create a Jenkins Master to put on the Kubernetes cluster.
Much of the challenging work with building a Master/slave Kubernetes Jenkins setup takes place after the instance is up
and running.  In my case I chose (although not best practice) to setup a LB with the NodePort to allow for external access.

If this were a production build I would likely instead create the NodePort and then just access it from a Windows JB which
has limited RDP scope.

What might be interesting here is the rbac file which includes the ability for jenkins to access a specific application namespace
in order to perform tasks required.
