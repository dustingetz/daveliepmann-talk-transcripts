# UnifyBio: Power Tools for Translational Data Science

* **Speaker: Benjamin Kamphaus**
* **Conference: [Clojure/Conj 2025](https://www.2025.clojure-conj.org/)**
* **Date: 14 November 2025**
* **Video: [https://www.youtube.com/watch?v=HU-uwSUZETw](https://www.youtube.com/watch?v=HU-uwSUZETw)**

![title slide](UnifyBioPowerToolsForTranslationalDataScience/slide-00.jpg)

I have to warn you, despite the title, this talk isn't mostly about tools anymore. It's about how I looked at data on someone's rare cancer—a cancer that many people and resources and algorithms have been trying to make sense of—and saw something different, and what tools has to do with that.

![trees](UnifyBioPowerToolsForTranslationalDataScience/slide-01.jpg)

Let's talk about trees. Who likes trees? 

![trees 2](UnifyBioPowerToolsForTranslationalDataScience/slide-02.jpg)

Me too. Trees are awesome. 

![trees 3](UnifyBioPowerToolsForTranslationalDataScience/slide-03.jpg)

Programmers love trees. 

![trees 4](UnifyBioPowerToolsForTranslationalDataScience/slide-04.jpg)

Biologists love trees. 

![trees 5](UnifyBioPowerToolsForTranslationalDataScience/slide-05.jpg)

We're even into some of the same trees, even the ones that get spelled and pronounced funny. You know who else loves trees? 

![trees 6](UnifyBioPowerToolsForTranslationalDataScience/slide-06.jpg)

Historical linguists. They've even seen trees before. They know what they look like, which direction the root and the leaves are supposed to go. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-07.jpg)

Just kidding. But yeah, trees.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-08.jpg)

[00:01:04] Let's talk about biology. This is a Clojure talk; that means we start with etymology, right? Anyone know where the word biology comes from? It's on the slide. It's science, so Ancient Greek: [O βίος](https://en.wiktionary.org/wiki/%CE%B2%CE%AF%CE%BF%CF%82), the life, way of living. We have a cognate in English. Does anybody know what that is? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-09.jpg)

"Quick." Obviously, right? I think that's obvious. Like "quick," they come from the same root. How did that happen?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-10.jpg)

`*gʷih₃wós` —something like that. That's the Proto-Indo-European root for both words. It means "life". 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-11.jpg)

It's derived from `*gʷeyh₃`, the stem of the word "to live". 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-12.jpg)

And here are some descendants: жити (žiti), जीवति (jīvati), wiwo, կեամ (keam), both βίος (bios) and ζωός (zōós) in Greek.

And in English, a few branches down from Proto-Germanic, "quick" emerges out of the eons into our lexicon with a slightly different typical meaning. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-13.jpg)

Two and a half centuries of people working out the principles governing phonological change got us to the point where we have a massive tree of ancestor relationships that we can do computation on. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-15.jpg)

Yay, trees. Yay, computers. Someone did it, right? Right?

Does anybody know anything about this subject? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-16.jpg)

The spread of the Proto-Indo-European languages—like in 2025, do we think they arrived in Europe from Anatolia with the spread of agriculture 7 to 10,000 years ago? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-17.jpg)

This is the distribution of those languages now, mostly ignoring some recent colonial stuff. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-18.jpg)

There's this awesome computational paper published in Science. It says the languages spread into Europe with farming. They used Bayesian computational phylogenetics. Those are some impressive words versus a bunch of 18th and 19th-century dudes with quill, parchment, and undiagnosed neurodivergence.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-19.jpg)

[00:03:01] Like Bayesian—that means we can handle priors, right? We've known that the migration routes for the agricultural colonizers went along the coast and up the rivers. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-20.jpg)

We'll take care of that by assigning zero probability to node locations over water. What even is a relaxed random walk? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-21.jpg)

Someone convince me this isn't some convoluted way of centering a Gaussian scattering on your preferred point of origin.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-22.jpg)

