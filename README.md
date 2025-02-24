# Online Supplement to The Perpetuation of the Racialized Ideology of Neighborhood Quality: Evidence From 16 US Rental Markets

## Appendix A. Deduplication

As I worked with this data, it became very clear that duplicate or near-duplicate listings were very common in scraped Craigslist data. Sometimes the listings were for the same unit posted at various points in time, often with the same rent. Just as often, though, the duplicates were postings for different units in the same building, or in different buildings but managed by the same property manager. In some cases the duplicates reflect spam or fraud, where the poster copies the text and pictures from a legitimate advertisement. For many use cases, like for estimating rents for small areal units, these kinds of duplicate listings are not a large problem. Even for my analysis using STM, the model recovers very similar topics when including or not including these duplicates. However, I believe that including the duplicate listings raises two issues for my analysis as a whole, one quantitative and one qualitative. First, quantitatively I believe it is likely that high levels of duplicates are likely to be unequally spread through space: they could be more common in areas with higher rents, since landlords there may repost more often, and in areas with more large multi-family properties, since those areas likely have more nearly-identical postings. Since those features are likely associated with neighborhood socioeconomic status and racialization including the duplicates could bias my estimates.

Qualitatively, I use high-matching texts to interpret the STM output. However, when there are many duplicate or near-duplicate texts, the high-matching texts for each topic tend to be composed of those duplicates. That makes interpreting the topics difficult: I want to identify topic titles and understandings of the topics that can reasonably be generalized to other texts with a high proportion of that topic, but if there are only duplicate texts, I cannot be sure if what I’m reading is about the topic, or just about this particular multi-family building, or a particular landlord or property manager.

For those two reasons, I use a very-greedy deduplication algorithm that excludes almost four fifths of my original 2.5million text sample. Directly comparing all 2.5 million texts to each other is not computationally feasible. Instead, I use a two-step approach which takes advantage of the data structure. First, I deduplicate within addresses: my experience with the data shows that most of the duplicates come from repeated postings of the same unit or similar posts about units in the same building. Comparing within addresses takes care of those kinds of duplicates. I always keep the earliest observed instance of a text. After address deduplication, I use STM itself to ferret out duplicates. When there are duplicates they tend to cluster as the highest-matching texts in a particular topic, I iteratively fit STM models and deduplicate within the top texts for each topic.

The deduplication itself uses the R ​​stringdistmatrix package’s Jaccard distance. I set a threshold of .7 which I arrived at after comparing my own qualitative coding of duplicates to deduplication using various measures of distance at various thresholds. For this use case I found a Jaccard distance of .7 often removed all of the texts I considered to be practically duplicates, while leaving almost all of the texts I considered distinct. I expect that with other corpora, even other corpora of Craigslist listings, the right distance measure and threshold could be quite different.

##

## Appendix B. Topic Description

This paper focuses on two topics out of 50. Appendix Table I includes some details about all 50 topics contained in the model used for the analysis. The nine topics related to neighborhoods, as opposed to unit or lease details, are highlighted below.

Appendix Table I: Topic Descriptions

| **Topic** | **topic title** | Top Words |

| Topic1 | Property Amenities | concierge, conference, valet, lounge, simulator, clubroom, cabanas, grooming, yoga, amenity, billiards, technogym, leed, cardio, trx |

| Topic2 | Appointments and Hours | monday, tuesday, thursday, wednesday, friday, emergency, select, hours, townhomes, patios, saturday, garages, connections, bark, microwaves |

| Topic3 | NYC Area Commute | journal, brunswick, rutherford, jsq, caldwell, fordham, metuchen, seton, njit, palisade, raritan, rahway, cranford, metropark, brkr |

| Topic4 | Walkability | distance, stores, walking, banks, shops, grocery, restaurants, away, farmers, store, joe, markets, within, bakeries, pubs |

| Topic5 | Scenic Views | needle, slu, elliott, elliot, olympics, seward, tableau, melinda, admiral, yesler, pointe, cascades, territorial, century, magnolia |

| Topic6 | Ocean Access | ocean, mahalo, uri, beachfront, kcc, ewa, barracks, ohana, surfboard, hpu, corps, canoe, oceanview, kunia, pupukea |

| Topic7 | Lease Details | signing, month, rent, security, months, due, first, last, year, upfront, total, requires, deposit, upon, lease |

| Topic8 | Parking and Unit Location | condo, unit, spot, secured, condominium, assigned, secure, balcony, complex, reserved, parking, designated, underground, spots, locker |

