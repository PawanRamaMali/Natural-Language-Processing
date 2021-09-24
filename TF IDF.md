
> TF*IDF is an information retrieval technique that weighs a term’s frequency (TF) and its inverse document frequency (IDF). Each word or term that occurs in the text has its respective TF and IDF score.
The product of the TF and IDF scores of a term is called the TF*IDF weight of that term. Put simply, the higher the TF*IDF score (weight), the rarer the term is in a given document and vice versa.


Google has already been using TF*IDF (or TF-IDF, TFIDF, TF.IDF) to rank your content for a long time, as the search engine seems to focus more on term frequency rather than on counting keywords.

The visual complexity of the algorithm might turn you off. But it isn’t actually difficult to understand how TF*IDF works.

TF*IDF is used by search engines to better understand the content that is undervalued. For example, when you search for “Coke” on Google, Google may use TF*IDF to figure out if a page titled “COKE” is about:

a) Coca-Cola.

b) Cocaine.

c) A solid, carbon-rich residue derived from the distillation of crude oil.

d) A county in Texas.

Whether you’re a content writer or an SEO expert, this article will guide you through the unknown topic of TF*IDF.

By understanding how Google utilizes this algorithm, content writers can reverse-engineer TF*IDF and optimize content towards both users and search engines.

And SEOs can use it as a tool for hunting keywords with a high search volume and a comparatively low competition.


## What is TF*IDF?

The TF*IDF algorithm is used to weigh a keyword in any content and assign importance to that keyword based on the number of times it appears in the document. More importantly, it checks how relevant the keyword is throughout the web, which is referred to as corpus.

For a term t in document d, the weight Wt,d of term t in document d is given by:

Wt,d = TFt,d log (N/DFt)

Where:

* TFt,d is the number of occurrences of t in document d.
* DFt is the number of documents containing the term t.
* N is the total number of documents in the corpus.

Let’s define this more concretely.

### Breaking TF*IDF down

How is TF*IDF calculated? The TF (term frequency) of a word is the frequency of a word (i.e. number of times it appears) in a document. When you know TF, you’re able to see if you’re using a term too much or too little.

For example, when a 100-word document contains the term “cat” 12 times, the TF for the word ‘cat’ is

TFcat = 12/100 i.e. 0.12

The IDF (inverse document frequency) of a word is the measure of how significant that term is in the whole corpus.

Let’s say the size of the corpus is 10,000,000 million documents. If we assume there are 0.3 million documents that contain the term “cat”, then the IDF (i.e. log {DF}) is given by the total number of documents (10,000,000) divided by the number of documents containing the term “cat” (300,000).

IDF (cat) = log (10,000,000/300,000) = 1.52

∴ Wcat = (TF*IDF) cat = 0.12 * 1.52 = 0.182

Now that you have this figured out (right?), let’s look at how this can benefit you.

### How you can benefit from using TF*IDF

Gather words. Write your content. Run a TF*IDF report for your words and get their weights. The higher the numerical weight value, the rarer the term. The smaller the weight, the more common the term. Compare all the terms with high TF*IDF weights with respect to their search volumes on the web. Select those with higher search volumes and lower competition. Work smart.

A good rule of thumb is, the more your content “makes sense” to the user, the more weight it is assigned by the search engine. With words having a high TF*IDF weight in your content, your content will always be among the top search results, so you can:

* stop worrying about using the stop-words,
* successfully hunt words with higher search volumes and lower competition,
* be sure to have words that make your content unique and relevant to the user, etc.

### Let’s get you up and rolling with TF*IDF optimization

1. Register your free account at Ryte.

First, you will need to sign up for Ryte.com (again: 100% free). Ryte lets you optimize your content using TF*IDF for free! With a very simple user interface, it is one of the best options for you or your content writer. Your content writer can create their own account and start work within minutes.

![image](https://user-images.githubusercontent.com/11299574/134665999-5123d7e6-5cdb-4228-a084-5dab6204003c.png)

You will see Register for free in the upper right corner and then come to this page.

After a couple of pages where they ask for your website and company information, you will come to this page:

![image](https://user-images.githubusercontent.com/11299574/134666045-43503afe-6650-412c-a5cf-5f6dd8e0520f.png)

You will be asked to confirm your email address and then you’re good to go.

2. Click on Content Success on the left side and then Analyze.

![image](https://user-images.githubusercontent.com/11299574/134666077-7386bb27-5c19-4666-a3f6-736475275834.png)

And then you will come to this page:

![image](https://user-images.githubusercontent.com/11299574/134666120-906984e3-4b56-4386-8c97-6687752bb6a0.png)


Once you are there, you simply need to choose your keyword and the language and country you are interested in, and click Get keyword recommendations.

![image](https://user-images.githubusercontent.com/11299574/134666172-b1692d26-c8da-42a2-8d4c-c8c147ead671.png)

As you can see, this is a lot of raw data that would be hard to use. Fortunately, we can do cool stuff to make it easier to understand and utilize.

Your options include Detail mode, Competition, and Compare.

And the last one is what we want to focus on.

When you click Compare, you’ll see an Add URL button.

3. Add URL is where all the magic happens. Let’s check it out in more detail.

We are going to compare the results with this article (apologies for getting all meta with this thing!).

![image](https://user-images.githubusercontent.com/11299574/134666222-6164a8e3-9969-4be2-bd71-7ebe118167a1.png)

And here are the results:

![image](https://user-images.githubusercontent.com/11299574/134666243-64eebe94-609f-4969-ac1f-147437832aca.png)

Again, by looking at the screenshot above, we don’t really see any actionable data. Let’s change that. We have a few options (as presented below with number tags).

Using sliders on the upper part of the bar chart, we can filter out the results to only see the most important and relevant terms. Those two sliders can be confusing at first, but once you understand them, they become quite easy to use.

* Proof Keyword Filter is the slider button on the left. With this slider, you can filter out all the less relevant keywords and, depending on your content detail level and length, keep only the most important ones. In most cases (when you are writing a blog post or short article), you probably will be OK with 10-20 of the most important terms as the other ones can be too detailed or even off-topic.
* Zoom Tool is the slider button on the right. This slider doesn’t actually change our results. It is only used to zoom in and out of the results so they are easier to analyze.
Now that you know how to filter the data, let’s finally start optimizing our content.

### Comparing and optimizing our content

To start with content optimization, click Detailed Content Report located under Current content report. This view will show you the current level of your content optimization according to TF*IDF.

Now you are presented with a detailed comparison of the search results vs. your landing page or content.

![image](https://user-images.githubusercontent.com/11299574/134666381-ab468a7b-e3af-4ce1-9783-af37a99592e8.png)

Using the information above, you can determine the keywords not present in your content that are closely related to the topic. And by adding those keywords to your content, it will improve the topic relevancy and help your page rank better.

![image](https://user-images.githubusercontent.com/11299574/134666620-b83a3eca-6a45-4afc-84fd-8c84b670f9bd.png)

Once there, all you have to do is paste your content and click Get keyword recommendations. It’ll prompt you for a focus keyword and then voila:

![image](https://user-images.githubusercontent.com/11299574/134666642-d53ed9cd-b0ad-4a4c-a9a2-4eb386320f59.png)

Now it all gets extremely easy. All you have to do is edit your content until you are happy with it.

And that should be more than enough to get you started. See, that wasn’t so bad, was it?

Good luck and happy optimizing with TF*IDF!



### Sources 

* [Onely](https://www.onely.com/blog/what-is-tf-idf/)