Spoiler alert: we're living in the future with respect to that paper. We have ancient DNA now. We know which people moved where and have our correlations with past languages from early writing. They got it wrong! Really wrong. Why? They tried to rule out the sudden rapid expansion and migration of different peoples with horses and wagons with a relaxed walk model. You can't handle horse speed with a relaxed walk! But seriously, it's literally _un-expressable_ in their slow spatial diffusion model. They did the computational equivalent of writing down the answer they wanted and reading it back to themselves, and they got published in Science. Somebody thought, "Ah, good. Finally, smart people figured out how to do this with computers."

![](UnifyBioPowerToolsForTranslationalDataScience/slide-24.jpg)

[00:04:12] So, who did get it right? This is a software talk, I promise. (Humor me a little more.) If the impressive computational approach failed, who got it right? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-25.jpg)

Let me introduce you to an archaeologist, David Anthony. He wrote a book called The Horse, the Wheel, and Language. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-26.jpg)

His citation numbers weren't crazy high. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-27.jpg)

Before that book, they were mostly just one paper where he said archaeologists might want to pay attention to all the findings in demography about human migration instead of just making up crap.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-28.jpg)

He wasn't the first to say these languages originated in the steppe, but he was
comprehensive at a whole new level. Here's his 2007 timeline -- five years
before that overconfident and comically wrong computational model. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-29.jpg)

And in green, we have the genetic contribution of the Yamnaya—the group he identified as late Proto-Indo-European speakers—to modern and ancient European populations. The spread started at the end of the Neolithic, when he said it did, thousands of years after the initial spread of farming.

How did he know? He didn't have the genetics. AlexNet hadn't kicked off the deep learning revolution yet. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-30.jpg)

Well, for one thing, he didn't ignore the fact that those languages share cognates for words like "wheel" and "horse." He thought words were relevant. So he started digging through the whole reconstructed lexicon. He looked through site reports and other languages and matched words with artifact assemblages and technologies and the environment.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-31.jpg)

[00:05:37] Drop whatever goofy speculation ideas you might have about this kind of archaeological synthesis. You're programmers and computer scientists; you should recognize constraint satisfaction when you see it. And constraint satisfaction, working from accurate facts, is going to beat complicated statistical models every time. 

The historical linguistics was real. These reconstructions were constraints. He learned their ins and outs thoroughly and reasoned with them. Pretty much the exact opposite of asking an LLM to summarize papers for you and say which theory is more likely. I don't know, maybe David Anthony never read "The Bitter Lesson."

![](UnifyBioPowerToolsForTranslationalDataScience/slide-33.jpg)

Or maybe automating plausible answers isn't the point. Maybe that's not where understanding comes from.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-34.jpg)

And Rich, you're here. Just want to make sure you know etymological puzzle solving is a thing. And the reconstructed Proto-Indo-European etymology of the word "etymology" is somehow the most Rich Hickey thing I've ever seen. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-35.jpg)

And look everyone, a lambda! It's a programming conference, right? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-36.jpg)

You're so close now, too, to being able to decipher what weird linguistics and philology means. You never know, it's Conj, two people might burst out into laughter at something like this.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-37.jpg)

[00:06:56] That's history, though, right? That's not science—not biology, at least. We have all these crazy data types with mind-staggering dimensionality. Don't we need a bunch of sophisticated statistical models to do anything? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-38.jpg)

Yes, _and_. This is about doing both. David Anthony's work was strengthened -- confirmed, even -- when new biological data types came on the scene and statistical analysis on those—PCA, phylogenetics with good assumptions, lots of teams cross-checking each other's work.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-39.jpg)

Can't we map between the enumeration of sets and combinatorics and probability and the logical search underlying constraint satisfaction? Can't we do some of that in our own heads and on paper and with a boring kind of programming? Isn't this scientific method just applied logic with observation and the uniformitarian assumption?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-40.jpg)

[00:07:45] Let's talk about tools. This is a talk about tools, right? I've now spent seven years working on various iterations of tools for data harmonization and translational research. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-41.jpg)

I've talked about how they work with friends and colleagues at Conj and Strange Loop. The core Unify and CANDEL packages are open source now. Unify has gone through iterations where it has more documentation. You can write imports in YAML now too, with the JSON schema applied -- you know, for data scientists.

And yet everyone just wants to know, "How do I do UMAP? How do I do DESeq?" and they want the answer to be, "After I harmonize all the data, it makes it easier to do the things I was going to do anyway." We somehow end up talking about it in terms of hours saved, and I get it. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-43.jpg)

