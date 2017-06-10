Dog Age to Human Age Pitch
========================================================
author: Larry Belvin
font-family: 'Helvetica'
date: June 9, 2017
autosize: true

Convert Dog Age to Human Age
========================================================

- User selects a dog's breed and a dog's age
- Shiny App converts the dog's age to an equivalent human age
- Display shows the human age and a picture of the dog
- Conversion calculation takes two factors into account:
    - Dog's weight (smaller dogs live longer than larger dogs)
    - Dog's breed (some breeds live longer than others)

Details About the Shiny App
========================================================

- The breeds listed are the 20 most popular breeds in 2016
    - Most popular as defined by the American Kennel Club (AKC):
    - http://www.akc.org/content/news/articles/most-popular-dog-breeds-full-ranking-list/

- Dog Age to Human Age
    - Main source - Wikipedia - "Aging in dogs":
    - https://en.wikipedia.org/wiki/Aging_in_dogs
    - Other sources:
        - AKC:
        - http://www.akc.org/content/entertainment/articles/how-to-calculate-dog-years-to-human-years/
        - Dog Age to Human Age PHP Web App:
        - http://www.ajdesigner.com/fl_dog_age/dog_age.php

Sample Code
========================================================
- Convert a dog age of 10 to human age for a small dog:

```r
# Convert dog age to human age for dog weight class A (0 - 20 lbs.).
HumanAgeFromDogWeightClassA <- function(dog_age, slope_adj_factor)
{
  if (dog_age < 2.0) {
    human.age <- 0.0
  } else if (dog_age <= 6.0) {
    human.age <- 22.0 + 4.5 * slope_adj_factor * (dog_age - 2.0)
  } else if (dog_age <= 20.0) {
    human.age <- 40.0 + 4.0 * slope_adj_factor * (dog_age - 6.0)
  } else {
    human.age <- 0.0
  }
}
human_age <- HumanAgeFromDogWeightClassA(10, 1.0)
cat('Human Age: ', human_age, '\n')
```

```
Human Age:  56 
```

Shortcomings / Next Steps
========================================================
- Dog ages have more variation than human ages
    - The oldest verified human was 122:
    - https://en.wikipedia.org/wiki/Oldest_people
        - It is not uncommon for humans to live to 100; 100 is 82% of 122
    - The oldest verified dog was 29:
    - https://en.wikipedia.org/wiki/List_of_oldest_dogs
        - It is uncommon for dogs to live to 20; 20 is only 69% of 29
    - That is one reason it is hard to meaningfully map dog ages to human ages

- Some of the dog images are distorted:
    - I simplified the code by using the same size for all pictures
    - Proposed improvement - use the inherent size of the image
