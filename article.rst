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

Over the last decade, scientists, institutions, publishers and funding agencies
have made tremendous strides in the way scientific research is disseminated and
accessed. With the advent of open-access journals as well as the growing
availability of articles freely available online (e.g., PubMed Central,
arXiv.org, faculty websites), scientists face an expanding volume of scientific
literature. The increasingly interdisciplinary nature of research, high volume
of submissions and limited time and availability of expert reviewers have
resulted in high variability in the quality and timeliness of the review
process. Drawing on ideas, experience, and technology recently developed to
support code review in open source software projects, we propose an open
evaluation system for scientific publishing and a research reproducibility
metric that continues to quantify the impact and validity of the contribution
beyond the initial publication date. Given the massive influx of scientific
publications and the variability of results, an objective, thorough and timely
evaluation of research and continued re-evaluation in the context of new
information becomes essential. The current web technologies makes implementing
such a review system practical.

.. contents::

Introduction
------------

Peer-reviewed scientific publications continue to be the primary mechanism for
dissemination of scientific information and are the primary constituents of the
scientific credit score. In the current atmosphere of highly competitive and
uncertain research funding, publications are instrumental in the distribution of
resources and subsequently in forging research directions. With this
increasingly tight coupling between publications and research funding and its
consequence on academic tenure, scientists have adopted a publish or perish
mentality where the focus is on maximizing the number of publications rather
than on the validity and reproducibility of research. This has resulted in a
decreased minimum publishable unit (i.e., the information delta) and increased
redundancy in introductory background information across papers from a given
area. Given this central role of publishing and an increased variability in the
quality of papers, proper and rigorous evaluation procedures are essential to
the health and continued progress of science.

The most common form of the current evaluation process for an article involves a
preliminary screening by a journal editor followed by an anonymous and private
review, typically by a small group of peers (3-5 individuals) knowledgable in
the research topic. The journal editor integrates these reviewer recommendations
to either publish, reject or request revisions of the article under
consideration. Problems with published articles, either fraud or mistakes, are
addressed via retraction after publications, commentary via letters to the
editor or through new articles. Given that there are no objective standards for
the review process across journals and publishers, there is great variability in
the percentage and quality of articles accepted across journals. This has led to
a hierarchy in the status of journals, often quantified by the journal's impact
factor [cite: xx]. As such, certain journals have become an indirect proxy for
the quality and significance of published works instead of the review process. 

While it is encouraging to see journals and other scientists continue to improve
metrics for the importance of articles and the impact of authors (e.g., Hirsch’s
h-index [cite: xxx]), the existing evaluation procedures exhibit several
deficiencies. 

First, reviews are often not completed in a timely manner. Review deadlines vary
significantly from journal to journal and finding available and knowledgable
reviewers is often difficult. With increasing multidisciplinary research,
finding a reviewer knowledgable in all aspects of a article is
challenging. Although there are journal consortia that share reviews across
member journals, in case of rejection, review processes are often reinitiated by
a new journal. This increases the delays and effort on the part of reviewers.

Second, reviews themselves are not considered a timestamp for the intellectual
property in the work. Since the review process is typically anonymous and
private, information is hidden until time of publication. While a given journal
timestamps an article from initial submission to final acceptance, if the
article has gone through a chain of journals, such information is typically
lost.

Third, there is no consistency in the review process to solicit information
related to the contribution of each listed author. While certain journals have
stringent standards for clearly indicating the role of each author on a paper,
other journals do not collect such information. For example, there is implicit
acknowledgement In the field of biological sciences that the first and last
positions in the author list are typically used to signify primary contributor
and the primary director of the research. However, the journal of the Acoustical
Society of America and others expect author lists to be ordered in decreasing
amounts of contribution. Such inconsistency or lack of standards negatively
impacts consideration of author lists for promotion or in grant
reviews. Furthermore without a standard contributors are often not included or
adequately credited (e.g., technicians, research assistants) and certain authors
are included without any contribution.

Fourth, the closed and anonymous review process does not acknowledge the role
and importance of reviewers and information generated during the review
(reviewer criticism and feedback). Reviewing has thus become an extremely
important but seldom acknowledged process. This closed process also prevents an
objective standardization of the scientific process. 

Fifth, the typical review process does not require submission of code and data
associated with a publication making it increasingly limited as a mechanism to
ensure reproducible research. The descriptions provided in methods sections are
often inadequate for replication. In the context of increasing experimental and
analysis complexity, the lack of availability of data and the code or scripts
used to analyze data and generate results leads to an inability to verify
accuracy of the results or spot problems with code or data. 

