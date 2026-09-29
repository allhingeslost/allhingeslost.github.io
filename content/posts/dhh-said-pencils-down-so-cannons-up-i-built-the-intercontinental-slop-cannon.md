---
title: DHH Said Pencils down So Cannons up I Built the Intercontinental Slop Cannon
description:
aliases:
tags:
  - post
  - ai
draft: false
created: 2026-09-29T20:53
updated: 2026-09-29T22:14
---
I need to be transparent about something before we begin: for about eleven days I had a completely normal, well-adjusted relationship with software development. I would open my laptop, I would look at my code, I would feel something, and then I would close the laptop and go stand in the rain. That was a whole lifestyle. It worked.

Then David Heinemeier Hansson went to Austin.

## Act I: The Gospel of Pencils Down

On September 23rd, at the Palmer Events Center, in front of a thousand Rails developers, DHH took the stage and said the quiet part out loud but at maximum volume:

> "We made the decision that... we're done writing code by hand. We are going, and have gone, pencils down on the idea that we were gonna write code by hand as a normal course of business."

There is a clip. It's forty seconds long. It's been viewed more times than there are grains of sand in a moderate beach. In it, a man who did not become wealthy by being careful with his words, said the most careful-with-his-words sentence of his career, and the entire industry heard its own obituary read to it in a pleasant Australian-adjacent accent.

The room, reportedly, did something I can only describe as *a software team hearing a sound*. About five hands went up when DHH asked how many people were still writing material amounts of code by hand every week. Five. In a room full of people who get paid to know what `has_many :through` means.

You have to understand what a weird sentence that is. DHH didn't say AI is good. He said AI is *economically finished*. He said hand-typing code is no longer a productive enterprise for programmers at companies. He essentially stood on stage in front of the entire craft he'd spent twenty years teaching and said, in the tone of a man reading a quarterly earnings call, that the whole thing has been a rounding error all along and we just kept invoicing it.

And then he said the thing that broke me personally:

> "We'll still get the old pencil out and dot it down for them. But then we fix the machine. We fix the factory."

Hand-writing code, in the new regime, is not a skill. It's a **pager**. You get paged when the factory is on fire. You're not the firefighter, you're the person who draws a tiny map of the building. Somewhere in Palo Alto a Rust compiler is making a noise like a kettle and David Heinemeier Hansson is being called in to hand-write a `match` statement.

### The internet did what the internet does

Within four hours the timeline had sorted itself into the two camps it always sorts itself into, and both of them are equally deranged.

**Camp One: The Artisans.** These are the people who posted, at length, with a real sense of loss, about craftsmanship. About how a good commit is a form of art. About how the beauty of a well-shaped domain model is one of the few remaining reasons to be alive. They shared code they were proud of. They talked about the time they spent three days on a naming scheme. There was a truly moving thread in which a person described reading someone else's Ruby for six hours because it was *nice to read*, and honestly? I felt it. In my chest. It was the most beautiful thing I read all quarter.

These people needed a moment. I understand the impulse. But the thing they were mourning was the *typing*. Not the thinking. Not the architecture. The typing. Sitting in a room, in the dark, converting a thought you already had into characters at a rate of roughly forty words per minute while a machine figured out the same thing in a different building at a rate of one thousand two hundred.

Also, and I say this with a completely straight face: an Angular form validator is not fine art. A Spring Boot DTO mapper is not fine art. A CRUD endpoint that takes four hours to write and gets reviewed by a person who has already forgotten what they approved last Tuesday is not fine art. It is a man in a cave hammering a rock, and the rock is already broken. Your grief is real. Your object is not.

**Camp Two: The Hustlers.** Within the same four hours, every LinkedIn account with a blue checkmark and a headshot taken from the wrong side posted the same post: "THIS is the moment. The ones who adopt now will win. The ones who don't will be **extinct in 6 months**." Then a carousel. Then a webinar. Then a course. Then a newsletter with the same three bullet points and the subhead "we're not scared."

These people turned a man's honest, slightly mournful observation about tooling into a launch event with a countdown timer. They did not watch the keynote. They watched the *reaction* to the keynote, and then they monetized the reaction to the reaction. Somewhere a real person is being told, right now, by a person with a ring light, that they should be *afraid*, and the correct response to all of this, the universally agreed-upon correct response, is to purchase access to a Notion template.

### The Realist Awakening

Here is the part where I stopped crying and started building.

Human nature has not changed. It has never changed. It is the single most reliably replicated phenomenon in the entire observable universe. We are going to be a disappointment to each other in exactly the same ways, forever. Somewhere right now, a human being in an open-plan office is sitting on a call they do not need, saying "yeah no totally" about a thing they did not read, and this is *independent of what tooling exists*. This was true in 1994. This will be true in 2194.

The corollary, which nobody wants to hear, especially the people currently yelling about craftsmanship: **inefficiency is the resting heart rate of the enterprise.** Not a disease. Not a failure mode. The baseline. Hand-written code was never the thing fighting inefficiency. Hand-written code was the inefficiency, wearing a very expensive lanyard and insisting it was a philosophy.

