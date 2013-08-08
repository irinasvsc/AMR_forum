These changes are those listed in the offline file <em>AMR guidelines updates_part 2</em>:


•  Use of have-org-role-91

There is a new frame available, called <code>have-org-role-91</code>, which should be used when you have to annotate the position a person holds within an organization or that an entity is a member of an organization. This role is meant to cover all situations of membership/position within org that were previously annotated using :poss or :mod. 

```
(h / have-org-role-91
   :arg0 [role/office/function holder]
   :arg1 [organization]
   :arg2 [role/office/function])
```

Below you can find a few examples, but you should also check out the frame in the tool:

```
(h / have-org-role-91
  :ARG0 (p / person :name (n / name :op1 "Obama"))
	:ARG1 (c/ country: name (n2/ name :op2 “US”))
 	:ARG2 (p2 / president))

US President Obama

(h / have-org-role-91
  :ARG0 (c / country :name (n / name :op1 "Spain"))
  :ARG1 (m / military :name (n2 / name :op1 "NATO"))
  :ARG2 (m2 / member))

Spain is a member of NATO.


•	Expressing mathematical calculations using equal-01
If you have sentences containing mathematical calculation, you can use the frame equal-01, plus the concepts sum-of and product-of:
 
Three and two make five.
 
The sixth planet was ten times larger than the last one.

•	Reification of the role :quant
The reified version of :quant is have-quant-91.

•	Annotation of epistemic "must"
There are cases in which “must” doesn’t convey obligation or duty, rather it is used to make an inference based on an existing state, like in the sentence: “John isn't here, he must be sick”. In such cases, you should use the frame infer-01, as in the example below:
    (i / infer-01
      :ARG1 (s / sick
                 :domain p)
      :ARG2 (b / be-located-at-91 :polarity -
                 :ARG1 (p / person :name (n / name :op1 "John"))
                 :ARG2 (h / here)))

•	Annotation of location names within names of entities
This is usually an issue when references to a certain facility are made using the name of the city/region they are located in (so-called cases of metonymy).
 If the actual concept of the facility is mentioned together with the location in which it is based, then the NE is annotated as the location:
          :instrument(b / build-01
                    :ARG0 c
                    :ARG1 (s2 / station
                            :poss c2
                            :ARG0-of (p / power-01
                                       :mod (a / atom))
                            :location (c3 / city
                                        :name (n6 / name
                                                :op1 "Bushehr")))))
Ecological organization Greenpeace stated on June 21, 2002 that Russia helped Iran to develop nuclear weapons by building Iran's Bushehr atomic power station.
If the name of the location is used to refer to the facility/object itself, then you should annotate only the facility, with the given name:
(s / say-01
  :ARG0 (e / expert)
  :ARG1 (p / possible
          :domain (o / operate-01
                    :ARG1 (f / facility
                            :name (n / name
                                    :op1 "Bushehr"))
                    :time (d / date-entity
                            :year 2003
                            :month 9
                            :mod (e2 / early)))
          :prep-in (t / theory)))
Experts say Bushehr could in theory become operational as early as September 2003.

•	Annotation of “mass destruction”
In phrases like “weapons of mass destruction”, “mass” should be annotated using the role :degree under the predicate.

•	Use of monetary-quantity as generic entity type
Whenever you have such concepts like “ad spending”, “the price for …”, you can use monetary-quantity, to which you then link the predicate using the appropriate arguments, instead of using the generic “thing”.
 (b / become-01
            :ARG1 (p2 / plan
                  :ARG0-of (g / give-01
                        :ARG1 (t / thing
                              :ARG2-of (d / discount-01))
                        :ARG2 (c7 / company
                              :ARG0-of (a3 / advertise-01))
                        :ARG1-of (c8 / cause-01
                              :ARG0 (o / or
                                    :op1 (m2 / maintain-01
                                          :ARG0 c7
                                          :ARG1 (m3 / monetary-quantity
                                                :ARG3-of (s / spend-01
                                                      :ARG0 c7
                                                      :ARG1 (a4 / advertise-01))))
                                    :op2 (i / increase-01
                                          :ARG0 c7
                                          :ARG1 m3)))))
Plans that give advertisers discounts for maintaining or increasing ad spending have become permanent fixtures at the news weeklies.

•	Annotation of parentheticals with relevant content
There are cases when the information enclosed within parentheses actually adds content to the sentence, as opposed to conversion of monetary-quantity and abbreviations. In such cases, the content is annotated as any other concept outside the brackets. If, however, the content explains the phrase preceding it, then you should use a recently introduced role, :meaning (reification: mean-01), as in the sentence below:
     (r / reply-01
           :ARG0 (h / he)
           :ARG1 (s / she)
           :ARG2 (f / flame
                 :ARG0-of (m / mean-01
                       :ARG1 (e / email
                             :ARG0-of (i / insult-01)
                             :domain (h2 / hostile)))))

"He replied to her with a flame (a hostile and insulting email)."

•	Annotation of ordinals


If you have ordinals like “first”, “second” etc., you should use the new :ord role (you will find more info in the Roles window, including examples)

     (v / visit-01
           :ARG0 (w / we)
           :ord (o / ordinal-entity :value 1
                 :range (t / temporal-quantity :quant 10
                       :unit (y / year))))

our first visit in 10 years




•	Annotation of “global”

“global” should be annotated as “globe”


•	Annotation of “cross-border”

If you have phrases like “cross-border”, “cross-straits”, you should break down the phrase and use the frame cross-02.


•	Annotation of “approximately”

In the end, it has been decided that we should stick to “approximately”, followed by :op1, instead of using approximate-01, as in the example below:

(c / cost-01
      :ARG1 (p / project)
      :ARG2 (a / approximately
            :op1 (m / monetary-quantity :quant 51000000000
                  :unit (r / rupee))))

The project will cost approximately 51 billion rupees.


•	Annotation of "or" as an alternative way of expressing parenthetical equivalence

If you come across sentences like “The deal states Iran will supply 5.5 billion cubic meters or 194 trillion cubic feet of gas annually from 2011.”, in which the entity after “or” (in this case “194 trillion cubic feet”) doesn’t bring any extra meaning, then you should annotate just the first element, the one preceding the “or” (similar to the approach on semantically irrelevant parenthetical conversions).

•	Annotation of ideologies and sports
If you come across sports/martial arts like “tai chi”, “meihuazhuang” or names of movement/ideologies like Marxism, Maoism etc., then you should annotate them as common nouns.
•	Annotation of non-exact regions, identified based on cardinal points

If you have phrases like “southern Philippines”, in which case the phrase cannot be annotated as a single named entity (as is the case with “Southern France” for example), then you should use “south”, “east” etc., :part-of country_concept, as in the sentence below:

(r / remove-01
  :ARG1 …
  :ARG2 (s / south
          :part-of c2))

U.S. military trainers are aiding officials in the Philippines in attempting to remove Islamic guerrillas from the southern Philippines.


•	Annotation of “therefore”.

“therefore” should be annotated using either "cause-01" or "infer-01", depending on the case at hand. Please see the sentence below:

(s / state-01
      :ARG0 (p / person :name (n / name :op1 "Ali" :op2 "Asghar" :op3 "Soltanieh"))
      :ARG1 (i / infer-01
            :ARG1 (h / have-subevent-91 :polarity -
                  :ARG1 (j / jurisdiction
                        :poss (o / organization :name (n4 / name :op1 "International" :op2 "Atomic" :op3 "Energy" :op4 "Agency")))
                  :ARG2 a)
            :ARG2 (c / cover-01
                  :ARG0 (s2 / study-01
                        :ARG1 (w / weaponize-01
                              :ARG0 (c2 / country :name (n2 / name :op1 "Iran")))
                        :ARG1-of (a2 / allege-01))
                  :ARG1 (a / activity
                        :mod (n3 / nucleus)
                        :mod (s3 / strict :polarity -)))))

Ali Asghar SOLTANIEH stated that the alleged alleged Iranian weaponization studies covered activities that were not strictly nuclear and therefore did not fall under International Atomic Energy Agency jurisdiction.


•	Annotation of “domestic”

“domestic” should be annotated as such, the tool suggestion that you should use “dwelling“ should be ignored.


•	Choosing :age over :duration

Whenever you have an “N-year-old”/”N years old” construction, you should also use :age (or its reification), instead of :duration (even for building, laws etc.)