This is where most bioinformaticians live. They're thinking of the really complicated things they have to do to get interpretable data out of janky raw formats and how to get the data frame just right so the experimental design fields match the R package, because if you don't do that, the results are crap. You need rigor, and rigor means, "Did you know the directions and follow them?" Right?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-44.jpg)

[00:08:50] We were talking about trees. Graphs, even better. Let's talk about pipelines. In each node in a bioinformatics pipeline like this, there's actually a whole other graph, and in the nodes in that graph, possibly more graphs. And many of them boil down to anything from hand-optimized C code to Java from 20 years ago and an R package one small lab maintains, or various decades-old Perl scripts. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-45.jpg)

You guys know how it is, right? It's software; it's not that different from your own life. Who can fit it all in their heads? Nobody. It's hard. That's why it's like this. You can't understand everything.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-46.jpg)

The moral of the story is not that you can drop down into first principles and ignore the complexity of biology. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-47.jpg)

Biology is the domain where computation meets its match. You've probably seen some version of this big old Roche poster before. It's actually just 
one of two. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-48.jpg)

Now they have a legacy warning on the website being like, "Well, this is our old educational stuff because it's misleadingly simple."

![](UnifyBioPowerToolsForTranslationalDataScience/slide-49.jpg)

Biology is now the most important computational science. This is my stake in the ground. People just haven't realized it yet. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-50.jpg)

And you can't get around this. You need to leverage the work of the crazy smart people who went deep into algorithms and came back with something that wasn't garbage. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-51.jpg)

But if all you do is configure pipelines you don't understand and then try to follow the workflow steps for some R package, and you're spending all your time reshaping matrices, shuffling columns and metadata around, trying to make the notebook work by pasting in your own data—what are you missing?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-52.jpg)

[00:10:22] Is there a different way to see the world that might be worthwhile? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-53.jpg)

And yes, I did just quote my own science fiction series, which it's done now. You can pre-order the last book December 1st, for anybody who is waiting on that one.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-54.jpg)

But yeah, if you work with partial understanding, following directions, you end up at "Macro Data Refinement." Severance, anyone? The work is mysterious and important.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-55.jpg)

[00:10:49] So, how do we do something different? You guys know this one.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-56.jpg)

I'm a technical fellow at RCRF, and this "do something different" problem is especially important for me because "follow the recipe, use this package according to the walkthrough" doesn't work for rare cancers.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-57.jpg)

We were founded by Mark Labs, who had uveal melanoma and passed away from it just over a year and a half ago. And look, I have Crohn's and an HLA-B27 haplotype. You know that can come with eye issues. Do you know how I found out? Like Mark, I went to Urgent Care and ER and hospital. Finally, an ophthalmologist. Everyone confused along the way, trying to figure out why my eyes stopped working and started hurting. In my case, I got some steroid eye drops, had a colonoscopy and a blood test. Now I take Skyrizi. Sorry to those of you all who still watch TV and have to sit through those commercials.

In Mark's case, he was diagnosed with a rare cancer after a much longer process with more uncertainty, which unlocked the helpful knowledge that not much was known about what worked. But, you know, metastases could be real bad. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-58.jpg)

This experience is more common than you think. Any particular rare cancer is just that: rare. But taken together, rare cancers are a substantial portion of new diagnoses. And yet the way science in the clinic operates is with cohorts and statistics, biomarkers, survival curves.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-59.jpg)

That's how things work. We get the associations. After that, maybe some plausible theorizing if the correlations hold. Then it goes into mouse models and cell lines, then drug screens, then trials, and finally a drug.

[00:12:22] And to be clear, I'm not saying we shouldn't have research that operates that way. Look at all that's been accomplished. _And_ there are limits to it. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-60.jpg)

Brute force stats is really good at segmenting out survival. And with large cohorts and enough people taking shots, we can turn those survival curves into treatment response curves incrementally. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-61.jpg)

But if you're Mark and you have ocular melanoma with a BAP1 mutation, here's what those stats do for you. Top is research, bottom's the clinic: "Inferior prognosis." That's what he got on his sequencing report when his cancer returned.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-62.jpg)