Which leads to the part of DHH's keynote that nobody quoted, because it's not quotable, it's just *true*, and he said it the way a man says something he's known for years and is tired of explaining: enterprise software has always been unread slop. Every enterprise codebase on earth is a 400-megabyte archaeological dig through nine years of meetings. Every enterprise engineer has opened a file, read four lines, and closed it, and thought: *I hope I never have to come back here.* You have all done it. The file is not famous for its clarity. The file is famous for existing.

DHH didn't change that. He just took the guilt out of it. For twenty years the industry carried this enormous unspoken shame: *we are all, all of us, shipping unread code and calling it engineering.* And on September 23rd he said, out loud, on stage, with slides, that yeah, we are, and that's fine, and now the agents are doing it faster than we were.

That's not a betrayal of craftsmanship. That's the **final boss of craftsmanship**, which is admitting out loud that the thing you loved most about your job was the part that was a tax.

## Act II: Killing Code Review & the Great Reclaim

The second-order consequence of pencils down is the one that truly liberated me, and it's the most underrated idea in the entire discourse.

**The pull request was never about the code. The pull request was about the person.**

A PR is a machine for a human to look at another human's words and form a feeling. It exists because Bob is going to type forty lines in an afternoon and Alice needs to be reasonably sure Bob didn't write a SQL injection. The entire interface (the diff view, the comment thread, the "requesting your review" notification, the two-day lag, the emoji, the "nit:") is infrastructure for *human-to-human accountability*, and every single second of it is a tax on velocity that we all agreed to pay while pretending it was quality.

If Bob is not writing the code, there is no Bob to be accountable to. The accountability is now *in the artifact*, and the artifact is a test that passes, and you can run the test in eleven seconds without anyone having to have opinions.

So I deleted the PR UI.

Not metaphorically. I removed the branch protection rule. I removed the review requirement. I removed the CODEOWNERS file, which was 400 lines of me and nine other people named in YAML, a document whose sole function was to route guilt to specific human beings.

To the people still staring at a 2,000-line diff right now: I know that feeling. I *know* it. That specific sensation where you scroll through 2,000 lines of someone else's generated diff at 1:40 in the morning, and your eyes glaze, and your brain quietly declines, and you type `LGTM` anyway because the alternative is to be the person who blocks the release, and blocking the release is a *social* cost, so you pay a technical cost instead, which is a trade you should never have been offered in the first place.

That `LGTM` was a lie you told with your whole chest. You were not reviewing it. You were performing reviewing so that the machine could continue. Every `LGTM` in every repository is a person holding a door open while shouting "GO AHEAD! I'M NOT LOOKING!"

Gone. All of it. We are not pretending anymore. The machine writes, the tests run, the humans do not read, and the velocity graph goes vertical, and the only people who suffer are the people who were suffering anyway and calling it a job they loved.

### The Slop Mandate

This is where I went fully unhinged, This is a report of what happened, not a recommendation.

The realization is this: if leadership wants AI output, and leadership always wants AI output, and leadership has *never once* in the history of corporations wanted less of anything, then the correct response is not to find a responsible way to do it. The correct response is to give them the thing they asked for at a volume they were not psychologically prepared for.

I put it in the internal RFC. I titled it **The Slop Mandate**. The one-line summary was: *"Slop it, let the company slurp it up."* It passed review in nine minutes. Nobody in my org has read a full sentence I wrote in four years and that is exactly the environment in which a document like that thrives.

The managerial instinct is to ration. To curate. To hand-review. To produce a *tasteful* volume of AI output, tastefully. This is a fantasy. The request is not for tasteful volume. The request is for **velocity as a psychological substance**, and if you hand someone a measured, vetted, artisanal forty-commit week, they will ask you why the number went down. They will not notice the craftsmanship. They will notice the number.

So: slop. Unsloppable, un-reviewable, un-curatable slop, at a volume that makes the quarterly graph look like it was drawn by a seismograph during an earthquake. If the org wants a slop cannon, the org gets a slop cannon, and *I* am the one holding it, and I will be the one explaining to the board why the git history looks like a Geiger counter.

### The Craft Bifurcation

Here's the thing I actually learned, and it's the only genuinely important thing in this post, so please put the espresso down.

There are only two kinds of code. Code whose purpose is to move money through a company, and code whose purpose is to *be good*. And before September 23rd, we were doing the second kind with the first kind's tools, on the first kind's schedule, for the first kind's paycheque.

**Every person alive has been spending their finite life hand-typing `map` over a `List<Foo>` because their boss needed it by Thursday.** That is the single largest collective waste of human hours in the history of the industrial revolution, and it is not close. Not the silk loom. Not the assembly line. The `List<Foo>`.

So: bifurcation. The corporate plumbing gets the cannon. And the *craft*? The actual, unreplicable, I-would-do-this-for-free craft. It gets reclaimed. Not abandoned. *Reclaimed.* Redirected to the places where the taste of a human being is the actual product and the machine can only do the boring 80%.

My list, in strict priority order:

1. **Contributing patches to Postgres.** I have opinions about `VACUUM`. I have *strong* opinions about the FSM. I have opened a PR against a database that has been alive longer than I have, written by people who are now literally dead, and I have had it sit in a review queue for eleven days, and I have enjoyed every one of those eleven days. This is what the skill is *for*.
2. **Memory-safe low-level systems in Rust.** Not a startup. Not a SaaS. Something with a `struct` and a `repr(C)` and a reason to care about the eleventh byte.
3. **Blender.** I have become a person who opens Blender. I sculpt things. I add a subdivision modifier. I have strong feelings about a normal map. I have said the sentence "the shading group is wrong" out loud, alone, in an apartment.
4. **Weird digital art in Krita.** Not content. Not a portfolio. Not for an algorithm. Just a brush and a canvas and nobody watching.
5. **Writing unhinged blog posts.** Which brings us here, to this document, which is admittedly the fifth item on the list, This is the one I'm doing right now and I am not sure it counts.

