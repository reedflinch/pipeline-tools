* Why Immutable Infrastructure?

In an effort to leave behind the days of the monolithic application that evoked nightmares by developers and system administrators charged with maintiaing it, USCIS has made the forward-looking decision to "reboot the infrastructure."  To do this, we lean on the principle of **immutable infrastructure**.  

> Unchanging infrastructure might sound like the opposite of what you’d want in an agile environment.  But what it means is that once the image is working, only a working image is deployed. When it’s time to make changes a new is created, but the previous image is still available for rollback of the environment itself. The fact that we can now create exact, versioned, timestamped versions of an entire environment removes troubleshooting broken instances almost entirely. And thanks to OS-level virtualization, which is spearheading the movement for immutable infrastructure, these images are extremely fast to deploy.
> Adron Hall, [The New Stack](http://thenewstack.io/a-brief-look-at-immutable-infrastructure-and-why-it-is-such-a-quest/)

The core goal of immutable infrastructure is speed:  speed in reacting to changes, speed of implementing those changes in production, and speed of delivering value to customers.  As [Chad Fowler at Wunderlist writes](http://chadfowler.com/blog/2013/06/23/immutable-deployments/):

> It’s giving us the confidence we need to rapidly iterate on our backend infrastructure as we continue to make things faster, more scalable and dependable for our customers and flexible to move our applications forward more freely.

** Why Docker?

Simply put, Docker allows development teams to experiment and innovate in a fast, lightweight, consistent and secure manner.  To demonstrate this concept, take a look at how Docker allows teams to utilize immutable infrastructure.

Understanding Docker begins at the **container** level.  A container is a lot like a Linux virtual machine, [except that it's not](http://www.informationweek.com/strategic-cio/it-strategy/containers-explained-9-essentials-you-need-to-know/a/d-id/1318961).  Where a virtual machine requires its own guest operating system, storage, CPU, and RAM, a Docker container shares the kernel of its host machine.  This means no large, often wasteful operating system needs to be tied to each container.  Containers are generally much smaller than their virtual machine counterparts -- sometimes [micro-sized, in fact](http://www.iron.io/blog/2016/01/microcontainers-tiny-portable-containers.html) (a fully working hello-world web application container written in Node.js can be as small as 5MB).