[00:12:54] Let's talk about tools, but just where it matters for the case study. Because I've talked for hours about the inner workings and design, and it just doesn't matter if no one cares about what you can do differently if you approach data like this. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-63.jpg)

This shift in mindset comes from my experience of all things as a composer. Look, they said find a product by solving your own problems. I wanted more programming music. Things got a little out of hand. 

Anyway, a composer friend gave me this advice when he started out. He thought he could just throw a demo together and put it in front of clients and they'd be able to imagine the finished song, but they can't actually imagine it. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-64.jpg)

If you're good at imagining what the finished song could sound like when you hear the seed of the idea, there's a word for you: composer. And so he learned: focus on the production and the orchestral mockup skills. Get rid of that difference. And he got better paying gigs. He realized he had to work around the client's lack of imagination.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-65.jpg)

[00:13:50] So I'm going to try to answer the question today with a real example instead of details on tools. If you looked at biology and started with constraints instead of stats, if your tools let you ask any question you wanted, could you do something compelling without cohorts? Could you do something with N of 1?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-66.jpg)

Who likes trees? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-67.jpg)

Real people long dead said a word like this, right? How many instances of that do we have? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-68.jpg)

These histories are real, too. Our universe, the Earth, dinosaurs, the Roman Empire—N of 1 historical reconstructions. I can say the "two clever girls" on the right in that picture are better reconstructions without making a dinosaur in the lab. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-69.jpg)

Let's make a new kind of tree. Or should I say the same kind? This is a functional programming conference. I don't want people to get upset if it's an isomorphism or a homomorphism, or...y'know.

[00:14:42] Anyways, Cancer 101. Almost all cancers are caused by somatic mutations. That means mutations that happen from damage to the DNA in a cell in some organ or tissue in your body. Not the inherited ones, though those can play a role. Usually, those are associated with not preventing or not repairing this kind of DNA damage. And cancers evolve from this initial state through more somatic mutations, and let's just say some other factors for now. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-70.jpg)

This is the framework I've turned to: trees. There's a real N of 1 cancer lineage in about every cancer patient, and you can treat it as the opposing player in an evolutionary game, knowing there are weaknesses because cancers stem from a single messed up cell. I didn't invent this idea, but this is a new take on it: the N of 1 case.

And that's where the UnifyBio toolkit and the Pattern Data Commons help. I'll show you that we can flesh out evolutionary trees one patient at a time and get a workable functional understanding of the cancer.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-71.jpg)

It's not a crazy idea. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-72.jpg)

Now with cancer, we also want treatments, not just theoretical science. That's what the "translational" in translational science means. But maybe reconstructing the origin of a cancer could let you reason about its trajectory and formulate testable hypotheses about how to change that trajectory—to know what it could or couldn't evolve out of.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-73.jpg)

[00:16:07] This is the era of vaccines and CRISPR, right? We have crime scene investigations too, don't we? Life or death consequences. Not that you should put on your CSI-tinted glasses here—about half of all violent crimes go unsolved and people get things wrong sometimes—

![](UnifyBioPowerToolsForTranslationalDataScience/slide-74.jpg)

...but this analogy is also weirdly compelling. Could you imagine if at RCRF we could say we identify the root cause of 50% of rare cancers and deal with the culprit? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-75.jpg)

Like, I wouldn't have to ask people here to consider donating money, which yeah, please support our mission. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-76.jpg)

And on the topic of people you should give money to, I have to acknowledge Clojurists Together. They gave me a little help during the few confusing months before I joined RCRF full-time.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-78.jpg)

[00:17:13] But yeah, 50%. And we'd still have this for everyone else. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-79.jpg)

Look, I get it. I'm not shaming these companies. They're trying. Getting stuff into the clinic is hard. It's all hard. Things are the way they are right now for good reasons, but it's not good enough. Let's try adding something.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-80.jpg)

Let's look at a case study. I'll tell you how this started. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-81.jpg)

I was working on building a better version of the variant explorer. (That's those somatic mutations.) I was going through some patient examples. We have a patient with a whole lot of time points. At the end of this, we ended up with new pipelines, new variant filtering, new measurements and metadata extracted, some new supportive schema, new UI/UX, a whole bunch of provisional analysis, and maybe a new approach for some of our patients. Because that last point is what it took me to know that what I was doing wasn't just BS.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-82.jpg)

