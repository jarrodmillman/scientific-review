.. |emdash| unicode:: U+02014

========================================================================
Learning from open-source software projects to improve scientific review
========================================================================

:author: Satrajit Ghosh
:institution: MIT

:author: Arno Klein
:institution: Columbia University

:author: Brian Avants
:institution: University of Pennsylvania

:author: K. Jarrod Millman
:institution: University of California, Berkeley

Abstract
--------

Over the last decade, scientists, institutions, publishers and
funding agencies have made tremendous strides in the way scientific
research is disseminated and accessed. With the advent of open-access
journals as well as the growing availability of articles freely
available in online repositories such as PubMed Central, arXiv.org,
and faculty websites, scientists face a rapidly expanding volume of
scientific literature. The increasingly interdisciplinary nature of
research, high volume of submissions, and limited time and
availability of expert reviewers have resulted in high variability in
the quality and timeliness of the review process and resulting
articles. Drawing on ideas, experience, and technology recently
developed to support code review in open source software projects,
we propose an open evaluation system for scientific publishing and a
research reproducibility metric that continues to quantify the impact
and validity of contributions beyond their initial publication dates.
Given the massive influx of scientific publications of variable
quality, an objective, thorough and timely evaluation and continued
re-evaluation of research work in the context of new information is
essential. The current web technologies make implementing such a
review system practical.

.. contents::

Introduction
------------

Peer-reviewed scientific publications continue to be the primary mechanism for
dissemination of scientific information and for establishing
precedence and credit for scientific research. In the current atmosphere of highly
competitive and uncertain research funding, publications are instrumental
in determining how resources are distributed, who gets promoted,
and in which directions research advances. This has cultivated a publish-or-perish
mentality where the focus is on maximizing the number of publications
rather than on the validity and reproducibility of research findings, and
a decrease in the amount of information apportioned to each
article, the "minimum publishable unit." Moreover, given that there are no
objective standards for the review process across journals and publishers, there
is great variability in the percentage and quality of articles accepted across
journals. This has led to a hierarchy in the status of journals, often quantified
by the journal's impact factor [cite: Thompson's index, Hirsch’s h-index,
the Eigenfactor index,...]. As such, certain journal titles are taken as arbiters
of quality and significance of published works instead of the review process.

The most common form of the current evaluation process for an article involves a
preliminary screening by a journal editor followed by an anonymous and private
review, typically by a small group of (3-5) peers presumed to have
expertise in the research topic. The journal editor takes into consideration
the reviewers' recommendations to either publish, reject or request revisions
of the article. After publication, problems such as fraud or mistakes are
addressed via retraction after disclosure or exposure by countering articles or
letters to the editor. Through the review process and
the scientific community's history of policing itself, science is thought to
have a self-correcting character. However, with the ever-increasing deluge of articles
of variable quality, the increasingly multidisciplinary content of articles, and
the use of journal impact factors as proxies for evaluations of individual articles,
the integrity of the review process, and indeed science, is imperiled.
For the review process to continue to play a critical role in science,
there are a number of problems that need to be addressed, some of which we list below.

**Reviewers work in isolation and have limited expertise.**
Reviewers work in isolation, unable to discuss the content of the
article with the authors or other reviewers. When faced with an
article that may be authored by half a dozen or more experts in their
respective disciplines, how could a few reviewers be
expected to have the range of expertise necessary to adequately
understand and gauge the significance (or insignificance) of a given
article? Why are the different components of an article, including
the background, experimental design, methods, analysis of results,
and interpretations handed over as a package to each reviewer, rather
than delegated to many experts in each domain?

**Reviewers have little incentive.**
Reviewing is currently considered one's unpaid "duty" to
maintain the standards and credibility of scientific research.
The reviewer stands to gain by early exposure to relevant areas of research,
while a publisher stands to gain financially through either publication or
subscription fees. In order to further motivate potential reviewers to
participate in the review process, there should be some form of
acknowledgment for their services that would factor into their
evaluations for promotion and funding opportunities.

