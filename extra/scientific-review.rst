.. note::

    `Beyond open access: visions for open evaluation of scientific papers by
    post-publication peer review
    <http://www.frontiersin.org/Computational%20Neuroscience/specialtopics/beyond_open_access__visions_fo/137>`_
    
    #. Open evaluation is defined as `an ongoing post-publication process of
       transparent peer review and rating of papers`
    
    #. They are looking for papers that "focus on constructive ideas and
       comprehensive designs for open evaluation systems."
    
    #. They raise a number of interesting questions, which we should keep in
       mind as we work on this article:
    
       - Should the reviews and ratings be entirely transparent, or should some
         aspects be kept secret?
        
       - Should other information, such as paper downloads be included in the
         evaluation?
        
       - How can scientific objectivity be strengthened and political
         motivations weakened in the future system?
        
       - Should the system include signed and authenticated reviews and
         ratings?
        
       - Should the evaluation be an ongoing process, such that promising
         papers are more deeply evaluated?
        
       - How can we bring science and statistics to the evaluation process
         (e.g. should rating averages come with error bars)?
        
       - How should the evaluative information about each paper (e.g. peer
         ratings) be combined to prioritize the literature?
        
       - Should different individuals and organizations be able to define their
         own evaluation formulae (e.g.  weighting ratings according to different
         criteria)?
        
       - How can we efficiently transition toward the future system?

:author: K. Jarrod Millman
:email: millman@berkeley.edu
:institution: University of California Berkeley

:author: Satra Ghosh
:email: 
:institution: MIT

:author: Arno Klein
:email: 
:institution: Columbia University

-------------------------------------------------------------
A continuous, transparent peer review and paper rating system
-------------------------------------------------------------

.. class:: abstract

   A short version of the long version that is way too long to be written as a
   short version anyway.

Introduction
------------

- look at code review process and NumPy documentation editor
- look at Wikipedia's review process
- the idea of a living, growing document, rather than a series of articles each with the same tedious introduction
- scientist typically have a few scientific projects -- more like a software project


Learning from open source software projects to improve scientific review
------------------------------------------------------------------------

Satrajit S. Ghosh (MIT), Arno Klein (Columbia University), Brian Avants (University of Pennsylvania), K. Jarrod Millman (University of California, Berkeley)

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
publishing. In the article, we will demonstrate how these ideas can improve the
quality of published articles in the highly interdisciplinary field of
neuroimaging. Here, we briefly describe a few important aspects of the proposed
evaluation system.  

First, we suggest a distributed peer review process involving morereviewers than
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
lots of reviewers instead of 2-4, reviewers can reanalyse the data, all software
can be submitted with each paper). While the ideas you outline seem desirable,
it is unclear whether they can be realised.  

I would like to invite you to contribute a full paper with the caveat that you
will need to carefully clarify what aspects of your proposal are realistic and
exactly how they can be realised, and what happens if they fail (e.g. scientists
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