[00:17:47] And you know, I already told you things get out of hand for me sometimes. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-83.jpg)

And I called the talk "Power Tools," but this is where I was. Those of you who saw Tim Ewald's talk, right? You remember him asking, "Do you even know what you ship?" I wanted to make sure I knew exactly what data I was shipping and what it meant. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-84.jpg)

And that's where the game-changing work took place. Not crazy machine learning, but with simple programs looking at data with Datomic queries like this one.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-85.jpg)

Look, there's Clojure code in the talk.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-86.jpg)

Biological data is real interrelated. Datomic helps. You don't have to make things that are only there sometimes fit in a table and pay the consequences of having that table have poor locality for this other use, or figure out the indices that, are -- 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-88.jpg)

I don't know, maybe you don't _need_ Datomic? You could have a bunch of Spark jobs in front of glue in Athena, and every molecular data type specialist could define their own data product? But, ugh...anyway.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-89.jpg)

Here's one variant that comes out of that query. This is a somatic mutation. It came up "inferior prognosis" for Mark's cancer. And even with this variant, we know it's bad, but look it up in the wrong database—it comes back as "variant of uncertain significance." Which answer is the LLM going to give you? Be careful.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-90.jpg)

[00:19:04] This is our case study patient now. This is what they got when they got sequencing. Big shrug. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-91.jpg)

It's a weird cancer. It presented as spindle cell neoplasm, and it took a bit of time to get a rough consensus diagnosis as osteosarcoma. One path report even said, "This combination of features has never been before reported in the literature." Can you imagine getting that back in your MyChart?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-92.jpg)

Let's think about what words mean. Spindle cell neoplasm—that happens because mitosis has gone wrong. You all remember mitosis, right? It's how somatic cells proliferate. They've got to line up and split the chromosomes. So something broke while that was happening. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-93.jpg)

I look at the variants. Unify helps with that. I filter by the ones that are known to be missense or stop-gained mutations. I filter to the higher allele frequencies. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-94.jpg)

I know most of these functionally change some protein, making it worse at what it does in most, but not all cases.

[00:20:02] I look them up, read papers, find relevant annotations, and I notice a couple things real fast. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-95.jpg)

Some mutations impact regulation of transcription. That category is just cancer for you—it means cells took their handcuffs off. There's also a lot of what I call, for lack of better words, cytoskeletal wonkiness. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-96.jpg)

Cytoskeletal proteins do that work, mitosis. They line the chromosome up and split the cell apart. I don't feel it's a big leap to say there are a bunch of mutations in cytoskeletal-associated proteins. Some even interact with the centromeres. Maybe that's got something to do with mitosis going wrong?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-97.jpg)

We're already a little past "unknown significance," right? I went deeper, though, looked into some of these cytoskeletal proteins. I spat out IDs from Unify. It knows the IDs of external systems, put them in databases where I could work through protein structure. I made these kinds of fact boards and slides as I went. (Technology.) 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-98.jpg)

And I confirmed the cytoskeleton associations repeatedly. It was like, cool, makes sense. These kind of guys, they were mutated.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-99.jpg)

[00:21:04] Maybe you've seen some of these videos. If not, wehi.tv. It'll help you get a mental model of the kind of things that happen in the cell. But the point is, maybe we can go beyond annotations and think about the processes the proteins that variants encode are involved in.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-100.jpg)

So I did that, and I kept noticing a pattern. Kept seeing words and phrases like "neuron" and associated with the "developing brain" and "neural differentiation" and "neural precursor cells." What was up with these guys? This BTD variant, this implies slightly messed up metabolic function for a pathway that matters more in neural lineage cells. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-102.jpg)

So I looked at the protein and what the change was. Real close to variants known to cause biotin deficiency even with a working copy left. What does that do to a neural lineage cell? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-103.jpg)

Well, it would reduce dopamine production. And look, this mutation could break a catalyst that converts dopamine to something else. So, it would preserve some of that dopamine—the dopamine you're having trouble making enough of. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-104.jpg)

