---
layout: post
title: "Incompleteness and the Underground"
author: "Jordan Bryan"
categories: journal
tags: [documentation,sample]
image: godstoevsky.jpeg
---

## Introduction

> We hear within us the perpetual call: There is the problem. Seek its solution. You can find it by pure reason, for in mathematics there is no ignorabimus.<sup>1</sup>

Though not a writer himself, David Hilbert had a flair for the literary. And, at the moment in history when he spoke these words, he had every right to indulge it. When he delivered his address at the Paris conference of the International Congress of Mathematicians in 1900, he stood atop a century of immense mathematical achievement, which, along with advances in analysis, algebra, and geometry, had witnessed the development of the first inferential methods designed to draw conclusions from data collected in the natural world. The conspicuous success of these methods, beginning with Carl Frederich Gauss's prediction of the orbit of Ceres in 1801 and continuing with Quetelet's statistical examination of the "average man" in 1835,<sup>2</sup> did more than to aid in the progress of mathematical theory: they breached the public imagination.

Indeed at the beginning of the 20th century, it seemed that nothing could escape the expanding reach of an increasingly complex, yet astonishingly effective mathematical reasoning.  However, even as he championed its progress, David Hilbert knew more than anyone that the empirical successes of mathematics lay on suspect foundations. For one thing, it had yet to be completely formalized in a way that was satisfying to mathematical logicians. More disturbingly, axiomatic set theory had recently generated paradoxes that threatened to throw the whole project into doubt.

Hilbert's solution was to enlist the minds of the greatest logicians in the world in an effort to unite all of mathematics under a single, coherent, unassailable system. In 1902, he laid out 23 unsolved problems whose resolution would ensure that mathematics could recover from its crisis.<sup>1</sup> One logician who answered the call was Kurt Gödel, a doctoral student at the University of Vienna. After attending one of Hilbert's lectures in 1928, he adopted the completion of mathematics as the object of his dissertation.<sup>3</sup>

Yet only one year after receiving his doctorate, Gödel accomplished quite the opposite: in the process of trying to complete mathematics, he proved that said completion was impossible. Gödel's explosive, yet esoteric mathematical results from 1931 -- known today as his Incompleteness Theorems -- did more than to slow Hilbert's progress. They proved that the culmination of his program would never be realized.

Decades earlier, the failure of Hilbert's Program had been informally presaged by an unlikely figure: a man living Underground for over forty years, scribbling intense philosophical ramblings onto pages never intended to meet the eyes of an audience. Undoubtedly, the creator of this Underground Man, Fyodor Mikhailovich Dostoevsky, was himself influenced by mathematical thought.<sup>4</sup> One may trace exactly how specific mathematical concepts made their way to Dostoevsky's ears, and from those ears into the minds of characters like the Underground Man.<sup>5</sup> But *Notes from Underground* was published in 1864. Dostoevsky died in 1881. How did he come to know Incompleteness before it was formalized?

Like Gödel's theorems, *Notes from Underground* was a rebuke of a program of sorts: the rational egoist program of Nikolai Chernyshevsky as described in his novel *What is to Be Done?* Chernyshevsky's utopian philosophy embodied a Western emphasis on individual progress through rational self-improvement, which Dostoevsky saw as a harmful intrusion into the Russian psyche.

There is no question that Dostoevsky wanted to answer Chernyshevsky's radical rationalism with a different vision of reality, one in which mechanistic mathematical logic becomes twisted around its own axles. But when we read *Notes from Underground* today, why do we feel the urge to pit the Underground Man *against* mathematics? Why do we believe that he stands in *opposition* to rationality and scientific progress? Because he says so? Nonsense.

A fair reading of *Notes from Underground* in light of Gödel's Incompleteness Theorems suggests that the Underground Man is not an illogical creature. He is rather an unavoidable consequence of logic, a strange byproduct of formal reasoning. In fact, the necessary ingredients of Gödel's proof of the Incompleteness Theorems, as well as the mathematical context in which they were devised, bear an uncanny resemblance to the Underground Man's predicament. At their conclusions, *Notes from Underground* and Gödel's Incompleteness Theorem lead readers to surprisingly similar places: they are constructive arguments that reveal uncomfortable truths about the nature of formal logical systems.

