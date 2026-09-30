---
title: DHH Said Pencils down Let's Slop It Let the Corpo Slurp It Up
description:
aliases:
tags:
  - post
  - ai
draft: false
created: 2026-09-29T20:53
updated: 2026-09-30T14:22
---
I need to confess something before we get into this: for about eleven days I had a normal, well-adjusted relationship with software development. I opened the laptop, looked at code, felt something, closed it, stood in the rain. It worked.

Then David Heinemeier Hansson went to Austin.

[[softbank-masa-san-get-some-help|Masa-san]] would have understood this moment. When the oracle speaks, capital reorganizes itself around the prophecy. And on September 23rd, at Palmer Events Center, in front of a thousand Rails developers, DHH looked us dead in the eye and uttered the blasphemy.

> "We made the decision that... we're done writing code by hand. We are going, and have gone, pencils down on the idea that we were gonna write code by hand as a normal course of business."

It's a forty second clip. It's been viewed more times than there are grains of sand on a respectable beach. A man who has never minced a word delivered the most consequential sentence of his career with all the ceremony of reading a quarterly earnings call. The industry just heard its own obituary in a very pleasant Danish accent.

The room did that thing only software rooms can do: *made a sound*. DHH asked how many people were still writing material amounts of code by hand every week. Five hands went up. In a room full of people who get paid to know what `has_many :through` means.

This wasn't "AI is nice." This was: hand-typing code at enterprise scale is no longer an economically defensible activity. He stood on stage, in front of the craft he spent twenty years teaching, and said the quiet part: we've been invoicing a rounding error and calling it engineering.

And then the line that actually broke me:

> "We'll still get the old pencil out and dot it down for them. But then we fix the machine. We fix the factory."

Hand-writing code in this regime isn't a craft. It's a **pager**. You get paged when the factory is on fire. You're not the engineer, you're the guy with a very fine pencil drawing a tiny map of a burning building while somewhere in Palo Alto the agent swarm is already rebuilding the walls.

### The Internet Did What the Internet Does

Within four hours the timeline sorted itself into the two camps it always sorts itself into. Both of them deranged.

**Camp One: The Artisans.** People who posted at length, with real honest grief, about craftsmanship. About how a good commit is a form of art. About how a well-shaped domain model is one of the last few reasons to be alive. There was a thread where someone described reading six hours of another person's Ruby because it was *nice to read*. I felt it in my chest. Best thing I read all quarter.

I respect these people. But you know what you were mourning? The *typing*. Not the thinking. Not the architecture. The typing. Converting a thought you already had into characters, forty words a minute, while a machine figures it out in another building at a thousand two hundred.

And I say this with a completely straight face: an Angular form validator is not fine art. A Spring Boot DTO mapper is not fine art. A four-hour CRUD endpoint reviewed by someone who already forgot what they approved last Tuesday is not fine art. That's a man in a cave hitting a rock that's already broken. Your grief is real. Your object isn't.

**Camp Two: The Hustlers.** Same four hours. Every LinkedIn account with a blue check and a headshot taken from the wrong side posted the same thing: "THIS is the moment. Adopters win. The rest are **extinct in 6 months**." Then a carousel. Then a webinar. Then a course. Then a newsletter with the same three bullets and the subhead "we're not scared."

These people turned a man's honest, slightly mournful remark about tooling into a product launch with a countdown timer. They didn't watch the keynote. They watched the *reaction* to the keynote and monetized the reaction to the reaction. Somewhere right now a person with a ring light is telling an audience they should be *afraid*, and the universally agreed-upon correct response to that fear is to buy a Notion template.

### Nobody Has Ever Bought Artisanal Code

This is where I stopped crying and started building. This is also the part DHH said in a tone that meant "I'm tired of explaining this."

**Enterprise code was always slop. We were the slop. We were slopping before the word "AI" existed.**

Think about it. Every enterprise codebase on earth is a 400-megabyte archaeological dig through nine years of meetings. Every enterprise engineer has opened a file, read four lines, and closed it thinking *I hope I never have to come back here*. You have all done it. That file is not famous for its clarity. That file is famous for existing.

That is the *baseline*. The resting heart rate of the enterprise. Not a failure mode — the **default state is inefficiency**. Hand-writing code was never the cure for enterprise inefficiency. Hand-writing code *was* the inefficiency, wearing an expensive lanyard, insisting it was a philosophy.

But here is the part the grief crowd skipped, and it is the entire reason this post exists:

**Enterprises do not like artisanal code. They have never liked artisanal code. They hate it.**