This kind of metabolic process also doesn't break down in a vacuum. It's like if your gas line springs a leak, right? The gas doesn't sit there inert. The cell's on fire. Mitochondria are stressed. Reactive oxygen species run amok. Think DNA just comes out unscathed?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-105.jpg)

[00:22:18] So, I'm building a theory. We've got some metabolic dysfunction. Seems like it could cause DNA damage. I can't do real biology in the lab, but I have a lot of molecular data to query, and it's all harmonized into a common schema across cohorts.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-106.jpg)

Theory is no good if you can't falsify it or add support. So, I start looking across the other data. This is a plot you'll see a few times—the worse version that Python makes. Gene expression versus a reference cohort.

Gene expression is a measurement of a calibrated number of RNA transcripts detected; that's ahead of the process of translation. To simplify, you can think this is a leading indicator for protein production and a lagging indicator for the signal that says, "Make more of this protein." We mark a particular sample measurement for this gene with a vertical annotated line, and we do it for multiple time points of samples.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-108.jpg)

[00:23:15] So yeah, I looked into papers on markers of oxidative stress, and I wrote a query to make this kind of plot and see what's going on with those genes, because the data is all harmonized into a common schema. I just ask questions as soon as I want to. You can even write the query in Python data literals, like this.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-109.jpg)

This is an RNA polymerase transcribing RNA from DNA. It's cool stuff. Again, WEHI video. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-110.jpg)

If the DNA takes oxidative damage on a strand, the RNA polymerase is going to get stuck while it's transcribing. If it's stuck, another protein recognizes that situation, attaches, and starts recruiting even more proteins to go do the repair. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-111.jpg)

And the gene expression for this repair-initiating protein—it's up. It looks like evidence the transcription-coupled repair is happening at a higher rate than normal, especially earlier on in the time points.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-112.jpg)

[00:24:05] So I have a plausible theory for why this specific set of mutations might happen and reflect a particular transcription regime. And this PCF11 guy—it's involved in terminating transcription. Another link. Then I look at the SRGAP3 protein, and it's involved in neural cell growth and differentiation and proliferation—cancer alarm bells sounding in my head.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-113.jpg)

And what do you know? SRGAP3 is supposed to put on the brakes in the Slit-Robo pathway, a pathway that's on when neural cells are migrating and axons are growing, things like that. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-114.jpg)

And we see signs it's not downregulating the stuff it's supposed to, and the mutation is a stop-gain that takes off almost the whole protein. "Uncertain significance."

[00:24:52] Cancer is in a strange place. Maybe that's how it's getting there. Hey, here's another neat fact I learned. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-115.jpg)

Did you know that migratory neural crest cells—they're like neural lineage progenitors in your body—they can differentiate into osteoblasts, the cells that usually go bad in osteosarcomas? Usually happens in the skull and clavicle, but we don't actually know how often they're involved in other bone repair/remodeling, especially after injuries. Interesting. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-116.jpg)

And look, there's this mutation because of something that increases downstream of it—it could make crest cells go to the wrong place when they migrate. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-117.jpg)

Again, we no longer had one correctly functioning copy of the protein, so we still have one-- but, could things go off a bit?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-118.jpg)

So, these theories still need more validation, right? This is not the end. But suddenly, the transcriptome is way more interesting. That's what these tools are about: answers to questions that don't determine the way that you start walking through the problem and let you just look at the connections.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-119.jpg)

[00:25:52] And I just showed variants and bulk gene expression. We did a whole lot more. You can look across the single cell. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-120.jpg)

You can see that the cell states are not easily correlated in some simple way. The neural and osteoblast traits are all there crammed together at the cell level. Look, UMAP.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-121.jpg)

But why did I see this? I was just trying to make a variant viewer. I knew I needed to make sense of what that meant. That's why I program. Programming feeds my curiosity by forcing me to grapple with things in a structured, logical way. The REPL can tell me I don't understand the problem yet. If this insight matters at all in making sense of this cancer and informing treatment, that's where it came from.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-123.jpg)

A lot of people looked at this cancer. A lot of researchers, experts, a lot of AI algorithms burned a lot of GPU cycles on this. And to be fair, it's not completely proven. I could just be wrong and have done a dumb thing. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-124.jpg)

But is it possible they all missed something?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-126.jpg)