## Reductio ad absurdum

> Come up out of your godforsaken underworld, my friends, come up. It's not so difficult. Come out into the light of day, where life is good; the path is easy and inviting. Try it: development, development.<sup>6</sup>

To get a sense for how the Underground Man's exposition resembles Gödel's proof, it will be useful to understand exactly what is meant by a proof. At its most basic level, a mathematical proof is a derivation of truths: it begins with statements held to be true *a priori* and arrives at new statements using circumscribed rules of inference. If one follows the rules exactly, the *a posteriori* statements must also be true. 

Both Gödel and Dostoevsky knew these rules intimately. In fact, Dostoevsky scholars have pointed out the likeness between *Notes from Underground* and a "proof by contradiction."<sup>5</sup> Rather than establishing a truth constructively, a proof by contradiction rejects a given premise due to the "absurd" conclusions that follow from it. Specifically, the proof must derive a conclusion that shows a statement known to be true to also be false. When this occurs, the premise that led to the disastrous contradiction must be abandoned, and its opposite assumed true.

The premise in a proof by contradiction may be something that initially seems quite plausible. A famous example known to most students of mathematics is the proof of the irrationality of \\(\sqrt{2}\\), which follows from the rejection of the premise:

$$
\sqrt{2} \text{ is a rational number}
$$

The proof is not so long: assume that \\(\sqrt{2}\\) *can* be expressed as a fraction in lowest terms.<sup>a</sup> Then

$$
\frac{a}{b} = \sqrt{2} \implies a^2 = 2b^2
$$

The equality on the right of the "implies" symbol (\\(\implies\\)), tells us that \\(a\\) must be an even number.<sup>b</sup> Making explicit \\(a\\)'s representation as an even number reveals that \\(b\\), too, must be even.<sup>c</sup> So \\(b\\) divides \\(a\\). But, also, \\(b\\) does not divide \\(a\\).<sup>d</sup> Since mathematics does not abide statements that are both true and false -- a property called *consistency* -- \\(\sqrt{2}\\) cannot be a rational number.

So much for \\(\sqrt{2}\\). What of Hilbert and Chernyshevsky's cherished premises? They too were enticing: all of mathematics, under one watertight roof, atop one solid slab of concrete, housed within an intricate structure of its own making, humankind's moral and economic prosperity assured simply by following an algorithm, the aim of which -- blessedly -- is to maximize one's self-interest.

Given the lofty implications of these premises, the temptation to strike them down is understandable. An acolyte of Hilbert's program, Gödel arrived at his results almost by mistake. Dostoevsky, on the other hand, seemed personally affronted by Chernyshevsky's vision; in writing *Notes from Underground*, he was out for blood. Whatever their motivations, however, ultimately neither Gödel nor Dostoevsky showed that their respective rationalist systems led to formal contradictions. Armed with the tool of proof by contradiction as it was outlined above, we therefore conclude that *Notes from Underground* is *not* a proof by contradiction at all, but rather something stranger. The parallels between Gödel and Dostoevsky's arguments suggest that the Underground Man's proof is constructive: it reveals something about the nature of the system that made him, a darkness at its core.

Though it may seem a mere technicality, the need for a formal contradiction to justify rejecting a premise suggests a new reading of *Notes from Underground*. The Underground Man's reasoning leads to a place of extreme discomfort, but it is not a place that forces us to dispense with the premises that brought us there. At best, the discomfort may seem so great as to suggest a meta-textual contradiction: one would hope that life simply cannot be so! Within the bounds of the text, however, Dostoevsky stops short of contradiction. He leaves us Underground.

## Consistency and Completeness

> How does it come about that all the statisticians and experts and lovers of humanity, when they enumerate the good things of life, always omit one particular one? They don't even take it into account as they ought, and the whole calculation depends on it.<sup>7</sup>