These deficiencies undermine the role of peer-review in implicitly acknowledging
the veracity and time of the performed research, in accounting the contribution
of authors and in timely dissemination of scientific results.


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
both science and the scientific community evolved

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
  - as the volume and diversity of submissions increased new review procedure
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

- propose an open evaluation system based on our experience
  with open source software development

- we have organized our proposals according to how quickly we believe
  they can be implemented/adopted

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

.. admonition:: Proposal X
   
   Increased number of reviewers to improve scientific rigor

In any complex software project, there are specialists who focus on certain
components of the software. However, code review is not limited to specialists.
When multiple pairs of eyes look at code, the code improves, bugs are caught,
and all participants are encouraged to write better code. Opening up scientific
reviews to the community will also ensure that the people most interested and
knowledgeable on a topic review it, thereby speeding up the review process.
Furthermore, the interdisciplinary papers today require far more than two to
three reviewers to adequately spot problems.  

A large collaborative project typically entails integration of a variety of
disciplines. In such settings, project managers bring in consultants to provide
expert information on specific domains. Similarly, current research articles
aggregate a diverse variety of information. And currently, journal editors will
bring in "experts" to review that information. However, given the diversity of
research topics today, it is highly unlikely that a single reviewer has
extensive knowledge of every single component of the article.

.. admonition:: Proposal X

   An open and recorded discourse between authors and reviewers.

Although certain journals have an interactive discussion before a
paper is accepted, the discussion is still behind closed doors and limited to
the editor, the authors, and a small set of reviewers. An open and recorded
review ensures that there is a timestamp on the work that has been done, an
acknowledgement of who performed the research and the possibility of rectifying
errors early in the process. Such discourse can itself be used to quantitatively
assess the importance of a submission. Formal acceptance should merely be an
annotation indicating agreement in the evolution of the discourse that should
continue.  

We recommend an open review process that solicits reviewers from a subscribed
pool of reviewers (for details see proposal X). The author or an editor can
still choose to solicit reviewers directly for an article. However, the key
element of this proposal is to allow reviewers to review specific components of
the article they are knowledgeable about.

.. admonition:: Proposal X

   Create a pool of reviewers, a quantitative assessment of reviewers and
   integrate reviewer assessments into promotions and grants

Currently reviewers are solicited by the editors of journals based on either
names recommended by the authors who submitted the article, the editors'
knowledge of the domain or from a internal journal reviewer database. Reviewing
is currently considered your "duty" to science to keep the wheels
turning. However, this same altruistic process results in a narrow selection of
reviewers and an intrinsic variability in the review process that's highly
dependent on the particular set of reviewers assigned to a paper.

An alternative way to solicit reviewers, is to broadcast an article to a pool of
reviewers and to let reviewers choose articles and components of the article
they want to review. These are ideas that have already been implemented in
scientific publishing. The Frontiers system [cite: XXX] as well as the Brain and
Behavioral Sciences publication [cite: XXX] solicit reviews from the
community. In the former case, from a select group of review editors and in the
latter from the community. But this can be extended using current web
technology. A mock-up of the intended review system is provided in Fig: xxx.

Insert Fig: xxx

As shown in the figure, reviewers can select which components of the article
they are reviewing and for what content. This choice is coupled with a
stack-overflow/math-overflow like interface, where the rest of the community can
agree or disagree with the reviewers comments and choose to have a discussion on
the topic. We can also draw on "kudos" received [cite: ohloh] as a function of
commits made to a software project.

There are two things that can be used towards assessment of reviewers. First,
reviewer names are immediately associated with the publication. Second, reviewer
grades eventually become associated with the reviewer based on community
feedback on the reviews.

.. admonition:: Proposal X
   
   A review process should allow and quantify positive-, negative-
   and non-results

Currently review processes are biased towards reporting novel findings
distributed via a hierarchical ordering of journals. However, from a scientific
perspective positive-, negative- and non-results are useful to the
community. Instead of adopting a novelty-detector for every article published,
the review process should not discourage replication of experiments as well as
publication of experiments that did not produce results. By appropriately
labeling the articles as such, one can quantify the success of a method or
paradigm as well as provide an additional factor in assessing scientists
contribution to the community.

.. admonition:: Proposal X

   Living document annotated with status information (e.g., submission,
   revised, published, retracted).

- living publications

  - incremental science

In the long run, the review process need not be limited to publication, but can
be engaged throughout the process of research, from inception through planning,
execution, and documentation. This facilitates collaborative research and also
ensures that optimal decisions are taken at every stage in the evolution of a
project.

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
