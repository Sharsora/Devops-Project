Hello folks. Welcome back. Until previous section, we have completed this entire CI-CD pipeline
and we could able to deploy application on Docker container successfully. However, in
case this Docker container goes down, there is no way to recover. So to overcome this
problem, we can use Docker native service called Docker Swamp or else we can use container
management service like Kubernetes. But using Kubernetes gives lot of advantages comparatively
Docker Swamp. That is the reason we are not going to deploy our applications as a Docker
container. We are going to deploy it as a pod on our Kubernetes environment. Now we
need to set up our Kubernetes environment because everything is in place so that we
can deploy our applications as a pod. In next video, I am going to show you how to set up
Kubernetes.

We are going to see how to set up our Kubernetes environment. I just searched
for Kubernetes setup and we got an official document that is kubernetes.ibo. Let's go
inside and see what are the different methods we have. If you see here, we have learning
environment and production environment. So if I go with the what are the different ways
we can set up production environment. Here again, we have different ways among them
installing Kubernetes with deployment tools, turnkey cloud solutions, Windows and Kubernetes.
We will be measuring using either deployment tools or turnkey cloud solutions. So let's
go and check what are the methods we have under deployment tools. Here we can set up
Kubernetes by using kubeadium, nextcobs and kube spray. And if we go with the turnkey
cloud solutions. Here again, we have various ways that is on Microsoft, Azure, Alibaba
cloud, AWS, AKS, Baidu AI cloud. Like that we have various clouds who are providing their
cloud solutions to set up Kubernetes. Among this, we are going to set up our Kubernetes
on AWS by using EKS. For this one, I have prepared a documentation in my GitHub repository
that is Kubernetes setup using EKS CTL. EKS CTL is a utility which helps us to set up
Kubernetes on Amazon EKS. Apart from this, I have two more documentations to set up Kubernetes
that is Kubernetes setup using cobs and Kubernetes setup using kubeadium. You can use any of
these methods to set up your Kubernetes. But once it is set up, managing is same. All right,
but I would like to prefer to go with the Kubernetes setup using EKS CTL. In next lecture,
I'm going to show you how to set up Kubernetes by using EKS CTL. Thanks for watching and
see you there.