| Topic9 | On-Site Sports | tennis, courts, court, swimming, pool, basketball, pools, racquetball, playground, volleyball, sauna, spa, clubhouse, spas, resort |

| Topic10 | Section 8 Availability | cargarage, appt, bdrm, duplex, bdr, section, ere, appointment, sec, call, gary, bth, showing, loretta, text |

| Topic11 | Utilities | alll, plowing, snow, removal, numc, floria, eatin, coccia, annadale, bentahar, oil, tottenville, rwu, verdeschi, livingroom |

| Topic12 | Positive Adjectives: Unit | won, see, right, summer, coming, perfect, fall, come, soon, awesome, make, gem, wow, miss, beat |

| Topic13 | Free Standing Homes | house, fenced, yard, shed, single, shotgun, ups, driveway, family, bungalow, hook, back, backyard, unfinished, fence |

| Topic14 | Pet Details | purrr, wooof, turbo, sja, macpherson, redside, sandco, martisa, shinsato, wpm, verraterra, description, terms, eberly, duration |

| Topic15 | Appliances | fans, conditioning, wall, air, ceiling, blinds, refrigerator, fan, microwave, molding, stove, conditioner, ceramic, range, heating |

| Topic16 | Furniture | sofa, linens, mattress, towels, stocked, pots, toaster, utensils, pans, channels, bedding, cookware, sheets, plates, sleeper |

| Topic17 | Least Timing | sublease, takeover, july, sublet, march, min, august, april, dec, transfer, october, earlier, starting, november, february |

| Topic18 | Fees and Deposits | refundable, nonrefundable, adult, insurance, non, damage, pdt, case, application, lbs, holding, processing, brink, charged, liability |

| Topic19 | Lofts and Studios | unhide, studio, urth, posting, studios, deco, loft, lofts, bachelor, vermont, korea, melrose, factory, alcove, ktown |

| Topic20 | Renovations | new, paint, newly, brand, fresh, completely, recently, remodeled, redone, remodel, totally, painted, renovated, freshly, plumbing |

| Topic21 | Architectural Details | doors, sliding, vanity, faucet, enclosure, glass, sink, double, led, shower, french, shelving, porcelain, dispenser, panel |

| Topic22 | Boston Commute | bus, minute, rail, lowell, commuter, stops, miles, merrimack, kenmore, artery, lines, andover, reservoir, hingham, massart |

| Topic23 | Universities and Hospitals | drexel, delaware, ardmore, plymouth, wales, goshen, malvern, forge, abington, darby, villanova, brandywine, hup, radnor, hospital |

| Topic24 | Disclaimers | reusable, comprehensive, race, origin, religion, familial, discrimination, rcw, discriminate, pursuant, prohibits, jmw, consumer, reports, sex |

| Topic25 | Non-Rental: Scams, Offers, Requests | deemed, hyperlink, specialize, ads, obligation, purchase, lender, webpage, consultation, browser, homeownership, copyright, consult, scam, financing |

| Topic26 | Utilities and Parking Included | electricity, pays, sewer, trash, electric, water, sewage, included, plex, paid, utilities, garbage, tenant, except, smoking |

| Topic27 | Driving Distance | canyon, calabasas, saddleback, doheny, pedro, glassell, zaya, palmdale, rowland, danville, ortega, winnetka, springs, talega, freeway |

| Topic28 | High-end Room Size | formal, curb, entertaining, bonus, cape, piece, opens, secondary, berdoom, cod, sliders, colonial, ranch, paver, finished |

| Topic29 | Unit Features | deleaded, medford, applianced, waverley, salem, cushing, watermarked, rentsource, Blackstone, jwu, avl, marescia, sotheby, shilalis, lambergs |

| Topic30 | Contact Information | inquiries, respond, reply, messages, thank, inquires, serious, name, please, message, number, responding, calls, questions, mail |

| Topic31 | Room Count and Layout | washer, dryer, two, one, bedroom, private, three, full, dish, stackable, four, size, bathroom, dyer, den |

| Topic32 | Special Deals | special, ready, hurry, immediate, save, reduced, receive, waived, today, savings, fast, ask, drop, priced, upgrades |

| Topic33 | Roomate/home search | housemate, bit, respectful, stuff, really, hello, roommate, tell, trying, folks, lived, anything, looking, tidy, wanted |

