# Why Immutable Infrastructure?

In an effort to leave behind the days of the monolithic application that evoked nightmares by developers and system administrators charged with maintiaing it, USCIS has made the forward-looking decision to "reboot the infrastructure."  To do this, we lean on the principle of **immutable infrastructure**.  

> Unchanging infrastructure might sound like the opposite of what you’d want in an agile environment.  But what it means is that once the image is working, only a working image is deployed. When it’s time to make changes a new is created, but the previous image is still available for rollback of the environment itself. The fact that we can now create exact, versioned, timestamped versions of an entire environment removes troubleshooting broken instances almost entirely. And thanks to OS-level virtualization, which is spearheading the movement for immutable infrastructure, these images are extremely fast to deploy.
> -- Adron Hall, [The New Stack](http://thenewstack.io/a-brief-look-at-immutable-infrastructure-and-why-it-is-such-a-quest/)

The core goal of immutable infrastructure is speed:  speed in reacting to changes, speed of implementing those changes in production, and speed of delivering value to customers.  As [Chad Fowler at Wunderlist writes](http://chadfowler.com/blog/2013/06/23/immutable-deployments/):

> It’s giving us the confidence we need to rapidly iterate on our backend infrastructure as we continue to make things faster, more scalable and dependable for our customers and flexible to move our applications forward more freely.

## Why [Docker](https://www.docker.com/)?

Simply put, Docker allows development teams to experiment and innovate in a fast, lightweight, consistent and secure manner.  To demonstrate this concept, take a look at how Docker allows teams to utilize immutable infrastructure.

Understanding Docker begins at the **container** level.  A container is a lot like a Linux virtual machine, [except that it's not](http://www.informationweek.com/strategic-cio/it-strategy/containers-explained-9-essentials-you-need-to-know/a/d-id/1318961).  Where a virtual machine requires its own guest operating system, storage, CPU, and RAM, a Docker container shares the kernel of its host machine.  This means no large, often wasteful operating system needs to be tied to each container.  Containers are generally much smaller than their virtual machine counterparts -- sometimes [micro-sized, in fact](http://www.iron.io/blog/2016/01/microcontainers-tiny-portable-containers.html) (a fully working hello-world web application container written in Node.js can be as small as 5MB).

A container generally runs a single process or serves a single function -- an application "server", a database, a load balancer, or a continuous integration tool, for example.  De-coupling these application components allows teams to scale efficiently and handle infrastructure failures gracefully.  As part of a Continuous Integration/Continuous Delivery (CI/CD) pipeline, this means that containers and host machines can all be provisioned and clustered easily and automatically.

Isolating resources means that processes running in one container cannot "see" or affect the processes in another container.  Consequently, each container can be designed to run the most efficient solution for the task at hand, and no more -- which, by eliminating as much extraneous fluff as possible, provides fewer attack vectors for potential threats.

The security and immutability aspects of Docker are where **images** shine.  [An image is](http://stackoverflow.com/questions/23735149/docker-image-vs-container/26960888#26960888) a snapshot of a container that is inert, or immutable.  It is the foundation of each container, composed of layers of other images, which describe the features and commands to be implemented for the containers built upon it.  By beginning with a lightweight, secure, and consistent image, such as [CoreOS for example](https://coreos.com/), images can be designed for very specific and logical purposes.  By [hardening](http://linux-audit.com/docker-security-best-practices-for-your-vessel-and-containers/), or reducing the surface of vulnerability, Docker images and containers can be made even more secure.  In fact, image hardening research and experimentation is already happening at USCIS.

## Why [Gradle](http://gradle.org/)?

Gradle is a [self-described](https://github.com/gradle/gradle) flexible and powerful build tool with a focus on build automation and support for multi-language development.  The open source software supports the entire development lifecycle, from code compile to deploy, and integrates with almost every tool imaginable in a DevOps workflow.  Gradle fills an important development need by serving as a general puprose aggregate compiler (compiler, source sets, and dependencies) that also supports native code, uniting the compiler, assembler, and linker.

Gradle implements the best of both Apache's Ant and Maven build tools.  Using a Groovy-based domain-specific language for project configuration eases the headaches commonly found in Maven's XML configuration files.  

Most importantly, Gradle can scale intelligently.  It was designed for large, multi-project builds in an enterprise environment, and is used by technology powerhouses such as Netflix, LinkedIn and Twitter.  Incremental builds are supported, with Gradle determining which parts of a project are up-to-date, reducing redundant tasks.  At USCIS, using Gradle means a commitment to consistency and automation in the deployment process.

## Why [Jenkins](https://jenkins-ci.org/)?

Jenkins, at its core, makes it easier for developers to integrate changes into a software project.  The powerful orchestration and automation server has gained incredible traction in recent years, due to a combination of its ease of use, incredible integration support, and extensibility.  

Jenkins is used to communicate with almost every service of the CI/CD pipeline.  From [code commit in GitHub](https://wiki.jenkins-ci.org/display/JENKINS/GitHub+Plugin), to unit tests, integration tests, performance tests, security scanners, code coverage tools, to the application itself -- Jenkins orchestrates with them all, and can do so without any human intervention.  Jenkins can be configured to run a full suite of operations upon a commit to a GitHub repository and, in addition, [even be triggered](https://hubot.github.com/) [by a user entering a simple message in Slack](https://www.pagerduty.com/what-is-chatops/).

The most powerful effect of using Jenkins or other CI servers is the incredibly fast [feedback loop](http://pathfindersoftware.com/2009/06/agile-fundamentals-the-feedback-loop/).  With these tools, development teams are able to instantly know who and what introduced a failing change, and can react accordingly.  Once a successful change is committed and all tests pass, Jenkins has the ability to deploy the new build on immutable infrastructure, completing the development lifecycle.

