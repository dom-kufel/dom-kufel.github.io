---
layout: post
title: Quick intro to the knotty subject
description: This is a brief, rough, sketch of the workshops I conducted for gifted high-school students in Lublin, Poland, Dec 2022.
---

<section><h2>Intro</h2>

<p>No doubt: we all had to untie some annoyingly tangled knot at some point. So here's a fun problem: Is there any way to rigorously tell if one knot is more difficult to be untangled than another? Or even if two unlike looking knots are the same or actually different? You might be tempted to think that in practice it is easy to tell. Then consider the (un)knots in Fig. 1 and Fig. 2:</p>

 <div class="row">
  <div class="column">
  <figure>
    <p style="text-align:center;"><img src="/assets/img/outreach/haken.png" width="450"></p>
  </div>
    <figcaption><b>Fig. 1</b>: Haken's unknot. Yes, if you spent long enough untangling it, you would be able to make a simple loop!</figcaption>
  </figure>
  <div class="column">
    <p style="text-align:center;"><img src="/assets/img/outreach/thistlethwaite.png" width="450"></p>
    <figcaption><b>Fig. 2</b>: Thistlethwaite's unknot. Same story: you can disentangle it to get a simple loop (or transform it to the Haken's unknot if you really wish...)!</figcaption>
    </figure>
  </div>
</div> 

<br>

<p>What is plotted above are 2D projections (known as knot diagrams) of the simple loop (living in 3D), just twisted in some elaborate ways. Curious! Okay, since it might not be so easy to tell if two knot diagrams correspond to the same or different knot. At least, is there any algorithm, which, if one followed it rigorously, would guarantee that in finite number of steps we would get the simplest possible form of the knot? Short answer: yes. We will explore it in the next section. </p>

</section>
<section><h2>Reideimeister moves</h2>

<p>To understand the algorithmic approach, we will have to clarify few things.</p>

<p>First, we need to say what techniques of disentangling knots are allowed. You might be sneaky, and just like Alexander the Great (at least in one version of the <a href="https://en.wikipedia.org/wiki/Gordian_Knot">legend</a>) start cutting the knot under consideration. To the disappointment of Zeus, this is not allowed: we deal with a beautiful branch of math known as topology. In topology, we are already allowed to do a lot of things (e.g., we can deform the precise geometrical shape of the knot in any way we want!), but cutting/glueing stuff is not one of it, period.</p>

<p>Second, what does "the simplest possible form of the knot" mean? Simplest possible knot corresponds to the alternating knot. An alternating knot has the following property: if one followed the thread on the knot diagram, she would see over-crossing, followed by under-crossing, followed by over-crossing, followed by ... - you get the "alternating" pattern. See Fig below</p>

<p style="text-align:center;"><img src="/assets/img/outreach/alternating.jpeg" width="450"></p>
<figcaption><b>Fig. 3</b>: Alternating knot example. This knot is known as a trefoil knot. </figcaption>
</figure>

<blockquote style="border: 2px solid #666; padding: 10px; background-color: #ccc;"> Exercise: Convince yourself that alternating knot cannot be further simplified. Can you think about any exceptions to this? (Hint: think about a loop with a single twist)</blockquote> <br>

<!-- (The fact that alternating knot cannot be further simplified is the reason why all knots in knot tables - such as one in Fig. !!! - have the alternating knot property...) -->

<p>Equipped with these two points we can proceed to the algorithm. The algorithm consists of iterative application of three basic disentangling moves, known as Reideimeister moves, and presented in Fig. 4 below: </p>

<p style="text-align:center;"><img src="/assets/img/outreach/reidemeister.jpeg" width="550"></p>
<figcaption><b>Fig. 4</b>: Three Reideimeister moves. I hope it is intuitively clear why these moves do not change the knot in the disallowed way! <br>
</figcaption>
</figure>

<br>

<p>Simple! We will demonstrate the R-moves by disentangling the knot below (which corresponds to trefoil knot in Fig. 3 with one crossing changed from overcrossing to undercrossing): </p>

<p style="text-align:center;"><img src="/assets/img/outreach/disentangling.jpeg" width="550"></p>
<figcaption><b>Fig. 5</b>: Algorithmically disentangling a knot with the help of R-moves. <br>
</figcaption>
</figure>

