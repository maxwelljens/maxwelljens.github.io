---
title: "You Don't Need Docker for Everything"
description: "Docker is an unnecessary abstraction for small-scale sysadmins, and the rise of Rust and Go makes it even more indefensible."
tags: ["technology"]
cover:
  image: /you_dont_need_docker/card.jpg
date: 2026-05-21
---

Before we get to the meat, let me state plainly that I am not talking about
enterprise-scale deployments. If you are managing hundreds of microservices
across a Kubernetes cluster at a company with more employees than your home
town has residents, Docker is probably the right tool. I have never pretended
to be an enterprise sysadmin, and I am not about to start. What I am talking
about is what you and I do: running a personal website, hosting a blog,
deploying a small game server, setting up a fediverse instance. The kind of
casual sysadmin work that normal people do on a box in their living room or a
five-euro VPS that has been running for three years without a reboot. For
this, Docker is not just unnecessary. It is actively harmful.

I run this website, another website, a Matrix server, and a handful of
other services/microservices on a modest Lenovo ThinkPad in my lounge room.
None of those services run from Docker. Each one is a systemd unit. Each one
has its config in `/etc`, its data in `/var/lib`, and its logs in the journal.
If something breaks, I do not have to remember which abstraction layer the
service is hiding behind. I `systemctl status`, I `journalctl -u`, and I fix
the problem. This is not advanced sysadmin work. This is knowing how to use the
operating system you chose to run. Yet the dominant advice I see online, in
tutorials, in README files, and in the mouths of every developer, is to wrap
absolutely everything in Docker. Why?

Luke Smith [has written on this
topic](https://lukesmith.xyz/articles/everyone-should-be-avoiding-docker/)
in a write-up that has been in the back of my mind lately. He frames Docker as
a crutch for people who do not know how to use UNIX, and he is largely correct.
But I want to extend his argument with something he does not touch on: the
language revolution that has made Docker's core selling point irrelevant for
people like us, because, the truth is, Docker was solving a real problem. That
problem has mostly been solved by better tools, and you probably already use
them.

## The Problem Docker Actually Solved

Docker emerged to solve what people dramatically called dependency hell. You
have application A that needs Python 3.8 and some obscure C library version
2.1, and application B that needs Python 3.12 and version 2.3 of that same
library, and installing both on the same machine is a ritual of forced
self-harm. I remember those days. Anyone who has done serious work with Python
or Node.js knows exactly what I am talking about.

Let me paint the picture properly. You install a Python application. It needs a
specific version of `libffi`. Your distribution ships version 3.2. The
application needs 3.1. You cannot have both because the package manager will
scream at you. So you compile from source, or you add a third-party repository
that ships the old version, and now your system is held together with
superstition. Then you install a second Python application and it needs
`libffi` 3.3, which also conflicts. You are now in dependency purgatory, and no
amount of `pip install --user` will get you out, because `pip` only manages
Python packages. It does not manage the C libraries those Python packages link
against. This is the actual problem Docker solved. It wraps each application in
its own little universe, its own filesystem, its own library versions,
completely isolated from every other application and the host operating system.
For a certain era of software development, this was genuinely useful.

The same story played out in other ecosystems. Ruby had `rvm` and `rbenv` and
`bundler` and still somehow you would end up with a mystery `Gemfile.lock` that
only resolved on one specific machine. Node.js gave us `node_modules` folders
that weighed more than the operating system and version conflicts that `nvm`
could only partially paper over. The entire interpreted-language world spent
the 2010s building increasingly baroque toolchains to manage the fact that
their languages could not produce a self-contained artifact. Docker was the
nuclear option. Instead of fixing the languages, we gave each application its
own pretend computer. It worked, but it was also insane and annoying.

## The Real Fix

But here is what changed: [Rust](https://rust-lang.org/) and
[Go](https://go.dev/) happened.

![Rust mascot and Go's Gopher](/you_dont_need_docker/rust_go.jpg)

A Go program compiles to a single, statically linked binary. No runtime. No
virtual environment. No system libraries to conflict. You cross-compile for
Linux from your MacBook with `GOOS=linux GOARCH=amd64 go build`. You `scp` the
resulting binary to your server, and you run it. That is the entire deployment
story. The binary contains everything it needs. The Go team explicitly designed
the language this way because they had all lived through the dependency hell
era and decided, correctly, that the solution was not better dependency
management. The solution was to make dependencies a compile-time concern and
produce a single artifact that has no dependencies at runtime. Ken Thompson and
Rob Pike, the people who gave you UNIX itself, looked at the state of software
deployment and said: this is stupid, let's fix it at the language level, and
they did.

A Rust program follows the same philosophy with even stricter compile-time
guarantees. Rust's borrow checker eliminates entire categories of runtime bugs
before the binary even exists. Its `cargo` build system produces a single
binary by default. If you need to link against system libraries, Rust makes it
explicit and controllable. In practice, most Rust services you would deploy on
a personal server are statically linked. The binary is self-contained. You copy
it. You run it. No Docker, no virtualenv, no `nvm`, no `rbenv`, no container
registry, no YAML file with seventeen stanzas describing how to recreate the
pretend computer inside your real computer.

If every service you run is a single binary, what exactly is Docker isolating?
Nothing. There is nothing to isolate. The problem Docker solved does not exist
in this world, thankfully, but for some reason developers still persist in
insisting on it.

This is not theoretical. I am describing the actual deployment process for this
very website. Hugo compiles to a single binary. I run it. That is it. The
Matrix server I mentioned? It's [Conduit](https://gitlab.com/famedly/conduit),
which is written in Rust. It is one binary. When I need to update Conduit or
any other services, I download the new binary, I restart the service, and I am
done. The entire process takes seconds. There even is
[bin](https://github.com/marcosnils/bin), a program written in Go, that manages
these binaries from GitHub and other Git repository hosts. If I were running
each of these in Docker, I would be managing three separate container
lifecycles, three sets of volumes, three network configurations, and three
Docker Compose files that I would need to remember the structure of every time
something went wrong. This would be obnoxious to maintain.

The practical difference is stark. Consider deploying a small web application
with Docker:
1) You write a Dockerfile.
2) You build an image. 
3) You push it to a registry, or you build it on the server itself.
4) You configure volumes, networks, environment variables, port mappings.
5) You write a `docker-compose.yml` or a `docker run` command with seventeen flags.

