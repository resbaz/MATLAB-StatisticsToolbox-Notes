# MATLAB Statistics Toolbox Course Notes

This is a true story illustrating the misuse of statistics

In 1968 the case *People v. Collins*, was heard by the California Supreme Court. Here are the facts of the case as presented in the court decision (68 Cal. 2d 319, 438 P.2d 33, 66 Cal. Rptr. 497 (1968) [online here](http://www.law.harvard.edu/publications/evidenceiii/cases/people.htm)):


> On June 18, 1964, about 11:30 a.m. Mrs. Juanita Brooks, who had been shopping, was walking home along an alley in the San Pedro area of the city of Los Angeles. She was pulling behind her a wicker basket carryall containing groceries and had her purse on top of the packages. She was using a cane. As she stooped down to pick up an empty carton, she was suddenly pushed to the ground by a person whom she neither saw nor heard approach. She was stunned by the fall and felt some pain. She managed to look up and saw a young woman running from the scene. According to Mrs. Brooks the latter appeared to weigh about 145 pounds, was wearing “something dark,” and had hair “between a dark blond and a light blond,” but lighter than the color of defendant Janet Collins’ hair as it appeared at the trial. Immediately after the incident, Mrs. Brooks discovered that her purse, containing between $35 and $40, was missing.


> About the same time as the robbery, John Bass, who lived on the street at the end of the alley, was in front of his house watering his lawn. His attention was attracted by “a lot of crying and screaming” coming from the alley. As he looked in that direction, he saw a woman run out of the alley and enter a yellow automobile parked across the street from him. He was unable to give the make of the car. The car started off immediately and pulled wide around another parked vehicle so that in the narrow street it passed within six feet of Bass. The latter then saw that it was being driven by a black male, wearing a mustache and beard.


A few days after the incident the Los Angeles police arrested two suspects, Malcolm Ricardo Collins, and his wife, Janet on the basis that the the couple fit the description of the man and woman who committed the robbery. 
The evidence against the couple was minimal. Neither of two witnesses were able to positively identify Malcolm or Janet Collins as the driver or perpetrator. 

The case seemed unlikely to win, until the prosecution made the following 'mathematical' argument in favor of conviction. 

A witness, described only as an "instructor of mathematics at a state college", testified that the fact that the defendants were “a Caucasian woman with a blond ponytail ... [and] an African American with a beard and mustache” who drove a partly yellow automobile was enough to convict the couple. As proof, the prosecution presented this table, quoted here verbatim from the supreme court decision:

| Characteristic | Individual Probability |
| -- | -- |
| Partly yellow automobile | $$\frac{1}{10}$$ |
| Man with mustache  | $$\frac{1}{4}$$ |
| African American man with beard  | $$\frac{1}{10}$$ |
| Girl with ponytail  | $$\frac{1}{10}$$ |
| Girl with blond hair  | $$\frac{1}{3}$$ |
| Interracial couple in car |  $$\frac{1}{1000}$$ |

The math instructor called by the prosecution concluded that the chances of a couple fitting all these distinctive characteristics are 1 in 12 million. Accordingly, he said, one could infer that the chances that the couple was innocent were 1 in 12 million.

The jury bought it and convicted the couple.

(The conviction was later overturned)