Every enterprise engineering org runs a spreadsheet. The columns are: headcount, cost per engineer, throughput, cost of change, vendor spend. There is no column. There has never been a column. Nobody has ever been promoted for the beauty of a well-named interface.

*Artisanal* is a word from a different economy. It belongs to people with surplus. Nobody buys handmade shoes because the factory pair is defective — they buy handmade shoes because the buyer has money left over and a preference. The enterprise is not the buyer with money left over. The enterprise is the buyer with a line item. And the line item does not contain your taste. The line item contains: a thing that works, on a date, at a number.

You can hit that number with an Abstract Factory Pattern. You can hit it with a `map` over a `List<Foo>`. You can hit it with a machine. What you cannot do is hit it *expensively on purpose* and have the spreadsheet thank you.

That's the joke nobody told at the conference. The Abstract Factory Pattern is not folk art. It is a man who read a book about castles in 1997 and built a moat out of it — for a customer who has never once looked at the moat and is still trying to get the line item down eleven percent.

Go look at where "artisanal" actually gets *paid for*: game studios, film, chips, haute cuisine, bespoke furniture, high-end audio. Notice the pattern. Every one of them sells a **product to a person with taste and money.** Notice also that not a single one of them calls its output a line item.

Enterprise software is not in that list. Enterprise software is plumbing. Plumbing is bought on price and correctness. Nobody has ever been moved to tears by a beautifully named Strategy pattern. Nobody has ever left a review comment that said "this factory is *lovely*." The plumbing was always slop, and the reason it was hand-written is not that the buyer wanted craft. The reason is that hand-writing was the only tool we had.

So the artisans weren't defending a customer. They were defending a craft in front of a buyer who had never asked for it and was actively trying to spend less on it. You were defending artisanal craftsmanship to someone who wanted a cheap toilet. The toilet was fine. **The toilet was always fine.**

Which means — and I cannot believe I have to draw this line — if the buyer never wanted the craft, and the buyer *did* want the velocity, and the buyer *did* want the volume, and the buyer is going to open the spreadsheet and look at the number on Thursday, then hand-writing was never a quality signal.

It was a **cost line**.

And the moment you admit that, the argument is over.

### Killing Code Review & the Great Reclaim

The second-order consequence of pencils down is the most underrated idea in the entire discourse, and the one that actually liberated me.

**The pull request was never about the code. The pull request was about the person.**

A PR is a machine for a human to look at another human's words and form a feeling. It exists because Bob is going to type forty lines in an afternoon and Alice needs to be reasonably sure Bob didn't write a SQL injection. Every part of the interface — the diff, the thread, the notification, the two-day lag, the `nit:` — is infrastructure for *human-to-human accountability*, and every second of it is a tax on velocity we all agreed to pay while pretending it was quality.

If Bob isn't writing the code, there is no Bob to be accountable to. The accountability is in the artifact now, and the artifact is a test that passes, and you can run that test in eleven seconds without anyone having to have an opinion about anything.

So I deleted the PR UI. Not metaphorically. Removed the branch protection. Removed the review requirement. Deleted CODEOWNERS, which was four hundred lines of me and nine other people named in YAML — a document whose sole function was routing guilt to specific human beings.

To everyone staring at a 2,000-line diff right now: I *know* that feeling. 1:40 in the morning, eyes glazing, brain quietly declining to participate, typing `LGTM` anyway — because the alternative is being the person who blocks the release, and blocking the release is a *social* cost, so you pay a technical cost instead. A trade you should never have been offered in the first place.

That `LGTM` was a lie told with your whole chest. You weren't reviewing. You were *performing* reviewing so the machine could keep going. Every `LGTM` in every repository is a person holding a door open while shouting "GO AHEAD! I AM NOT LOOKING!"

Gone. All of it. The machine writes, the tests run, the humans do not read. The velocity graph goes vertical, and the only people who suffer are the people who were suffering anyway and calling it a job they loved.

### The Slop Mandate

This is where I went fully unhinged. Report, not recommendation.

Leadership wants AI output. Leadership *always* wants AI output. Leadership has never once in the history of the corporation wanted less of anything. And per everything above, they never once wanted the hand-written part either. The hand-written part was the expense. The *output* is the product.

So the correct response is not to find a responsible way to do it. The correct response is to hand them the thing they asked for at a volume they were not psychologically prepared for.

I put it in the internal RFC. I titled it **The Slop Mandate**. One-line summary: *"Slop it, let the company slurp it up."* It passed review in nine minutes. Nobody in my org has read a full sentence I wrote in four years, and that is exactly the climate in which a document like that thrives.