**Review data are closed.**
The closed and anonymous review process does not acknowledge the role
and importance of reviewers and information generated during the review
(reviewer criticism and feedback). Reviewing has thus become an extremely
important but seldom acknowledged process. This closed process also prevents
an objective standardization of the scientific process.

**Author contributions are unclear.**
There is no consistency in the review process to solicit information
related to the contribution of each listed author. While certain journals have
stringent standards for clearly indicating the role of each author on a paper,
other journals do not. Even the order of author names does not abide by a single
convention. For example, in biology publications, the first and last
positions in the author list are typically used to signify primary contributor
and primary director or sponsor of the research. However, journals such as
the Acoustical Society of America expect author lists to be ordered by decreasing
degree of contribution. Such inconsistencies negatively
impact consideration of author lists for promotion or in grant reviews.
Furthermore, without a standard, contributors
(such as technicians and research assistants)
are often not included or adequately credited and others
are included without their having made any contribution.

**The review process is slow.**
Reviews often take a considerable amount of time. Review deadlines vary
significantly from journal to journal, and with increasingly multidisciplinary research,
finding an available reviewer knowledgeable in all aspects of an article is
challenging. Although there are journal consortia that share reviews across
member journals in case of rejection, review processes are often reinitiated by
a new journal, adding delays and demands on reviewers.

**Precedence may be compromised.**
Reviews themselves are not considered a timestamp for the intellectual
property in the work. Since the review process is typically anonymous and
private, information is hidden until the time of publication. While a given journal
timestamps an article from initial submission to final acceptance, if the
article has gone through a chain of journals, such information is typically
lost.

**Studies are not reproducible.**
The typical review process does not require submission of code and data
associated with a publication, making it increasingly limited as a mechanism to
ensure reproducible research. The descriptions provided in methods sections are
often inadequate for replication. In the context of increasing complexity of
experimental design and analysis methods, the lack of accessibility to data and
software used to analyze data and generate results leads to an inability to verify
the accuracy of the results or to identify problems with the data or software.

**A review has a limited lifespan.**
After an article has been published, the review process simply ends,
as if the work and interpretations of the results are sealed in a time capsule.
Data, methods, analysis, and interpretations of the results are all
a product of their time and context, and at a later time may not stand up to
scrutiny or may yield new insights. Simply enabling a continuing dialogue about each
article would make it a living document and integrate it in a rich scientific dialogue.

In this article, we attempt to address these deficiencies by drawing on
the ideas, experience, and technology recently developed to support
code review in open source software projects, by proposing an open
evaluation system for scientific publishing, and by proposing a
research reproducibility metric that continues to quantify the impact
and validity of contributions beyond their initial publication dates.

Historical background
---------------------

.. epigraph::

  Science alone of all the subjects contains within itself the lesson of the
  danger of belief in the infallibility of the greatest teachers in the
  preceding generation... Learn from science that you must doubt the experts.

    |emdash| Richard Feynman, What is Science? (1969)

.. epigraph::

  ...so when a man tries all kinds of experiments without method or
  order, this is mere groping in the dark; but when he proceeds with
  some direction and order in his experiments, it is as if he were
  led by the hand...

    |emdash| Francis Bacon, Novum Organum (1620)


the scientific journal and review process have evolved over time as
both science and the scientific community have evolved

- origin of the scientific method

  - Francis Bacon's Novum Organum (1620) one of the early
    proponents of experimental science
  - the beginning of the use of controlled, repeatable experiments
    to advance knowledge
  - provided a method for questioning received wisdom
    
- origin of scientific communities

  - small groups started forming
  - official societies such as the
    Royal Society of London for Improving Natural Knowledge (1660s)
 
    - Royal Society's motto of *nullius in verba* (Take nobody's word for it)

