--- 
layout: post 
title:  "How To Efficiently Read a Research Paper"
date:   2019-05-22 00:20:26 +0900
categories: 
--- 
Reading a research paper efficiently is a skill which is formally never taught but is the
first essential step towards doing research. Most of us learn it through
a lot of trial-and-error process and waste our precious time before
reaping any desired benefit. I have been there too and I understand how
much struggle young researchers face in this process, often feeling
bored and overwhelmed. Also, many young researchers often ignore the
dual benefits of efficient paper reading which are: <br> 1) new ideas +
2) better technical writing.

So based on my experience in data science research, I share 7 tips on
how you can read a research paper like a pro.

*Disclaimer: The following advice is based on my experience with reading
machine learning and computer vision research papers. Although the tips
are general but they may not be applicable in some domains.*

Let’s get started!

### 1. 3-pass approach 
 
When you come across a new paper, don’t just start reading it
end-to-end. Instead follow a 3-pass approach as explained in the figure
below.


![image]({{site.url}}{{site.baseurl}}/assets/images/3pass.png){:style="
float:center;margin-left: 200px"}

<br> Keep in mind the following points:

* After the first pass, if the paper does not interest you, don’t read
it further. It is not relevant for you.

* After the second pass, draw a block diagram of the proposed method by
hand. This ensures that you have completely understood the flow of the
method and functions of each block.

* For the third pass, be very selective and search for open-source codes
before  implementing yourself. Generally authors share their codes on
GitHub or project website. Another useful website is [Papers with Code].

### 2. 6 Q's to extract the main contribution
Each paper is trying to sell an idea to solve a specific problem. You
need to clearly identify both. If a paper tries to sell two ideas,
that’s a warning sign of a bad paper. Ask these 6 questions  to extract
the main contribution.

1. What is the main research field and why it is important? 
2. What are the common problems in this field? 
3. How the Previous work has address those problems? 
4. What problem is yet unsolved by the previous work?
5. How is this paper tackling that problem? 
6. What is the novelty of the paper?

An advice from Andrej's Karpathy blog:
```
You will find answers of most of these questions from just reading the
introduction part. Basically, each paper follows a structure which goes
as follows: [1] X is an important research field. [2] The core
challenges are this and that. [3] Previous work on X has addressed this
with Y, but the problem with this are Z [4] In this work, we do W to
solve the problem Z [5] This has the following appealing properties and
our experiments show this and that. So cracking the above structure will
help you find answers to the 6 core questions.
```

### 3. Read actively and critically
Talk to your paper when you read, ask questions where you don’t
understand and clarify assumptions. I strongly recommend you to take a print-out
rather than reading online. Write all the questions in the margin as you read and mark the
parts which do not fit your common sense

### 4. Circle the unknown terms
* While reading, there may be many terms or concepts that you are unfamiliar with. Circle all those. Google them after first reading. These are bridge to fill your knowledge gaps.

* Another recommendation is to circle the words which eased your understanding and made your reading smooth. This helps you to learn how to select words for concise, cohesive writing.

* If there are too many circles in the paper, it’s a warning sign that you are jumping into this paper too early. You must read some more basic paper first, and then shift to the advanced one.
  
### 5. Mark all the important references
* You can refer them to find new papers for your literature survey. Literature survey is another skill which I will discuss about in another blog.

* Helps you to create a chain of thoughts and innovations.

### 6. Build upon it
Your goal to read a paper is to get new ideas and further stimulate new ideas in your mind for your own problem. So after reading the paper, you can do the following things:

  i. If you do not have a problem at hand, find the areas of improvement in the paper.  Which assumptions/limitations can you minimize? Which application you can make with this technique? What problems are yet to be solved?
  
  ii. If you have the problem at hand from a different domain, find how this technique can be used in your domain?
  
  iii. What’s the author perspective on future work?
  
### 7. Formats to save your knowledge
After reading the paper you must create a system to save your knowledge because in this era of information overload, our memory is highly volatile. I suggest three tools:

a. Spreadsheet – create columns

b. Powerpoint – same points as in spreadsheet but you can save figure too and arrange papers logically

c. Research journal – on-the-go paper reading
	 

That’s it folks! I hope my 7 tips will make your paper reading process more enjoyable and effective. Do let me know if you any great suggestion. Let’s grow collaboratively.