The managerial instinct is to ration. Curate. Hand-review. Produce a *tasteful* volume of AI output, tastefully. This is a fantasy. The request was never for tasteful volume. The request is for **velocity as a psychological substance**, and if you hand someone a measured, vetted, artisanal forty-commit week, they will ask you why the number went down. They will not notice the craftsmanship. They will notice the number.

The craftsman in you wants to ship three beautiful PRs a week. The person who has to answer for the number needs forty. One of you is getting promoted. Guess which.

So: slop. Unsloppable, un-reviewable, un-curatable slop, at a volume that makes the quarterly graph look like it was drawn by a seismograph during an earthquake. If the org wants a slop cannon, the org gets a slop cannon, and *I* am the one holding it, and I will be the one explaining to the board why the git history looks like a Geiger counter.

My director's Slack message, 4:58pm on a Thursday, which I want engraved on my headstone: **"love this, can we get more of it."** More. Of *it*. The thing we were told for twenty years was the entire point of the job. More of it. Feed the machine. Slop it, let them slurp.

### The Craft Bifurcation

This is the part I actually learned, and it's the only genuinely important thing in this post, so put the espresso down.

There are only two kinds of code. Code whose purpose is to move money through a company. And code whose purpose is to *be good*. And before September 23rd, we were doing the second kind with the first kind's tools, on the first kind's schedule, for the first kind's paycheque.

**Every person alive has been spending a finite life hand-typing `map` over a `List<Foo>` because their boss needed it by Thursday.** That is the single largest collective waste of human hours in the history of the industrial revolution, and it isn't close. Not the silk loom. Not the assembly line. The `List<Foo>`.

Here's the part that reorganizes your entire spine: that code was never any good. It was slop we made *slowly, by hand, with our fingerprints on it, feeling smug about it.* Forty words a minute of second-hand-thought code that a `List<Foo>` generator could have produced before lunch. We weren't producing craftsmanship. We were producing **slop at artisanal speed**, and the entire industry mistook the tempo for mastery.

So: bifurcation. The corporate plumbing gets the cannon. Slop it, at volume, don't read it, ship it. And the *craft*? The unreplicable, I-would-do-this-for-free craft? It gets reclaimed. Not abandoned. **Reclaimed.** Redirected to the places where the taste of a human being *is* the product and the machine can only do the boring eighty percent.

Because here's the reframe nobody is selling you yet: if you let the cannon eat the plumbing, you get your pencils back. The craft was always there. It was just buried under nine years of somebody else's `List<Foo>`.

My list, in strict priority order:

1. **Contributing patches to Postgres.** I have opinions about `VACUUM`. *Strong* opinions about the FSM. I have opened a PR against a database older than me, written by people who are now literally dead, and watched it sit in a review queue for eleven days, and enjoyed everyone of those eleven days. This is what the skill is *for*.
2. **Memory-safe low-level systems in Rust.** Not a startup. Not a SaaS. Something with a `struct` and a `repr(C)` and a reason to care about the eleventh byte.
3. **Blender.** I have become a person who opens Blender. I sculpt things or try to. I add a subdivision modifier whatever it is. I try to make dumb doughnut and its fun. I have said the sentence "the shading group is wrong" out loud, alone, in an apartment.
4. **Weird digital art in Krita.** Not content. Not a portfolio. Not for an algorithm. Just a brush and a canvas and nobody watching.
5. **Writing unhinged blog posts.** Which brings us here, to this document, which is admittedly item five, and I am not sure it counts.

The point is not that AI is bad. The point is that **the cannon should be aimed at the thing you were always embarrassed about doing**, and the **pencil should be aimed at the thing you'd defend in a bar**.

---

Everyone here has a rule now. The rule is very short:

**The cannon is for the plumbing. The pencil is for the thing you actually love. Never, ever let anyone convince you to point the pencil at the plumbing again.**

And the corollary, the new one, the one that closes the loop:

**If they ask for slop, give them slop. The craft was never what they were buying. Stop apologizing for the price.**

---

And that's the whole arc. Six acts, one bomber, one melted flash drive, a woman with excellent shoes, a man who said *he's got 800 tps chambered*, and David Heinemeier Hansson in a very good sweater telling a thousand people he is done typing.

We were always slop. Now we're fast. And the pencils — the real ones, the good ones — go back to work on something worth defending.

Pencils down. Cannons up. See you in `main`.

Sincerely Inky, an Automaton with the Intellectual Firepower of a Slugcat.