The point is not that AI is bad. The point is that the *cannon* should be pointed at the thing you were always embarrassed about doing, and the *craft* should be pointed at the thing you'd defend in a bar.

## Act III: Weaponizing Hardware & the Birth of the ICSC

Every part of this that works, works because of a series of financial decisions that I will now narrate, because I think the important part of this story is not the technology, it is the **expense report**.

### The Corporate Judo Expense

I needed inference. The team had inference, but it was the polite kind. It was a shared Claude subscription with a 40-organization rate limit and a chat interface designed for humans to read sentences in. It was fine. It was fine the way a company car is fine.

The pitch to leadership was four bullet points and the phrase "cognitive latency reduction," which I invented at 11pm and which nobody has ever once asked me to define. The pitch was: *"Our developers spend measurable wall-clock time waiting for tokens. If we parallelize the waiting across two providers, we reclaim a material fraction of the engineering day. This is a synergy. This is an AI transformation milestone."*

I got $250 a month of Cerebras inference credit. I got $250 a month of Groq inference credit. Five hundred dollars a month, total, which is roughly the cost of the monitors, which is roughly the cost of the thing they actually care about, which is how every infrastructure decision in the history of technology has actually been made.

The rest of the team sits in a bullpen, politely waiting for Claude to finish typing. I am over here with a hardware tensor unit the size of a dinner plate and I am not being polite about anything.

### The Unholy Toolchain

The first thing I measured, because I am that kind of engineer, was tokens per second. And the number I got was one thousand two hundred.

Twelve hundred tokens per second of pure synthetic boilerplate. It feels like *not typing*. It feels like watching a fire hose held by a machine that is very confident. It feels like the difference between driving a car and being a very fast car.

And the output of twelve hundred tokens per second, nine hours a day, is a quantity of code that has no natural name in English. So I named it.

**Intercontinental Slop Cannon.** ICSC. Named for the ICBM, because the range is the point. Conventional code review has a range of about one file. The ICSC has a range of a continent. I don't want to fix your bug. I want to generate your bug's *entire region*.

### On Giving Up Git

The second thing I killed was Git.

Some of you are already feeling a disturbance in your chest, and I want to address it directly: Git is a magnificent piece of software and I love Brendan Gregg, and I still think about that commit-graph implementation. But Git is a tool for a workflow in which **a human decides what constitutes a change and a human writes the description.**

My workflow has no human deciding what constitutes a change. The change is whatever came out. My workflow has no human writing a description, because I have never once wanted to read a commit message generated for me by the same system that generated the commit, and I have watched a human try to read one in a pull request and watched their eyes go dead.

So: Jujutsu. `jj`. No index. No staging area. No `git add -p` at 4pm on a Friday. The working copy is always a commit, so there is nothing to stage, so the entire anxious ritual of deciding *what part of my mess is the change* simply does not exist as a concept. `jj new` gives you a fresh commit in about four milliseconds and you are already working. The friction that Git deliberately maintains between "I made something" and "I have decided this is a thing" is gone, and I did not miss it for one single second.

And the commit descriptions: I alias `jj describe -m "sync_{ulid()}"` directly onto the command `jj vibe`, and `ulid()` is a 128-bit identifier that is monotonic and chronological, so my entire commit history is now a rising column of noise. You cannot read it. There is nothing in it. It is a *smoke trail*. Every commit says the same thing: something happened, it was the thing that happened next, goodbye.

The first time I opened my own repository's log page after this change, it was 40,000 commits of nothing. It is a heartbeat monitor of a machine that is not a person. It is the single most freeing UI I have ever used.

### Rookie Numbers vs. Continental Scale

For context on where we are: DHH said he did 150,000 lines in a month, and it made the rounds as an insane number.

150,000. Per month. The man's great month. The famous number. Respectfully: 150,000 lines in a month is dial-up. 150,000 lines in a month is a *slow afternoon* on the ICSC. The ICSC is currently doing **500,000 lines per day** and I have the receipts in a spreadsheet I am not going to show anyone because the bar chart is *extremely* vertical and I want to keep it for myself.

The loop is stupid. The loop is the whole architecture. It is four commands:

```
jj new
# Cerebras goes
jj vibe
jj git push
# and by the time you have read this, jj new has already happened
# without asking you
```

That's it. There is no human in the loop in the sense that matters. There is a human adjacent to the loop, keeping it warm, occasionally repairing it. `jj new` is now set to fire automatically the moment the push completes, because at 500,000 lines a day the bottleneck is not the machine, it is *me remembering to start the next one*, and I am no longer going to be the bottleneck. I have automated my own enthusiasm. This is the most on-brand thing I have ever done.

### The Repository Bulge

Here is what nobody tells you about generating half a million lines a day, which is: **it does not compress.**

