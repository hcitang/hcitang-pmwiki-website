title: ''
author: ''
appears: ''
updated: Invalid date

---

# VisTACO: Visualizing TAbletop COllaboration

This site provides some insight into the problem of visualizing users' interactions with a tabletop.  Most of the work here was presented at the acm interactive tabletops and surfaces conference in [the following paper](http://hcitang.org/papers/2010-its2010-vistaco.pdf).  The paper gives a starting point for many of the ideas that we talk about here.  The purpose of this site is to act as a supplement to that information.

The PowerPoint deck for the presentation is also available: [pptx deck](http://hcitang.org/papers/2010-its2010-vistaco-presentation.pptx)

## Basic Analytic Model of Tabletop Collaboration

Our interest in analyzing tabletop collaboration can often be categorized into three sets of factors: spatial, entity, and temporal.  We have further subdivided these categories as follows:

(insert table)

## Simple Visualization Methods Implemented in VisTACO

We designed a number of very simple visualization techniques in VisTACO that address a number of those elements in the analytic model.

### Example: Objects to Recent Objects to People

This video illustrates the idea of progressively abstracting from a playback of log data to simple emphasizing "recently touched" objects to emphasizing who is moving those objects.

### Example: Global Traces, Emphasis on Specific Entities

This illustrates the basic idea of visualizing all the traces made by users in a session.  Our visualization uses a fading trail that illustrates both the beginning and end of the trace, and we also employ colour to distinguish between users.  In the second image, we illustrate emphasizing the traces that relate to a specific entity.  In this case, we are specifically interested in the touches by one individual.  It is also possible to select by object/artifact on the table.

### Example: Spatial Selection and Highlighting

Another simple technique we allow for is spatial selection of a region in a space.  As can be seen in the figure below, once a region is selected, all traces that passed through the region are highlighted.

## Publications

**Tang, A.**, Pahud, M., Carpendale, S., and Buxton, B. (2011). [VisTACO: Visualizing Tabletop Collaboration](http://hcitang.org/papers/2010-its2010-vistaco.pdf). In Proc. Interactive Tables and Surfaces 2010 (ITS 2010). (November 7-10, Saarbrucken, Germany). (Acceptance: 32/120 ' 26%)

## Open Problems:

* identifying the "owner" of a set of contact points
* identifying the fingers making the contact points as well as correlating between different contact instances
* semantic labeling of raw data
* integration with video/audio feed and manual labeling

## Related Visualizations
