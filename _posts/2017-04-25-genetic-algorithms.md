---
layout: post
title: "Playing God with Genetic Algorithms"
---

<i>“The fact that life evolved out of nearly nothing, some 10 billion years after the universe evolved out of literally nothing, is a fact so staggering that I would be mad to attempt words to do it justice.”</i>
-Richard Dawkins
<div class="divider"></div>
During my voyage of exploring the neverending world of machine learning, I came across a peculiar concept, a concept that
I carried with me in my very **DNA**,yet I was unaware of it's applications.While I was working on training data processing models to generalize datasets and give fairly correct outputs on new datasets,I came across a training method which was inspired by how we as organisms have evolved(trained) ourselves over all these generations to adapt and survive in our environments by simply optimizing our attributes throughout generations. A training algorithm inspired by the nature itself!
Genetic Algorithms stand at the intersection of computing and the theory of evolution.Genetic Algorithms mainly comprise of three steps:

# 1. Selection

On a given generation, compute the values of a fitness function and select the parents from the generation probabilistically depending on the values of their fitness function,i.e. the member with higher fitness has higher probability of getting selected.

# 2.Crossover/Reproduction

Defining some merging procedure to produce a crossover from the selected parents to produce a child.Repeat the selection and crossover procedure until a new generation is generated.

# 3. Mutation

Mutation,although rare exists in the nature so our algorithm cannot evade it either.With minute probability,we mutate the children of the generation.


<div class="divider"></div>
Now when we compute the values of our fitness function on the new generation, we see better results.Our generation has evolved to suit our requirments.We again apply the same procedure on this generation,to find newer generations which  have evolved even furthur.
<div class="divider"></div>

Although error correction based algorithms like gradient descent, which adjust the attributes(genomes) of our data items by 
evaluating a degree of error between by the given output and the desired output give better results than genetic algorithms,genetic algorithms help us optimize a collection of data items altogether rather than working on a single data item.Also genetic algorithms,are useful to obtain a global minima when our back-propagating paradigm settles for a local minima.

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

# A look at the `select()` `reproduce()` and `mutate()` methods
### select
```python
def select(generation):
	fitness={}
	for x in generation:
		fitness[x]=calfit(x)
	parents=selectparents(fitness)
	return parents
  ```
### reproduce
```python
def reproduce(parents):
	l1,l2=map(list,parents)
	child=''
	for i in range(len(l1)):
		x=random.randint(0,2)
		if x==0:
			child+=l1[i]
		else:
			child+=l2[i]
	child=mutate(child)
	return child
  ```
### mutate 
  ```python
  def mutate(child):
	child=list(child)
	l=list(string.ascii_lowercase)
	for i in range(len(child)):
		x=random.randint(1,101)
		if x==5:
			c=random.choice(l)
			child[i]=c
	return ''.join(child)
  ```
  The probability of mutation is 1%.If I don't seed the random number generator,everytime I run the code,most of the time cat is created within 3000 generations!Although sometimes I got vague results like 'clq' which occur due to mutation.You might be thinking why do we incorporate mutation even when it is leading to vague results.It's because mutation can help to adjust datasets to optimum when the initial fitness values are low,i.e., cat can be created from [box,rat,dog].Genetic Algorithms can be used to train Neural Networks by itertating through a list of synapse values and performing selection,crossovers and mutation.
  
  
Check out the entire code [here](#).
  
