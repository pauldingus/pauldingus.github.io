---
name: South Carolina Voting Accessibility
tools: [R, Geospatial]
image: /assets/images/Low_Density_Prop_Black.jpg" caption="EuroSat image data
description: Investigating whether there are racial disparities in polling place accessibility in South Carolina.
---

# Investigating Geographic Voting Accessibility in South Carolina 

&nbsp;

<p>
{% include elements/button.html link="https://github.com/pauldingus/south-carolina-voting-accessibility" text="View the Code on GitHub" %}
</p>

&nbsp;

In 2019, I volunteered with a congressional candidate in a special election in North Carolina. When voting neared, our campaign had to petition the state courts to redo the distribution of polling places, as it was fairly skewed towards more polling places in republican-voting areas. While this was a fairly straightforward case in North Carolina (it being a special election, the polling places were fewer than normal), it got me to thinking: are there more general cases of bias in polling station placement? I chose to look into South Carolina's placement, as a state with a large black population, and a history of voter suppression. In this project, I seek to answer whether there is any difference in *geographic* voting accessibility – i.e, are black populations further from their closest polling places on average? It's important to note that I didn't look into other aspects of accessibility, just a naïve analysis of proximity.

### The Analysis

#### *The Data*

As with many cases involving voting district geographic data, half the challenge here was just getting the correct data. Thank you to ____ for going through the effort of making available address lists of U.S. polling places in every state for the 2018 election. You can access them [here](https://github.com/PublicI/us-polling-places).