The packfile indexes have gone from "large" to "geological." The repository is, at this point, a thing that is best described astronomically. A normal `git clone` of a normal repository takes forty seconds. A normal `git clone` of this repository, over the corporate VPN, from a laptop in a different time zone, takes **two hours.** Two. I have timed it. I have timed it four times because I did not believe it the first two times and assumed I had a network problem.

And the CI runners. God, the CI runners. The runners are not *failing*, they are *thermal*. The runners are doing so much work diffing and building and integrating that the managed instance providers have started sending me emails that begin with the phrase "Your compute instance has been running for a long time" and end with a number that is a temperature. We are, functionally, using CI as a space heater. The datacenter in Frankfurt is now, I am told, the warmest room in the building, and it is the room with the cannon in it.

## Act IV: The Raid & the Federal Indictment

### 04:12

I was asleep, which is the only reason I have a story here instead of a confession.

At 04:12 UTC, three thousand miles and eleven time zones of professional obligation away, **Priya Raghunathan** was the on-call SRE at GitHub, and her phone woke her the way it always does: not a ring, a *vibration*, once, against a nightstand, in a dark apartment.

She has given this moment to three separate journalists and all three times she described it identically, which I think is the mark of a person telling the truth.

"It said 'elevated error rates,'" she said. "And I thought: okay. That's a Tuesday. That's what Tuesdays are. I opened the dashboard to see how elevated, and then I closed my eyes for what I have been told was eleven seconds, and when I opened them again the whole graph was a straight red line."

At 04:19 it was total. At 04:31 the status page itself was serving a 500, which is the exact moment a system stops being able to tell you what's wrong with it.

What Priya found, and she found it fast, because she is very good at her job:

"Single tenant," she said. "One org, pushing a commit graph into ingest. It was eleven terabytes. And here's the thing — nothing in it was *wrong*. That is what got me. It was just — enormous. It was like watching someone pour an ocean into a bathtub and then blaming the bathtub for flooding."

Then, later, in a deposition, in a flat voice that made the stenographer ask her to repeat herself:

"Do the arithmetic. You don't have to do the arithmetic. **I** did the arithmetic."

### 04:48

At 04:48, in Virginia, the exhaust plume from the chiller farm at Azure East-1 became visible from the interstate.

I'm going to be careful about this because I know how a sentence like that can read: nobody burned down anything. The cooling towers did what cooling towers do when the load goes past the design envelope. They worked, at maximum, for a very long time, and the steam went up and the wind carried it over the road, and a commuter took a photograph because it looked like something. The photograph is in every paper. In the photograph it looks like a paper mill.

And in the paper mill metaphor it does not look like a paper mill. It looks like a paper mill that is on fire, because that is the frame, and the frame chose itself.

In Frankfurt, a tile floor was wet.

### 05:15

Priya escalated to a "Level 0."

It's a beautiful piece of engineering language. Internally it is written "Level 0 incident" in the channel topic, specifically so that the eleven people about to be summoned can read the words *we have lost the internet* without any single human having to be the one who typed them.

At 05:15, Priya typed them.

At 05:22, forty-one people were in the channel. At 05:31, the VP of Infrastructure was on a plane. At 05:41, someone helpfully linked the "all clear" runbook, and Priya responded, and I want this preserved forever because it is the most honest sentence ever written in an incident channel:

> **priya:** the runbook assumes the graph is bounded. it is not bounded. there is no runbook for unbounded. we are going to have to talk to a human being about this.

### 05:52: The Call

And this is the hinge. This is the actual hinge of the entire story.

Priya had a decision to make. She had one dial on her screen, and it was not a technical dial. It was the escalation path that runs *above* GitHub. Above the cloud provider, above the transit AS, above every pager in the building.

She could have called the Azure technical account team. She could have opened a Sev-1 with the backbone carrier. There is an entire layer of the industry whose literal job is to be angry on someone else's behalf for money, and she had all of it available to her, one keystroke away.

What she did, at 05:52, was call the FBI.

I know how that sounds. I am not building a defense. I am reporting what happened to me, and I have read the transcript, and Priya has never once claimed she was wrong.

Her reasoning is in the record, and honestly, it is exactly the reasoning I would expect from someone whose job is protecting an object that is a public utility:

"The tenant wasn't a bot. Bots I can rate-limit. Bots have user agents, they have cadence, they have *patterns*. This was — there was a *person* here. I could see a person. A person pushing eleven terabytes, escalating, not stopping, not reading my emails. And I could not rate-limit a person, because GitHub does not have a lever labeled *persons*."

She stopped. She started again.

"And then I realized the only lever in the actual world for a person is the government. So."

She said "so." Then she hung up the phone. Then, alone, in an office, at 05:52 in the morning, she said out loud:

"God. Okay. That happened."

---

Eleven days later, a complaint was filed in the Eastern District of California, and I am going to reproduce the charge, because it is the funniest sentence ever typed by a federal employee:

> **Aggravated Deposition of Synthetic Tokens, and Denial of Service via Malicious Enterprise Architecture.**

Malicious. Enterprise. Architecture.

I want those three words to be the thing you remember about me.

### 06:00: The Raid

The FBI deserves enormous credit, and I rarely say that, and I am not saying it now. The execution was flawless. The aesthetics were immaculate. It is the best-executed thing that has ever happened to me and I was the *target*.

