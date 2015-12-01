          Reuters-21578 text categorization test collection
                        Distribution 1.0
                       README file (v 1.2)
                        26 September 1997

                         David D. Lewis
                      AT&T Labs - Research     
                     lewis@research.att.com

# I. Introduction

   This README describes Distribution 1.0 of the Reuters-21578 text
categorization test collection, a resource for research in information
retrieval, machine learning, and other corpus-based research.


# II. Copyright & Notification 

   The copyright for the text of newswire articles and Reuters
annotations in the Reuters-21578 collection resides with Reuters Ltd.
Reuters Ltd. and Carnegie Group, Inc. have agreed to allow the free
distribution of this data *for research purposes only*.  
   If you publish results based on this data set, please acknowledge
its use, refer to the data set by the name "Reuters-21578,
Distribution 1.0", and inform your readers of the current location of
the data set (see "Availability & Questions").


# III. Availability & Questions

   The Reuters-21578, Distribution 1.0 test collection is available
from David D. Lewis' professional home page, currently:
             http://www.research.att.com/~lewis

Besides this README file, the collection consists of 22 data files, an
SGML DTD file describing the data file format, and six files
describing the categories used to index the data.  (See Sections VI
and VII for more details.)  Some additional files, which are not part
of the collection but have been contributed by other researchers as
useful resources are also included.  All files are available
uncompressed, and in addition a single gzipped Unix tar archive of the
entire distribution is available as reuters21578.tar.gz.

   The text categorization mailing list, DDLBETA, is a good place to
send questions about this collection and other text categorization
issues. You may join the list by writing David Lewis at
lewis@research.att.com.


# IV. History & Acknowledgements

   The documents in the Reuters-21578 collection appeared on the
Reuters newswire in 1987.  The documents were assembled and indexed
with categories by personnel from Reuters Ltd. (Sam Dobbins, Mike
Topliss, Steve Weinstein) and Carnegie Group, Inc. (Peggy Andersen,
Monica Cellio, Phil Hayes, Laura Knecht, Irene Nirenburg) in 1987.  

In 1990, the documents were made available by Reuters and CGI for
research purposes to the Information Retrieval Laboratory (W.  Bruce
Croft, Director) of the Computer and Information Science Department at
the University of Massachusetts at Amherst.  Formatting of the
documents and production of associated data files was done in 1990 by
David D.  Lewis and Stephen Harding at the Information Retrieval
Laboratory.

Further formatting and data file production was done in 1991 and 1992
by David D. Lewis and Peter Shoemaker at the Center for Information
and Language Studies, University of Chicago.  This version of the data
was made available for anonymous FTP as "Reuters-22173, Distribution
1.0" in January 1993. From 1993 through 1996, Distribution 1.0 was
hosted at a succession of FTP sites maintained by the Center for
Intelligent Information Retrieval (W. Bruce Croft, Director) of the
Computer Science Department at the University of Massachusetts at
Amherst.

At the ACM SIGIR '96 conference in August, 1996 a group of text
categorization researchers discussed how published results on
Reuters-22173 could be made more comparable across studies.  It was
decided that a new version of collection should be produced with less
ambiguous formatting, and including documentation carefully spelling
out standard methods of using the collection.  The opportunity would
also be used to correct a variety of typographical and other errors in
the categorization and formatting of the collection.

Steve Finch and David D. Lewis did this cleanup of the collection
September through November of 1996, relying heavily on Finch's
SGML-tagged version of the collection from an earlier study.  One
result of the re-examination of the collection was the removal of 595
documents which were exact duplicates (based on identity of timestamps
down to the second) of other documents in the collection. The new
collection therefore has only 21,578 documents, and thus is called the
Reuters-21578 collection.  This README describes version 1.0 of this
new collection, which we refer to as "Reuters-21578, Distribution
1.0".

In preparing the collection and documentation we have benefited from
discussions with Eric Brown, William Cohen, Fred Damerau, Yoram
Singer, Amit Singhal, and Yiming Yang, among many others.

We thank all the people and organizations listed above for their
efforts and support, without which this collection would not exist.

A variety of other changes were also made in going from Reuters-22173
to Reuters-21578:

   1. Documents were marked up with SGML tags, and a corresponding
SGML DTD was produced, so that the boundaries of important sections of
documents (e.g. category fields) are unambiguous.
   2. The set of categories that are legal for each of the five
controlled vocabulary fields was specified. All category names not
legal for a field were corrected to a legal category, moved to their
appropriate field, or removed, as appropriate.
   3. Documents were given new ID numbers, in chronological order, and
are collected 1000 to a file in order by ID (and therefore in order
chronologically). 