- the origin of the scientific journal

  - as these scientific societies grew they needed a mechanism to disseminate
    work and provide attribution
  - journals such as the Society's Philosphical Transactions (1665)
    edited by Henry Oldenburg appeared
  - initially submission acceptance in these journals was left to the editor's
    discretion
  - as the volume and diversity of submissions increased, new review procedures
    were needed

    - (1750s):  select group of members formed to review submissions and make
      recommendations to the editor

  - early scientific journals had more space than articles so journals began
    adding assistant editors to help solicit articles and reviews

- peer review limited by existing technologies

  - in addition to a shortage of work to be published technology limited
    the journals ability create copies of submissions for review
  
   - advent of typewriters / carbon papers in 1890s simplified making 3-5 copies
   - photocopiers (1959)
   - modern personal computers / printers these limitations vanished 

- new technologies are again changing scientific publications

  - online publications:  preprints, continuous revision, open discussion

- new technologies are also changing the everyday practice of science

  - increased data storage is rapidly expanding the amount of experimental
    data we can acquire and analyze
  - increased computational power is vastly increasing our ability to model
    and 

http://www.nature.com/nature/peerreview/debate/


Open evaluation system
----------------------

We believe that opening up the review process to everyone, not just to a
select few anonymous reviewers, has the potential to address every one of the
problems with the review process that we raised in the Introduction.
We will address each of the problems in order and make reference to
lessons from distributed code review in open source software development.
A mock-up of the intended review system is provided in Fig: xxx.

**Open reviews to everyone.**
Reviewers would no longer work in isolation or in anonymity,
benefitting from direct communication with the authors and the world
of potential reviewers to clarify points, resolve ambiguities, receive
open collegial advice, attract feedback from people well outside of the
authors' disciplines, and situate the discussion in the larger scientific
community. Because each reviewer's feedback can be focused on his or her
specialty or area of interest, there there is less burden placed on any
one reviewer.

In any complex software project, there are specialists who focus on certain
components of the software. However, code review is not limited to specialists.
When multiple pairs of eyes look at code, the code improves, bugs are caught,
and all participants are encouraged to write better code. Opening up scientific
reviews to the community will also ensure that the people most interested and
knowledgeable on a topic review it, thereby speeding up the review process.
Furthermore, the interdisciplinary papers today require far more than two to
three reviewers to adequately spot problems.

In case there is an overwhelming amount of participation in a review,
or fear of disclosure prior to publication, there are at least two types
of compromise available. One would be to assign certain reviewers as
moderators for different components of the article, to lessen the burden
on the editor. Another would be to increase the number of reviewers
(solicited from a subscribed pool) without opening up the review process
to everyone. This would still improve scientific rigor
while lessening the burden on each individual reviewer, as long as they
review specific components of the article they are knowledgeable about.

Currently, reviewers are solicited by the editors of journals based on either
names recommended by the authors who submitted the article, the editors'
knowledge of the domain or from an internal journal reviewer database.
This selection process results in a very narrow and biased selection of
reviewers. An alternative way to solicit reviewers is to broadcast an article
to a pool of reviewers and to let reviewers choose articles and components of the
article they want to review. These are ideas that have already been implemented in
scientific publishing. The Frontiers system [cite: XXX] solicits reviews from a
select group of review editors and the Brain and Behavioral Sciences publication
[cite: XXX] solicits reviews from the community.

**Acknowledge reviewers**
When reviewers are given the opportunity to provide feedback regarding just
the areas they are interested in, the review process becomes much more enjoyable.
But there are additional factors afforded by opening the review process
that will motivate reviewer participation. First, the review process becomes the
dialogue of science, and anyone who engages in that dialogue gets heard.
Second, it transforms the review process from one of secrecy to one of
engaging social discourse.
Third, an open review process makes it possible to quantitatively assess
reviewer contributions, which could lead to assessments for promotions and grants.
There are two things that can be used towards assessment of reviewers. First,
reviewer names are immediately associated with the publication. Second, reviewer
grades eventually become associated with the reviewer based on community
feedback on the reviews.