| Topic34 | Modern' Decor | tops, granite, stainless, appliances, steel, counter, countertops, floors, counters, quartz, hardwood, modern, gorgeous, throughout, cherry |

| Topic35 | Boston Brokers | broker, cotter, peterborough, upright, hot, hhw, signature, gtn, valencius, comm, beds, mastercard, bradsfield, beacon, alex |

| Topic36 | Historic Charm | lined, original, ocf, tree, magazine, claw, restored, charm, character, victorian, clawfoot, antique, rowhouse, carriage, classic |

| Topic37 | Chicago Commute | bjb, hermitage, kwgc, rehabbed, welles, rehab, schiller, belden, hoyne, illinois, ukranian, mariano, fultongrace, healy, division |

| Topic38 | Restrictions and Stipulations | ago, consider, taken, rules, owners, noise, tenants, repairs, cleaned, install, portion, disturb, increase, lives, rented |

| Topic39 | Mid-Range Room Size | large, room, closet, living, lots, space, plenty, dining, separate, extra, huge, spacious, storage, ample, closets |

| Topic40 | Garage and Bathroom Counts | townhouse, upstairs, attached, car, garage, level, downstairs, story, townhome, master, opener, upper, fireplace, lower, tri |

| Topic41 | On-Site Community | offer, comfort, furry, variety, convenience, deserve, residents, lifestyle, proud, choose, dip, invite, plans, experience, discover |

| Topic42 | Subject to change without notice | change, notes, vary, staffordshire, represent, chows, prices, availability, subject, presa, terriers, pricing, shepherds, actual, hybrids |

| Topic43 | High-End Unit Descriptions | design, idwm, contemporary, elements, timeless, sophisticated, striking, incorporates, culture, chic, sleek, eclectic, incorporate, refined, elegance |

| Topic44 | Public Transportation Access | apartment, transportation, near, close, yasmine, located, keerah, conveniently, carollo, gesler, public, maintained, beautiful, bedroom, kept |

| Topic45 | High-End Apartment Buildings | uws, skips, flex, stabilized, doorman, streeteasy, trains, windowed, prewar, bochen, crosstown, hell, antagoniste, postwar, net |

| Topic46 | Background and Credit Checks | verifiable, statements, felonies, stub, salary, copies, proof, returns, felony, paycheck, judgments, paystubs, requirement, credit, applicants |

| Topic47 | Schools | elementary, clyde, proctor, finn, chinook, cougar, woodridge, tahoma, kingsgate, tyee, elem, rambler, wedgwood, cumming, school |

| Topic48 | Virtual Tours | alamo, waiver, edwardian, void, contrary, biker, walker, webpass, tours, protocol, walkthrough, golden, cole, japantown, guerrero |

| Topic49 | Anuncios en Español | por, cocina, mes, cerca, sala, grande, dos, piso, disponible, dormitorios, mas, bano, recamaras, esta, tiene |

| Topic50 | Positive Adjectives: Location | location, great, excellent, area, easy, terrific, convenient, open, access, value, prime, ideal, including, areas, friendly |


##

## Appendix C. STM

Topic models can be sensitive to the analyst’s choice of the number of topics. Wilkerson and Casas (2017) outline a method to check whether similar topics are recovered when the number of topics is adjusted. They develop that method for LDA topic models, and I have modified that method to use with STM topic models. For the analysis I use a topic model with 50 topics, for the robustness check I estimate new models with 47-53 topics. I then compare the topic-vocabulary vectors in my 50 topic STM to the topic-word vectors of the six alternative models to see if similar topics were recovered with those choices of K. I show the results below for the two topics I focus on in this paper:

Appendix Table II: Topic Stability With Changes in K

| Topic Name | 47  | 48  | 49  | **50** | 51  | 52  | 53  |

| Historic Charm (36) | 0.99 | 0.99 | 0.98 | **\-** | 0.99 | 0.99 | 0.99 |

| Positive Adjectives: Location (50) | 0.98 | 0.98 | 0.98 | **\-** | 0.98 | 0.98 | 0.98 |


_Green cells are those which have at least one topic with a cosine similarity of >.95 with a topic in the other model. The number is the cosine similarity of the closest match. Some cells show 1.00, but they’re actually just very close. In other words, this analysis suggests that these topics are very stable by this measure across models with other choices of K._

### Appendix D. Triangulation