<br>

<p>In the above case it turned out that the original knot was in fact equivalent to the simple loop (unknot). Okay, great! To test your understanding solve the following exercise:</p> <br>

<blockquote style="border: 2px solid #666; padding: 10px; background-color: #ccc;"> Exercise: Simplify the knot diagram in Fig. 6 as much as possible using three Reidemeister moves.</blockquote> <br>

<p style="text-align:center;"><img src="/assets/img/outreach/exercise_rmoves.png" width="550"></p>
<figcaption><b>Fig. 6</b>: Knot diagram to be simplified.
</figcaption>
</figure>

</section>

<section><h2>Knot invariants</h2>

<p>We have repeatadely seen that by Reidemeister moves we can convert knot diagrams which initially do not look alike might in fact correspond to the same knot. It of course means that each knot might have many different diagrams which are related by a series of R-moves (or in this context we might also loosely say "topologically equivalent"). It would be nice if to each knot diagram we might have associated a number (or set of numbers) which would be neccesarily the same for two knot diagrams corresponding to the same knot. This is the idea of a <b>knot invariant</b> and restated in the Fig. 7 below: </p> <br>

<p style="text-align:center;"><img src="/assets/img/outreach/invariant.jpeg" width="450"></p>
<figcaption><b>Fig. 7</b>: Idea of knot invariants: for any knot diagram (D1,D2, D3, etc.) of knot K we associate the same quantity I (knot invariant).
</figcaption>
</figure>

<p>What are some examples of knot invariants? Here I will just list some of them: unknotting number, Jones polynomial, X-polynomial, fundamental group of the knot, existence of knot tri-coloring etc. To any knot we might associate multiple knot invariants. We will see that, sometimes, a particular invariant for two <i>different knots</i> might return the same value.</p><br>

<p>Perhaps the simplest invariant to describe is the unknotting number. Unknotting number is the minimum number of changes of overcrossings to undercrossings (or vice versa) one would have to perform to get a knot equivalent (up to R-moves) to a simple loop (unknot). We have seen before in Fig. 5 that trefoil knot has an unknotting number 1. To train the unknotting number calculation consider the following exercise: </p> <br>

<blockquote style="border: 2px solid #666; padding: 10px; background-color: #ccc;"> Exercise: Calculate the unknotting number of the knots in Fig. 8.</blockquote> <br>

<p style="text-align:center;"><img src="/assets/img/outreach/exercise_unknotting.png" width="450"></p>
<figcaption><b>Fig. 8</b>: Calculate the unknotting number of these knots. 
</figcaption>
</figure>

</section>

<section><h2>Conclusion</h2>
Alright, we have studied how to convert one equivalent knot diagram into another such that we can create simplest-looking knot diagram (use Reidemeister moves). We have also discussed idea of knot invariants and learnt how to calculate one of them (unknotting number). If you would like to learn more about mathematical basics or applications of knot theory to other fields (such as DNA biology or quantum computing) see further reading below. 
</section>

<section><h2>Further reading</h2>

<p>For a better mathematical grounding of knot theory ideas, and exploration of other knot invariants see section 4 of these excellent <a href="https://people.math.harvard.edu/~ctm/home/text/class/harvard/101/22/html/home/course/course.pdf 
">lecture notes</a> </p><br>

<p>There is some research on knotedness of DNA. (Very rough idea: It turns out that it is energetically favorable fot the DNA double-helix to form a <a href="https://en.wikipedia.org/wiki/DNA_supercoil#/media/File:Helix_vs_superhelix.png">super-coiled</a> structure which contains knots. Topoisomerase is an enzyme which is able to cut and reglue the super-coiled structure - effectively converting over-crossing to under-crossing. Thus using unknotting number we might calculate the number of required topoisomerase passes before DNA will be unknotted - something which seems to be neccesary for the DNA replication and its prevention e.g., in cancer treatment.) See: <a href="https://www.pathlms.com/siam/courses/2724/sections/3585/video_presentations/29347#">Video (2012) on research on topoisomerase in biology and links to knot theory</a>, <a href="https://iubmb.onlinelibrary.wiley.com/doi/pdfdirect/10.1002/bmb.20244">Review on DNA topology studies (2009)</a> or <a href="https://math.mit.edu/research/highschool/primes/circle/documents/2020/Ayinon_2020.pdf">Popular-science article on topoisomerase and knot theory. </a> </p><br>