**Open data generated by reviews.**
Although certain journals hold a discussion before a
paper is accepted, it is still behind closed doors and limited to
the editor, the authors, and a small set of reviewers. An open and recorded
review ensures that there is a timestamp on the work that has been done, an
acknowledgement of who performed the research, and a higher probability
of rectifying errors early in the process.
By opening up the review process, the role and importance of reviewers
and information generated during the review would be shared and acknowledged.
The exchanges themselves can be used to quantitatively assess the importance
of a submission, and analysis of the review process then becomes possible
and could lead to an objective standardization of the scientific process.

**Clarify author contributions.**
An open review is like an open discussion, where questions could be
directed at individual authors to establish accountability for their
contributions. This would make it far more likely that otherwise unacknowledged
contributors, such as technicians and research assistants, would be heard.

**Expedite the review process.**
An open discussion could happen in real time [like the Frontiers journals?],
so reviews become an interactive and efficient process.

**Establish precedence.**
Open review establishes a clear provenance of ideas and a timestamp
for the intellectual property in the work.

**Facilitate reproducibility.**
In a widescale, open review, descriptions of experimental designs and
methods would come under greater scrutiny by people from different fields
using different nomenclature, leading to greater clarity and cross-fertilization
of ideas. Software and data quality would also come under greater scrutiny by people
interested in their use for unexpected applications, pressuring authors
to make them available for review as well, and potentially leading to collaborations,
which would not be possible in a closed review process.