To further validate the results presented in the main text, I compare the results using the topic model to results based on a set of keywords or search strings that reflect my understanding of Topic 50: Positive Adjectives: Location. To be clear, the expectation is not that results will be identical: the topic model uses every word in the vocabulary to assign its proportions, and my search strings will only use at most 12 words. What I am looking for is that the pattern of the keywords generated by my understanding of the topic roughly align with the results from the topic models. I first reproduce the plot with covariates used in the main analysis. Then I present 1 or more plots that use search strings or keywords I generated. I offer brief comments about the similarities and differences.

Appendix Figure I: Expected Topic Proportion of ‘Positive Adjectives: Location (50)’ by Neighborhood Type

![]

_The expected prevalence of ‘Positive Adjectives: Location (50)’ is on the X axis, while the neighborhood type is on the Y axis. Error bars represent 95% credible intervals. All other covariates held at their means._

Appendix Figure II: Probability of Observing Positive Terms + ‘neighborhood’

![]

_The expected probability of observing the terms is on the X axis, while the neighborhood type is on the Y axis. Error bars represent 95% credible intervals._

The first search string I used for Topic50 looks for a combination of any word with the word ‘neighborhood’. This has similar results to the main finding in that Black neighborhoods have significantly the lowest expected probability of observing that search string. However, Asian neighborhoods, which have a large portion of Topic50, seem to have this search string much less often. I realized that this search string only uses the term ‘neighborhood’ to operationalize the location portion of the topic. So I did an additional test adding the term ‘location.’

Appendix Figure III: Probability of Observing Positive Terms + ‘location’

#### ![]

_The expected probability of observing the terms is on the X axis, while the neighborhood type is on the Y axis. Error bars represent 95% credible intervals._

Adding the term ‘location’ changes the plot so that it looks very much like the topic-generated plot. Interestingly it seems like the high prevalence of the term ‘location’ is what might partially account for the results for Asain neighborhoods.

### Appendix E. HLM

### Mixed Effects Analysis

I use three level mixed-effects models to examine the variation in discourse about neighborhood quality and exclusion across metropolitan areas. For discourse about exclusion, I run three models for each discursive theme, two to assess variation across metropolitan areas and one to assess association with metro-level variables. For discourse around neighborhood quality, I fit five models: all three used for metro-level variance and two more models that estimate random slopes for neighborhood racialization. For more information on these choices and comparisons with frequentist results (which are substantially similar) see Appendix VIII.

As an example of the staged modeling strategy, consider my examination of neighborhood quality. First I examine just the variation in the neighborhood quality topic across metropolitan areas using a model with random intercepts for each metro (not shown). Then I create a similar model that maintains the metro-level intercepts and adds random intercepts for each tract. For models operationalizing discursive features with topic models, the model takes the form shown in (1).

(1)

Where is a metro-level random intercept, and is a tract-level intercept. Both have priors on their means of since the topic prevalence is normalized and demeaned.

Next I model the proportion of the total variance, and of metro-level variance that is accounted for when adding metro-level variables. This model is shown in (2)

(2)

+

Where , , and are as in (1), are a vector of coefficients (with Normal(0,1) priors) and a matrix of metro-level variables. These models so far are used for all of the discursive themes. The two models described below are used only to examine whether the racialization of discourse surrounding neighborhood quality is consistent across metropolitan areas.

I fit two models, both of which add random slopes, nested within metropolitan areas, for the neighborhood typology. One of them includes no other covariates and is not shown. The other is the model shown in (3) and also includes covariates at all three levels.

(3)

+

Where all is as in (2) and is the random slope for each neighborhood type and each metro area, with a prior, where is a covariance matrix with a LKJ Correlation prior with .

In the case of racialized discourse about neighborhood quality, there is some variation in how that language is racialized across metropolitan areas. However, that variation is lessened with the inclusion of tract-level variables. In the fully-specified model all metropolitan areas shared a significant contrast between positive language in Black and White neighborhoods.

Racialized housing dynamics in the US, including segregation and gentrification, are and have historically been tied to racialized notions about housing quality. Redlining was a legal practice whereby neighborhoods were marked nominally by quality, but that conception of quality was strongly driven by racist interpretations of who lived in the neighborhoods (Rothstein 2017). Gentrification also carries implicit notions about what kinds of people make a quality or authentic neighborhood (Rucks-Ahidiana 2021; Hwang 2016). A fuller discussion of this background is available in Chapter 1.

I operationalize descriptions of neighborhood quality by using a topic I label ‘Positive Adjectives: Location (50).’ Advertisements with a high proportion of this topic used phrases like ‘location, location, location’ and ‘great neighborhood’ to emphasize the quality of the neighborhood as a feature of the unit for rent.