If something goes wrong, you have to remember whether you are inside the
container or outside it, which logs live where, whether that config file is in
a volume or baked into the image, and why `docker exec` needs the full
container ID but the logs command only needs the first three characters. You
also have to contend with Docker's virtual network, which assigns private IP
addresses to containers and requires port forwarding rules that overlap and
conflict with your host firewall. It is a maze of incidental complexity, and
none of it has anything to do with your application.

{{< figure src="/you_dont_need_docker/hero.avif" alt="Francisco Goya, 'Saturn Devouring His Children'" caption="This is what Docker makes you do after a while." >}}

Now consider deploying the same application as a Go binary. You compile. You
copy the binary to the server. You write a twelve-line systemd unit file that
looks something like `ExecStart=/usr/local/bin/myapp`, `Restart=always`, and
`User=myapp`. You enable it. Done. Logs go to journald, where every other
service on your system keeps its logs. Config files sit in `/etc` where config
files belong. If something breaks, you look at the service file, you look at
the config, you look at the logs. It is the same process you use for every
other service on the machine. No special incantations, no context switching,
just the UNIX way.

![Thumbs up kid at the computer GIF meme](/you_dont_need_docker/thumbs_up.gif)

Of course, someone will point out that not everything is a Go or Rust binary.
Fair enough. PHP is still widely used, and it has always been surprisingly good
at this. A PHP application is just files in a directory. Deploying it is
`git pull`. There is no build step, no dependency resolution at the system
level, no binary to manage. It is the original zero-friction deployment story,
and it is worth acknowledging that the PHP ecosystem got this right decades
before Docker existed. The entire shared-hosting industry was built on PHP's
deployment model, and it worked at a scale Docker still struggles to match
without Kubernetes. But even PHP, for all its simplicity and battle-tested
reliability, cannot match the performance, safety, and resource efficiency of
Rust or Go. A PHP-FPM pool serving WordPress will use more memory and CPU than
a Go binary serving the same traffic. If you are building something new, and
you have the choice, you should choose a compiled language. When you do, Docker
becomes superfluous.