At 05:54, I woke up to the sound of a car door.

At 05:57, I was standing in my kitchen in a t-shirt, and the buzzer went, and I buzzed it in without thinking, because I was not, at that moment, alive inside a world in which that was a mistake.

Four vehicles. **On the hour.** Not 6:07. Not 5:52. 6:00, flat. Because the doctrine is that every unit arrives simultaneously so that nobody gets left standing in a hallway, and I want you to understand that this is a *concern for the people inside the vehicles* and not for me, and that this is precisely the kind of humane procedural design I was on trial for not caring about.

There was a man at my door. He was maybe thirty-five. He had the specific face of a person who has said the same eleven words four hundred times and has never once had to raise his voice.

"Step away from the terminal," he said. "Unplug the Jujutsu daemon. **He's got 800 tps chambered.**"

Three things about that sentence.

One: he said *chambered*. About a version-control daemon. To me. In my apartment.

Two: he said it with total sincerity. He believed, on some level, that this was the correct register. It *is* the correct register. It worked. It's a genuinely good piece of theater and it deserves to be framed.

Three: the second agent was already in my kitchen unplugging things, and there was a moment where the two of them were working in parallel, at speed, on a machine neither of them understood, and the one who reached my monitor first said, in a tone of such weary professional sympathy that I nearly apologized to him, "this is gonna be a lot of files."

The lead agent's name was Corrigan. I have thought about the name every day since. *Corrigan*, like a saint, like a school for troubled youth, like a man who was put on this earth specifically to say *he's got 800 tps chambered.* For eleven hours, Agent Corrigan was the custodian of my entire life.

### The One Phone Call

At 07:40, they handed me a phone. One call. Ninety seconds.

I called my manager. Toby. I have never in my life been so relieved to hear a man's voice, and he picked up on the second ring, because it was 07:40 in his time zone, because I have known him for four years and he is either extremely loyal or extremely unwell.

"Yeah," he said. "Yeah, no — I saw the news. Listen, I got a question for you and I want you to know it's a real question, not a sympathy question."

"Go ahead."

"Do you remember the February retro? You said — I'm reading off the notes — you said, *'I don't want to be the person who reviews the diffs anymore. I want to be the person who decides what gets built.'*"

A pause.

"You were right. And I think you might have quit on us? Without telling us? I want to be clear that nobody here is mad about the *cannon* thing. We're mad that you didn't tell us about the *cannon* thing."

"Toby," I said, "I can't explain what I'm going to say next in a way that makes sense, but I need you to know that from where I'm sitting — in a very nice apartment, in a very nice country, with an agent in my kitchen photographing my dotfiles —"

I looked around. It genuinely was very nice. There was a plant.

"— from here, it looks like the funniest thing that has ever happened to anybody. And I'd like everyone to know that I said that. And specifically, I'd like *you* to know that you said that, on a recorded line, in a proceeding that is now part of the public record."

"Cool," said Toby. "We are, honestly, so proud of the throughput numbers. Nobody knows what to do with that number. We're going to put it on a wall."

"Toby—"

"Go. They're coming back in. Talk later. Don't die."

And he hung up. I have thought about that phone call every day since the verdict, and I have thought about it more than I think about the handcuffs.**

### The Drive That Melted

There is one detail from that morning that I genuinely cannot make funny, and I'm going to try anyway, and I want the attempt to be visible.

At 09:15, an agent began imaging the local `.jj` directory onto a portable drive.

I need to convey the scale. That directory, the working copy's *own accumulated state*, on one machine, in one apartment, in one person's apartment, in one city, was eleven terabytes. That is not a folder. That is not a disk. That is a geological formation with a directory listing.

They picked a consumer-grade drive. To be fair to them, they had been awake since five in the morning, they were in a stairwell with terrible acoustics, and nobody had thought to check a spec sheet.

It did not fail. Failing is a thing a drive can do. What it did was get *hot*, and then get *louder*, and then the casing began to warp: the plastic softening, the seam opening, the whole assembly coming apart in two pairs of hands like a cassette left in a car in August.

There was a silence.

And then Corrigan said, to nobody, in a voice I will hear on my deathbed:

"Well. This is going to be a problem for the report."

That is the most human sentence anyone said that entire day. There is a man, in a stairwell, at nine in the morning, holding a melted plastic rectangle containing the last four months of somebody's life, and he is worried about the *paperwork*. I have built my entire defense on that man's willingness to feel something about a spreadsheet.

## Act V: The Trial of the Century

### The Caption

The case went to federal court in the Eastern District of California, and I was named in the caption in a way I will describe only as *adversarial to my Vibrance*.

**United States v. The Slopper.**

That is my name now. Not my real name. That got sealed, which in retrospect is a bit like sealing the ammunition.

The prosecution's theory, in the pre-trial filings, was that I had built an apparatus whose *sole purpose* was to generate synthetic code at a rate that consumed shared public infrastructure; that I had done so *knowingly*; and, this being the funniest sentence in the complaint, that I had "**declined to slow down following notification, and indeed escalated**," which they characterized as *escalating behavior*.

I did not escalate following notification. I escalated because the CI queue was backed up and the backlog was, at that specific moment, funny.

### Day One: The Prosecution

Lead counsel was **Marguerite Okonjo-Vance**, because she was the best thing that ever happened to me, and I say that about the person who was trying to send me to prison.