I begin by examining how that topic varies in expected prevalence across the 16 metros in my study area. A model with only metro random intercepts, shown in Figure III.5.1 expects ‘Positive Adjectives: Location (50)’ to be most common in New Orleans, San Francisco, and Charlotte, and least common in Riverside and New York. There are no clear patterns based on region and city size. The metro-level random intercepts only account for around 5% of the variation in this topic, lower than for any other discursive theme I investigate.

Appendix Figure IV: Expected Prevalence of Positive Adjectives: Location (50) with Null Specification

![]

Figure IV shows the expected topic prevalence on the y-axis for each metropolitan area on the x-axis in a model with metropolitan-level random intercepts alone.

#####

Looking at Appendix Figure IV, we can see that though the expected values for some metropolitan areas are significantly different from the population mean, those differences are small.

#### Figure III.5.2

![]

##### Figure III.5.2 Caption: Figure III.5.2 shows the expected topic prevalence on the y-axis for each metropolitan area on the x-axis in a model with tract-level random intercepts, metropolitan-level random intercepts, and metropolitan-level covariates

Indeed, adding tract-intercepts and metro-level variables shrinks those differences further, so that none are significantly different from the population mean.

To look at differences in racialization across metropolitan areas, I fit new models with random slopes for each of five neighborhood types: Black, White, Asian, Latinx, and Other.

###

#### Figure III.5.3

![]

##### Figure III.5.3 Caption: Figure III.5.3 shows the expected topic prevalence on the y-axis for each metropolitan area on the x-axis, colored by neighborhood type in a model with tract-level random intercepts, metropolitan-level random intercepts, and neighborhood type random slopes

Looking at a model with random slopes for neighborhood types within each metropolitan area, Figure III.5.3 shows that the variation between neighborhood types is comparable to the variation between metropolitan areas. The estimate for the neighborhood with the highest prevalence in Riverside, the metro with the lowest average prevalence, is higher than the estimate for the neighborhood with the lowest prevalence in Worcester, the metro with the highest average prevalence.

Moreover, there are clear racialized trends here, inline with the findings presented in Chapter 1. White and Asian neighborhoods have consistently the highest point estimates in most metro areas while Black and Latinx neighborhoods have consistently the lowest, with the only exception being Worcester. This suggests that the anti-blackness that was inherent in redlining seems to be embedded in contemporary racialized discourse across this 16 metro sample. Put another way, this consistent racialization is reflective of a more general dynamic in the contemporary United States in which the composition of the neighborhood is erroneously accepted as an indication of its "quality."

#### Figure III.5.4

![]

##### Figure III.5.4 Caption: Figure III.5.4 shows the expected contrast in topic prevalence between a White and a Black neighborhood on the y-axis in each metropolitan area on the x-axis in a model with tract-level random intercepts, metropolitan-level random intercepts, and neighborhood type random slopes

That theme of anti-Blackness is perhaps even more clear looking at the contrasts. All but two metros reflect higher values for White neighborhoods than for Black neighborhoods in terms of ‘Positive Adjectives: Location (50).’ A core question, however, is whether there is something about Worcester and Riverside that helps resist this trend of anti-Blackness, or if these results instead might reflect specificities about those metros that we could account for in our modeling strategy.

#### Figure III.5.5![]

##### Figure III.5.5 Caption: Figure III.5.5 shows the expected topic prevalence on the y-axis for each metropolitan area on the x-axis, colored by neighborhood type in a model with tract-level random intercepts, metropolitan-level random intercepts, neighborhood type random slopes, and listing-, tract-, and metro-level covariates

Figure III.5.5 shows a model where I add socio-economic and housing stock controls at the neighborhood level, and housing policy and segregation at the metro-level. With those variables included in the model as fixed effects, the racialization of ‘Positive Adjectives: Location’ is not only upheld, but in the case of anti-Blackness, may even be more stark. The pattern of Black and Latinx neighborhoods having the lowest expected values, while White or Asian neighborhoods have the highest is also strengthened. However, while the point estimates for Black neighborhoods are significantly lower than for other neighborhoods, the Latinx neighborhood estimates are now not statistically significantly different from other neighborhoods in most metropolitan areas, with the exception of New Orleans, Seattle, and Honolulu.

#### Figure III.5.6

![]

