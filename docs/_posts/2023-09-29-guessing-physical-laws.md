---
title: Guessing Physical Laws
layout: post
tag: statistical physics
categories: ["general"]
---
Theoretical physics is a precise business. You choose your principles
carefully, put them in to mathematical form and use rigorous logical
deduction to infer consequences. Or perhaps you take a hithertho
unexplained phenomenon and start from a known physical theory, using
judicious approximations and clever calculation techniques to produce a
brilliant explanation for its features. You might even write a computer
program to apply numerical methods to theories and get your results that
way. Either way, it's clearly a job for the logical goober! That's how
you should do physics.

Well, except if you just want to play a guessing game. I mean...

-   Bohr deduced his famous atomic model by guessing physical principles
    that were totally wrong, he managed to get the right result anyway;

-   Maxwell used gears and other mechanical devices to explain his
    theory of electromagnetism, and those turned out to be totally
    useless;

-   Modified Newtonian dynamics was originally based on just guessing a
    generic form for Newton's law of gravity;

-   Dirac derived his equation using mathematical methods and simply
    guessed the positron solutions were actually real particles

and on and on it goes.

So, hell, it's pretty useful to know how to just wing it.
Back-of-the-envelope calculations and leaps of logic abound in physics
departments everywhere, and great discoveries are often made just as
much by inspired guesswork as they are by logic. Still, there's rules
even to leaps; no matter how magical Michael Jordan's jumps look, he
can't actually fly. Well, I don't think so anyway. To be fair, a few of
the videos I've seen seem to defy the laws of physics -- for the sake of
argument, suppose he doesn't know how to fly to make my point make
sense. Magical guesswork isn't actually magical!

In this text, I'll go over a few methods to just guess, using simple
physical intuition, one particular example of a physical law: the
Maxwell-Boltzmann speed distribution.

# What the Hell Do You Know, Anyway?

Our problem is to find the distribution of the speed of gas molecules in
a room full of molecules. What is it that we know about this problem?

Well, any schoolboy knows that rooms feel different at different
temperatures. Even a 5 year old pipsqueak can tell you that temperature
differences are caused by the speed of the molecules whizzing about in
the room. You can guess that the kind of the molecules matters, too --
different speeds for different types. And you probably already knew in
your mother's womb that distributions are normalized; that is, if we
have a speed distribution, then

$$\int f(v) dv = 1$$

with $f(v)$ our mysterious distribution. We can perhaps make a further
guess: presumably there's nothing special about any of the directions --
the distribution looks the same in $x$, $y$ and $z$ directions, so we
can deal with them separately.

Well, you say, without further information this doesn't amount to much.
Unless I can use the principles I learned in my statistical physics
class, there's no way to make progress!

Or that's what you would say if you were a *pathetic little weakling.*
Are you a pathetic weakling? No? Then let me introduce you to
dimensional analysis.

# There's Rules To Combining Quantities

You see, we just identified a number of things a speed distribution
probably depends on:

-   The actual speed of the particles (obviously, since it's a speed
    distribution)

-   The kind of molecule

-   The temperature of the room

The first one is evident, but the other two aren't. Let's talk about
them.

First of all, we're not really interested in the kind of molecule in the
room, just some property of it. Unless you're feeling confident and
think you can solve this problem by starting from the quantum mechanics
of molecules (if so, good luck, see you in 5 years). No, what we really
want is just the inertia of the molecule, how hard it is to accelerate.
In principle, if there were enough molecules in the room, or if they
were big enough, then we might have to care about intermolecular
interactions, but let's just suppose they're far enough apart to not
really interact in a meaningful way. So we want the *mass* of the
molecules.

As for the temperature, I already told you that even a schoolboy knows
temperature differences are measured by the speed -- or more accurately,
the kinetic energies -- of the particles. So let's simply call the
quantity of interest here \"energy\", for that is in fact what it is.

What now? We have three quantities, $v, m$ and $E$. We also know the
normalization of the distribution. But this normalization gives us our
first clue.