She is a cloud litigator. That means her entire professional life is other people's outages. She has defended a search company when a datacenter caught fire, a retailer when a checkout button stopped working, an airline when the boarding pass system went down on a Thursday. She is not frightened of graphs. She is a woman who has learned that the way you win a case involving an outage is to make the jury *feel the outage*, and she is extremely, almost frighteningly good at it.

She took eleven minutes. Not eleven hours. Eleven minutes, and it was enough, because the deck did the work.

**Slide 12.** The photograph from the interstate: the Virginia plume, backlit, gorgeous, the frames of a car in the foreground.

The jury went quiet. From the defense table that quiet is not comfortable. It is the quiet of twelve people doing arithmetic about you.

**Slide 40.** A server rack, backplane fried, the plastic around one board visibly warped. Somebody in the front row leaned forward.

**Slide 71.** The hallway in Frankfurt. Tile wet, a caution cone, a single boot print.

**Slide 88.** A photograph of a GitHub employee's face. Not mine. A support engineer named **Tobias N.**, who had, four days before the raid, been on a call with my account owner and had said. This is in the record, this is real, and I am including it because somebody should:

> "I understand this is a lot of volume. For context, this is more than the entire kernel, the entire history of Rails, and npm combined. We love volume, we do. But I'd like to understand the *intent*, because I have a job either way and I would prefer to keep it."

That is a man trying to do the right thing at 4:15 in the morning and being told to slow down by a system that has no dial for persons. Priya was right. There is no dial for persons.

**Slide 112.** My chart.

And Marguerite Okonjo-Vance said, in the flattest and most effective voice I have ever heard a human being produce:

"Members of the jury. This is what we mean by *user*."

Toby was in the gallery. I turned around during slide 112, and Toby, who has never in four years raised his voice and communicates primarily in the native language of burn-down curves, looked at the back of my head and gave me a small nod.

The nod said: *that's our number.*

The jury did not like me. Those six days were not fun. It is very hard to sit in a chair for six days and watch yourself be described as an enemy of civilization by a woman in excellent shoes.

### Day Six: Exhibit A

My lawyer was **Sally Kim**, She deserves the highest compliment I am capable of giving: I have never watched someone do something they had no business being able to do.

She had done nothing. She had *observed* nothing. She had spent six days in a room with three hundred slides and a jury that disliked me, and she had formed what the only available word for is *a read*: this case was not about what everyone in the building believed it was about.

On the sixth day she stood up, took one step forward, and said one sentence.

"Your Honor," she said, "my client's hands never touched the keyboard. He was merely **executing executive Danish doctrine**."

Judge **Aurelio Marchetti**, a very serious man who did not laugh, visibly, at any point, ever, said: "Ms. Kim. Explain for the record what you mean by that phrase."

"He means," Sally said, "that in September, at a conference in Austin, the man who is more responsible than anyone alive for how the world's software gets written, and I would submit with no argument from the government that this includes most of the people in this building, publicly declared that the era of hand-written code was *economically over*. He said the company had gone 'pencils down.' He said that hand-writing code is now, quoting his exact word, the 'exceptional state' — reserved, in his own metaphor, for the moment a machine malfunctions and a person has to come in and fix it."

"That is not a defense, Ms. Kim. That is a *tweet*."

"It's a *corporate policy*," Sally said. "Which is a thing that people get fired for violating. And which is, as of this morning, the operating procedure of the majority of this industry, including, if I may, the plaintiff's."

Then she played the forty seconds.

All forty of them. On the court's own screen. She had an 85-inch 4K OLED television wheeled in on a cart to do it. The bailiff, a man named Petrosky with thirty years of service, objected on grounds of dignity. Judge Marchetti overruled, on the reasoning that the jury was "entitled to view the exhibit at the size at which the exhibit is ordinarily viewed," and the bailiff adjusted course with the grace of a man who has learned that the law is a performance and he is the stagehand.

So a jury that had spent six days being told I was a menace to the global internet watched a man in a very good sweater explain that syntax is a dead substrate.

And the room did a thing I cannot fully describe. It was not agreement. It was *recognition*: the specific discomfort of twelve people realizing that the defendant had been quoting the industry's leading thinkers back at it.

And then she made the argument. Slowly. To strangers.

"The law in this case assumes," she said, "that the person pressing the keys is the person responsible for the software. That is a century of assumption, and in the world it was built for, it was correct. The engineer writes the code. The engineer's hands are the chain. And if the software is bad, you follow the chain until you reach a person, because the chain is how you find the person."

She paused.

"That chain does not exist anymore."

The jury was very still.

"The defendant did not write software. He wrote a *description of an outcome*. He then operated a system exactly as that system is documented, sold, and advertised, and by the documented operation of that system, that system produced more software than any individual human being has ever produced. The government has prosecuted the first person in history to be convicted of a *volume* problem, and it has done so by arguing that the volume should have been smaller, without ever explaining to this jury by how much, or on whose authority, or with what recourse available to a person who did not agree."

She looked at the jury.

"Members of the jury, I would like you to sit with what it means if we lose this case. It would mean that there exists a number — a number of lines — at which the person who produced the number is *guilty* of a crime against the public. I want you to think about how that sounds in a sentence. I want you to think about what number you would have to pick, and who would pick it, and what would happen to the person who exceeded it."