##### Figure III.5.6 Caption: Figure III.5.6 shows the expected contrast in topic prevalence between a White and a Black neighborhood on the y-axis in each metropolitan area on the x-axis in a model with tract-level random intercepts, metropolitan-level random intercepts, neighborhood type random slopes, and listing-, tract-, and metro-level covariates

The size of the difference in the estimates of positive adjectives connected to the neighborhood for White and Black is even clearer when we look at the contrasts: while Worcester and Riverside had higher estimates for Black neighborhoods in the model without covariates, in the full model those metros have estimates near the median. That is likely because the other information about the neighborhoods helped allow for a better estimate of the prevalence and racialization of ‘Positive Adjectives: Location (50).’ Specifically, these tract-level covariates account for compositional and housing stock differences in Worcester and Riverside that likely hid this relationship. Similarly, when accounting for socioeconomic, housing, metro policy, and segregation, the magnitude of these contrasts are smaller, but their variation across metro areas is also smaller.

## Appendix F. Sample

I use Craigslist advertisements from 16 metro areas, spanning from 2017 to 2021. The listings were scraped by the National Rent Project at the University of Washington, and the scraping process changed several times during that period, and was not always the same for all of the metropolitan areas. There are two notable changes over time in the scraping process. First, only listings from Seattle were scraped from late 2017 to early 2019. During that period the project was testing scraping infrastructure. Scraping expanded to 100 metropolitan areas in early 2019, and has continued since then. However, due to a change in the Craigslist platform, we were unable to effectively scrape rents from August 2019 through February 2020. During that period we still successfully scraped listing text and other data, but the rent information is mostly incomplete. Since this paper uses the rent of the listing as a covariate in the regression analysis, I do not include any advertisements from that period which are missing rent information. Finally, the COVID-19 pandemic started in March 2020 and significantly altered rental markets. However, a large portion of the data included in this analysis comes from that period from March 2020 to April 2021, which was COVID-impacted. However, I run a number of robustness checks to confirm that the results do not depend on these aspects of the data.

The results of the regression analysis are consistent if we use the topics presented in the paper but limit the listings included. This is true if I exclude the Seattle advertisements from the period when only Seattle was scraped (2017-early 2019), and if I exclude the advertisements from the COVID-impacted period from March 2020 on. For instance, consider the interaction plot in the paper.

#### Figure A.7

![]

#### Figure A.8

![]

The two plots are nearly identical, though Figure A.8, which used the limited data sample has slightly wider errors. I include the whole regression output for these two models below. Note that there are no changes in sign or significance across the models. The coefficient for the interaction between Black neighborhoods and median income is itself not significant in the limited model, but the interaction as a whole still adds to model fit in that case, and the plot is very similar.

#### Table 2

|     | _Displayed Model_ |     |     | _Model With 2019 February-August Only_ |     |     |
| --- | --- |     |     | --- |     |      --- |
| Predictors | Estimates | CI  | p   | Estimates | CI  | p   |
 --- 
| (Intercept) | \-3.78 | \-3.92 – -3.64 | <0.001 | \-3.52 | \-3.72 – -3.33 | <0.001 |
 --- 
| ntype \[asian\] | 0.23 | \-0.03 – 0.49 | 0.081 | 0   | \-0.38 – 0.38 | 1   |
 --- 
| ntype \[black\] | \-0.49 | \-0.71 – -0.27 | <0.001 | \-0.48 | \-0.76 – -0.20 | 0.001 |
 --- 
| ntype \[latinx\] | \-1.44 | \-1.67 – -1.22 | <0.001 | \-1.44 | \-1.73 – -1.15 | <0.001 |
 --- 
| ntype \[other\] | \-0.61 | \-0.88 – -0.34 | <0.001 | \-0.5 | \-0.85 – -0.15 | 0.005 |
 --- 
| log income | 0.06 | 0.04 – 0.07 | <0.001 | 0.03 | 0.02 – 0.05 | <0.001 |
 --- 
| cbsa \[Urban Honolulu, HI\] | 0.01 | \-0.01 – 0.03 | 0.277 | 0.02 | \-0.00 – 0.04 | 0.091 |
 --- 
| cbsa \[Worcester, MA-CT\] | \-0.03 | \-0.06 – -0.00 | 0.021 | \-0.05 | \-0.09 – -0.02 | 0.001 |
 --- 
| pov proportion | 0.05 | 0.00 – 0.10 | 0.032 | \-0.02 | \-0.09 – 0.04 | 0.461 |
 --- 