Though he is a self-described windbag, the Underground Man uses only three ingredients to construct his argument. Remarkably, all three find their mathematical counterparts in Gödel's proof. The first ingredient is the elucidation of an obscure corner of the calculus of "goods." The second is a flirtation with -- not a full embrace of -- the illogical escape one finds in contradiction. The nature of the Underground is such that neither of these elements seem satisfactory to a mind of sufficient complexity: this is the third and last bitter pill of Incompleteness.

In a formal logical system, one deals in truths and falsehoods. Given a set of axioms, or given truths, one need only turn the crank of inference<sup>e</sup> and the whole universe of truths implied by the axioms will spill out automatically. Chernyshevsky's key innovation to this scheme was to equate the concept of logical truth with experiential goodness. Specifically, the system devised by Chernyshevsky worked by tabulating self-interest, and proceeding in a manner so as to enhance it. Admissible actions, therefore, were those that maximized self-interest, and any explanation for the goodness of an action had to stem from furthering this cause. Importantly, Chernyshevsky's rational egoism mapped logic onto individual and societal benefit, but otherwise left it unchanged. The crank of formal reasoning turned just the same. Implicit in the promise of rational egoism was that once man's actions perfectly aligned with his interests, peace, prosperity, and "all that is highest and best"<sup>7</sup> would follow automatically.

Amidst the churning of Chernyshevsky's machine, however, the Underground Man posits a good, which comes "precisely from being too clearly aware of your own degradation; from the feeling of having gone to the uttermost limits; that it was vile, but it could not have been otherwise"<sup>7</sup>  In doing so, the Underground Man hints at the existence of actions that are undecidable by rational-egoism, actions that are good but could never be shown to be so using Chernyshevsky's rules of inference. It is tempting to believe that through his self-degradation, the Underground Man is merely lobbing absurdities at rationalism. But one must take him seriously. His argument is all the more devastating for it, as the good he references truly is "distinguished precisely by upsetting all our classifications and always destroying the systems established by lovers of humanity for the happiness of mankind."<sup>7</sup>

In Gödel's proofs, the Underground Man's claim finds vindication -- *mathematical* vindication. To understand how, one needs to adopt some of the logical terminology that Gödel used:

+ **Consistency**: If a system \\(S\\) is incapable of proving *both* \\(A\\) and \\(\neg A\\), then it is consistent.<sup>f</sup>
+ **Decidability**: A sentence \\(A\\) is decidable by a system \\(S\\) if either \\(A\\) or \\(\neg A\\) is provable within \\(S\\)
+ **Completeness**: A system \\(S\\) is complete if every sentence \\(A\\) within it is decidable.

In other words, if a formal system is capable of proving every truth it can express, then it is *complete*. If, using the rules of inference, a system cannot possibly derive a contradiction, it is *consistent*. Gödel proved that a formal system of sufficient complexity cannot be both consistent and complete. Since consistency was an indispensable property of Hilbert's idealized system of mathematical logic, the Incompleteness Theorems were interpreted as showing that there must exist undecidable mathematical sentences, which, despite being incapable of proof or disproof, are nonetheless true.

Gödel came to his conclusion by constucting a self-referential statement eerily reminiscent of the Underground Man's good that is "incapable of classification".<sup>7,</sup><sup>g</sup> What Gödel did was to use the language of a formal system \\(S\\) and its laws for creating admissible statements to express a special statement \\(D_S\\), which asserts its own unprovability within \\(S\\). The late logician and Gödel scholar Soloman Feferman summarizes Gödel's sentence as follows: "\\(D_S\\) says of itself that it is not provable in \\(S\\)."<sup>8</sup>