<p>Some ideas from knot theory were proposed to be paramount for topological quantum computation. (Very rough idea: 2D-confined "particles" (also known as anyons) in a quantum computer travel on 3D space-time diagrams creating "worldlines". When we take two such particles their worldlines might tangle with one another making knots. Calculating knot invariant for such knot is classically an exponentially difficult problem. On a quantum computer though we can directly measure these knot invariants and thus achieve an exponential speed-up. Further, encoding information in non-local topological properties makes such encoding to be more robust to a local noise - physical counterpart to what we have said in R-moves section on being allowed to deform the geometrical shape of the knot as long as we don't cut/glue stuff.) See Chp 1 and Chp 2 of: <a href="http://www-thphys.physics.ox.ac.uk/people/SteveSimon/topological2020/TopoBookOct27hyperlink.pdf">this book</a> - rather advanced but still somewhat accessible; though to appreciate it requires basic knowledge of quantum mechanics</p>
</section>



 <!-- <div class="row">
  <figure>
    <p style="text-align:center;"><img src="/assets/img/outreach/haken.png" width="250"></p>
    <p style="text-align:center;"><img src="/assets/img/outreach/thistlethwaite.png" width="250"></p>
    <figcaption>Fig. 1: Haken and Thistlethwaite unknots. Yes, if you spent long enough untangling them, you would be able to make a simple loop!</figcaption></figure>
</div>  -->



<!-- <p style="text-align:center;"><img src="/assets/img/outreach/haken.png" width="250"/></p>
<p style="text-align:center;"><img src="/assets/img/outreach/thistlethwaite.png" width="250"/></p> -->



<!-- ## Reidemeister moves

We define the <a id="eq:H_TC">Hamiltonian</a> for the system to be
\begin{equation}
H = -\sum_v A_v - \sum_p B_p
\end{equation}   

## Further reading -->


<!--
### Header 3


```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip


### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item


### Definition lists

Name
: Godzilla

Born
: 1952

Birthplace
: Japan

Color
: Green

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this. Or is it?
```

<div class="gumroad-product-embed" data-gumroad-product-id="nuOluY"><a href="https://gumroad.com/l/nuOluY">Loading…</a></div>

## Large Tables

| Default aligned |Left aligned| Center aligned  | Right aligned  | Default aligned |Left aligned| Center aligned  | Right aligned  | Default aligned |Left aligned| Center aligned  | Right aligned  | Default aligned |Left aligned| Center aligned  | Right aligned  |
|-----------------|:-----------|:---------------:|---------------:|-----------------|:-----------|:---------------:|---------------:|-----------------|:-----------|:---------------:|---------------:|-----------------|:-----------|:---------------:|---------------:|
| First body part |Second cell | Third cell      | fourth cell    | First body part |Second cell | Third cell      | fourth cell    | First body part |Second cell | Third cell      | fourth cell    | First body part |Second cell | Third cell      | fourth cell    |
| Second line     |foo         | **strong**      | baz            | Second line     |foo         | **strong**      | baz            | Second line     |foo         | **strong**      | baz            | Second line     |foo         | **strong**      | baz            |
| Third line      |quux        | baz             | bar            | Third line      |quux        | baz             | bar            | Third line      |quux        | baz             | bar            | Third line      |quux        | baz             | bar            |
| Second body     |            |                 |                | Second body     |            |                 |                | Second body     |            |                 |                | Second body     |            |                 |                |
| 2 line          |            |                 |                | 2 line          |            |                 |                | 2 line          |            |                 |                | 2 line          |            |                 |                |
| Footer row      |            |                 |                | Footer row      |            |                 |                | Footer row      |            |                 |                | Footer row      |            |                 |                |
{:.scroll-table}


## Code blocks

~~~js
// Example can be run directly in your JavaScript console

// Create a function that takes two arguments and returns the sum of those
// arguments
var adder = new Function("a", "b", "return a + b");

// Call the function
adder(2, 6);
// > 8
~~~

 -->