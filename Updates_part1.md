These changes are also mentioned in the offline file <em>AMR guidelines updates</em> you received a few months ago: 



•  If the sentence contains a <b>“yes/no”</b> answer to a previous question/statement, then “yes" and "no” are omitted from the annotation, e.g.:

```lisp
(t / true
  :domain (t2 / that))
```  
<em>"Yes , that is true."</em>


•	In case of negative indefinite pronouns like “<b>nobody</b>”, “<b>no one</b>”, “<b>nothing</b>”, you should use the surface forms of the pronouns (and not break down into polarity – and positive pronoun form, e.g. anything :polarity -), e.g.:

```lisp
(s / sleep-01
:arg0 (n / no-one))
```

<em>no one is sleeping</em>

```lisp
(n / nobody
:arg1-of (l / like-01
:arg0 (i / i)))
```

<em>there is nobody that i like</em>


•	The generic pronoun “<b>one</b>” should be annotated as a concept in itself and not be normalized to “</b>person</b>”, e.g.:

```lisp
(r / recommend-01
  :ARG1 (t / try-01
          :ARG0 (o / one)
          :ARG1 (t2 / this)))
```

<em>One should try this.</em>


•	If you have structures like “<b>to me/you</b> …” (meaning “in my/your opinion”), then you should use opine-01, e.g.:

```lisp
(o / opine-01
  :arg0 y
  :arg1 (e / engineer
          :domain i
          :mod only))
```

<em>To you, I am only an engineer.</em>


•	At the moment, the sentences should be considered self-contained and annotated as such. This means annotating only the content within the boundaries of the sentence. However, if the elliptic nature of the sentence would lead to an incomplete/inaccurate annotation, the previous sentence(s) should be considered. E.g.:

Case 1:

    Previous sentence: <em>He said, "Yes.</em>
    Current sentence: <em>That's true.</em>

> In this case the content of the second sentence suffices and concepts from the previous sentence are not needed.

Case 2:

    Previous sentence: <em>Wait?</em>
    Current sentence: <em>For what?</em>

> In this second case, the predicate wait-01 from the previous sentence is needed in order to correctly reflect the argument structure implied by “for”:

```lisp
(w / wait-01
  :ARG2 (a / amr-unknown))
```


•	If the sentence contains exclamations reflecting a person’s emotions, then you should use :mode expressive

E.g.: <em>outch!</em>, <em>wow!</em>, <em>hmm</em>, <em>d'uh!</em> etc.

:mode expressive doesn’t cover onomatopoeia or other interjections.


•	If you encounter the prefixes “<b>anti<b>-” and “<b>pro</b>-”, you should use the following to annotate them:

oppose-01 – for political/opinion use of “anti”, as in “an anti-Syrian journalist” (i.e. journalist who opposes Syria)
counter-01 - when there is an implied action/force (destroy, prevent), as in “anti-virus program”

For some verbs, there is a core :ARG already available, as in “an anti-Assad fighter”: 

```lisp
person 
     :ARG0-of fight-01 
            :ARG1 Assad
```            

favor-01 (for “pro”), as in “pro-road position”


•	The epistemic use of “must” should be annotated as follows:

```lisp
    (i / infer-01
      :ARG1 (s / sick
                 :domain p)
      :ARG2 (b / be-located-at-91 :polarity -
                 :ARG1 (p / person :name (n / name :op1 "John"))
                 :ARG2 (h / here)))
```

<em>“John isn't here, he must be sick.”</em>