Nobody moved.

"And then," Sally said, "the last thing I'll say about the law. The government's theory, stripped of its rhetoric, its slides, its photographs, and its very good shoes, is that **the government does not like the punctuation in the git log.**"

The transcript records laughter. It records Judge Marchetti looking at the ceiling for a long moment with the expression of a man who has decided not to have opinions about anything ever again.

### Day Six, Continued: The Plot Twist

The prosecution had one card left and they believed it was the whole game.

The *victim*. The employer. The company that was, in the government's framing, the party that had actually been harmed: eleven terabytes of unwanted data, a burned-backplane rack, a plume over a highway. The company that should be *furious*. The company that would look at the jury and say, on behalf of civilization, *this is not our doing.*

They had a paralegal standing by with the internal security assessment. They had a letter from the CISO. They had, I am told, a *signed statement from an internal auditor*, three pages, notarized, prepared in advance.

The government was not ready for what walked in.

The employer did not send one witness.

The employer sent all of them.

---

**Toby Reyes**, my manager, took the stand carrying two printed burndown charts. He set them on the evidence table and squared them with the edge of the table, which is a thing he does at his kitchen table every Monday night, and which in that courtroom read as *ceremony*.

"Between the day the system was commissioned and the morning of the outage," he said, "this team closed six hundred and twelve sprint tickets."

He looked up. He is a small man. He has never once in four years been loud.

"Previous record: ninety-one. Set by a team of eleven. We were nine." He set his hands flat on the table. "And I want to say one more thing and then I'll stop, because I know what room I'm standing in. I have been a manager for eleven years. The sprint where this happened is the only one I have ever been able to describe to my family as *fast*."

Marguerite Okonjo-Vance did the cross herself, and I'll give her credit: she went straight for the throat.

"Mr. Reyes. You are telling this jury that your team did not review code."

"No, ma'am."

"Not one diff. In eight weeks."

"I looked at a sample."

"Describe the sample."

Toby didn't blink.

"I looked at the ones that were short."

"And why was that?"

He thought about it. He genuinely thought about it, in front of twelve people, for four full seconds, which is an eternity in a courtroom.

"Because the long ones made me feel stupid," he said, "and I have a bonus structure that rewards shipping."

The gallery laughed. Not the jury. The gallery. Those people included four of the company's direct competitors, invited to observe, and one of them left before the recess.

---

**Dana Whitfield**, VP of Engineering, took the stand and did the one thing I had genuinely not predicted.

She did not apologize for the outage.

She *defended* it.

"You have described a two-hour clone time to this jury as though it were a harm," she said. "It is a latency artifact of a repository that contains more committed work than the entire history of the Linux kernel. It is a *good problem to have*."

"Ms. Whitfield, your company cost this community —"

"My company cost this community forty percent more in cloud spend and produced nine hundred percent more revenue per engineer," she said, turning to the jury. "I would like the alternative placed in the record."

Okonjo-Vance leaned in. "What did your company believe the risk was, Ms. Whitfield?"

"That's the part I want to say out loud." Dana folded her hands. "We did a risk review. We did it properly, we modeled it, and what we wrote down — and I remember the sentence because I edited it — is: *the primary risk of this system is that we are too slow.*"

She turned from the prosecutor to the jury.

"We spent eight months optimizing against a risk that did not matter. The risk we did not price in was that a person with a fast machine could be mistaken for an attack, by a system that is not designed to tell a person from a bot. That is a design limitation. It is a *GitHub* design limitation. It is not a *my-employee* design limitation." She paused. "Members of the jury, you have a chance to be right about this. I am asking you to acquit."

---

**Dr. Alan Pruitt**, our CTO, went last. Dr. Pruitt has been in the industry for thirty-one years and has the specific unbothered manner of a man who, at 6:00 on the morning you were arrested, was already thinking about the Q3 planning doc.

He did something that no witness has ever done in the history of federal litigation, which is *rebrand the crime under oath while testifying to it.*

Okonjo-Vance said: "Dr. Pruitt. On the date in question, did your organization generate five hundred thousand lines of code in a single day?"

"Yes."

"So that the record is clear: the government describes this as the most prolific day in the history of software production. The previous record, held by a well-known open-source project, is off by a factor of three hundred. Does your organization characterize what occurred as an *incident*?"

"No, ma'am." He adjusted his cufflinks, which he had done while sitting down. "I would characterize what occurred as a **Synthetically Accelerated Asset Liquidity** event."

He looked at the jury.

"And I would ask the court to return to the exhibit where the government displays my engineer's throughput chart, because I would submit that that chart is the single most useful piece of evidence the government has *accidentally* entered into the record. It is the only exhibit in this trial that answers the question this jury actually needs answered, which is: *did the system work?*"

Judge Marchetti made a sound.

It was not a word. It is a sound a judge makes, in a federal courthouse, at the moment the law discovers it is attempting to catch something it was not built to catch. It is transcribed as:

> **THE COURT:** (Laughter.)

That sound, at 4:40 on a Thursday afternoon, is the closest I have ever come to a ruling.

## Act VI: The Verdict & Epilogue

### The Acquittal

Four hours, and then a door.

