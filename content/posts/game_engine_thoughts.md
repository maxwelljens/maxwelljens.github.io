---
title: "My Thoughts on Unreal Engine, Unity, and Godot"
description: "As a Linux user, after having tried all the major game engines, I can give an honest review and overview. Here are my thoughts."
tags: ["software", "gamedev"]
cover:
  image: /game_engine_thoughts/card.jpg
date: 2026-03-19
draft: true
---

In this article, I will dissect what are unmistakably the three most widely
used game engines in PC gaming today:

- Unreal Engine 5
- Unity 6
- Godot 4.6

Before we get to the actual technical teardown, however, I need to establish
some context. If you are expecting a standard, Windows-centric review from a
studio developer who only cares about which engine has the easiest asset store
to flip from, you are reading the wrong article. My baseline assumptions about
what makes a piece of software *good* are fundamentally different from the
industry standard, and it is important to understand why before I seemingly out
of nowhere start panning multi-billion-dollar corporations for their software
design.

## The allure of the impossible

First and foremost: I am not a professional game developer. Where for most
people the extent of their understanding of "technology" is Instagram filters
or the latest AI gimmick, my interest lies at the foundational level. I care
about programming languages, free software architecture, and using digital
workflows to solve non-trivial problems. 

To me, a computer is a tool that allows for what, even just a quarter-century
ago, would be considered magic. *"Sufficiently advanced technology is
indistinguishable from magic,"* as the famous Arthur C. Clarke quote goes. This
is precisely why I became interested in game engines. Video games are
incredibly complex, interconnected systems of logic, physics, and art. 