Notice how the end result of $\int f(v) dv$ is a pure number -- no
dimension? Let's call the units of mass $[m] = M$, units of time $T$ and
units of length $L$ (these could be anything -- meters, inches, a fruit
fly's average wingspans -- as long as you keep your units consistent).
Then we know that $[f(v)] = [1/v] = T/L$, because $[dv]=L/T$. See how
that works? The units of $f$ have to cancel out the units of integration
measure $dv$, since the end result 1 doesn't have units.

So we're looking for a distribution that has units of $T/L$. How could
we combine our quantities $m$, $E$ and $v$ to get units like that?
Notice that $[E] = ML^2/T^2$ Think about it for a while, come up with
options. Here are the easiest options I came up with:

$$\begin{align}f(v) &\propto 1/v g\bigg(\frac{v^2m}{E}\bigg)\\
    f(v) &\propto \sqrt{\frac{m}{E}}g\bigg(\frac{v^2m}{E}\bigg) \\
    f(v) &\propto \frac{vm}{E}g\bigg(\frac{v^2m}{E}\bigg)\end{align}$$

The function $g$ is unknown, but must be a function of dimensionless
quantity, since $1/v$ and $\sqrt{\frac{m}{E}}$ and $\frac{vm}{E}$
already have the right dimensions (check for yourself!). The simplest
dimensionless quantity you can construct from $v$, $m$ and $E$ is
$v^2m/E$.

Alright, is there any way to eliminate any of these possibilities using
our intuition? How do you think the distribution of the speeds should
behave?

Well, I don't know about you, but I don't think that the distribution
blowing up as $v\rightarrow 0$ seems very reasonable. I mean, maybe the
slower speeds are more likely, but is that prefactor really supposed to
be divergent? How would you even find a reasonable $g$ that would still
integrate to a finite number over the infinite interval
$v\in [0, \infty)$?

As for the third one, it suggests that the distribution is proportional
directly to the speed and mass of the particles. Does it seem likely
that $f(0) = 0$? Really, just a straight up zero at the origin? Maybe
it's possible -- we can keep it in mind.

However, the middle one is the least offensive choice for at least my
sensibilities (I also happen to know this guess produces the right
answer, so my \"intuition\" is greatly aided by foreknowledge!) Since
the dimensionful part doesn't contain $v$, there's no immediate
pathologies that jump out.

Let's go with the middle guess there. Our distribution is of the form
(with $\alpha$ and $\gamma$) some yet to be determined constants)

$$f(v) = \alpha \sqrt{\frac{m}{E}} g\bigg(\gamma \frac{v^2m}{E}\bigg)$$

We now need to find an appropriate $g$. It has to be some function that
is integrable from 0 to $\infty$. Presumably, the speeds closer to 0 are
way more likely than the tail end -- we don't have too many infinitely
fast particles flying about, that would just be straight up painful. Try
to find some functions that satisfy that property. Go on, I'll wait.

You can probably find a bunch. You can plot them to see what they would
look like, just pick some easy values for $m$ and $E$. However, we now
remember the Central Limit Theorem, which says that everything is always
the damn exponential distribution (well, it doesn't quite say that, but
close enough), so that

$$g\bigg(\frac{v^2m}{E}\bigg) = e^{-\frac{\gamma v^2m}{E}}$$

Plot this -- it certainly seems reasonable, right?

Supposing we're right, is there some way to go even further? Can we
guess $\alpha$ and $\gamma$?

Well, notice what we have in the exponential function: $mv^2$. Does that
look like any form of energy you know of?

Right, it's the kinetic energy of a particle if we take
$\gamma = \frac{1}{2}$. So let's plug that in! And, lucky for us, we now
remember the normalization of the distribution:

$$\int _0^\infty f(v)dv =\int _0^\infty\alpha \sqrt{\frac{m}{E}} g\bigg( \frac{v^2m}{2E}\bigg)dv = 1 \\
    \implies \alpha \frac{1}{2}\sqrt{2\pi } = 1 \\
    \implies \alpha = \sqrt{\frac{2}{\pi }}$$

So, our answer is

$$f(v) = \sqrt{\frac{2}{\pi }} \sqrt{\frac{m}{E}}e^{-\frac{\gamma v^2m}{E}}$$

which, wouldn't you know it, is exactly right.

# You Cheated!

\"Ah yes\", you say, \"of course you're able to do this because you
cheated! You already knew the end result, and used that as a guide! You
can't use this for anything real!\"

First of all, who the hell do you think you are, assaulting me with the
truth??

It's not quite that simple, though. As I said, real physicists making
real discoveries have used various forms of guesswork all throughout
history (see Anthony Zee's book \"Fly by Night Physics\" for plenty of
examples of exactly this sort of historical reasoning). Order of
magnitude estimates, dimensional analysis, intuitively inspired
approximations -- all of these are tricks you can find in the literature
that have really been used for research, not just when you know the end
result.

It might also help you if you're a student. Suppose you only very
vaguely remember some formula or end result of a calculation, and it's
asked on the exam. Well, if you mostly remember it -- like was the case
for me and the Maxwell-Boltzmann distribution when I did this
calculation -- you can guess your way to the right solution using this
kind of reasoning. Mr. Zero Points turns in to Mr. Partial Credit.

What are the principles we used here?

1.  Identify the relevant quantities at play; in our case, mass, energy,
    speed.

2.  Make the necessary approximations. We implicitly approximated that
    the particles are non-relativistic, and we don't care about
    intermolecular forces or quantum mechanical effects; basically, it's
    a normal room full of something like air.

3.  Perform dimensional analysis on the quantity you're interested in
    calculating. Find any combinations of the quantities that you
    identified that give the right units and satisfy any other
    constraints you identified. Eliminate the combinations that don't
    fit the constraints; if more than one combination remains, pick the
    one that seems right to you based on your intuition.

4.  Try to fix any undetermined constants by some bullshit argument if
    possible; if not, just leave them there.

It is clear that this sort of reasoning can't give you the same
certainty as a logical deduction from well-justified principles. It's
equally clear that it's far easier to use this method than to come up
with the correct fundamental principles for a problem you're not all
that familiar with. If you got it wrong -- eh, it happens, whatever.
