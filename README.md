## Naive Bayesian Classification

[![Build Status](https://travis-ci.org/drzippie/bayesian.svg)](https://travis-ci.org/drzippie/bayesian)

Perform naive Bayesian classification into an arbitrary number of classes on sets of strings.
------------
 
### Features

- Conditional probability and "log-likelihood"-like scoring.
- Underflow detection.
- Simple persistence of classifiers.
- Statistics.

------------
### Example

To use the classifier, first you must create some classes
and train it:

    import . "bayesian"

 
    
    classifier := NewClassifier(`Good`, `Bad`)
    goodStuff := []string{"tall", "rich", "handsome"}
    badStuff  := []string{"poor", "smelly", "ugly"}
    classifier.Learn(goodStuff, `Good`)
    classifier.Learn(badStuff,  `Bad`)


    classifier.AddOption(`Normal`)
    normalStuff  := []string{"normal", "usual", "common"}
    classifier.Learn(normalStuff,  `Normal`)



Then you can ascertain the scores of each class and
the most likely class your data belongs to:

    scores, likely, _ := classifier.LogScores(
                            []string{"tall", "girl"}
                         )

Magnitude of the score indicates likelihood. Alternatively (but
with some risk of float underflow), you can obtain actual probabilities:


    probs, likely, _ := classifier.ProbScores(
                            []string{"tall", "girl"}
                         )

Use wisely.


## License
Forked: https://github.com/jbrukh/bayesian
 
Copyright (c) 2011. Jake Brukhman. (jbrukh@gmail.com).
All rights reserved.  See the LICENSE file for BSD-style
license.
