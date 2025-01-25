+++
title = "Licensing for Beginners"
date = 2022-03-22
type = "post"
tags = ["programming"]
+++

The most fundamental, yet seriously overlooked, aspect of any software is licensing. Whether we like it or not, the
fact is that anything we create or want to use is subject to copyright. Worst of all, legal illiteracy is a major issue
in the free and open source software (FOSS) sphere. Here's how to correctly licence your software, and what licensing
means to begin with.

**Disclaimer**: This article is not legal advice. If you are uncertain about this topic and valuable assets are at
stake, come into contact with qualified legal counsel.

# Copyright

The basis of licensing is copyright. If you wish to understand licensing, you need to understand the basics of
copyright law. What is copyright? Encyclopedia Britannica [defines it](https://www.britannica.com/topic/copyright) as
follows:

> **copyright**, the exclusive, legally secured right to reproduce, distribute, and perform a literary, musical,
> dramatic, or artistic work.
>
> Now commonly subsumed under the broader category of legal regulations known as intellectual-property law, copyright
> is designed primarily to protect an artist, a publisher, or another owner against specific unauthorized uses of his
> work (e.g., reproducing the work in any material form, publishing it, performing it in public, filming it,
> broadcasting it, or making an adaptation of it).

In summary, the goal of copyright is to protect the author of a work. The person who owns the copyright is called a
copyright holder.

How is copyright established and put into effect? Historically, centuries ago, this used to vary by national
jurisdiction. It was not guaranteed that a book author would have his creative work of art protected in every country.
Today, however, most nations on the planet, including North Korea, are signatories of the [*International Convention
for the Protection of Literary and Artistic Works*](https://www.britannica.com/topic/Berne-Convention), or *Berne
Convention* for short. Signatories of the *Berne Convention* constitute the *Berne Copyright Union*, which as of 2022
totals 179 nations.

The practical effect of the *Berne Convention* for the normal person is that the strictest possible copyright
protection applies by default to any creative work they create. This means that if you write a book in USA, Germany,
China, or any other of the *Berne Copyright Union* countries, all rights of the work are reserved to you, and nobody is
legally allowed to derive from or distribute your work. This applies to software, musical composition, or any other
work that the local jurisdiction considers "creative". Violating copyright is called copyright infringement.

There exists an unfortunate, but widespread, pop myth: that lack of monetisation of derivative copyrighted work makes
you immune to prosecution. This is wrong. It is still copyright infringement. If you create "fan art" of Warhammer
40,000 or Star Wars, not taking money for the work has no legal impact. Warhammer 40,000 and Star Wars are copyright of
Games Workshop and Disney, respectively, and you are legally obliged to ask for permission from these copyright holders
if you may create derivative work of their work. The only reason why "fan communities" of popular media franchises are
allowed to operate is because they are a net benefit to the copyright holders. Fans create hype, and so it is sound
business to let their copyright infringement slide. This strange symbiotic relationship has an unfortunate effect of
distorting people's understanding of copyright law.

# Licensing

As you might imagine, reserving all rights for copyright to yourself is good, but it is not very useful without
allowing others to see and maybe even distribute the work, in exchange for financial benefit to you. This is where
licensing comes in.

Although film theatres do not own the copyright of Star Wars, they are still allowed to screen films, at least for a
time, from the Star Wars franchise. This is because Disney is giving film theatre companies the *licence* to play the
films. Usually this comes at a fee. Usually licences come with many terms that dictate what the licensee is allowed to
do with licensed work. In this way, Disney allows the general public – in a controlled way – to consume their
copyrighted work. Disney might stipulate that the latest Star Wars film shall be in theatres for only six months, or
most of any other stipulation, as long as it is legally enforceable and not in violation of contract law.

## Software

As explained earlier, when you create a work, all rights are automatically reserved to you, per *Berne Convention*.
This includes software. Nobody is allowed to use your software without your explicit permission when you first create
it. Licensing is a legal avenue of providing permission to others of when and how they may use your software. Therefore
it is essential that you understand how to select and employ your licence for your program.

Before we get to that, we should look at one last thing: open source versus closed source software. Encyclopedia
Britannica [defines open source](https://www.britannica.com/topic/open-source) as follows:

>**open source**, social movement, begun by computer programmers, that rejects secrecy and centralized control of
>creative work in favour of decentralization, transparency, and unrestricted ("open") sharing of information. *Source*
>refers to the human-readable source code of computer programs, as opposed to the compiled computer programming
>language instructions, or object code, that run on computers but cannot be easily understood or modified by people.
>
>In closed-source, or proprietary, software development, only the object code is published; the source code is held
>secret in order to control customers and markets.

The question of open source and closed source software caused, and continues to cause, controversy in the tech world.
Proponents of [free and open source software](https://www.gnu.org/philosophy/free-sw.html) (FOSS) claim that copyright
law is outdated, and not fit for modern demands. We can briefly investigate how that is.

## Closed source

Software that is closed source, or proprietary, cannot be modified and freely distributed. This is the most common type
of software, since it is in line with the traditional ways of copyrighted work: reserving most of all rights, allowing
access only for direct financial benefit.

This is understandable, but at the same time it poses philosophical and ethical questions. To take the most obvious
example: Windows is the most widely used proprietary software on the planet. If you have Windows 10 installed on your
computer, do you know what your computer is doing at any given time? No, because you do not have access to the source
code of Windows 10. It is also doing not very good things, as illustrated by Edward Snowden, who exposed PRISM.
Microsoft and many other large US-based tech companies forward information about you to the National Security Agency.
To many people that came as a shock, but to most proponents of FOSS it was exactly to be expected. FOSS proponents are
deeply distrustful of proprietary software for this, and many other, reasons.

These concerns are entirely unique to software. Copyright law is on the side of Microsoft in spying on its users and
even sending data to intelligence agencies without their consent. Songs, books, prose, newspapers, paintings,
sculptures, and so on, cannot spy on you. This is why the issue of software licensing is not just legally complicated,
but also philosophically complex.

## Open source

On the other hand, open source software is software that can be freely modified and distributed by its users. You are
entitled to view the source of the program, modify it, and distribute it however you desire, without restriction.
Otherwise it is not considered open source software.

This raises an obvious question: why make your software open source? There are many reasons for why it is beneficial,
even if it's not immediately obvious why.

- **You don't have to do everything yourself.** Volunteer programmers will contribute to an open source project in
  exchange for absolutely nothing. Their sole incentive is seeing a project come to life that they think will benefit
  not just them but also others. It also tests their skill as a programmer, and allows them further work opportunities.
- **Open source software facilitates security.** All serious private people, companies, and institutions that have need
  for cryptographic solutions will use only open source solutions. USA's National Security Agency uses the [Advanced
  Encryption Standard](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard), or AES, to encrypt secret and top
  secret documents in the government. AES is open to the general public. Anybody is free to review and test AES for
  security errors. AES is therefore one of the safest cryptographic solutions in existence, as the entire planet has
  looked at the code and no errors have been found.
- **Open source software can be monetised.** Common misconception of open source software is that open source software
  cannot be monetised. This is false. It is entirely possible to make software open source, but ask for money in
  exchange for it. There are already a few major projects where this is the case.
  - [DOOM](https://github.com/id-Software/DOOM): The code base of the game is open source, but the art assets are still
    copyrighted and not free for distribution. You still have to pay for the art assets, in other words.
  - [Mindustry](https://github.com/Anuken/Mindustry): The game is both free (no cost) and open source, but you may
    purchase a licence of the game on Steam for additional features.
  - [Zrhythm](https://www.zrythm.org/en/index.html): Open source, but the executable files have to be paid for. This
    means that if you are sufficiently tech-savvy, you can simply compile the executable files yourself, and you skip
    the costs.
- **Open source software protects end-user rights.** In most cases one is forced to use, and be dependent on, a
  producer's continual support for a purchased product. For instance, if one purchases a Mercedes-Benz, it is likely
  that one will be forced to drive to the nearest Mercedes-Benz workshop if something breaks in the car. With open
  source software, the end-user does not have just the possibility to solve software errors on their own, but also see
  if the software does exactly what it is supposed to do. With proprietary software this is usually impossible to
  verify. If something is wrong with proprietary software, you are at the mercy of the company behind the software.

These are just some of the reasons why FOSS proponents choose to make their software open source. You simply have to
explore [GitHub](https://github.com/). It is the largest website for open source software.

# Open source licences

Contrary to proprietary licences, open source licences allow conditional or unconditional access to the source code for
everyone. Open source licences are applicable to all forms of media, but are typically used for software. The European
Union maintains an [interactive
list](https://joinup.ec.europa.eu/collection/eupl/solution/joinup-licensing-assistant/jla-find-and-compare-software-licenses)
of the various known open source licences. Here is a curated list of the three best licences that preserve the rights
of both the author and end-users of their software:

- **[GNU General Public License v3](https://www.gnu.org/licenses/gpl-3.0.en.html) (GPL-3.0)**
  - **Can:** Use/reproduce, Distribute, Modify/merge, Commercial use, Use patents, Place warranty
  - **Must:** Incl. Copyright, State changes, Disclose source, Copyleft/Share a., Include licence
- **[European Union Public Licence 1.2](https://www.eupl.eu/1.2/en) (EUPL-1.2)**
  - **Can:** Use/reproduce, Distribute, Modify/merge, Commercial use, Use patents, Place warranty
  - **Must:** Incl. Copyright, Royalty free, State changes, Disclose source, Copyleft/Share a., SaaS/network, Include
    licence
- **[Mozilla Public License 2.0](https://www.mozilla.org/en-US/MPL/) (MPL-2.0)**
  - **Can:** Use/reproduce, Distribute, Modify/merge, Commercial use, Use patents, Place warranty
  - **Must:** Incl. Copyright, Disclose source, Copyleft/Share a., Lesser copyleft, Include licence

There are a few legally acknowledged, or "correct", ways of licensing a program. To learn more about that, [read
this](https://www.gnu.org/licenses/gpl-howto.html). Information on that page is applicable to any other licence you
use for software. If you follow the directions, your software should be legally protected. Make your licence as easily
visible as possible, so that both end-users and abusers understand that your rights and rights of the end-user are
protected.

# Software and present copyright law

If you do not care about the particulars of licensing, and want to secure your software, using the licences mentioned
above is enough. Otherwise, there are important issues to be known with how licensing of software works with today's
copyright law. As mentioned earlier, software is unusual as a medium, and copyright law was not designed to fairly
process it – fairly for the consumer, anyway.

The key to understanding open source licences is that they are an ugly jury-rig. A hack, if you will, of copyright law.
It glues together modern demands of software and the Internet with old, rigid, outdated legislation from over one
hundred years in the past. Here's what that means:

Technically, the copyright holder of the Linux kernel is still Linus Torvalds. However, he, through the GNU General
Public License 2.0 (GPL-2.0), allows conditional access to the kernel code. The biggest condition of the licence is
that a person, who redistributes or performs a modification on the kernel, has to license his distribution or
modification under the GPL-2.0 licence. In this way, all derivative versions of the kernel become licensed under the
licence, because it is itself a licence term. This "legal virality" is how the kernel is legally protected, and retains
its protection across all modifications. Where does Linus Torvalds, as a copyright holder, fit in this? That's the
thing: he doesn't. Him being a copyright holder is entirely irrelevant, because the licence terms do not give him any
special treatment. There is no clause that allows him to revoke licensed access to the kernel. The kernel is going to
be free and open source, forever.

Yet, he is required to be a copyright holder, because legally the copyright holder cannot be "nobody". It's simply a
legal concept that does not exist in copyright law, as there was never a time in history where that was useful for
anybody.

# Idiotic licensing

Not all open source licences are created equal, and you should be wary of certain ones. GPL-3.0, EUPL-1.2, and MPL-2.0
are the best, as they secure the largest amount of rights for both the author and the author's end-users. There are,
however, licences that do none of these things. Here's a few of them, but the list is by no means exhaustive:
- Apache License, Version 2.0
- BSD Zero Clause License
- BSD 2-Clause "Simplified" License
- BSD 3-Clause Clear License
- MIT License

What is wrong with these licences? The issue is rather simple: the terms of these licences *do not* include that all
modifications of the software fall under terms of the same licence. What this means is that if one were to for instance
take code licensed under MIT License, and perform modifications on it, one would be allowed to apply *all*
modifications under *any* licence; regardless of whether they're proprietary or not. This is what's called a
*permissive licence*, or *idiotic licence*, because it misses [the entire
point](https://www.gnu.org/philosophy/open-source-misses-the-point.en.html) of making a software's source open to begin
with.

To underline how catastrophically useless an idiotic licence can be, one should look no further than the story of
Andrew Tanenbaum and his MINIX venture. MINIX is an operating system, and was licensed under some form of BSD licence
and, to Tanenbaum's utter obliviousness, was used by Intel in their [Management
Engine](https://www.fsf.org/blogs/sysadmin/the-management-engine-an-attack-on-computer-users-freedom). The Management
Engine, or ME for short, is a micro operating system that runs on any modern Intel CPU. Nobody knows what it does, and
theoretically can be used by governments or sufficiently savvy hackers to steal cryptographic keys, or do other
nefarious things no sane person would consent to. Intel was entirely justified in appropriating MINIX to build ME from.
None of the terms in the BSD licence force Intel to reveal source, its modifications, or even license modifications
under the same licence. Tanenbaum did not even know that MINIX was used for this purpose until several years after the
fact.

Tanenbaum has been in personal conflict on this issue, since he got to know that MINIX is now world's leading spyware.
He regrets choosing an idiotic licence to license his software, but occasionally copes with the catastrophic,
ill-advised decision as being inevitable:

> Many people (including me) don't like the idea of an all-powerful management engine in there at all (since it is a
> possible security hole and a dangerous idea in the first place), but that is Intel's business decision and a separate
> issue from the code it runs. A company as big as Intel could obviously write its own OS if it had to.
> – *Andrew Tanenbaum*

Tanenbaum is correct in that Intel would, at some point, write their own operating system to become hardware-level
spyware on all of their products, but it doesn't change the fact that one person is responsible for the origin of ME:
Tanenbaum. If MINIX had been licensed under, for example, GPL-3.0, Intel would have been forced to disclose source code
of ME, all of its modifications, reveal Tanenbaum as the copyright holder, and many other important conditions. If
Intel did not wish to face this immense legal liability, they would have been forced to spend their own cash, time, and
manpower to develop a new, proprietary alternative. It would have been a lot of money, but, because of Tanenbaum, they
were spared all of that. Thanks, Tanenbaum.

All in all, everyone who develops any kind of software has to avoid idiotic licences. MIT Licence is [the most commonly
used](https://github.blog/2015-03-09-open-source-license-usage-on-github-com/) open source licence, which should speak
for itself of how serious legal illiteracy is in software engineering. Do not make the same mistake, and pick an
appropriate licence for your work.