Currently, reviews are biased toward reporting novel findings.
However, from a scientific perspective, positive-, negative- and non-results
are extremely useful to the community. 
[http://www.plosmedicine.org/article/info:doi/10.1371/journal.pmed.0020124]
[http://www.plosmedicine.org/article/info%3Adoi%2F10.1371%2Fjournal.pmed.0040028]
Instead of judging every article based on novelty,
the review process should encourage replication of experiments as well as
publication of experiments that did not produce results. By appropriately
labeling the articles as such, one can quantify the success of a method or
paradigm as well as provide an additional factor in assessing scientists'
contribution to the community.

**Extend the review process indefinitely.**
Once open and online, there is no reason for a review process
to end after an article has been published. The article can continue as
a living document, where the dialogue can continue and flourish,
and references to different articles could be supplemented with references to
the comments about these articles, firmly establishing these communications within
the dialogue and provenance of science, where science serves not just as a
method or philosophy, but as a social endeavor. This could make science and
scientific review a more welcoming community, and more desirable career choice.

Insert Fig: xxx

As shown in the figure, reviewers can select which components of the article
they are reviewing and for what content. This choice is coupled with a
stack-overflow/math-overflow like interface, where the rest of the community can
agree or disagree with the reviewers comments and choose to have a discussion on
the topic. We can also draw on "kudos" received [cite: ohloh] as a function of
commits made to a software project.

In the long run, the review process need not be limited to publication, but can
be engaged throughout the process of research, from inception through planning,
execution, and documentation. This facilitates collaborative research and also
ensures that optimal decisions are taken at every stage in the evolution of a
project.



- analogies with modern best-practices in code review
  - web-based discussions
    - discussion graph
  - inline comments
  - continuous integration
  - multiple reviewers
  - timely reviews
  - most important community members are often not authors
    - Linus doesn't write code anymore

- open reviews
  - open for comments
  - timely
  - make paper best it can be  
  - micro-reviews
    - review by best experts
    - muli-tiered review (perhaps by graduate students/postdocs and then by experts)
  - new measures for impact factors
    - higher impact discussions rather than just citations


Reproducible research
---------------------

- long-term need
- published code/data
- verified

We suggest making data and software used for the research available as
part of the submission process. This not only ensures transparency and helps
reviewers but will also enhance reproducibility and encourage method reuse.  It
is in everyone’s scientific interest that every reviewed article is the best
that it can be. An open review process can improve the quality of articles and
research through constructive feedback, and reduce the time period between
initial submission and acceptance of an article.

- difficulty in exactly repeating published results

  - increasing size of data sets used in experimental science make including them
    in traditions publications impossible
  - the extensive computational processing used in experimental science make
    completely specifiying the analysis difficult

- increasing awareness of need to address these problems has led to a growing
  number of scientists to advocate for *reproducible research*

  - growing literature
  - several special sessions at conferences

.. epigraph::

   "An article about computational science in a scientific publication is not the
   scholarship itself, it is merely advertising of the scholarship. The actual
   scholarship is the complete software development environment and the complete
   set of instructions which generated the figures."
   |emdash| David Donoho, Wavelab and Reproducible Research, 1995


A scientific article represents a summary of the work done, not the lab
notebook. It is generally left up to the review process to determine if the
methods were implemented and executed properly and if the appropriate parameters
were used in the methods, based on this summary. Given the small fraction of any
scientific community that is well versed in and understands the intricacies of
the methods, the current review system simply does not address reproducibility
or validity of methods used in research.

We propose that data and scripts be submitted together with the article. Scripts
can often help reviewers follow what was done without necessarily rerunning all
the analyses. While rerunning the entire analysis as part of a review process
may not be computationally feasible, having the data and scripts available
allows replication of the results in the long run as well as comparisons of
different methods on the same dataset or different datasets on the same methods.

Fig: XX a nipype graph showing what steps were used in an imaging experiment

In the long run, virtual machines or servers may indeed allow standardization of
analysis environments and replication of the results for every publication.

.. admonition:: Proposal X

   A retrospectively applicable reproducibility metric.   all papers
   would come with this --- e.g., C for code, D for data, R for reproducible

   Annotate articles to indicate how much effort has been expended to make the
   work reproducible (e.g., data publically available, code publically available,
   results independently reproduced).

- journals beginning to do this

  - Biostatics (C, D, and R annotations)

    - reproducibilty editor (Roger Peng)

  - open research computation

- potential difficulties

  - large data sets
  - computations that take weeks to run on supercomputers or specialized hardware

- reproduction using same data and code doesn't mean the data and code are correct

  - independent replication still needed

.. admonition:: Proposal X

   Articles embedded with provenance information.

- Madagascar
- VisTrails
- Donoho's Universal Identifier for Computational Results

  - http://www.stanford.edu/~vcs/AAAS2011/AAAS_slides_new.pdf

.. admonition:: Proposal X

   Adopt the Reproducible Research Standard (RRS) [stodden2009enabling]_

- http://www.stanford.edu/~vcs/AAAS2011/AAAS_slides_new.pdf

.. admonition:: Proposal X

   Reproducible research data license --- allows authors to release data
   with the constraint that it only be used for reproducing a paper's
   results.

.. This could get a little tricky.  Would it be possible to report whether
   the results were reproduced or not?  It would be very odd to not allow
   researchers to try different parameters or preprocessing when analzing the
   data. There are already licenses that require attribution or getting
   permission prior to publishing new results from published data.

Discussion
----------

- changing the review process will take time and will most likely be
  implemented in an iterative manner

  - different fields may have different constraints

    - medical research
    - animal research
    - experimental vs. observational science
    - wet-lab based vs. computation-based

  - resistance to change

- new opportunities / changing nature of scientific communication

- In a local minimum: time to shake the optimization process

  - conservatism and the inertial nature of science
  - why change? and why now?

- Practical and psychological limitations

  - the balance between commercial benefits and scientific advance
  - can publications replace the patent system?
  - should incentives play a role?
  - a revised role for journals

- the ideal world

  - open reproducible research 
  - collaboration, reviews and reproducibility as the alternative metric for
    funding/promotions
