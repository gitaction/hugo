---
title: Home Introduction
type: docs
---

# Hugo Source Code Reading

> Our source code reading series, the reading method used is intensive reading.
Because they are all excellent open source projects.
The language is mainly the Go language, because the reading direction chosen is the cloud native direction, and many excellent open source projects in the cloud native are developed in the Go language.

There are many excellent materials about Hugo on the Internet, and the advantages and history of Hugo will not be repeated here.
Put pen and ink on the design and implementation of the source code.

In order to better understand the design concept of Hugo, we will start from the global architecture and expand and analyze it layer by layer.
It is not enough to talk about theory alone, but to do it in practice.
Only in this way can we achieve our ultimate goal of reading source code: **Learn about outstanding open source project designs, acquire domain knowledge of efficient site building, and unlock new capabilities in this area.
Share this glass of wine with Hugo with more people, and hope that through these sharing, you can continue to give back these excellent open source projects.**

## Source Code Interpretation Steps

1. Use two examples to help understand how to use the Hugo, one is to rebuild your personal site with the Hugo, and the other is to extract the theme of the site.
2. Prepare a Hugo amusement park (Source Code Lesson), let's focus on the core frame combing.
3. The Event Storm Practice in Event Driven Design (DDD) helps us to sort out the core events of Hugo and learn domain knowledge from these domain events.
4. Sort out the overall architecture and knowledge of key areas based on domain events.
5. Finally, according to the basic framework, starting with the source code, using the timing diagram to help understand the source code logic, through abstract summary, analysis of design ideas, and combined with the runnable source code example, not only understand but also master it.
   
## Writing Process Review
   
**Initial mind:**
   
Let yourself enjoy source code reading more.
Enrich your knowledge repository and convert knowledge into capabilities.
Visualize the knowledge graph, so that the dimensions are richer, and you know clearly what knowledge points need to be supplemented, so that you do not repeat, step by step every day, and continue to accumulate.

**Master Standards:**

It is true that others can understand and do it.
The explanation should be simple and easy to understand and hands-on practice should be convenient enough.
Theory with practice.

{{< columns >}}
## Where you can stick

* There are steps to write. Starting from the event storm, divide the domain knowledge. Then from the timing diagram, one by one split comb, by drawing pictures to help understand. Ultimately verified with a code implementation.
* The pictures are becoming more and more handy. Timing diagrams look at the steps of implementation, and architecture diagrams help to visualize design concepts. The final example implementation helps to review and validate the concept.
* Complete from the concept to the final example implementation. The process is complete, like yourself who persists to the end.

<--->

## There can be some changes
* 
* The article source code and sample source code are too scattered, using two sets of source code libraries.
* The reuse part of the source code in the example does not currently have a special explanation. Hiding knowledge points is not good for readers to understand.
* Poor reusability, if this knowledge is also used in the next open source code library, how to use the knowledge points already learned to accelerate the reading of the next source code?
* Feedback cycle is long, how to get feedback quickly and constantly adjust writing details.
* Writing platform is a communication channel, but now there are too many writing platforms and the supported formats are not the same. I don't want to be bound.

{{< /columns >}}