A lot of people will tell you that game development is hard, but I had to learn
the hard way that it isn't just hard; it is crushingly, ruthlessly unforgiving.
It made me understand exactly how [Amazon's game
studios](https://www.gamesindustry.biz/another-tech-giants-gaming-ambitions-bite-the-dust-opinion)
found themselves completely helpless when trying to develop their own titles.
According to Jason Schreier, Amazon dedicated an eye-watering 500 million USD
annual budget to their game studios, yet their flagship MMO, *New World*,
is [shutting its servers down in January
2027](https://www.polygon.com/new-world-aeternum-shutting-down-delisted-offline/).

I mention this because the fact that game development can crush even the
richest Silicon Valley monopolies makes me appreciate it as an actual artform.
Trillions of dollars in market capital cannot buy you a bypass around the sheer
complexity of making a good game. It requires immense technical skill and
discipline. It is intimidating, but equally alluring.

## The analytical outsider

Given my appreciation for the technical foundation of games, one might assume I
am a professional software engineer. That is not true, either. While I would
categorise my programming skill level as intermediate, I don't actually
consider myself a "programmer" by trade or identity, simply because I don't
program all that often. 

My interest in coding is highly pragmatic and shares space with a myriad of
other, highly physical interests. I am just as likely to be found doing graphic
design, or engaging in physical craftsmanship like blacksmithing and fletching,
as I am to be found writing OCaml. However, out of all my hobbies,
programming is undoubtedly the most cost-effective. It requires nothing but a
machine and time, yet produces that aforementioned magic.

I approach game engines not as a corporate developer trying to meet a milestone
for a publisher, but as an analytical outsider who wants to build complex,
artful systems from the ground up. In my opinion, the options on this front are
highly limited, which is why I was not immediately keen on Godot; a free
software project.

## Linux and the free software lens

This brings us to the most critical piece of context: I am a Linux user, and I
place a very high premium on free (as in freedom) software. 

When people think of "gamedev," the default assumption is a Windows user who
doesn't mind giving up ownership of their tools, or even their computer, so
long as the graphical interface looks nice. I am different in this regard.
Because I approach technology analytically, I generally despise black box
software, although I have nowhere near the level of personal integrity that
Richard Stallman does to use 100% free software and hardware. Anyway, I want to
know how the engine works. I want the freedom to modify it without being a
multi-million dollar organisation, and I expect my operating system of choice
to be treated as a first-class citizen, not an afterthought.

This lens drastically changes how I evaluate Unreal Engine, Unity, and Godot.
As you will see, engines that rely on closed-source ecosystems are inherently
fragile in ways that free software is not. Furthermore, if an engine claims to
be an industry standard but features a virtually non-existent Linux support
pipeline or a fundamentally broken plugin system, I am not going to grade it on
a curve just because it can render pretty lighting (usually washed out in TAA). 

With that framework established, let's look at the engines.

## Unreal Engine 5

My first real foray into game development was, ironically enough, with Unreal
Engine 5 (UE5). Starting with a bloated, proprietary monolith might seem like a
blatant contradiction given my strict preference for free software, but I ask
you to bear with me. The reasoning will make perfect sense once we get to the
section on Godot. For now, consider it a necessary first step.

Unreal Engine 5 has perpetually been caught in a media pendulum, violently
swinging from overwhelmingly positive hype to overwhelmingly negative backlash.
When I first dipped my toes into game development, however, I lacked the
hands-on experience to separate valid criticism from industry noise. All I knew
was that the technical output of UE5 was undeniably impressive. The real hook
for me, surprisingly, was the initial setup. Discovering that getting Unreal
running on Linux was practically a one-click affair was enough to entice me
into giving it a fair shot, despite its closed-source nature.

### A galaxy of features

What immediately captured my attention, and genuinely motivated me to start
building, was the staggering breadth of features available straight out of the
box. It delivered a legitimate "wow" factor. The ability to construct
photorealistic landscapes in a matter of hours, seamless real-time in-editor
playthroughs, Lumen's dynamic global illumination, automatic rig
retargeting -- the list of out-of-the-box tools is so exhaustive it could fill
volumes.

Furthermore, the licensing model was hard to brush off just on the basis of the
engine being closed source. Access to a toolset of this magnitude, completely
for free, up to a million dollars in gross revenue? That is an objectively good
deal. I might be a staunch advocate for software freedom, but I am also a
pragmatist. I am more than capable of recognising a highly compelling business
proposition when I see one.

### My first first-person shooter

With the engine installed and the initial awe subsiding, it was time to
actually build something. I didn't want to overreach, so I opted for a classic,
foundational genre: the first-person shooter. More specifically, I wanted to
see if I could recreate the core gameplay loop of an *ArmA 3* custom map called
[ArmA 3
Survival](https://steamcommunity.com/sharedfiles/filedetails/?id=2300293692).
It is a simple, highly addictive co-op wave defender with rudimentary
battle-royale-style looting elements.

Conceptually, it didn't seem overly ambitious. On paper, it is just basic state
management, some spawn logic, simple enemy AI, and an inventory system. I
started cracking at it.

This was also the exact moment I discovered Fab, Epic Games' official asset
storefront, and its rotating carousel of limited-time free assets. I happened
to check it just in time to claim the [Brushify - Desert Mountains
Pack](https://www.fab.com/listings/ae80aa4f-7f9f-4140-8afb-8f91f4ac41fa); an
incredibly high-fidelity environment asset that normally runs for about 1,000
USD under a professional license. Wow! What a deal, right? 

Within an afternoon, I had dragged and dropped my way into a sprawling,
photorealistic landscape that could comfortably stand shoulder-to-shoulder with
the environments of *Assassin's Creed* or *Middle-Earth: Shadow of War*. It was
wildly motivating to see my "game" look AAA almost instantly, but it also made
me acutely aware of how easy it is to fall into the infamous "asset flip" trap.
I had a gorgeous, million-dollar desert, but zero actual game mechanics. For
that, I had to code.

### The C++ conundrum and visual spaghetti

This is where the honeymoon phase abruptly ended, and my real conundrum began.
Unreal Engine is built entirely in C++, and uniquely among modern game engines,
it does not offer a high-level, text-based scripting language, like Lua or C#,
as an alternative.

Given that I am an intermediate programmer -- most importantly also not a
self-flagellating masochist -- I knew that diving into Unreal's C++ was a grim
prospect. I probably *could* do it, but did I really want to subject myself to
that kind of brain damage? C++ is notoriously antiquated, and Unreal probably
had specific flavor of it that was a bloated, macro-heavy behemoth that
requires you to wrestle with poor or non-existent documentation, 20 different
ways to initialise a variable, and agonisingly slow compilation times. For
someone who values clean architecture, C++ feels like [the worst programming
language in history](https://www.youtube.com/watch?v=7fGB-hjc2Gc).

Fortunately -- maybe unfortunately, depending on how you look at it -- the
bright engineers at Epic Games provided a built-in alternative: Blueprints. 

Blueprints is Unreal's proprietary visual scripting engine. Instead of typing
lines of code, you drag boxes onto a grid and connect them with colored wires.
As someone who lives in Neovim and strongly prefers navigating complex logic
through a keyboard and a terminal, the idea of abandoning my highly optimised
text-editing workflow to drag noodles around with a mouse was not ideal. It was
a hard pill to swallow.

Furthermore, from a software engineering perspective, Blueprints are binary
files. If you use Git for version control, which any sane person does, you
cannot simply `git diff` a Blueprint to see what logic changed between commits.
It is a black box. But, faced with the alternative of wrestling with Unreal's
C++ API, I reluctantly conceded. Visual scripting ultimately beat C++, but it
felt like choosing the lesser of two distinct evils.

### Visual logic and AAA polish

With my reluctance safely compartmentalised, I started building logic with
Blueprints. To my horror, I actually started to enjoy it. Once you let go of
the ingrained urge to rapidly prototype systems via text and force yourself to
think of logic as a visual flow of data, it becomes a rather zen experience. It
was an interesting exercise, if nothing else.

Actually getting core logic implemented opened the door to the engine's more
impressive, interconnected systems. An integral part of any first-person
shooter is animation, and UE5 does not disappoint in this department. Setting
up state machines, blending animations, and managing transitions was an
absolute breeze. Generating automatic collisions for complex objects, or
watching Nanite dynamically handle level-of-detail (LOD) scaling without any
manual intervention, was staggering. The technical cohesion of these systems
was so sharp it was almost hard to believe I was running it on a local Linux
machine.

This progress inevitably led me to my first third-party plugin purchase. Unreal
plugins generally fall into two categories: those exposing C++ libraries, and
those built entirely in Blueprints. I needed a more sophisticated line-of-sight
system for humanoid characters. Out of the box, the engine provides basic
raytrace-to-object checks, but if you want something nuanced, such as an NPC
recognising a player's leg sticking out from behind cover, you either write a
complex system from scratch, or you buy a plugin. I opted for the latter. The
specific plugin isn't important; what matters is that money changed hands.

Next came the NPCs -- giving the player something to actually encounter and shoot
at. The systems Epic has in place for artificial intelligence (specifically
Behavior Trees and the Environment Query System) are arguably the starkest
advantage UE5 holds over the competition. The tools available are robust enough
to create virtually any type of humanoid NPC behavior. Within days, I had
created an NPC that could intelligently flank the player, bound from cover to
cover, and dynamically evaluate the height of obstacles. To this day, the AI
toolset is the only thing I genuinely miss about Unreal Engine. The rest, I can
live without.

### The black box shatters

It was at this exact peak of productivity that the entire ecosystem fell apart. 

The culprit was Fab, Epic's recently integrated plugin and asset
infrastructure. One day, I booted up my project and noticed that several of my
plugins in the launcher were missing the `+` icon required to add them to a
project. Assuming this was a minor, Linux-specific configuration bug, [I opened
an issue on the Unreal Engine
forums](https://forums.unrealengine.com/t/unable-to-add-several-plugins-to-project-linux/2654549),
hoping a staff member could point me toward a quick workaround.

At first, it was just an annoyance. I wanted to try out an *ArmA 3*-style
inventory plugin, but couldn't add it. Then, I realised the severity of the
situation: my *NPC Eyes Sight System*, the line-of-sight plugin I had previously
mentioned, was also locked out. I had paid actual currency for a software
license, and the proprietary launcher had arbitrarily decided I could no longer
access my property.

How does a multi-billion-dollar company, maintaining an engine engineered to
power multi-million-dollar AAA franchises, allow its core financial
infrastructure to break like this? For a Linux user who inherently distrusts
closed-source ecosystems, this was the ultimate validation of that paranoia.
You don't own your tools; you merely rent access to them at the total mercy of
a corporate launcher. Granted, I did not expect this level of negligence, but I
am not suing a company over 3 USD.

I halted development on the game, patiently waiting for a response, hoping this
was just a temporary backend outage.

If you are curious: no, I never received a response. That forum issue, opened
in September 2025, remains unresolved to this day. As far as I can tell, there
is no expedited support priority for paying marketplace customers. There was
legitimately zero reason for me to purchase another asset, or even attempt to
use free ones, if the engine's infrastructure simply refused to inject them into
my project.

Shocked by this glaring failure, I started digging deeper into Epic Games and
the modern state of Unreal Engine. I found it difficult to wrap my head around
the fact that such financially sensitive infrastructure was left to rot. It
forced me to look at the broader AAA gaming industry -- which these days is
heavily reliant on UE5 -- from a technical standpoint. Suddenly, the fact that
so many modern AAA releases are unoptimised, stuttering, or outright unplayable
made a lot more sense. If the underlying foundation is this fragile, it's no
wonder the house built on top of it is also populated by clowns.

### The Fab fiasco and corporate apathy

Down the rabbit hole I went. It turns out that when Epic forcefully replaced
the Unreal Engine Marketplace with Fab in 2025, it was an overwhelmingly
unpopular decision, and it is incredibly easy to see why.

For instance, during the migration of marketplace listings to Fab, only the
numerical star ratings were preserved. All written reviews from users were
completely deleted. Why? The cynic in me assumes it was a deliberate move to
wipe the slate clean of detailed, critical feedback on broken assets, but
officially? Nobody knows.

But the erasure of important product history was just the appetiser. The main
course was the sheer, unadulterated flood of digital sewage that Epic allowed
to wash over the platform. When Fab launched, it didn't just break plugin
installations and remove access to previously free Megascans assets; it opened
the floodgates to generative AI spam on an industrial scale.

If you read my [previous article](debunking_anti_ai_cult), you know I do not
harbor a paranoid, Luddite hatred for AI. I view it as a tool. The blame for AI
misuse lies entirely with the user wielding it and the platforms enabling it.
Fab is perhaps the most spectacular real-world validation of that exact
argument.

In May 2025, a horrifying milestone on the platform: [a single Fab user had
uploaded over 38,000 AI-generated models to the
shop](https://80.lv/articles/this-one-fab-user-has-over-38-000-ai-generated-assets).
I am not exaggerating the number. This individual was clogging Epic's servers
with gigabytes upon gigabytes of awful-looking 3D buildings, each inexplicably
composed of around half a million triangles. For the non-technical reader: half
a million polygons for a single generic background building is an absurd,
catastrophically unoptimised waste of computational resources. It is digital
sludge in its purest form. Even Alex "YandereDev" Mahan didn't do this.

Worse still, nearly 10,000 of these assets weren't even tagged as AI-generated.
The digital storefront's brilliant moderation strategy of "just throw in some
tags" was instantly exposed as a completely ineffective farce. The platform's
vetting process was evidently either fully automated and broken, or practically
non-existent. From what I understand, it's there, just broken.

The most depressing revelation was that, aside from failing to properly tag a
portion of the uploads, this user hadn't actually broken any of Fab's core
rules. Epic’s design philosophy actively permits a single individual to bury
legitimate, human-made assets under a mountain of half-million-triangle AI
slop.

But this wasn't just an aesthetic crime; it became a catastrophic
infrastructure failure. This single user managed to pump so much unoptimised,
automated sewage into the system that it triggered what amounted to an
unintentional denial-of-service (DoS) attack. The sheer volume of automated
uploads actually knocked the entire Fab website offline for several hours. Is
Epic Games not aware of CloudFlare? Rate limits? Hello?

Let that sink in. The proprietary asset pipeline for the most dominant game
engine on the planet -- a company with billions in revenue -- was brought to
its knees because it did not bother installing a rate limit, allowing a single
person running an automated upload script to make it unavailable for several
hours.

This brings me back to my foundational philosophy on software. When you build
your project inside a closed-source ecosystem, you are entirely at the mercy of
its steward. I couldn't fix the launcher. I couldn't bypass the marketplace to
install the plugins I legally owned. I was locked out. So, despite the
breathtaking graphics, the cool visual scripting, and the AAA polish, I did the
only logical thing a Linux user could do: I uninstalled Unreal Engine
5 and never looked back.

### The enshittification of modern graphics

If the broken infrastructure wasn't enough to drive me away, the fundamental
rendering philosophy of Unreal Engine 5 would have eventually done the job.
When you step back from Epic Games' breathtaking marketing tech demos and
actually analyse what UE5 is doing to modern video games, a grim picture
emerges. Far from elevating the medium, Unreal Engine 5 is actively
contributing to the enshittification of real-time graphics. 

A lot of these underlying rendering flaws have been meticulously documented by
[Threat Interactive](https://www.youtube.com/watch?v=Ls4QS3F8rJU), a YouTube
channel dedicated to dissecting modern graphics pipelines. I feel obligated to
mention that the author behind the channel is a rather controversial character
in the rendering scene, mostly because he is notoriously thin-skinned and tends
to take immense personal offence at any criticism levied against him or his
work. However, his prickly personality should not be used as a convenient
excuse to dismiss his otherwise strictly factual analysis, and my inclusion of
his findings here is certainly not an endorsement of his character. Regardless
of the messenger, I highly recommend looking into his teardowns. They
mathematically prove that Unreal Engine 5 is a complete farce at the
foundational level, aggressively contradicting almost every single one of its
miraculous marketing claims. That is, if simply looking at UE5 games is not
enough proof.

Anyway, to understand why the marketing is dishonest, we have to look at Epic's
twin golden calves: Nanite (virtualised geometry) and Lumen (global
illumination). On paper, Nanite promises the end of level-of-detail (LOD)
pop-in by allowing developers to import cinematic-quality models with millions
of polygons. In reality, it is a computational black hole. Shoving that much
micro-geometry onto the screen introduces catastrophic sub-pixel aliasing and
massive inefficiencies in material shading due to quad overdraw. Meanwhile,
Lumen attempts to provide real-time bounce lighting, but the underlying
implementation is incredibly fragile. It smears light across characters' faces
in unnatural ways, loses all sense of environmental stability the moment the
camera moves, and leaves a trail of noisy, ghosting artifacts in its wake. 

So, how does Epic hide the fact that its two flagship features produce a
chaotic, noisy image? They smother the entire frame in Temporal Anti-Aliasing
(TAA).

This is where the true visual degradation of the current console generation
originates. Unreal Engine 5 relies entirely on aggressive TAA to act as a
digital rug, sweeping all of Nanite's aliasing and Lumen's noisy shadows
underneath it. Virtual textures, heavily compressed shadow maps, and unresolved
lighting calculations are all violently blurred together across multiple frames
just to make the image passably coherent. The result is the infamous 'Unreal
Engine look' -- a dithery, blurry, muddy mess that completely destroys motion
clarity. It is only after this research that I started to understand why *The
Talos Principle 2*, a game I enjoyed somewhat, looks so... weird. Now I get it.

If you have played a recent AAA game and felt like someone rubbed vaseline all
over your monitor the second you started moving the camera, you are not alone.
We have reached a point where [older engines from the late 2010s are producing
vastly clearer, more stable imagery at a portion of the hardware
cost](https://www.youtube.com/watch?v=ljWylilACdI). By contrast, UE5 forces
developers into a pipeline that inherently murders image quality, replacing
sharp, intentional art direction with a smeared, TAA-dependent soup.

### The deferred rendering trap

To be entirely fair to Epic Games, this systemic visual rot did not happen
because their engineers are stupid; because they are not. If we want to
understand *why* Unreal Engine 5 relies so heavily on blurry temporal
reconstruction, we have to look at a fundamental architectural shift in
real-time computer graphics: the mass migration from forward rendering to
deferred rendering.

Historically, this technique [traces its mainstream origins all the way back
to, funny enough, the 2001 Xbox title
*Shrek*](https://sites.google.com/site/richgel99/the-early-history-of-deferred-shading-and-lighting).
Following that, nearly the entire AAA industry adopted it, and the appeal was
obvious. Deferred rendering decouples geometry from lighting. This allows
developers to throw a practically infinite number of dynamic lights into a
scene and render complex elements, like decals, in a single draw call. For
scaling massive, complex environments, it felt like a silver bullet.

But this convenience came at a severe, fundamental cost. In a deferred
pipeline, scene geometry is flattened into what are called G-buffers before the
lighting is actually applied. Because the image is flattened, the engine loses
the crucial geometric edge data required to perform traditional, crisp,
hardware-level Multi-Sample Anti-Aliasing (MSAA). The GPU simply no longer
knows where the physical edges of objects are when calculating the final pixel
colors.

Ideally, hardware manufacturers like NVIDIA and AMD would have recognised this
massive bottleneck and innovated at the silicon or driver level to rectify the
problem, perhaps creating new hardware-accelerated edge-smoothing techniques
specifically tailored for G-buffers. They didn't bother. Their inaction
effectively forced engine developers like Epic Games into a corner, relying
entirely on post-processing patchwork solutions, like TAA and modern
upscalers, to hide the resulting jagged edges.

TAA is not a technological leap; it is a desperate software band-aid that
attempts to fix a foundational rendering flaw by simply blurring the evidence
across multiple frames. Then, through aggressive marketing and nearly cultish
appeals to abnormally loyal consumers, they try to convince everyone that their
eyes are deceiving them.

Ultimately, Unreal Engine 5 is a masterclass not in technical accomplishment,
but marketing sleight of hand. It sells developers the illusion of infinite
detail and dynamic lighting, but the cost of that illusion is paid by the
player in the form of bloated file sizes, abysmal framerates, and a baseline
visual mediocrity that has infected the entire industry. I want to build games
that are crisp, highly optimised, and logically sound. I learned the hard way
that UE5, fundamentally, is the antithesis of that goal.

## Unity 6

Leaving Unreal Engine 5 felt like stepping out of a dysfunctional relationship.
The initial charm, the grand promises, the breathtaking views. It all eventually
gave way to the realisation that I was trapped in a gilded cage with no say in
how the furniture was arranged. My next logical step was to seek out the most
prominent alternative: Unity.

Now, if you follow game development news with even half an eye, you know that
approaching Unity in 2026 feels a bit like adopting a stray dog that you're
pretty sure bit several children a few years ago. The shadow of the 2022
licensing fiasco looms over everything the company does, a permanent stain on
its reputation that [no amount of apologetic blog
posts](https://unity.com/blog/unity-is-canceling-the-runtime-fee) can fully
scrub clean. For those who need a refresher: Unity Technologies, in a move of
breathtaking self-immolation, announced a new "Runtime Fee" that would charge
developers every single time their game was installed. Not a royalty on
revenue, but a per-install tax. Yes, it sounds like something a mental asylum
patient would suggest, but it happened. Seriously. The gaming community,
rightfully, reacted, and fiercely. The backlash was so swift, so vicious, and
so universal that the company was forced to walk it back, with then-CEO John
Riccitiello retiring in the aftermath.

The damage, however, was permanent. It tainted the entire engine for me before
I even downloaded it. It wasn't just a bad business decision; it was a
declaration of intent. It told developers, in no uncertain terms, that Unity
saw them not as partners or customers, but as livestock to be harvested. How
can you trust a tool when the company holding the leash has openly admitted
they'd like to strangle you with it the moment they figure out how?

But, as I mentioned before, I am a pragmatist. The Linux user in me was
screaming to stay far away, but the game developer in me needed a tool that
actually worked. I learned that the new Unity EULA actually explicitly mentions
how the company will never downgrade or upgrade licence terms for a given
customer's Unity version without mutual consent. It seemed like Unity
Technologies learned their lesson.

So, with a heavy dose of scepticism and my hand never too far from the
uninstall command, I gave Unity 6 a shot.

### The strange workflows and windows

Firing up Unity for the first time is a disorienting experience if you're
coming from Unreal. Where UE5 feels like a monolithic, opinionated beast that
wants you to do things its way, Unity feels scattered. It's not necessarily
worse, but it is profoundly different.

My immediate and most practical concern, however, was assuaged almost
instantly: platform support. This, in my opinion, is Unity's single greatest
strength. Unreal Engine 5, for all its bluster, is a Windows engine that
tolerates other operating systems. If you develop on Linux with UE5, you can
only build a Linux game, full stop. UE5 has no cross-platform building support
on Linux. I knew that when I used UE5, but I was holding out with the idea
that, if I ever complete a project, I would compile the project on someone
else's machine with Windows, use a VM, or find some other convoluted
workaround.

Unity, on the other hand, treats Linux as a legitimate development environment.
From my Fedora machine, I could, without any difficulties whatsoever, build my
project for Windows. This is the kind of fundamental, unsexy feature that free
software advocates actually care about. It respects the developer's choice of
operating system and doesn't punish you for stepping outside the Microsoft
monoculture. It was a breath of fresh, if slightly musty, air.

With the ability to actually ship a game to a real audience established, I set
about trying to build something. I didn't want to replicate the *ArmA 3*
survival map immediately; I just wanted to get a feel for the engine's rhythm.
I knew not to invest too much time into a project without properly researching
everything first, lest I run into a similar dead-end as I did with UE5.

The first thing you notice is that Unity feels like an engine designed by
programmers for programmers. C# is a genuinely pleasant language to work with,
especially after staring into the abyss of Unreal's C++. It's modern, it's
expressive, and it compiles decently quickly. Still slow, but tolerable. I
could write a script, hit save, and see the results in the editor. Unlike UE5,
however, it was not seamless, but it was not a big deal. The edit-compile-debug
cycle, the lifeblood of any coding workflow, was not foreign to me.

### The barebones toolbox

The more I built, however, the more I realised just how much of a blank slate
Unity actually is. Where Unreal hands you a fully-furnished mansion with
automated lighting, built-in AI behaviour trees, and a visual scripting
language, Unity hands you a hammer, some nails, and a plot of land. It is, for
lack of a better term, strikingly barebones.

This is not inherently a criticism, but it is a stark contrast that needs to be
understood. It was mildly disappointing, but understandable. In UE5, if you
want an NPC to react to the player, you have Behavior Trees, EQS queries, and a
whole suite of AI tools waiting for you. In Unity, you have `GameObject` and
`MonoBehaviour`. You want an NPC? Write a script. You want that NPC to have a
state machine? Write another script. You want that NPC to react to sound? Write
a third script, or find a plugin that does it. The engine provides the
primitive building blocks, but it offers almost no opinion on how they should
be assembled.

This leads to the other major observation: the features that do exist feel
disjointed, as if they were designed by different teams that don't communicate.
The UI system, the animation system, the input system... they all exist, and
they all work, but they don't snap together with the kind of pre-coded
integration you get in UE5. Want to press a button to open a door? In UE5,
there's a node for that. In Unity, you are wiring up event listeners, writing
delegate callbacks, and manually hooking the input system into your animation
controller. It works, but at times it feels like you are playing translator
between different pieces of software that don't share a common language.

For instance, there is a new input system that is a lot better than the old
one, but the old one is not phased out. If you follow old tutorials, you can
call the old input system API, which results in a compile error. If you are
using the new input system, you cannot call API from the old one. Why is the
old one built-in if a new and better one exists? There's a lot of oddities like
that in Unity. Someone who slavishly follows Unity blogs and forums probably
knows the answer, but most people don't seem to.

### The ecosystem hangover

Then there's the Asset Store. After the Fab fiasco, approaching any Unity-owned
marketplace filled me with much scepticism. However, given the fact that the
engine is a lot more barebones than UE5, I knew that plugins of some kind were
likely inevitable, so I had to take a look.

The Unity Asset Store, in stark contrast to the AI-sludge apocalypse of Fab, is
a remarkably professional and well-curated environment. It feels like an older,
wiser sibling. The assets I downloaded were clearly made by people who
understood the engine, although I mostly consumed creative assets. In either
case, it is clear at a glance that Unity Technologies did not give the Asset
Store the Fab treatment. This made me a bit more confident in proceeding with
trying the engine out more properly.

### A stealth game

With Unity, I started with a significantly more ambitious project than with
UE5. Here, I wanted to have a go at a game inspired by *Tom Clancy's Splinter
Cell: Chaos Theory*, more specifically the co-op part of the game. For a novice
game developer, this might sound like insanity, and later I would learn that,
yes, it absolutely was insane.

But there was method to the madness. After UE5 collapsed from underneath me, I
wasn't about to invest months into another project without first validating
that the core mechanics were even possible. I needed to prototype the
fundamental systems that would make or break a stealth game: light and shadow
detection, enemy awareness, and player coordination. If I could get those
working, the rest was just content. At least, that's how I explained it to
myself at the start.

The first order of business was the line-of-sight system. In *Chaos Theory*,
enemies don't have a simple binary "seen/not seen" state. They have a metre
that fills based on how exposed you are, how much light is hitting you, and how
far away you are. Recreating this required something more sophisticated than a
simple raycast from an enemy's head to the player's centre of mass.

This is where Unity's component-based architecture, for all its barebones
frustration, actually shines. The engine's Mechanim humanoid rigging system,
primarily designed for animation, exposes a detailed map of the character's
skeleton. I wrote a script that automatically placed detection points on
specific body parts; head, torso, arms, legs. Then, for each of these points, I
cast a ray towards every light source in the scene.

Here is where the magic happened. By reading the intensity data from
the light that hit each body part, and factoring in the distance to the enemy
and the angle of exposure, I could calculate a visibility percentage. Stand
fully in shadow? Zero percent. Stand directly under a floodlight? One hundred
percent. Peek an arm into a beam of light while the rest of you is dark? One
hundred percent, and the alarm is sounding. It worked. It actually worked.
Within a few weeks, I had a stealth system that felt genuinely reactive, and I
had built it from scratch using nothing but C# and the engine's exposed
transform data. There were no issues on the scale of Fab's critical
infrastructure failure. Awesome!

This moment crystallised something important about Unity. In UE5, I would
have been searching for a plugin that did this for me, or wrestling with
Blueprints to approximate the logic. In Unity, I just wrote code, the way I
always would do in any other project on my Linux machine. The engine got out of
my way and let me implement my exact vision, not an approximation of it. It was
empowering in a way that UE5 never was.

### The networking surprise

With the core stealth loop feeling solid, I turned my attention to the co-op
aspect. This, I assumed, would be the point where the project hit a wall.
Networking is notoriously difficult. It is the domain of dedicated engineers
who spend years untangling latency compensation, state synchronisation, and
rollback logic. I am not one of those engineers.

Then I discovered [Mirror](https://mirror-networking.com/).

For the uninitiated, Mirror is a high-level networking framework for Unity that
essentially abstracts away the soul-crushing complexity of multiplayer game
development. It is, without exaggeration, one of the most impressive pieces of
free software I have ever encountered. It wraps Unity's underlying transport
layer in a clean, authoritative server architecture that feels like it was
baked into the engine from day one.

The API is a masterclass in design. You mark a script as a `NetworkBehaviour`
instead of a `MonoBehaviour`. You tag variables with `[SyncVar]` to
automatically synchronise them across clients. You call functions with
`[Command]` (from client to server) and `[ClientRpc]` (from server to clients).
That's it. The framework handles the rest: spawning, despawning, interest
management, even lag compensation if you dig deep enough. It's crazy work.

Within a week, I had two characters spawn into the same level, saw each other
smoothly moving in real-time, and could trigger the alarm system for both
players simultaneously. I had done absolutely nothing to earn this. It almost
felt illegal. Mirror simply worked, and it worked because C# as a language
enables this kind of elegant abstraction. The framework feels less like a
third-party add-on and more like a natural extension of the language's syntax,
because it is. It uses attributes and method hooks in a way that C++ simply
cannot replicate, at least not without some kind of demonic preprocessor abuse.

This experience forced me to reconsider my entire framework for evaluating game
engines. UE5's AI toolset is undeniably powerful, but it is a walled garden.
You use it as Epic Games intended, or you do hours of research and acrobatics
around the engine. Unity, by contrast, is porous. Great ideas can seep in from
the outside and become first-class citizens through the sheer quality of their
implementation. Mirror is not an official Unity product, yet it integrates more
seamlessly than half of Unity's own packages, at least in my experience.

### The issues

Of course, even though Unity does not suffer from the same catastrophic
failures as UE5's plugin management system, it is not all sunshine and
rainbows. There are a few issues and hiccups, particularly to the editor
experience. And, as you might have guessed by now, these issues tend to cluster
around the operating system I deliberately choose to use.

All things considered, Unity is still primarily aimed at Windows users. The
engine runs on Linux, yes, and the build pipeline is impeccable, but the editor
itself carries the distinct scent of a port. It works, but it works in the way
a car with a check engine light works: you learn to ignore the faint rattle
because the alternative is walking.

One of the main ways this manifests is through dreadful user interface bugs,
particularly in the realm of windowing and rendering. The editor was clearly
debugged primarily on X11, with Wayland support feeling like an afterthought at
best. Much to my own pain, I use a Wayland-based desktop environment called
Niri, where all sorts of Wayland-specific issues arise. Dropdown menus render
in the wrong place, or don't render at all. Context menus flash and disappear
before you can click them. The entire interface sometimes decides that the
mouse cursor is thirty pixels offset from where it's actually clicking. It is
the kind of low-level, grinding frustration that makes you question every life
choice that led you to this moment.

[If you search the
web](https://discussions.unity.com/t/no-ui-scaling-for-linux-you-gotta-be-joking/1638248),
you can find scattered forum posts confirming the pattern: there is no UI
scaling or font resizing on Linux, despite both features being present and
functional on Windows. This is not a technical limitation; it is a
prioritisation failure. The Linux version of the editor treats your
high-resolution display with the same contempt that a console porter treats a
PC port. Everything is small. If you do `GDK_SCALE=2`, comically large. There
is no in-between.

But the most infuriating issue, the one that nearly made me uninstall the
entire thing, is that some dropdowns simply cannot be interacted with. Adding
collision layers, a fundamental task for any game with physical interactions,
is apparently impossible through the standard editor interface on my setup. The
dropdown appears, you click it, and nothing happens. It just sits there,
mocking you. The only way I could add collision layers was to write custom
editor scripts that bypass the broken UI entirely. This is, to put it mildly,
annoying.

These issues are not dealbreakers in the same way that Fab's infrastructure
collapse was a dealbreaker. They are death by a thousand paper cuts. They
remind you, constantly, that you are not the intended audience. The engine
functions, the build system is robust, and the underlying architecture is
sound, but the interface through which you interact with it all is held
together with spit and prayer on anything other than Windows.

Yet, I persist. Godot users are probably screaming at me right now. Why?
Because for all its neglect, Unity on Linux is still more functional than UE5
ever was. The broken dropdowns are annoying, but they are not insurmountable.
The Wayland flickering is irritating, but it doesn't lock me out of my own
purchased assets. The engine trusts me enough to write scripts that fix its own
UI, and in a twisted way, that feels appropriate. Unity is a toolkit, and
sometimes that toolkit includes tools to fix the toolkit itself. It is, at the
very least, an honest kind of broken. Bitterly funny, in my opinion. In this
regard Unity triumphs over UE5 any time of the day.

### Finishing a tech demo

With those frustrations out of the way, however, I did eventually create something
that can be at the minimum be called a tech demo. The source code is hosted
[here](https://codeberg.org/maxwelljensen/muspelheim). It is a stealth game
that successfully connects two players together, allowing them to scour a dark
corner of Europoort to retrieve data, while avoiding detection by guards. At
the end of the level, if they make it out, they receive a rank on their stealth
performance. If they get shot and neither is available for revive, or they run
out of revive charges, the game is over, and they are shown a game-over screen
before being booted back out to the lobby.

Never thought that would happen, but it did. It's an actual game with a win
condition and fail condition. It is not just 3D, but networked, something that
ordinarily is far out of reach for any novice.

This experience proved something to me that I had only suspected before: the
game engine is very much capable if you can work around the issues. Underneath
the UI bugs, the Wayland flickering, and the Windows-centric neglect, there is
a rock-solid foundation. C# is a very cool language and I like that it is
Unity's backbone. The component model, for all its simplicity, scales
gracefully from a single-player prototype to a multiplayer project with
synchronised state and custom editor scripts. Mirror alone is worth the price
of admission. It transforms networking from a dark art into something
approaching mundane.

However, I would be lying if I said it was easy to get to that point.

### The documentation labyrinth

But I would be lying if I said it was easy to get to that point. Not because
the documentation is bad—it isn't. Unity's official documentation is actually
quite good, as far as reference material goes. It is thorough, well-organised,
and technically accurate. If you need to know exactly what parameters a
particular function accepts, or how a specific component behaves under the
hood, the documentation will tell you.

The problem is that it is often fairly minimal. It tells you what something
does, but rarely why you would use it, or how it fits into a complete system.
If you want to learn the engine using purely official documentation, you will
get absolutely nowhere. It is a reference, not a teacher. This is in stark
contrast to Godot's documentation, which can, at least I am sure,
single-handedly show you how to make almost any game. Unity's docs assume you
already know what you're doing; they just need to look up the syntax.

This forces you into the wider ecosystem of tutorials, forums, and YouTube
videos, which brings its own chaos. The core issue is fragmentation. Unity has
multiple rendering pipelines: the Built-in Render Pipeline (BRP), the Universal
Render Pipeline (URP), and the High Definition Render Pipeline (HDRP).
Tutorials rarely specify which one they are using. You will follow a
beautifully crafted YouTube guide from 2021, only to discover halfway through
that the "Standard Asset" package they just told you to import was from the
Jurassic era and doesn't support URP. The comments section is a graveyard of
confused beginners saying the same thing with a one-star rating: *"Doesn't work
in URP"* To an outsider, this looks like a bizarre problem. Unity Technologies
also started to realise that it needs solving, and [Unity 6 is on its way to
absorb both BRP and HDRP into
URP](https://discussions.unity.com/t/render-pipelines-strategy-for-2026/1710004),
but it is unknown when that will take place -- or if it will be successful.

And then there is the age problem. Game development moves fast, and Unity moves
faster. A tutorial from 2018 might as well be written in Sumerian. The UI has
changed, the packages have changed, the entire workflow has changed. Yet these
ancient tutorials remain at the top of search results, luring unsuspecting
developers into dead ends. I spent more time debugging outdated information
than I did debugging my own code. Eventually I gave up on tutorials and started
using online LLMs as search engines to find relevant information. Surprisingly,
this worked very well.

### The weird decay

But the documentation ecosystem, frustrating as it is, is not what stopped me.
What stopped me was the gradual, inexorable decay of the editor itself.

As my project grew -- adding more assets, more scripts, more scenes -- the
editor started to buckle under its own weight. It began subtly: a slight
hesitation when clicking play, a momentary freeze when recompiling a script.
Then it got worse. By the time I had a full level built, complete with
networked enemies and dynamic lighting, the editor would crash inexplicably
about half of the time when I exited a playthrough. Not every time, but often
enough that I developed a reflexive habit of saving before every test. The
crashes were not reproducible; they simply happened, and the editor would
vanish, taking any unsaved changes with it. I did not bother trying to figure
out why they happened and powered through by testing levels as little as
possible.

The performance degradation was equally maddening, but in a more confusing way.
Running the game inside the editor became mind-numbingly slow. Single-digit
framerates, stuttering movement, input lag that made the stealth mechanics
nearly impossible to test properly. I assumed this was just the cost of doing
business. The editor is also running all its own systems, after all. So I
started doing more frequent builds to test the "real" performance.

Here is where things got genuinely bizarre. The Linux builds of my game were
still slow. Not as slow as the editor, but noticeably sluggish. Choppy
framerates, inconsistent pacing, a general feeling of something being wrong at
a rendering or physics processing level. I tried tweaking a few settings,
adjusting quality levels, disabling post-processing, convinced I had made some
catastrophic mistake in my lighting setup or asset optimisation. It seemed very
bad. I was afraid I had finally hit the Fab moment.

Then, as an experiment, I built a Windows version of the game. I do not have a
Windows machine, but I have Bottles, a WINE wrapper that handles Windows
executables super well. I built the Windows build, launched it through the
compatibility layer, and held my breath.

It ran flawlessly. Smooth framerates, responsive controls, no stuttering. The
Windows build, running through an emulation layer on Linux, performed better
than the native Linux build running directly on my hardware. Let that sink in.
A compatibility wrapper, translating Windows API calls on the fly, delivered a
superior experience to the officially supported Linux build of the engine.
Something is profoundly broken in Unity's Linux player pipeline, and I lack the
patience to become a compiler engineer just to diagnose it.

As if to add insult to injury, the build process itself was an exercise in
chaos theory. Sometimes, building the project would take three hours. Three
hours of watching the shader compilation progress bar crawl across the screen,
recompiling every single shader in the entire project. Other times, the exact
same project with the exact same settings would build in ten minutes or less,
performing an incremental build as it should in theory always do. In theory,
the engine should detect which shaders have changed and only recompile those.
In practice, on my Linux machine, it was a coin flip whether I would be waiting
three hours or ten minutes. This is the kind of bug that never gets caught by
beta testers, because the beta testers are overwhelmingly on Windows. It is a
Linux-specific failure mode -- I think, at least -- and Unity Technologies
clearly does not have enough Linux testing to ever encounter it. Oh, well.
That's what I get for using Linux, I know.

### The Rider problem

This brings me to the final, perhaps most frustrating piece of the puzzle: the
tooling.

The only functional environment for working with C# on Linux, in my experience,
is JetBrains Rider. I do not use Visual Studio Code. Neovim, my editor of
choice, was a non-starter. I spent an hour trying to get the language server
protocol configuration to work, wrestling with Omnisharp, Roslyn, whatever,
debugging project files, and reading forum posts on Reddit. Nothing worked
reliably. C# is still a Microsoft-centric product, made primarily for the
Windows ecosystem, and it shows. The language itself is beautiful, but the
tooling around it assumes you are using Visual Studio on Windows or, at best, a
Jetbrains product as a cross-platform concession.

And Rider. Damn, Rider. It is dreadfully, inexcusably bloated software. Opening
my project would peg all 16 logical cores of my CPU at 100% for up to a minute.
The fan would spin up like a jet engine, my desktop environment would be
choppy, and I would sit there, staring at the screen, waiting for the behemoth
to finish indexing my code. As the project grew, this startup time only
worsened. The actual coding experience, once loaded, was excellent. Refactoring
tools, debugger integration, navigation, and, most importantly, a Vim mode. All
of that was top-tier. But the cost of admission was handing over a significant
chunk of my system's resources every single time I opened the project. I don't
remember how much RAM it used, but it is a lot.

This is the Unity paradox. The engine itself, for all its flaws, is capable.
The language is a joy. The frameworks built on top of it, like Mirror, are
engineering marvels. But the path to using them is steep for Linux users, with
broken dropdowns, outdated tutorials, editor crashes, and a dependency on a
resource-hungry IDE that treats my CPU like a rented mule. It's not ideal.

### Final evaluation

I ran out of patience. That is the honest truth. Not because the project was
impossible, not because the engine was fundamentally broken, but because the
cumulative weight of all these small frictions finally exceeded my willingness
to push through them. I realised, somewhere around the fiftieth editor crash,
that making a 3D game is actually pretty hard. Not just technically hard, but
existentially hard. It requires a level of sustained focus and tolerance for
pain that I simply do not possess. Remember, I am neither a game developer nor
a programmer.

The tech demo exists. It works. Two people can connect, sneak through a level,
and extract data. That is more than most people ever achieve. But the path to
that demo was so littered with obstacles -- some of Unity's making, some of my
own, some of Linux's -- that I cannot honestly recommend Unity to another Linux
user without a long list of caveats. To a Windows user? Most certainly.

If you are willing to tolerate UI bugs, outdated tutorials, editor crashes,
and the necessity of running Rider, Unity will reward you with a genuinely
powerful development environment and a language that doesn't make you want to
tear your hair out. It is, as I said, an honest kind of broken. The cracks are
visible from the start, but the foundation is sound.

I do not regret the time I spent in Unity. I learned more about game
architecture from those three months of non-stop work than from any other
project. However, I also learned that I value my sanity more than I value
finishing a project. And so, with the tech demo uploaded to Codeberg and a
quiet sense of accomplishment, I closed the editor for the last time. Unity had
taught me what was possible. It was time to see if another engine could teach
me what was sustainable.

## Godot 4.6

If you have been paying attention, you might have noticed a small inconsistency
in my earlier storytelling. I claimed that my "first real foray" into game
development was with Unreal Engine 5. That is true in the sense that it was the
first time I seriously committed to a project, but it is not true
chronologically. My actual first steps into game development were taken with
Godot, years before I ever installed Epic Games' launcher.

This might seem contradictory given my Linux and free software leanings. Why
would a free software advocate start with a proprietary engine and only later
try the libre alternative? The answer, as with most things, is complicated. I
did try Godot first. I wanted it to work. I believed in its mission. But my
early experiences with it were frustrating enough that I convinced myself I
needed something more "professional." Only after being burned by Unreal's
infrastructure and worn down by Unity's editor decay did I find myself circling
back, older and perhaps wiser, to see if the free software project had matured.

### The first steps

My initial experiments with Godot were humble, as all first steps should be. I
was not trying to build a networked 3D stealth game; I was trying to understand
the fundamentals of game development in an environment that respected my
freedom. The engine was lightweight, launched instantly, and didn't try to sell
me anything. It felt as I would expect from a free software project.

I started two small projects, both 2D, both intentionally limited in scope. The
first was a subtle horror platformer, aiming to replicate the aesthetic and
constraints of NES-era hardware. Limited colour palettes, chunky pixels, tight
jump physics, scanlines; the kind of game that forces you to focus on
atmosphere and mechanics. The second was a 2D spaceship game, something in the
vein of, where you would pilot a small vessel through ruins and try to salvage
scrap.

Both projects taught me the contours of the engine. The node system, Godot's
architectural core, is a thing of beauty. Everything is a node, and nodes can
have children, creating a hierarchical scene tree that is intuitive to anyone
who has ever thought about how objects relate to each other. A player is a
node. Their sprite is a child node. Their collision shape is another child.
Their weapon is a child of the player, and the weapon's projectile spawner is a
child of that. It is clean, logical, and immediately comprehensible in a way
that Unity's `GameObject`-with-components model is not. Not to say that I don't
like Unity's approach, but it requires more work and care. Godot's approach is
like a preschooler drawing a house with a crayon. It is simple, but it conveys
exactly what it needs to. It's clear it's a house.

GDScript, the engine's primary language, is similarly approachable. It is
essentially a drastically simplified Python with game development keywords
bolted on. If you can write Python, you can write GDScript. The integration
with the engine is seamless.

If that is the case, why did I leave?

### The editor workflow war

My frustrations, as they often do, came down to the text editor. I live in
Neovim. It is not just a preference; it is an extension of my thinking. The
idea of abandoning my carefully cultivated configuration, my muscle memory, my
modal editing workflow, to use a built-in editor with primitive Vim emulation
was like nails on chalkboard to me.

At the time I first tried Godot, it was version 3.x. The language server
protocol integration was poor. It was supposed to work in theory, but in
practice it I never got it to work. It sucked, but I wanted to try Godot
anyway. The built-in editor, thankfully, had a Vim mode plugin, but it left a
lot to be desired. It supported basic motions, but anything beyond that, such
as macros, complex repeats, window navigation, was absent. It did not feel too
great, but a Vim mode is better than no Vim mode. If there was no Vim mode, I
would have never bothered in the first place.

This might sound like a minor complaint, the whining of a developer who refuses
to adapt. But workflow is not minor. Workflow is the thing you do for hours
every day. If the tools fight you at that level, the friction accumulates until
you cannot think past it. I wanted to love Godot, but every time I opened the
editor, I was reminded that I was not in my environment. I was in someone
else's environment, and they had different ideas about how code should be
written. It was annoying.

### The disaster

Then came the straw that broke the camel's back, the moment that sent me
furious and made me not bother with game development for a long time
afterwards.

I have opinions about indentation. Not strong opinions, but opinions
nonetheless. I prefer two spaces to tabs. It is a small thing, but it is my
small thing. In Godot's editor settings, I changed the default from one tab to
two spaces, assuming this would affect how the editor displayed and inserted
whitespace in new files.

What I did not realise, because I was a gamedev rookie and had not yet learned
to treat every project like a potential supernova, was not taking into account
that this setting could reset and trigger changes to the project. One time I
opened my project, Godot helpfully reformatted every single script I had
written, converting all spaces to tabs. No idea why that happened. This would
have been annoying but survivable, except that the reformatting introduced
subtle syntax errors in many places, because GDScript is one of those languages
that uses indentation for scope delimiting. Honestly I strongly dislike
indentation for scope delimiting, but I digress. My game no longer ran. Worse,
I had not been using version control. I was a rookie, and rookies make
mistakes.

The project was not irrecoverable. I could have manually fixed the errors, or
reverted the files from backup if I had thought to make one. But the violation
of trust was profound. The engine had reached into my project and changed my
files without asking. It had assumed, with the arrogance of software that knows
better, that its interpretation of my preferences was more important than my
existing work. I was furious, and more than that, I was scared. If the engine
could do this once, what else could it do?

In my frustration, I made a decision that now seems bitterly ironic: if I was
going to use software that did not respect my workflow or my files, I might as
well use the software with the most features. When I did eventually decide to
come back to game development, I told myself that at least Epic's monolith
would not secretly reformat my code while I was not looking. The fact that I
later discovered Unreal's own deep disrespect for its paying customers, in the
form of the Fab fiasco, is the kind of cosmic joke that's played on people who
make decisions out of anger rather than principle. Totally deserved.


### Round Two! Fight!

After having used both Unreal Engine 5 and Unity, with far more game
development experience and education under my belt, I started appreciating
Godot for what it was: a free software project. Yes, it has its issues, just
like nearly all other software on the planet. Yes, pull requests take eons to
get reviewed and merged. Yes, it doesn't have AAA landscapes. You know what it
doesn't have, though? Bloat and five-business-day loading times.

You click on your project, you wait maybe two seconds, and the entire project
is loaded. Nothing is loaded in the background; if you see the window, it is
ready to be used. No jittering, no lag, just the project, ready. After months
of watching Unity's editor slowly choke on its own complexity, and after years
of knowing that Unreal's build requires a coffee break, this felt like a
miracle. It reminded me why I fell in love with computers in the first place:
they are supposed to be fast. They are supposed to get out of your way. I guess
I just needed to try actually horrendous software first before I started
appreciating Godot properly.

### Making peace

The first thing I had to do was swallow my pride about indentation. I spent
years using two spaces, convinced it was the objectively correct choice. Tabs
are for savages, I told myself. But GDScript's official style guide specifies
tabs, and the wider ecosystem has settled on them. Fighting this would mean
constantly reformatting other people's code, creating unnecessary diff noise,
and generally creating problems for myself.

The real revelation, however, was Godot 4. Something fundamental shifted
between version 3 and version 4: the engine's relationship with external tools
improved dramatically. The language server protocol integration, once not
working or only barely nightmare, now just works. It took some effort to
configure. I had to look at a few blog posts, since nothing in Neovim is truly
plug-and-play, but once I had it set up, the experience was remarkably close to
perfectly functional.

The LSP does not crash. It does not bug out. It provides autocomplete,
go-to-definition, find-references, and all the other amenities I expect from a
modern development environment. Even the debug adapter protocol (DAP) works,
allowing me to set breakpoints and step through GDScript code from inside
Neovim. This is the workflow I always wanted: the engine in one window, my
editor in another, and a fast, reliable communication channel between them.

For the first time, I felt like a game editor was actually designed to work on
my PC. Not someone else's commercialised idea of a PC, but my PC. It did not
force me into its editor. It did not punish me for wanting modal editing and a
terminal-based workflow. It finally provided the language server and got out of
the way. This is the free software way: you build the components, and users
assemble them into the system that works for them.

### Lessons applied

My time in Unity, for all its frustrations, taught me something valuable: how
to structure a project. Unity's component-based architecture forces you to
think in terms of reusable behaviours attached to game objects. Godot's
node-based system is different, but the underlying principles of separation of
concerns and data-driven design are essentially the same.

I applied these lessons ruthlessly. In my GDScript files, I use `@export var`
whenever possible, exposing variables in the inspector instead of hardcoding
`NodePath`s. This is the kind of practice that makes a project maintainable. It
allows you to tweak gameplay parameters without diving into code, and it forces
you to think about which values actually need to change during development.
Unreal Engine taught me nothing useful in this regard. Its Blueprint system
actively makes clean separation by very difficult, without a lot of messing
around with boxes and groupings. Unity, for all its editor crashes and build
inconsistencies, taught me how to actually architect a game.

The other lesson I carried forward was typing. In my early Godot experiments,
my GDScript were not rigorously typed, leading to runtime errors that could
have been caught statically. This time, I never left anything untyped. Every
variable, every function parameter, every return value: explicitly typed.
GDScript's type system is not as sophisticated and intricate as C#'s, but it is
more than sufficient to catch entire classes of bugs before they reach runtime.
I am grateful that this feature was well thought-out from beginning, unlike
with Python, where type annotations were bolted onto Python 3.x, far after its
architecture settled for good.

I configured the editor to throw errors if a variable is left untyped or cannot
be inferred. This might seem strict, especially for a dynamic language, but it
transformed the programming experience into pure joy. The language server
provides instant feedback, the autocomplete knows exactly what methods are
available, and refactoring becomes a safe, mechanical process rather than a
leap of faith. When your tools catch your mistakes before you even run the
game, you spend less time debugging and more time creating.

Godot, in its current form, is not the engine I abandoned years ago. It is
significantly better, at least enough to get me back into action. It is free
software, it respects my workflow, and it loads in two seconds. For the first
time since I started this gamedev journey, I feel like I am building with the
right tool.

### Size of the ecosystem?

I will not say too much about the Godot ecosystem, because this topic has been
done to death in every other game engine review that exists, but I want to say
a few words that have not been said all that often.

Most certainly, Godot is not as popular as Unreal Engine 5 and Unity, therefore
its ecosystem is small. This is to be expected. You will not find thousands of
high-fidelity assets ready to drag and drop. You will not find a Fab
equivalent, for better or worse. What you will find is an Internet forum of
people who genuinely care about the software because they built it, or at least
contributed to it. There is a different energy in Godot spaces, less
commercial, more collaborative.

However, if this article has shown anything, it is the value of free software.
And free software has a unique advantage that no proprietary engine can ever
replicate, no matter how many assets flood their marketplace.

### The fork escape hatch

Godot's management, almost like every other free software project, [has been
partially hijacked by weird, mentally ill
men](https://lunduke.locals.com/post/6174150/godot-responds-to-mass-banning-no-apology-blames-banned-users)
who feel the strong need to inject their incoherent political ideologies into
places where no politics are expected or wanted. This is, regrettably, a
constant pattern in free software projects. Some people cannot separate their
personal crusades from the code they maintain. They rename branches from
`master` to `main`, they roleplay human resource departments with "Codes of
Conduct", they plaster manifestos in README files, and they generally make the
experience of developing software feel like you're a nurse in a low-security
psychiatric facility. However, if a patient tells you that he can fly, you just
ignore him. Just make sure he stays away from high elevations.

In a proprietary engine, you are stuck with whatever you get. If the CEO of a
company like Unity decides that you will now pay a runtime fee, you are out of
luck. If Epic's management decides that Fab should be flooded with AI-generated
sludge and your paid plugins become inaccessible, you have no recourse. You can
complain, you can write angry forum posts, but you cannot fix it. You are a
tenant, not an owner.

In Godot, the situation is a lot less concerning. If the project's leadership
were to go off the rails, injecting nonsense into the core, you can fork it.
Keep whatever copy you have, forever. However, so far, the project is flowing
as before, so I don't have to fork it. Nevertheless, it is highly comforting to
know that I actually own the software. I do not need to worry about anything,
at all. Life is good.