The statement \\(D_S\\) is certainly curious, but it may not be immediately clear why it was such a thorn in the side of Hilbert's program. To see this, one has to come to terms with the fact that if \\(S\\) is consistent, \\(D_S\\) must be true. Here again the method of proof by contradiction is a helpful tool. For if one assumes that the statement \\(D_S\\) is false, then one helplessly concludes that \\(D_S\\) *can* be proved using the language of \\(S\\). Therefore \\(D_S\\) must also be true! This contradiction upsets the consistency of \\(S\\), and one has to reject the possibility that \\(D_S\\) is false. Hence, Gödel's First Incompleteness Theorem, which Feferman summarizes as:

$$
\text{if } S \text{ is consistent, then } D_S \text{ is not provable within } S
$$

In the Underground Man's context, Gödel's First Incompleteness Theorem states that there really *do* exist actions, which say of themselves that they cannot be derived from the inferential rules of self-interest-maximization. And yet they are good -- provably so.

This alone would frighten Chernyshevsky to death. But there is more. A non-trivial corollary to Gödel's first result is the Second Incompleteness Theorem, which states, in Gödel's own words

> For any well-defined system of axioms and rules [...] the proposition stating their consistency (or rather the equivalent number-theoretical proposition) is undemonstrable from these axioms and rules.<sup>9</sup>

Internal consistency was of utmost importance to Hilbert's program. Hilbert himself was just as concerned with the metaphysics of formal systems and their syntactic objects as the Underground Man is with his "primary causes." For Hilbert, the basis of mathematics had to be so fundamental as to be reduced to rules of concatenating signs whose "shape can be generally and certainly recognized by us -- independently of space and time, of the special conditions of the production of the sign, and of the insignificant differences in the finished product."<sup>10</sup>

But if, by the Second Incompleteness Theorem, one cannot use the language of a formal system to assert that the system is sound, then how can one know the system is sound? If one does claim that the system is sound, on what grounds does that claim stand? If it stands anywhere at all, it must stand *outside* the formal system, on some even more primary ground. In the words of the Underground Man, "*where are my foundations*?"<sup>7</sup> Incredibly, even if one adds \\(D_S\\) as an axiom to the list of founding premises upon which \\(S\\) is built, the modified system \\(S'\\) is capable of spitting out another undecidable statement \\(D_{S'}\\), and so on until the end of time.

Of course, there is one way out of this undecidable mess. We can reject consistency altogether. It turns out that this rejection can be accomplished efficiently by way of the following relationship:

$$
S \text{ is consistent} \\ \iff \\ \text{The sentence } \neg(0=0) \text{ is not provable within } S
$$

The above merely states that a necessary and sufficient condition for the consistency of the system \\(S\\) is that one cannot prove that zero is not equal to zero within it. It does not take a skilled mathematician to see that the Underground Man's beloved \\(2+2 = 5\\) is precisely the assertion of this condition.<sup>h</sup> He toys with the notion of inconsistency explicitly:

> 'Excuse me,' they cry, 'you can't fight it; twice two is four! Nature doesn't ask you about it; she's not concerned with your wishes or with whether you like her laws or not. You must take her as she is, and consequently all her results as well. I mean to say, a wall is a wall,' etc. etc. But good God! what have the laws of nature and arithmetic to do with me, when for some reason I don't like those laws or twice two?<sup>7</sup>

The Underground Man claims that the laws of nature do not apply to him. However, as seriously as we must take other components of his argument, we must recognize that this is just bluster. For Gödel's First Incompleteness Theorem tells us that accepting \\(2 + 2 = 5\\) is a way out of the mouse hole that is undecidability. If the Underground Man truly believed in his \\(2 + 2 = 5\\), he would have long ago left his hovel.

The key point is that he is capable of contemplating the possibility of inconsistency, though he is unable to fully believe it. In this way, he is distinguished from those who believe that a wall is a wall without needing further explanation.

## The thinking man

> A wise man can't seriously make himself anything, only a fool makes himself anything. Yes, a man of the nineteenth century ought, indeed is morally bound to be essentially without character; a man of character, a man who acts, is essentially limited.<sup>7</sup>

