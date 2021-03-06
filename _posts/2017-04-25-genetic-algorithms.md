---
layout: post
title: "Playing God with Genetic Algorithms"
---

<i>“The fact that life evolved out of nearly nothing, some 10 billion years after the universe evolved out of literally nothing, is a fact so staggering that I would be mad to attempt words to do it justice.”</i>
-Richard Dawkins
<div class="divider"></div>
During my voyage of exploring the neverending world of machine learning, I came across a peculiar concept, a concept that
I carried with me in my very **DNA**,yet I was unaware of it's applications.While I was working on training data processing models to generalize datasets and give fairly correct outputs on new datasets,I came across a training method which was inspired by how we as organisms have evolved(trained) ourselves over all these generations to adapt and survive in our environments by simply optimizing our attributes throughout generations. A training algorithm inspired by the nature itself!
Genetic Algorithms stand at the intersection of computing and the theory of evolution.They mainly comprise of three steps:

# 1. Selection

On a given generation, compute the values of a fitness function and select the parents from the generation probabilistically depending on the values of their fitness function,i.e. the member with higher fitness has higher probability of getting selected.

# 2.Crossover/Reproduction
Using a merge procedure,produce an offspring from the selected parents. Repeat the selection and crossing until a new generation is produced.

# 3. Mutation

Mutation,although rare exists in the nature so our algorithm cannot evade it either.With minute probability,we mutate the children of produced generation.


<div class="divider"></div>
Now when we compute the values of our fitness function on the new generation, we see better results.Our generation has evolved to suit our requirments.We again apply the same procedure on this generation,to find newer generations which  have evolved even furthur.
Although error correction based algorithms like gradient descent, which adjust the attributes(genomes) of our data items by 
evaluating a degree of error between by the given output and the desired output give better results than genetic algorithms,genetic algorithms help us optimize a collection of data items altogether rather than working on a single data item.Also genetic algorithms,are useful to obtain a global minima when our back-propagating paradigm settles for a local minima.
<div class="divider"></div>
# Getting my hands dirty

I coded up a simple implementation of a genetic algorithm in python which accepted a target string("cat" in this case) and a list of string in the current generation eg.,['car','hut','box'].The fitness function will evaluate as percentage of no of characters in the string that are same as cat. ie; car will evaluate to 66.6% hut to 33.3% and box to zero. Then two parents will be chosen and crossed to generate an offspring.

```python
def createnewgeneration(generation):
	newgen=[]
	while len(newgen)!=len(generation):
		parents=select(generation)
		child=reproduce(parents)
		newgen.append(child)	 
	return newgen
  
```
The `createnewgeneration()` function accepts a generation and returns a new generation.
  The probability of mutation is 1%.If I don't seed the random number generator,everytime I run the code,most of the time cat is created within 3000 generations!Although sometimes I got vague results like 'clq' which occur due to mutation.You might be thinking why do we incorporate mutation even when it is leading to vague results.It's because mutation can help to adjust datasets to optimum when the initial fitness values are low,i.e., cat can be created from [box,rat,dog].Genetic Algorithms can be used to train Neural Networks by iteratating through a list of synapse values and performing selection,crossovers and mutation.
  
  
Check out the entire code [here](https://github.com/blackeagle01/AI/blob/master/evolve.py).

  
