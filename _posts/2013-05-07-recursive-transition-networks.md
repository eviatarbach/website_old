---
layout: post
title: Recursive transition networks
custom_js:
- jquery.min
extra_head: |
    <script src="http://sagecell.sagemath.org/static/embedded_sagecell.js"></script>
    <script>
    sagecell.makeSagecell({inputLocation:  '#mycell',
                               template:       sagecell.templates.minimal,
                               evalButtonText: 'Activate'});
    </script>

---

Here is my Python (2.7) implementation of the recursive transition networks given by Douglas Hofstadter in the book *Gödel, Escher, Bach*:

{% highlight python %}
import random

def article():
    return random.choice(['a', 'the'])

def adjective():
    return random.choice(['silly', 'thankless', 'big', 'red', 'blue',
                          'green', 'strange', 'purple'])

def noun():
    return random.choice(['shampoo', 'brunch', 'milk', 'cow', 'horns',
                          'bagels'])

def preposition():
    return random.choice(['without'])

def verb():
    return random.choice(['gobbled', 'sneezes'])

def relative_pronoun():
    return random.choice(['that'])

def walk_graph(graph, node='begin', sentence=None):
    if sentence is None:
        sentence = []
    if node == None:
        return ' '.join(sentence)
    if graph[node][0]:
        sentence.append(graph[node][0]())
    return walk_graph(graph, random.choice(graph[node][1]), sentence)

ornate = {'begin':[None, ['article', 'adjective', 'noun']],
          'article':[article, ['adjective', 'noun']],
          'adjective':[adjective, ['adjective', 'noun']],
          'noun':[noun, ['end']],
          'end':[None, [None]]}

fancy = {'begin':[None, ['ornate']],
         'ornate':[lambda: walk_graph(ornate), ['relative', 'preposition', 'end']],
         'preposition':[preposition, ['fancy1']],
         'fancy1':[lambda: walk_graph(fancy), ['end']],
         'relative':[relative_pronoun, ['verb1', 'fancy2']],
         'verb1':[verb, ['fancy3']],
         'fancy3':[lambda: walk_graph(fancy), ['end']],
         'fancy2':[lambda: walk_graph(fancy), ['verb2']],
         'verb2':[verb, ['end']],
         'end':[None, [None]]}

walk_graph(fancy)
{% endhighlight %}

This produces amusing (but often syntactically correct) nouns such as "red bagels that big shampoo sneezes" and "the green shampoo without shampoo that milk gobbled".

The program works by randomly walking the following graph:

[![Fancy noun recursive transition network](http://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/Fancy_noun_recursive_transition_network.svg/500px-Fancy_noun_recursive_transition_network.svg.png)](http://commons.wikimedia.org/wiki/File:Fancy_noun_recursive_transition_network.svg)

You can try it here by clicking the 'Activate' button:

<div id="mycell">
<script type="text/x-sage">
import random

def article():
    return random.choice(['a', 'the'])

def adjective():
    return random.choice(['silly', 'thankless', 'big', 'red', 'blue',
                          'green', 'strange', 'purple'])

def noun():
    return random.choice(['shampoo', 'brunch', 'milk', 'cow', 'horns',
                          'bagels'])

def preposition():
    return random.choice(['without'])

def verb():
    return random.choice(['gobbled', 'sneezes'])

def relative_pronoun():
    return random.choice(['that'])

def walk_graph(graph, node='begin', sentence=None):
    if sentence is None:
        sentence = []
    if node == None:
        return ' '.join(sentence)
    if graph[node][0]:
        sentence.append(graph[node][0]())
    return walk_graph(graph, random.choice(graph[node][1]), sentence)

ornate = {'begin':[None, ['article', 'adjective', 'noun']],
          'article':[article, ['adjective', 'noun']],
          'adjective':[adjective, ['adjective', 'noun']],
          'noun':[noun, ['end']],
          'end':[None, [None]]}

fancy = {'begin':[None, ['ornate']],
         'ornate':[lambda: walk_graph(ornate), ['relative', 'preposition', 'end']],
         'preposition':[preposition, ['fancy1']],
         'fancy1':[lambda: walk_graph(fancy), ['end']],
         'relative':[relative_pronoun, ['verb1', 'fancy2']],
         'verb1':[verb, ['fancy3']],
         'fancy3':[lambda: walk_graph(fancy), ['end']],
         'fancy2':[lambda: walk_graph(fancy), ['verb2']],
         'verb2':[verb, ['end']],
         'end':[None, [None]]}

print walk_graph(fancy)
</script>
</div>