In connection with the subject of so-called "men of action,"<sup>7</sup> we arrive at the third ingredient of Gödel's proof.  This final necessary ingredient for Incompleteness is not a statement derived by a formal system, but rather a property of a formal system. In Gödel's proof, the intricate construction of the special statement \\(D_S\\) depended on the fact that the system from which it was derived had enough complexity to "suffice to derive a certain portion of the finitistic arithmetic of integers."<sup>9</sup> Informally, the system \\(S\\) had to be expressive enough to produce the kinds of mathematical statements that are interesting to mathematicians, specifically those that comprised mathematics as Hilbert knew it.

Simpler systems of formal reasoning than the one Gödel used to prove his results do exist.<sup>i</sup> Unlike Gödel's \\(S\\), these simple systems may be both consistent and complete. So one might be curious as to what prevents the Underground Man from adhering to such a system and living out his days in blissful ignorance?

Strictly speaking, the Underground Man would only have to accept very basic mathematical statements to depart from completeness. In addition to \\(2+2=4\\), which he never fully rejects in the first place, he would also have to acquiesce to \\(2\cdot 2 = 4\\), a modest demand on an intellect such as his. 

More loosely, we do not need equations to understand the Underground Man's plight. He tells us directly where his troubles lie: "I swear to you that to think too much is a disease, a real, actual disease."<sup>7</sup> On a surface level, endless rumination explains part of the Underground Man's misery, which is perhaps even of a clinical grade. One layer deeper, introspection is the root of the existential doubt that haunts him. Finally, and most salient to the notion of Incompleteness, thinking is the sufficient condition for constructing the Underground Man's unprovable truths, for his acts of depravity that are in service of the highest good.

The manifestations of simple, complete systems become the objects of the Underground Man's ire and envy:

> I have mentioned this before. I repeat, and repeat emphatically: all spontaneous people, men of action, are active because they are stupid and limited. How is this to be explained? Like this: in consequence of their limitations they take immediate, but secondary, causes for primary ones, and thus they are more quickly and easily convinced than other people that they have found indisputable grounds for their action, and they are easy in their minds; and this, you know, is the main thing. After all, in order to act, one must be absolutely sure of oneself, no doubts must remain anywhere. But how am I, for example, to be sure of myself?<sup>7</sup>

Though he envies men of action, the Underground Man's self-awareness makes him incapable of joining their brood.  Viewed through Gödel's lens, these men are systems that are simple enough to be complete -- mindless and attending to their business algorithmically. When they encounter a wall they retreat from it according to a predetermined rule, no questions asked. Being self-aware -- being a "thinking man" -- gives the Underground Man more power of expression than these lower forms of consciousness. He is "free" to throw self-interest to the wind. But he is also expressive enough to admit Incompleteness and the psychic trauma it entails.

Herein lies the most insidious aspect of what Gödel's Theorems tell us about the hero of *Notes from Underground*, the inexorable conclusion of a painfully honest mathematical treatment of the text: the Underground Man believes that his spite and his whimsy are proof that he is not a "sprig in a barrel-organ,"<sup>7</sup> bound to mindlessly follow the rules of a deterministic universe. He delights in his depravity, and holds fast to it as the last vestige of will left to him after the statisticians have stolen all else. In actuality, his spite never breaches the walls of rationality and determinism. Though his hardware is undeniably more complex than that of the spontaneous man, it is still running the same program. What he does not know, but what Gödel proved, is that sufficiently expressive rational systems have built-in spite.

## The halting problem and inertia

> But what can one do, if the only straightforward task of every intelligent man is pointless chattering, the deliberate pouring out of emptiness?<sup>7</sup>

Algorithms. Machines. Programs. These words carry a precise meaning in the context of the Underground. In 1936, the mathematician and philosopher Alan Turing showed an equivalence between Gödel's Incompleteness Theorems and properties of physical computing machines.<sup>11</sup> His thesis showed that it is possible to pose an undecidable problem<sup>j</sup> to a computing machine, which will cause it to run forever, outputting zeros and ones until the end of time without reaching a conclusion.