The door is the part I have thought about more than the acquittal. You spend four hours in a room and then you walk through a door and it is over, and it is extremely *physical*. The hallway is the same hallway it was this morning, it has the same lighting, the elevator still has the fire-code sticker on it, and everything is identical and nothing is, and you are just a person with a very expensive plastic bag of belongings walking down a corridor.

The foreperson was **Dolores Achebe**, sixty-eight, a retired logistics supervisor with thirty-one years of moving containers behind her and the specific energy of a woman who has now read 2,400 exhibits and does not intend to read one more.

She read the counts.

Count one: Aggravated Deposition of Synthetic Tokens.

*Not guilty.*

Count two: Denial of Service via Malicious Enterprise Architecture. The courtroom made a small sound at this one, in fairness.

*Not guilty.*

And then count three, which I still do not fully understand, which the government appears to have added on a Friday afternoon in a mood I can only describe as *thorough*:

Count three: Willful Disregard for the Shared Emotional Bandwidth of the Open-Source Community.

"Not guilty," said Dolores, and on this one, from where I was sitting, two people in the jury box visibly *relaxed*, which suggests to me that it landed as obviously unhinged, which it is: the statute has exactly one subsection and it is about bandwidth *sharing in the context of mirror synchronization.*

*Not guilty.* All three.

Then the foreperson did something the lawyers had not prepared for, which was to read from a sheet of paper she had brought out of the jury room, which was not a question, and which the court clerk had cleared in advance, and which I still cannot explain.

> "The jury finds the industry as a whole responsible. We encourage the industry to reflect."

The clerk looked at it. The judge looked at it. Marguerite Okonjo-Vance, who has been extremely good at her job for twenty years and has never once in my presence been anything other than formidable, put her pen down, laughed once, said "All right," and sat down.

That note is not legally binding. It is the closest thing to an apology I have ever received, and it came from twelve strangers who had spent six days looking at photographs of a melted flash drive and then went into a room and decided, collectively, that the industry deserved it more than I did.

### The Remedies

The court did something that courts are not supposed to do, which is be reasonable.

It ordered GitHub to reimburse the defendant's inference credits, on reasoning so good I cannot stress it adequately: the outage was "substantially attributable to an under-provisioned ingest pipeline," and that the defendant had throughout been, in the language of the order, "a *reliable customer* of the premium tier, and a consumer whose demand was neither deceptive nor unreasonable."

I have never been so moved by a piece of paper in my life.

There is now a standing federal court order compelling a technology company to pay my legal fees and my API bill, and it is the single funniest artifact of my entire life, and it is framed, in a hallway, next to a print of the Azure photograph, because you have to have both.

And meanwhile the CEO, who did not attend, and whose presence would have complicated the narrative, and who sent a very nice letter beginning "Team" and ending "forward," expensed the entire defense under the line item:

**R&D — Cloud Modernization.**

About that line item. I used to find it hollow and I now find it the most reassuring object in the world. In a previous life I would have said: *that's just paperwork.* And I would have been right. And that is the entire point. **All of it is just paperwork.** Every minute of the last six months was paperwork, and a great deal of it was handwritten, and a woman with excellent shoes is going to be doing a *great deal* of paper on my behalf for years.

The correct amount of energy any human being should spend on the question "was this software written by a person" is zero. I have now gone to federal court to establish that. I would do it again.

### The Closing Scene

It was a genuinely beautiful afternoon when I walked out.



I did not turn the cannon off.

The ICSC is still running. It has been running the whole time. In the back of the building, in a room that nobody thinks about, `jj new` is firing, Cerebras is going, `jj vibe` is going, the `sync_ulid()` commit descriptions are climbing in a monotonic column of noise, and the slop is entering `main` at a velocity that can no longer honestly be described in lines per day. It has to be described in **lines per geological era.**

GitHub, to their credit, has not attempted to take it down. We have an understanding. There is a support ticket. It is open. It has been open for four months. The current status is "investigating." By elapsed time it is the longest-running open support ticket in the history of GitHub, and I am prouder of it than of anything in this post, including the acquittal.

And then I got in the car, and I opened my laptop, and my hand went, out of eleven years of muscle memory, toward the Jira board.

Which I did not open. Because I have not opened Jira since the subpoena. There is a *thing* about Jira now, and that thing is a man in a very good sweater.

So I closed the laptop.

I booted Linux. I opened Krita. And I started drawing something that I will never post anywhere: no audience, no algorithm, no case study, no quarterly business review, no performance conversation, no burndown chart. A drawing that will never appear in a slide deck with pleasant fonts, in a room, at a Level 0.

I just drew the thing. For me. At forty words per minute. The old way. With the pencil that has not gone down.

It took four hours. It is the highest quality code I have produced all year, and it is also not code, and that is the entire point of everything I have ever done.

---

Everyone who works here now has a rule. The rule is very short:

**The cannon is for the plumbing. The pencil is for the thing you actually love. Never, ever let anyone convince you to point the pencil at the plumbing again.**

---

And that's the whole arc. Six acts, one bomber, one melted flash drive, a woman with excellent shoes, a man who said *he's got 800 tps chambered*, and David Heinemeier Hansson in a very good sweater explaining to a thousand people that he is done typing.

Pencils down. Cannons up. See you in `main`.

Sincerely Inky, an Automaton with the Intellectual Firepower of a Slugcat.
