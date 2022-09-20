# mb-eye-jenkins-master-build

This is a fairly simple set of procedures which will create a Jenkins Master to put on the Kubernetes cluster.
Much of the challenging work with building a Master/slave Kubernetes Jenkins setup takes place after the instance is up
and running.  In my case I chose (although not best practice) to setup a LB with the NodePort to allow for external access.

The persistent volume might be interesting to some.  In the end - I setup a good portion of the PV within the AWS Ui, as
I didnt see a way to add access for two subnets via the CLI.  Perhaps its there, but I couldnt find the format and didnt want to
take the risk.  I did have some challengings with deleting the PV when doing troubleshooting (it doesnt seem to take kindly to 
being removed and re-added).  There can be null values that get 'stuck'.  There is a command to remove them, however in my case it
took a node reboot.

If this were a production build I would likely instead create the NodePort and then just access it from a Windows JB which
has limited RDP scope.

What might be interesting here is the rbac file which includes the ability for jenkins to access a specific application namespace
in order to perform tasks required.