This is an apt metaphor for the plight of the Underground Man. Incompleteness is intolerable. Inconsistency is absurd. Living a life of "action" is unimaginable once one has tasted basic number theory. Where is he to go? The only answer is "conscious inertia,"<sup>7</sup> in his case, an infinite vacillation between equally unacceptable outcomes.

But in fact the inertia that the Underground Man craves, the "something different, quite different, for which I am thirsting, but which I cannot find"<sup>7</sup> is not the one he experiences. Halting all cognition would be his ideal inertia. It would entail a full system shutdown. It would stop the generation of new propositions, new paradoxes, new doubts. Unfortunately, what he seeks lies in the non-existent crack between truth and falsehood.

## Conclusion

> But finally, and chiefly, all this proceeded from the normal basic laws of intellectual activity and the inertia directly resulting from these laws, and consequently not only wouldn't you change yourself, you wouldn't even do anything at all.<sup>7</sup>

Many readings of the first chapter of *Notes from Underground* would suggest that the Underground Man's spite represents a defiant act against logic. This reading does not. Reading *Notes from Underground* in light of Gödel's Incompleteness Theorms shows that the Underground Man's spite is actually an unavoidable consequence of complex mathematical logic. Logic subsumes the Underground, every act of its malice, every act of its whimsy.

This is not the first work to suggest that the Underground Man is a wholly logical creature, and that the weight of his logic buries him. In writing on *Notes from Underground*, Gary Saul Morson comments:

> We learn...that everything the
hero does to make himself unpredictable is itself subject to an iron logic, albeit of a peculiar and spiteful
kind.<sup>12</sup>

However, one unique contribution of this work is to point out that the Underground Man does not abide by some "alternate" logic that stands outside the one envisioned by Hilbert, or even that employed by Chernyshevsky. The Underground Man's self-degradation is an inherent property of the very same logic he curses. The Incompleteness Theorems remind us that when one tugs at the seams of rationality, one finds a more demented realm than expected. In short, the Underground Man is not following a twisted logic to his metaphysical nightmare. Logic as it is *is* twisted.

The philosophical implications of the Incompleteness Theorems were not lost on Gödel. Assuming the consistency of mathematics, he proposed the following, mutually exclusive, implications of his work:

> "Either [...] the human mind [...] infinitely surpasses the powers of any finite machine, or else there exist absolutely unsolvable diophantine problems."<sup>13</sup>

The hero of *Notes from Underground* leaves us with a similar dichotomy. Either mankind can decide things that computers cannot, or else we are all hyperconscious machines, stuck in the Underground. Most scholars today see diminishing room for the possibility that human minds are not finite machines, albeit of an amazingly intricate sort. However, the debate over the exact implications of the mechanistic quality of cognition for concepts like will still rages.<sup>14</sup> Some have even suggested that the assumption that mathematics is consistent ought to be revisited.<sup>15</sup>

David Hilbert is not Nikolai Chernyshevsky. Kurt Gödel is not the Underground Man, nor is he Dostoevsky himself. The motivations of these men were not the same. But the same angels and demons that whisper into the ears of writers and mathematicians alike spoke through their work.

# Footnotes

<sup>a</sup> *i.e.* it can be expressed as a fraction in lowest terms as \\(\frac{a}{b}\\) where \\(b\\) does not divide \\(a\\)

<sup>b</sup> The equality says that \\(a^2\\) must be equal to \\(2\\) times some number. Therefore, the square of \\(a\\) is even. Since the square of any odd number is odd, \\(a\\) cannot be odd. It must be even.

<sup>c</sup> If \\(a\\) is even, then it is twice some number \\(c\\). Then \\((2c)^2 = 2b^2 \implies 2c^2 = b^2\\). From here, the same reasoning that told us that \\(a\\) was even applies to \\(b\\) as well.

<sup>d</sup> We assumed this was true at the beginning.

<sup>e</sup> See the proof by contradiction above. Inference here refers to the rules for how one is allowed to move from one truth to another. In formal systems, even a concept as intuitively clear as inference must be carefully defined.

