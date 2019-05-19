## Different distances

* Euclidean
  * EuclideanDistance(x, xi) = `sqrt( sum( (xj – xij)^2 ) )`
  * Usually used when type of input variables are same (width, height for eg)
  * Is invariant to any rotation. It'll remain same in all directions. 

* Manhattan
  * Manhattan (x,xi) = `sum( abs(xj - xij) )`
  * Used more often when different input variables to manhattan distance are of different types (age, gender, etc). This is because if different inputs have very different ranges (and you're not normalising), then euclidean would dominate the ones having bigger ranges of values. Manhattan will at least reduce that effect!
  * Actually, to be honest, this is not used much. Mostly prefer euclidean only, unless above case. 

* Minkowski
  * This is generalised version of Euclidean and Manhattan. In Euclidean, n = 2, In Manhattan, n = 1. 

* Hamming
  * For strings it is how many characters have mismatch in total. In binary numbers, the number of bits where mismatch is there.
  * This is generally only used for finding distances between two points whose features are categorical in nature!
  * **simple matching coefficient** : this is basically now -- number of attributes/features that are same divided by number of total attributes
    * Example : If rows are users, and features are gender, race and country of origin. Then if i1 and i2's gender and race match, then it would be 2/3. 

* Jaccard
  * The simple matching coefficient introduces a big problem. 
    * Example : If rows are users, features are each movie if they've watched it (binary variable).
    * Now, if you calculate SMC, and there are 10000 movies, then only say 4 movies might be commonly watched and say 9950 of them both haven't seen and rest seen by either people, so SMC would be (9950+4)/10000 
    * The problem here is that it's not good measure. Because users are not actually similar because they haven't watched so many movies. 
    * This is where Jaccard comes in!
  * Jaccard in above case would be --- `( num of movies both have watched / (num_movies_1_watched + num_movies_2_watched - num_movies_both_watched) )`
  * Jaccard is basically intersection / overlap. 

* Cosine
  * dot product of two vectors divided by product of their magnitudes
  * In case of text / NLP stuff, we use this because we're concerned with word existence just as much we're concerned with word counts. 
  

### Notes

**Why/When to use cosine over euclidean?** 
OR, why is cosine used in document similarity instead of euclidean? 

See, vectors = magnitude + direction. Cosine is direction related similarity. Euclidean is distance releated similarity.

Direction is the "preference" / "style" / "sentiment" / "latent variable" of the vector, while the magnitude is how strong it is towards that direction.

When classifying documents we'd like to categorize them by their overall sentiment, so we use the angular distance.

Euclidean distance is susceptible to documents being clustered by their L2-norm (magnitude, in the 2 dimensional case) instead of direction. I.e. vectors with quite different directions would be clustered because their distances from origin are similar.  

**When mix of categorical and numerical features** 

distance final = α.distance numeric + (1- α).distance categorical

We decide alpha on our own.
