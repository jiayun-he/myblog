---
layout: "post"
title: "TF*IDF and document similarity"
date: "2018-10-23 21:35"
---
{% include mathjax.html %}
## What is TF*IDF and why do we need it?

TF\*IDF, which stands for Term Frequency - Inverse document Frequency. Intuitively, a TF\*IDF model tells us whether a specific term (or word) is important to identify a document among a collection of documents. Term frequency measures how often this term appear in one document and document frequency measures how often this term appear overall documents. When a word frequently appears in one document and not appears many in other documents, this specific word is very useful to identify this document. Assume we have 4 different documents:

Doc1. "Alice is a cute girl."<br>
Doc2. "Alice is a student."<br>
Doc3. "Bob and Alice are friends."<br>
Doc4. "Alice and Alice and Alice and Calvin"

Consider the term "Alice" and document 4. This term appear once in this document and twice overall documents. So the term frequency $$f_{(d,t)}$$ = $$f_{(doc4,Alice)}$$ = 3 and document frequency $$f_t$$ = $$f_{Alice}$$ = 6.

We can use a simple formula for calculation:<br><br>
$$TF*IDF\ =\ f_{(d,t)}\ *\ \frac{1}{f_t}$$<br><br> So,  $$TF*IDF_{(doc4,Alice)}\ =\ 1\ *\ \frac{3}{6}\ =\ \frac{1}{2}$$.<br><br>

The numeric value is quite small, which indicates that the term "Alice" may not be a good choice for identifying document 4. Let us try another term Calvin. <br><br>  $$f_{(d,t)}$$ = $$f_{(doc4,Calvin)}\ =\ 1$$,  $$f_t$$ = $$f_{Calvin}\ =\ 1$$ <br><br>
$$TF*IDF_{(doc4,Calvin)}\ =\ 1\ *\ \frac{1}{1}\ =\ 1$$.<br><br>
Here the interesting thing comes. Although the term "Alice" appears 3 times more than the term "Calvin" in document 4, "Calvin" has a larger TF\*IDF value. This is because Calvin only appear once overall documents, so if a document contains the term "Calvin", it has to be document 4. Clearly, the term "Alice" has weaker identification ability than "Calvin".

There are many different formulas for calculating TF*IDF, and they share the core of TF\*IDF. <br><br>
The classic TF\*IDF formular: $$w_{(d,t)}\ =\ f_{(d,t)}\ *\ log\frac{N}{f_t}$$<br><br>

You can find a lot more from [wikipedia](https://en.wikipedia.org/wiki/Tf%E2%80%93idf)