<sup>f</sup> We defined this notion earlier. The symbol "\\(\neg\\)" indicates the negation of a statement.

<sup>g</sup> Gödel was most likely unaware of this similarity. He was said to have thought of his statement as an analogue of the "liars paradox," a sentence that reads "this sentence is false."<sup>3</sup> If the sentence is true, then it is false. If the sentence is false, then it is true, and so on.

<sup>h</sup> Subtracting \\(4\\) from both sides of the Underground Man's fanciful equality, we get \\(0 = 1\\), which implies that \\(0 \neq 0\\). This is the negative statement \\(\neg(0=0)\\).

<sup>i</sup> One example is Pressburger Arithmetic,<sup>8</sup> which is distinguished from the system that Gödel used -- called Peano Arithmetic -- by its exclusion of the multiplicative operator \\(\cdot\\) and its associated rules.

<sup>j</sup> One example Turing gave was known as the "Halting Problem," in which one program is tasked with deciding whether another program will terminate.

# References

<sup>1</sup> D. Hilbert, “Mathematical problems,” *Bulletin of the American Mathematical Society*, vol. 8, pp. 437–480, July 1902.

<sup>2</sup> A. Hald, *A history of mathematical statistics from 1750 to 1930*. Wiley series in probability and statistics, New York: Wiley, 1998.

<sup>3</sup> R. Goldstein, *Incompleteness: the proof and paradox of Kurt Gödel*. New York: W.W. Norton, 2006. OCLC: 1033717217.

<sup>4</sup> C. A. Flath and J. Fitzpatrick, eds., *The new Russian Dostoevsky: readings for the twenty-first century*. Bloomington, IN: Slavica, 2010.

<sup>5</sup> M. Marsh-Soloway, *The Mathematical Genius of F.M. Dostoevsky: Imaginary Numbers, Statistics, Non-Euclidean Geometry and Infinity*. PhD thesis, University of Virginia, Aug. 2016.

<sup>6</sup> N. G. Chernyshevsky, N. H. Dole, and S. S. Skidelsky, *What is to be done?* Ann Arbor: Ardis, 1986.

<sup>7</sup> F. Dostoyevsky and F. Dostoyevsky, *Notes from underground: The double*. Penguin classics, Harmondsworth, Eng., Baltimore: Penguin Books, 1972.

<sup>8</sup> S. Feferman, “The impact of the incompleteness theorems on mathematics,” *Notices of the American Mathematical Society*, vol. 53, 2006.

<sup>9</sup> S. Feferman, “Are There Absolutely Unsolvable Problems? Gödel’s
Dichotomy,” *Philosophia Mathematica*, vol. 14, pp. 134–152, Jan. 2006.

<sup>10</sup> R. Zach, “Hilbert’s Program,” in *The Stanford Encyclopedia of Philosophy* (E. N. Zalta, ed.), Metaphysics Research Lab, Stanford University,
spring 2016 ed., 2016.

<sup>11</sup> B. J. Copeland, “The Church-Turing Thesis,” in *The Stanford Encyclopedia of Philosophy* (E. N. Zalta, ed.), Metaphysics Research Lab,
Stanford University, winter 2017 ed., 2017.

<sup>12</sup> G.S.Morson, *Narrative and freedom: the shadows of time*. New Haven:
Yale Univ. Press, 1994. OCLC: 832367365.

<sup>13</sup> K. Gödel and S. Feferman, Collected works. Oxford [Oxfordshire]:
New York: Clarendon Press; Oxford University Press, 1986.

<sup>14</sup> S. Aaronson, “The Ghost in the Quantum Turing Machine,” in *The Once and Future Turing* (S. B. Cooper and A. Hodges, eds.), pp. 193–296,
Cambridge: Cambridge University Press, 2016.

<sup>15</sup> T.Y.Chow, “The Consistency of Arithmetic,” arXiv:1807.05641[math],
July 2018. arXiv: 1807.05641.
