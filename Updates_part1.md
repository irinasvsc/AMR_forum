This changes were decided a few months ago: 


•  If the sentence contains a “yes/no” answer to a previous question/statement, then “yes/no” are omitted from the annotation, e.g.:

```lisp
(t / true
  :domain (t2 / that))
```  

"Yes , that is true."

•	In case of negative indefinite pronouns like “nobody”, “no one”, “nothing”, you should use the surface forms of the pronouns (and not break down into polarity – and positive pronoun form, e.g. anything :polarity -), e.g.:

(s / sleep-01
:arg0 (n / no-one))

no one is sleeping

(n / nobody
:arg1-of (l / like-01
:arg0 (i / i)))

there is nobody that i like

•	The generic pronoun “one” should be annotated as a concept in itself and not be normalized to “person”, e.g.:

(r / recommend-01
  :ARG1 (t / try-01
          :ARG0 (o / one)
          :ARG1 (t2 / this)))

One should try this.

•	If you have structure like “to me/you …” (meaning “in my/your opinion”), the you should use opine-01, e.g.:

(o / opine-01
  :arg0 y
  :arg1 (e / engineer
          :domain i
          :mod only))

To you, I am only an engineer.

•	At the moment, the sentences should be considered self-contained and annotated as such. This means annotating only the content within the boundaries of the sentence. However, if elliptic nature of the sentence would lead to an incomplete/inaccurate annotation, the previous sentence(s) should be considered. E.g.:

Case 1:

    Previous sentence: He said, "Yes.
    Current sentence: That's true.

>> In this case the content of the second sentence suffices and concepts from the previous sentence are not needed.

Case 2:

    Previous sentence: Wait?
    Current sentence: For what?

>> In this second case, the predicate wait-01 from the previous sentence is needed in order to correctly reflect the argument structure implied by “for”:

(w / wait-01
  :ARG2 (a / amr-unknown))


•	If the sentence contains exclamations reflecting a person’s emotions, then you should use :mode expressive

E.g.: outch!, wow!, hmm, oh, d'uh! etc.

:mode expressive doesn’t cover onomatopoeia or other interjections.

•	If you encounter the prefixes “anti-” and “pro-”, you should use the following to annotate them

>> oppose-01 – for political/opinion use of “anti”, as in “an anti-Syrian journalist” (i.e. journalist who opposes Syria)
>> counter-01 - when there is an implied action/force (destroy, prevent), as in “anti-virus program”

For some verbs, there is a core :ARG already available, as in “an anti-Assad fighter”: 

person 
     :ARG0-of fight-01 
            :ARG1 Assad

>> favor-01 (for “pro”), as in “pro-road position”

•	The epistemic use of “must” should be annotated as follows:

    (i / infer-01
      :ARG1 (s / sick
                 :domain p)
      :ARG2 (b / be-located-at-91 :polarity -
                 :ARG1 (p / person :name (n / name :op1 "John"))
                 :ARG2 (h / here)))

“John isn't here, he must be sick.”
