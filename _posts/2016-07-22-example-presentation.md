---
layout: slide
title: Example Reveal.js Presentation Deck
excerpt: A sample file showing the correct markup for creating a Reveal.js slide deck"
theme: simple
transition: convex
tags: [presentation]
category: presentation
---
<section data-markdown>

# Reveal.js and Jekyll Academic


</section>

<section data-markdown>
## HTML or Markdown
Reveal.js works with either. Use whatever you are more comfortable with.

</section>

<section data-markdown>
## Works Anywhere

By creating presentations using Reveal.js and hosting them on your Jekyll Academic site you will have access to them anywhere. No need to worry about software compatibility, no need to sign in to email accounts on public machines. Simply load your website and select the presentation.

</section>

<section>
   <div class="sage">
      <script type="text/x-sage">
         
         # some library objects we need
from numpy.random import binomial, seed
from numpy import zeros, arange
from matplotlib import pyplot as plt
# initial population
P0 = 80
# number of rolls per experiment
n_rolls = 50
# number of experiments
n_exp = 1
# probability that any given die will "decay" on a given roll
p = 1/6
# location to track average dice remaining for each roll number
pop_avg = zeros(n_rolls+1)
# "seed" the random number generator
# (This makes the results look different
# each time the code is run.)
seed()
# loop over experiments
for n in range(n_exp):
  # reset the dice population
  P = P0
  # roll the dice
  for k in range(1,n_rolls+1):
    # figure out how many dice decay this time
    r = binomial(P,p)
    # remove the dice
    P -= r
    # update the average
    pop_avg[k] += P
# final division to compute the averages
pop_avg /= n_exp
# we always started with P0
pop_avg[0] = P0
# compute the model predictions
model = (1.0-p)**arange(n_rolls+1.0)*P0
pl1 = list_plot(pop_avg,plotjoined=True,marker='+',legend_label='Model results',axes_labels=['roll #', '# dice'])
pl2 = list_plot(model,plotjoined=True,linestyle='--',color='red',marker='x',legend_label='Theoretical curve')
show(pl1+pl2)
      </script>
     </div>
  </section>
<section data-markdown>
## More Information

Jekyll Academic includes everything that you need in order to make Reveal.js work. Copy this file and edit it to begin making your own slide deck.  

For more information about all of the options available in Reveal.js please the [Reveal.js Demo Website](https://lab.hakim.se/reveal-js/#/)


</section>