The same applies to front-end development. Modern frameworks like
[Svelte](https://svelte.dev/) compile to static files. You build your site, you
get a folder of HTML, CSS, and JavaScript, and you serve it with Nginx. That is
it. If you want something more ambitious, like 3D rendering in the browser with
[Threlte](https://threlte.xyz/), you still end up with static files served by a
web server. The sophistication of the stack has no bearing on deployment
complexity. A single Go binary serving a Svelte front-end with Threlte-powered
3D graphics deploys exactly the same way a ten-line CGI script deploys. The
complexity lives in the build stage, not the runtime. Docker adds nothing to
this equation except more YAML, and YAML is a configuration format that cannot
even decide whether `yes` and `no` are booleans, so perhaps we should not be
building our infrastructure on it.

## The Cost of Convenience

This is where the Docker proponents lose me. They will tell you that Docker
makes things easier to set up. And they are right, for about the first ten
minutes. Running `docker compose up` is genuinely simple. But the bill comes
due. Three months later, when your Certbot certificate fails to renew, and you
cannot just run `certbot renew` because Certbot is trapped inside its container
like a wasp in a jar, and you have to look up the specific Docker incantation
to execute a command inside a specific container, and that incantation is forty
characters long and you mistype it twice, you will understand the bargain you
made. You traded long-term maintainability for a one-time convenience. You
outsourced understanding to an opaque abstraction, and now the abstraction owns
you.

The Certbot story is not hypothetical. [It is one of the most common failure
modes for self-hosted Docker
setups](https://eff-certbot.readthedocs.io/en/latest/install.html#alternative-1-docker),
because TLS certificates expire on a schedule and the renewal process must work
reliably without human intervention. A native Certbot installation hooks into
systemd timers. It renews. It reloads Nginx. It has been doing this for years
on millions of servers. The Docker version requires you to coordinate the
Certbot container's renewal schedule with the Nginx container's reload
mechanism, and if the maintainer of either image changes their volume mount
paths between versions, your setup silently breaks. You will not discover this
until your certificate has expired and your site is serving a browser warning
that makes you look like an amateur. By then, you have forgotten how you set it
up in the first place because you only touched that `docker-compose.yml` once,
six months ago, following a tutorial you can no longer find.

I say this from experience. I have run services both ways, and I can say,
with complete confidence, that the Docker way always, without exception,
becomes a headache the moment something goes off the happy path.

My memory is hazy, but here is a reconstruction of something that went like
this: I once spent an entire several hours in the afternoon trying to change
the database connection string for a containerised application. The string was
in an environment variable. The environment variable was set in the
`docker-compose.yml`. I changed it. I restarted the container. The application
still used the old connection string. I checked the running container's
environment. The variable was correct. I checked the application's config file
inside the container. It was reading from a different variable name, one that
was not documented, because the image maintainer had changed the naming
convention in version X.x and the tutorial I was following was written for
version Y.y. I only discovered this after `docker exec`-ing into the container,
installing `vim` because the container did not ship with an editor, and
grepping through the application source code. This is not administration, but
rather archaeology through an opaque obstacle course. Without Docker, I would
have opened `/etc/myapp/config.toml`, changed the string, and restarted the
service. Thirty seconds.

And for what? Security? Let us be serious. A container does not magically make
your application secure. If your application has a vulnerability, the container
will not save you. It might limit the blast radius if the attacker also does
not know how to escape a container, but betting your security on your
attacker's ignorance is not a strategy. The people who maintain the Docker
images you download from Docker Hub are not necessarily more security-conscious
than you are. In most cases, we should believe they are less so, and their
images sit unpatched for months because the maintainer lost interest. At least
if you install the package from your distribution's repository, you inherit the
security diligence of the distribution's maintainers, who have actual processes
and accountability. Debian's security team will ship a patch for `openssl`
faster than the maintainer of a random Docker image will even notice there is a
CVE.

People mistake the opacity of containers for security. It is unintuitive to
interact with a containerised program, therefore it feels protected. This is
the same logic that makes people put a padlock on a fence gate. It looks
secure, but the perimeter of your fence is still not any taller, therefore not
any harder to jump over than before you put the padlock on.

## Conclusion

To be clear, Docker does have a legitimate place. If you are running a software
company with dozens of developers on different operating systems, Docker
provides a reproducible development environment that prevents the classic "it
works on my machine" problem. If you are deploying hundreds of services across
a cluster that must scale up and down in response to traffic, Kubernetes and
container orchestration are the right tools. These are real problems at a
certain scale. But you are not at that scale. You are one person with one
server, or maybe three. You do not have a DevOps team. You do not have a
service mesh. You have SSH access and a shell.

And the cultural problem is that Docker has become a cargo cult. Junior
developers learn Docker before they learn how to use systemd. Tutorials assume
Docker as the default deployment method for everything, including
single-binary applications that could run on a toaster. I have seen README
files for Go projects that recommend Docker as the primary installation method,
which means running a Go binary inside a container that itself contains an
entire operating system, all so you can avoid running the Go binary directly.
This is not engineering. This is some weird pseudo-ritualistic approach to
ordinary system administration. The container has become a talisman of some
sort. You must recite the `docker run` incantation and draw the Docker Compose
diagram on the floor, or the software demon will escape and consume your
server... or something. The result is a generation of developers who reach for
a sledgehammer when they need to hang a picture frame, and who could not write
a systemd unit file if their server depended on it, which it does, but they
will never know because Docker is hiding it from them.

Here is a simple heuristic: if your entire application is a single binary, you
do not need Docker. If your entire application is a single binary and a
database, you still do not need Docker. Install PostgreSQL, configure the
PostgreSQL login, and run your binary. You are done. If your application is a
mess of Python, Ruby, Node.js, and conflicting system libraries, Docker might
be the least bad option, but you should also ask yourself why your application
is a mess of Python, Ruby, and Node.js in the first place, and whether you
could replace it with something that compiles.

You do not need Docker. Instead, you need to know how your operating system
works. You need to write systemd unit files. You need to understand where
configs go and where logs live. These are not arcane skills, but very basic
stuff that has been standard practice for close to two decades at this point.
They are basic UNIX/Linux literacy, and they will serve you for decades across
every Linux system you ever touch. Docker is a proprietary-adjacent layer of
indirection that teaches you Docker, not Linux. It is a product of an era when
we had collectively forgotten how to produce self-contained software, and we
responded by building pretend computers inside our real computers instead of
fixing the languages that caused the problem. That era is over. Rust and Go
fixed it. You can just run the binary now. When something breaks, as it always
does, the person who knows Linux will fix it in thirty seconds. The person who
only knows Docker will spend an afternoon on Stack Overflow and Google Gemini,
and the answer they find will be out of date because the image maintainer
changed the volume mount paths again.
