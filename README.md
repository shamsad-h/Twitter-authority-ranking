# Twitter-authority-ranking

This notebook demonstrates a technique for discovering the most authoritative users on Twitter for a given topic.

The method falls into three parts:

1) Calculate the general authority for any given user

i) This is done using a dynamically scaling h-index algorithm.

2) Discover relevant users for a given topic

i) Given the limitations of downloading and analysing large volumes of tweets via the API, an alternative heuristic to discovering users tweeting about a given topic has been implemented, specifically using User-created Lists as a kind of wisdom-of-crowds approach.

ii) Unfortunately, the Twitter API does not expose Lists. As a workaround, the notebook demonstrates how you can scrape an online service that indexes Lists.

3) Commbining (1) and (2), calculate the topical authority of those users and rank them.

i) The Lists are weighted relative to each other based on the idea that a List is more valuable if it has a high number of subscribers (implicit community approval) and few members (implicitly more highly curated).

ii) Using that weighting, look for Users who appear in at least two lists. This is done on the assumption that such Users are more likely to be significant on that topic, and is also done to reduce the number of tweets that would need to be downloaded to calculate their authorities as per (1).

Avenues for future testing:

* The major limitation of this method as demonstrated is in (2). While I believe the analysis of Lists is a sound method in theory (based on a pseudo-wisdom of crowds principle), the inability to search for Lists via the API is problematic, and the scraped service provides dubious results.

* A better way to find Lists might be via scraping search engine results.

* A more sophisticated analysis of the Users in the Lists could be performed (replacing 3.ii), such as by looking at their interpersonal interactions.
