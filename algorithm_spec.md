# Crvngs Recommendation Algorithm
We need some way to recommend recipes. We'll break this down into three major segments: recipe/meal identification and classification, user profile creation, and the process of matching the aforementioned identities: recipe and user. A brief rundown of how each will be implemented: 

    1) The original text for recipes/meals will be run through ChatGPT, which will be tasked with attaching scores to the recipe along various metrics, to be elaborated later. This process may be run a few times and averaged to account for any discrepancies that might occur during inference.
    2) User profiles and tastes will be updated based upon recipe profiles which they swipe to accept or reject. In addition to the binary user choice made per recipe, temporal, and, potentially - geographic (of course contingent upon user permission) - data will be recorded for recommendation purposes. 
    3) RL...? 

## Recipe ID
This section is quite straightforward, and is what is powered by **_ChatGPT_** (oooh ahhh). Recipes will be converted through the LLM into a vector of information, consisting of, but not limited to (list in progress):

    - Sweet, salty, sour, bitter, umami, spice (each of these will be a separate point.)
    - Cost
    - Cuisine type / culture
    - Estimated preparation time 
    - Dietary restrictions
    - Time of day most associated with meal

Additionally, the following metrics can likely be extracted from the recipes in a less sophisticated manner:

    - Cost
    - Estimated prep time
    - Dietary restrictions/allergies

Note the significant (currently complete) overlap between the two categories. The way in which this architecture will work is to use the ChatGPT metrics in a softer manner to generate recommendations, and then apply the latter metrics in more of a filter-based system (moreso user-specified, as a filter).

## User ID
User profiles will be constructed from an initial set of questions posed, including but not limited to:

Once this is done, user profiles will be updated based on the recipes which they like and dislike. As a first starting point, since the recipe profiles are relatively low-dimensional, we can simply track liked and disliked recipes and perform a nearest neighbors search through the database

## Matching Process 
Markov decision process
Bandit problem (k-armed bandit)
Available Ingredients
Explore / Exploit (give em somethin random occasionally)