| share oo | \-0.12 | \-0.14 – -0.09 | <0.001 | \-0.22 | \-0.25 – -0.19 | <0.001 |
 --- 
| share sf detached | \-0.27 | \-0.28 – -0.26 | <0.001 | \-0.16 | \-0.17 – -0.14 | <0.001 |
 --- 
| share car commuters | \-0.36 | \-0.39 – -0.33 | <0.001 | \-0.35 | \-0.39 – -0.31 | <0.001 |
 --- 
| share commute over 20 | \-0.31 | \-0.34 – -0.28 | <0.001 | \-0.28 | \-0.32 – -0.23 | <0.001 |
 --- 
| share rental over 20 | \-0.31 | \-0.33 – -0.29 | <0.001 | \-0.27 | \-0.30 – -0.25 | <0.001 |
 --- 
| share built before 40 | 0.08 | 0.06 – 0.09 | <0.001 | 0.11 | 0.09 – 0.13 | <0.001 |
 --- 
| share built after 10 | \-0.6 | \-0.65 – -0.56 | <0.001 | \-0.61 | \-0.67 – -0.55 | <0.001 |
 --- 
| share college | 1.43 | 1.38 – 1.48 | <0.001 | 1.4 | 1.34 – 1.46 | <0.001 |
 --- 
| log price | \-0.22 | \-0.22 – -0.21 | <0.001 | \-0.22 | \-0.23 – -0.21 | <0.001 |
 --- 
| beds | 0.05 | 0.05 – 0.05 | <0.001 | 0.05 | 0.05 – 0.06 | <0.001 |
 --- 
| ntype \[asian\] \* log<br><br>income | \-0.02 | \-0.04 – 0.01 | 0.2 | 0.01 | \-0.03 – 0.04 | 0.698 |
 --- 
| ntype \[black\] \* log<br><br>income | 0.02 | 0.00 – 0.04 | 0.025 | 0.02 | \-0.00 – 0.05 | 0.111 |
 --- 
| ntype \[latinx\] \* log<br><br>income | 0.12 | 0.10 – 0.14 | <0.001 | 0.12 | 0.10 – 0.15 | <0.001 |
 --- 
| ntype \[other\] \* log<br><br>income | 0.05 | 0.03 – 0.08 | <0.001 | 0.04 | 0.01 – 0.07 | 0.011 |
 --- 
| Observations | 253744 |     |     | 141316 |     |     |
| --- | --- |     |     | --- |     |      --- |
| R2 / R2 adjusted | 0.135 / 0.135 |     |     | 0.129 / 0.128 |     |     |
| --- | --- |     |     | --- |     |      --- |

## Appendix G. Regression Tables

Model Used to Produce Figure 1:

|     | _Bivariate Model_ |     |
| --- | --- |     | --- |
| Covariate | Estimate (SD) | 95% PI Range |

| Intercept | 0.64 (0.001) | 0.64 to 0.64 |

| ntype\[Latino\] | \-4.89 (0.002) | \-4.89 – -4.888 |

| ntype\[Black\] | \-4.85 (0.005) | \-4.86 – -4.843 |

| ntype\[Asian\] | \-5.2 (0.004) | \-5.21 – -5.195 |

| ntype\[White\] | \-5.17 (0.003) | \-5.18 – -5.165 |

| ntype\[Other\] | \-5.01 (0.005) | \-5.02 – -5.006 |

| Observations | 253744 |     |
| --- | --- |     | --- |

Model Used to Produce Figure 2:

| Covariate | Estimate (SD) | 95% PI Range |

| sigma | 0.6 (0.001) | 0.6 – 0.606 |

| a_nhtype\[Latino\] | \-1.99 (0.157) | \-2.28 – -1.679 |

| a_nhtype\[Black\] | \-1.92 (0.157) | \-2.22 – -1.618 |

| a_nhtype\[Asian\] | \-2.22 (0.156) | \-2.51 – -1.91 |

| a_nhtype\[White\] | \-2.08 (0.157) | \-2.37 – -1.766 |

| a_nhtype\[Other\] | \-2.03 (0.157) | \-2.32 – -1.719 |

| Proportion of Residents Below the Poverty Level | 0.01 (0.024) | \-0.04 – 0.056 |

| Share Owner Occupied Housing | \-0.12 (0.011) | \-0.14 – -0.094 |

| Median Household Income | 0.07 (0.006) | 0.06 – 0.083 |