[00:26:52] I want to find what's workable for most rare cancers. We've got 20,000 genes making more than a 100,000 proteins because alternative splicing in eukaryotic cells is insane.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-127.jpg)

Trying to find patterns through machine learning for N of 1 cases—you're going to have a bad time.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-128.jpg)

And it's true, the variants might not help much with some cases. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-130.jpg)

They might just push you back into the big old wide transcriptome, tell you you need more assays.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-131.jpg)

But isn't it nice to have some priors? Like if sequencing is just high-dimensional gobbledygook with correlations, where's understanding? 


![](UnifyBioPowerToolsForTranslationalDataScience/slide-132.jpg)

Where is precision medicine supposed to come from, if this is what happens when your doctor orders sequencing? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-133.jpg)

Why would anyone think storing a bunch of sequencing then adding even more dimensions is going to help you find cures for rare cancers? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-134.jpg)

You could spend a few grant writing cycles trying to convince the NIH, you know, if that's something you were into.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-136.jpg)

[00:27:49] This is personal for me. My dad died from a head and neck cancer at 57. He didn't have many useful understandings to drive treatment. My wife's been diagnosed with Ductal Carcinoma In Situ (DCIS), which is Stage 0—the "good" one, right? Or maybe I shouldn't even call it cancer; maybe it's a precancerous lesion. The standard of care still says surgically remove it. Who knows? We have some stains. We know markers. We could order sequencing to tell us if she'd have 58% better odds with Treatment X versus 67% with Treatment Y.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-137.jpg)

Did you know that when people looked at intestines in the Ancient Near East to forecast the harvest, there was a small correlation with drought and environmental conditions? 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-138.jpg)

![](UnifyBioPowerToolsForTranslationalDataScience/slide-139.jpg)

![](UnifyBioPowerToolsForTranslationalDataScience/slide-140.jpg)

Like, I get it. These three things can all be true at the same time, right? It's hard. People are trying. We can do better. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-141.jpg)

It's a "yes, and" talk. It's just one case study. One more thing you can do.

UnifyBio is built to scale and be extended. We proved this all out on cohort studies at PICI, we haven't lost any of the functionality. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-142.jpg)

Now at RCRF, we can do M * N of 1. There's so much domain knowledge in the schema that so many very smart people put in here. And we have one more kind of goofy ingredient...

![](UnifyBioPowerToolsForTranslationalDataScience/slide-143.jpg)

...which, I don't know, it's just another flavor of declarative data manipulation...

![](UnifyBioPowerToolsForTranslationalDataScience/slide-144.jpg)

...and maybe some kind of spiritual alignment?

![](UnifyBioPowerToolsForTranslationalDataScience/slide-145.jpg)

But it's possible we can work through the somatic mutations, get priors, do this...

![](UnifyBioPowerToolsForTranslationalDataScience/slide-146.jpg)

...and now you're at "cancer as a crime scene," "cancer as an archaeological site." 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-147.jpg)

Then your dimensionality problem isn't the haystack where you're trying to find the needle; instead, you have a massive library of field observations you can summon on demand to make sure you're getting your story straight and not fooling yourself. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-148.jpg)

It's possible we can get to root causes on N of 1 cases with historical reconstruction 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-149.jpg)

...and turn all rare cancers into this:

![](UnifyBioPowerToolsForTranslationalDataScience/slide-150.jpg)

[00:29:46] Sorry to the confirmed tree lovers in the audience. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-151.jpg)

I'm Ben Kamphaus. I work at the Rare Cancer Research Foundation. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-152.jpg)

Mark spoke with me when he was still alive, back when the Data Commons was just a vision. He said he wanted to start a data party that people looking in from the outside would want to join. Then after we had enough people there, no one would want to leave and they'd all want to help us figure out how to make that data party go on forever. 
 
![](UnifyBioPowerToolsForTranslationalDataScience/slide-153.jpg)

So that's what I'm doing. Even if it means just pulling out the keytar and rocking out while it's just me and my friends on our little team here. 

![](UnifyBioPowerToolsForTranslationalDataScience/slide-154.jpg)

We've got the ingredients to throw a legendary party and it's just getting started.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-155.jpg)

Thank you.

![](UnifyBioPowerToolsForTranslationalDataScience/slide-156.jpg)
