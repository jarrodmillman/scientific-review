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


Over the last decade, scientists, institutions, publishers and funding agencies
have made tremendous strides in the way scientific research is disseminated and
accessed. With the advent of open-access journals as well as the growing
availability of articles freely available online (e.g., PubMed Central,
arXiv.org, faculty websites), scientists face an expanding volume of scientific
literature. The increasingly interdisciplinary nature of research, high volume
of submissions and limited time and availability of expert reviewers have
resulted in high variability in the quality and timeliness of the review
process. Given the massive influx of scientific publications, an objective,
thorough and timely evaluation of research becomes essential. Drawing on ideas,
experience, and technology recently developed to support code review in open
source software projects, we propose an open evaluation system for scientific
publishing.

First, we suggest a distributed peer review process involving more reviewers than
in the current system. In any complex software project, there are specialists
who focus on certain components of the software. However, code review is not
limited to specialists. When multiple pairs of eyes look at code, the code
improves, bugs are caught, and all participants are encouraged to write better
code. Opening up scientific reviews to the community will also ensure that the
people most interested and knowledgeable on a topic review it, thereby speeding
up the review process. Furthermore, the interdisciplinary papers today require
far more than two to three reviewers to adequately spot problems.  

Second, we suggest an open and recorded discourse between authors and
reviewers. Although certain journals have an interactive discussion before a
paper is accepted, the discussion is still behind closed doors and limited to
the editor, the authors, and a small set of reviewers. An open and recorded
review ensures that there is a timestamp on the work that has been done, an
acknowledgement of who performed the research and the possibility of rectifying
errors early in the process. Such discourse can itself be used to quantitatively
assess the importance of a submission. Formal acceptance should merely be an
annotation indicating agreement in the evolution of the discourse that should
continue.  

Third, we suggest making data and software used for the research available as
part of the submission process. This not only ensures transparency and helps
reviewers but will also enhance reproducibility and encourage method reuse.  It
is in everyone’s scientific interest that every reviewed article is the best
that it can be. An open review process can improve the quality of articles and
research through constructive feedback, and reduce the time period between
initial submission and acceptance of an article.

In the long run, the review process need not be limited to publication, but can
be engaged throughout the process of research, from inception through planning,
execution, and documentation. This facilitates collaborative research and also
ensures that optimal decisions are taken at every stage in the evolution of a
project.

Editorial comments

This abstract contains several good ideas and important observations. However,
some of the ideas seem naively optimistic and unrealistic (e.g. let's just have
lots of reviewers instead of 2-4, reviewers can reanalyze the data, all software
can be submitted with each paper). While the ideas you outline seem desirable,
it is unclear whether they can be realized.  

I would like to invite you to contribute a full paper with the caveat that you
will need to carefully clarify what aspects of your proposal are realistic and
exactly how they can be realized, and what happens if they fail (e.g. scientists
fail to comply). This includes the required web-based infrastructure as well as
mechanisms of motivating authors (e.g. to submit data) and reviewers (e.g. to
review more papers). The abstract leaves a number of questions open (see in-line
comments). Please try to address these questions fully in the paper.  

The paper should communicate a comprehensive vision for your
replication-tracking system. Consider including a step-by-step description of
the process by which a paper is evaluated. Please try to address the design
decisions listed in the email insofar as they are relevant. Feel free to use
figures to communicate the key concepts and processes of your vision. Please
note that the innovative features that distinguish your approach from those
described in other contributions to this special topic should be clearly
communicated in the title, in the abstract, and through the headings and
terminology used in the paper.


Abstract
--------


Introduction
------------

What is the goal of scientific review?



Proposals
---------

#. Increased number of reviewers to improve scientific rigor

  A large collaborative project typically entails integration of a variety of
  disciplines. In such settings, project managers bring in consultants to provide
  expert information on specific domains. Similarly, current research articles
  aggregate a diverse variety of information. And currently, journal editors will
  bring in "experts" to review that information. However, given the diversity of
  research topics today, it is highly unlikely that a single reviewer has
  extensive knowledge of every single component of the article.

  We recommend an open review process that solicits reviewers from a subscribed
  pool of reviewers (for details see proposal X). The author or an editor can
  still choose to solicit reviewers directly for an article. However, the key
  element of this proposal is to allow reviewers to review specific components of
  the article they are knowledgeable about.

#. Create a pool of reviewers, a quantitative assessment of reviewers and
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

#. Submitting data and code

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

#. A review process should allow and quantify positive-, negative- and non-results

  Currently review processes are biased towards reporting novel findings
  distributed via a hierarchical ordering of journals. However, from a scientific
  perspective positive-, negative- and non-results are useful to the
  community. Instead of adopting a novelty-detector for every article published,
  the review process should not discourage replication of experiments as well as
  publication of experiments that did not produce results. By appropriately
  labeling the articles as such, one can quantify the success of a method or
  paradigm as well as provide an additional factor in assessing scientists
  contribution to the community.