# V. What is a Text Categorization Test Collection and Who Cares? 

   *Text categorization* is the task of deciding whether a piece of
text belongs to any of a set of prespecified categories.  It is a
generic text processing task useful in indexing documents for later
retrieval, as a stage in natural language processing systems, for
content analysis, and in many other roles [LEWIS94d].

   The use of standard, widely distributed test collections has been a
considerable aid in the development of algorithms for the related task
of *text retrieval* (finding documents that satisfy a particular
user's information need, usually expressed in an textual request).
Text retrieval test collections have allowed the comparison of
algorithms developed by a variety of researchers around the world.
(For more on text retrieval test collections see SPARCKJONES76.)

   Standard test collections have been lacking, however, for text
categorization. Few data sets have been used by more than one
researcher, making results hard to compare.  The Reuters-22173 test
collection has been used in a number of published studies since it was
made available, and we believe that the Reuters-21578 collection will
be even more valuable.

   The collection may also be of interest to researchers in machine
learning, as it provides a classification task with challenging
properties. There are multiple categories, the categories are
overlapping and nonexhaustive, and there are relationships among the
categories.  There are interesting possibilities for the use of domain
knowledge.  There are many possible feature sets that can be extracted
from the text, and most plausible feature/example matrices are large
and sparse.  There is even some temporal structure to the data
[LEWIS94b], though problems with the indexing and the uneven
distribution of stories within the timespan covered may make this
collection a poor one to explore temporal issues.


# VI. Formatting 

     The Reuters-21578 collection is distributed in 22 files. Each of
the first 21 files (reut2-000.sgm through reut2-020.sgm) contain 1000
documents, while the last (reut2-021.sgm) contains 578 documents.  

     The files are in SGML format.  Rather than going into the details
of the SGML language, we describe here in an informal way how the SGML
tags are used to divide each file, and each document, into sections.
Readers interested in more detail on SGML are encouraged to pursue
one of the many books and web pages on the subject.

     Each of the 22 files begins with a document type declaration line:
               <!DOCTYPE lewis SYSTEM "lewis.dtd">

The DTD file lewis.dtd is included in the distribution.  Following the
document type declaration line are individual Reuters articles marked
up with SGML tags, as described below.


   VI.A. The REUTERS tag:

    Each article starts with an "open tag" of the form

    <REUTERS TOPICS=?? LEWISSPLIT=?? CGISPLIT=?? OLDID=?? NEWID=??>

where the ?? are filled in an appropriate fashion.  Each article ends
with a "close tag" of the form:

     </REUTERS>

In all cases the <REUTERS> and </REUTERS> tags are the only items
on their line.  

     Each REUTERS tag contains explicit specifications of the values
of five attributes, TOPICS, LEWISSPLIT, CGISPLIT, OLDID, and NEWID.
These attributes are meant to identify documents and groups of 
documents, and have the following meanings: 

     1. TOPICS : The possible values are YES, NO, and BYPASS:
        a. YES indicates that *in the original data* there was at
least one entry in the TOPICS fields.
        b. NO indicates that *in the original data* the story had no
entries in the TOPICS field.
        c. BYPASS indicates that *in the original data* the story was
marked with the string "bypass" (or a typographical variant on that
string).
     This poorly-named attribute unfortunately is the subject of much
confusion. It is meant to indicate whether or not the document had
TOPICS categories *in the raw Reuters-22173 dataset*.  The sole use of
this attribute is to defining training set splits similar to those
used in previous research. (See the section on training set splits.)
The TOPICS attribute does **NOT** indicate anything about whether or
not the Reuters-21578 document has any TOPICS categories.  (Version
1.0 of this document was errorful on this point.)  That can be
determined by actually looking at the TOPICS field. A story with
TOPICS="YES" can have no TOPICS categories, and a story with
TOPICS="NO" can have TOPICS categories.
     Now, a reasonable (though not certain) assumption is that for all
TOPICS="YES" stories the indexer at least thought about whether the
story belonged to a valid TOPICS category.  Thus, the TOPICS="YES"
stories with no topics can reasonably be considered negative examples
for all 135 valid TOPICS categories.
     TOPICS="NO" stories are more problematic in their interpretation.
Some of them presumedly result because the indexer made an explicit
decision that they did not belong to any of the 135 valid TOPICS
categories.  However, there are many cases where it is clear that a
story should belong to one or more TOPICS categories, but for some
reason the category was not assigned.  There appear to be certain time
intervals where large numbers of such stories are concentrated,
suggesting that some parts of the data set were simply not indexed, or
not indexed for some categories or category sets.  Also, in a few
cases, the indexer clearly meant to assign TOPICS categories, but put
them in the wrong field.  These cases have been corrected in the
Reuters-21578 data, yielding stories that have TOPICS categories, but
where TOPICS="NO", because the the category was not assigned in the
raw version of the data.
     "BYPASS" stories clearly were not indexed, and so are useful only
for general distributional information on the language used in the
documents.

     2. LEWISSPLIT : The possible values are TRAINING, TEST, and
NOT-USED.  TRAINING indicates it was used in the training set in the
experiments reported in LEWIS91d (Chapters 9 and 10), LEWIS92b,
LEWIS92e, and LEWIS94b.  TEST indicates it was used in the test set
for those experiments, and NOT-USED means it was not used in those
experiments.

     3. CGISPLIT : The possible values are TRAINING-SET and
PUBLISHED-TESTSET indicating whether the document was in the training
set or the test set for the experiments reported in HAYES89 and
HAYES90b.

     4. OLDID : The identification number (ID) the story had in the
Reuters-22173 collection.

     5. NEWID : The identification number (ID) the story has in the
Reuters-21578, Distribution 1.0 collection.  These IDs are assigned to
the stories in chronological order.

In addition, some REUTERS tags have a sixth attribute, CSECS, which
can be ignored.  

The use of these attributes is critical to allowing comparability
between different studies with the collection, and is discussed
further in Section VIII.


  VI.B. Document-Internal Tags 

     Just as the <REUTERS> and </REUTERS> tags serve to delimit
documents within a file, other tags are used to delimit elements
within a document.  We discuss these in the order in which they
typically appear, though the exact order should not be relied upon in
processing. In some cases, additional tags occur within an element
delimited by these top level document-internal tags.  These are
discussed in this section as well.

     We specify below whether each open/close tag pair is used exactly
once (ONCE) per a story, or a variable (VARIABLE) number of times
(possibly zero).  In many cases the start tag of a pair appears only
at the beginning of a line, with the corresponding end tag always
appearing at the end of the same line.  When this is the case, we
indicate it with the notation "SAMELINE" below, as an aid to those
processing the files without SGML tools.  

     1. <DATE>, </DATE> [ONCE, SAMELINE]: Encloses the date and time
of the document, possibly followed by some non-date noise material.

     2. <MKNOTE>, </MKNOTE> [VARIABLE] : Notes on certain hand
corrections that were done to the original Reuters corpus by Steve
Finch.

     3. <TOPICS>, </TOPICS> [ONCE, SAMELINE]: Encloses the list of
TOPICS categories, if any, for the document. If TOPICS categories are
present, each will be delimited by the tags <D> and </D>.
     
     4. <PLACES>, </PLACES> [ONCE, SAMELINE]: Same as <TOPICS>
but for PLACES categories.

     5. <PEOPLE>, </PEOPLE> [ONCE, SAMELINE]: Same as <TOPICS>
but for PEOPLE categories.

     6. <ORGS>, </ORGS> [ONCE, SAMELINE]: Same as <TOPICS> but
for ORGS categories.

     7. <EXCHANGES>, </EXCHANGES> [ONCE, SAMELINE]: Same as
<TOPICS> but for EXCHANGES categories.

     8. <COMPANIES>, </COMPANIES> [ONCE, SAMELINE]: These tags always
appear adjacent to each other, since there are no COMPANIES categories
assigned in the collection.
    
     9. <UNKNOWN>, </UNKNOWN> [VARIABLE]: These tags bracket control
characters and other noisy and/or somewhat mysterious material in the
Reuters stories.

     10. <TEXT>, </TEXT> [ONCE]: We have attempted to delimit all the
textual material of each story between a pair of these tags.  Some
control characters and other "junk" material may also be included.
The whitespace structure of the text has been preserved. The <TEXT>
tag has the following attribute:

        a. TYPE: This has one of three values: NORM, BRIEF, and
UNPROC.  NORM is the default value and indicates that the text of the
story had a normal structure. In this case the TEXT tag appears simply
as <TEXT>.  The tag appears as <TEXT TYPE="BRIEF"> when the story is a
short one or two line note.  The tags appears as <TEXT TYPE="UNPROC">
when the format of the story is unusual in some fashion that limited
our ability to further structure it.

The following tags optionally delimit elements inside the TEXT
element. Not all stories will have these tags:

        a. <AUTHOR>, </AUTHOR> : Author of the story. 
        b. <DATELINE>, </DATELINE> : Location the story
originated from, and day of the year. 
        c. <TITLE>, </TITLE> : Title of the story. We have attempted
to capture the text of stories with TYPE="BRIEF" within a <TITLE>
element.
        d. <BODY>, </BODY> : The main text of the story.