| Share Single Family Detatched Homes | \-0.27 (0.005) | \-0.28 – -0.26 |

| Share Car Commuters | \-0.36 (0.015) | \-0.39 – -0.328 |

| Share Commute > 20 Mins | \-0.3 (0.018) | \-0.33 – -0.263 |

| Share Rentals in Buildings with >20 Units | \-0.31 (0.009) | \-0.33 – -0.292 |

| Share built before 1940 | 0.08 (0.006) | 0.07 – 0.092 |

| Share Built after 2010 | \-0.58 (0.023) | \-0.63 – -0.539 |

| Share College Graduate or More | 1.41 (0.024) | 1.36 – 1.451 |

| Logged Unit Rent | \-0.22 (0.003) | \-0.22 – -0.211 |

| Number of Bedrooms | 0.05 (0.001) | 0.05 – 0.052 |

| a_metro\[1\] | \-1.99 (0.157) | \-2.28 – -1.679 |

| a_metro\[2\] | \-1.92 (0.157) | \-2.22 – -1.618 |

| a_metro\[3\] | \-2.22 (0.156) | \-2.51 – -1.91 |

| a_metro\[4\] | \-2.08 (0.157) | \-2.37 – -1.766 |

| a_metro\[5\] | \-2.03 (0.157) | \-2.32 – -1.719 |

| a_metro\[6\] | \-1.93 (0.15) | \-2.22 – -1.642 |

| a_metro\[7\] | \-1.98 (0.15) | \-2.27 – -1.688 |

| a_metro\[8\] | \-1.79 (0.15) | \-2.08 – -1.498 |

| a_metro\[9\] | \-2.18 (0.15) | \-2.47 – -1.893 |

| a_metro\[10\] | \-2.15 (0.151) | \-2.44 – -1.86 |

| a_metro\[11\] | \-2.04 (0.15) | \-2.33 – -1.749 |

| a_metro\[12\] | \-1.99 (0.15) | \-2.28 – -1.704 |

| a_metro\[13\] | \-1.89 (0.15) | \-2.18 – -1.599 |

| a_metro\[14\] | \-2.28 (0.15) | \-2.57 – -1.988 |

| a_metro\[15\] | \-2.04 (0.15) | \-2.33 – -1.743 |

| a_metro\[16\] | \-2.01 (0.15) | \-2.3 – -1.721 |

| Observations | 253744 |     |
| --- | --- |     | --- |

Model Used to Produce Figure 3:

|     | _Interaction Model_ |     |
| --- | --- |     | --- |
| Predictors | Estimates | PI  |

| (Intercept) | \-3.78 | \-3.92 – -3.64 |

| ntype \[asian\] | 0.23 | \-0.03 – 0.49 |

| ntype \[black\] | \-0.49 | \-0.71 – -0.27 |

| ntype \[latinx\] | \-1.44 | \-1.67 – -1.22 |

| ntype \[other\] | \-0.61 | \-0.88 – -0.34 |

| log income | 0.06 | 0.04 – 0.07 |

| cbsa \[Urban Honolulu, HI\] | 0.01 | \-0.01 – 0.03 |

| cbsa \[Worcester, MA-CT\] | \-0.03 | \-0.06 – -0.00 |

| pov proportion | 0.05 | 0.00 – 0.10 |

| share oo | \-0.12 | \-0.14 – -0.09 |

| share sf detached | \-0.27 | \-0.28 – -0.26 |

| share car commuters | \-0.36 | \-0.39 – -0.33 |

| share commute over 20 | \-0.31 | \-0.34 – -0.28 |

| share rental over 20 | \-0.31 | \-0.33 – -0.29 |

| share built before 40 | 0.08 | 0.06 – 0.09 |

| share built after 10 | \-0.6 | \-0.65 – -0.56 |

| share college | 1.43 | 1.38 – 1.48 |

| log price | \-0.22 | \-0.22 – -0.21 |

| beds | 0.05 | 0.05 – 0.05 |

| ntype \[asian\] \* log<br><br>income | \-0.02 | \-0.04 – 0.01 |

| ntype \[black\] \* log<br><br>income | 0.02 | 0.00 – 0.04 |

| ntype \[latinx\] \* log<br><br>income | 0.12 | 0.10 – 0.14 |

| ntype \[other\] \* log<br><br>income | 0.05 | 0.03 – 0.08 |

| Observations | 253744 |     |
| --- | --- |     | --- |
