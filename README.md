**TODO: UPLOAD TO GITHUB**

**A: INTRODUCTION & BACKGROUND**

>
> *Round 1*: The initial round of annotations required to initiate the
> training of the singular/lineage marker classifiers. Ideally, the user
> should provide 8-10 annotations for each category (i.e. CDXX, Ignore),
> however, the user should aim for 10 is the marker is not sparse.
>
> *Round 2*: After loading the classifier, the user will provide
> training annotations in the 'Live Update' view in QuPath to further
> refine the classifier. The number of annotations provided in this
> portions can be affected by marker, stain, and/or patient-based
> variations.
>
> *Other:* Within a particular channel, brighter staining does not equate
    higher levels of expression

**B: DEFINITIONS**

> *Diffuse* (*staining*): staining that looks **hazy** and
> (subjectively) seems relatively + noticeably **less bright** than the
> staining in the surrounding area.
>
> *Complete* (*staining*): the most complete staining will manifest as a
> continuous pattern of staining forming a donut-like shape; however,
> the degree of completeness can be evaluated by the **total portion of
> the perimeter** of the cell and/or nuclear segmentation is encompassed
> by the staining. Note that this donut hole may also be 'filled' to be
> considered complete.
>
> *Specific* (*staining*): staining that is **localized** to the
> membrane (or clearly surrounding the nuclear compartment) of a cell
> according to the segmentation. The stain should either have some
> semblance of a donut/crescent shape around the nuclear compartment or
> cover the entirety of the nuclear compartment + cellular membrane.

**C: GENERAL GUIDELINES**

<b>Annotating</b>

1.  *Incorrect nuclear segmentation*:

-   **Grouped segmentations**: Refrain from annotating grouped/incorrect
    nuclear segmentations for CD8, CD4, CD45RO, and CD3. (Let the
    classifier do the work!)

<!-- -->

-   **Exceptions to grouped segmentations**: for very specific cases
    (see below), incorrect segmentations for macrophage and neutrophil
    markers may be annotated since they undergo phagocytosis and are
    often not segmented correctly.

2.  *Diversity of annotations*:

-   **Spatial variety**: n Round 1 of the annotation process, make sure
    to provide annotations in a wide variety of locations around the
    slide, particularly in dense areas and/or tumoral areas (usually
    they align)

    -   Avoid making more than 1-2 annotations of the same category in
        the same vicinity

-   **Including varying levels of positivity and negativity**: the user
    should be sure to include obvious cases of negativity and positivity
    in addition to edge cases.

3.  *Positive cases:*

-   **Requirements of a positive cell (Round 1)**: to make annotations
    in Round 1, the user should adhere very strictly to marking cells
    that have ([all]{.underline}):

    -   **specific** staining

    -   $\mathbf{\geq 50\%\ }$**completeness**

    -   the staining can be **bright or diffuse**, but the user should
        refer to classifier-specific information if the staining is
        affected by crosstalk and/or is *very* diffuse.

-   **Considerations for fixing predictions in Round 2**: the user can
    be more lenient with this rule when making annotations during Round
    2 (maybe down to 30-40%) and correct only cells that are **most
    certainly** either positive or negative.

4.  *Edge cases*:

-   **Making annotations when doubtful**: if the user feels doubtful
    about whether a stain is specific to a particular cell or not,
    consult the supplementary images. If the user still cannot tell,
    they should refrain from annotating in those regions.

    -   This is especially true for CD66b where the staining is very
        blotchy.

5.  *Ignore cases*:

-   The user should mark cells that:

    -   have **no/negligible** staining (i.e. the most obvious cases)

    -   are very diffuse and **broad/non-specific** staining

    -   are **edge cases** that should not be classified as positive
        (i.e. that satisfy only some of the requirements for a positive
        cell)

    -   **false positives** due to crosstalk (see marker-specific
        guidelines)

    -   **false positives** due to staining from adjacent positive cells

6.  *Crosstalk*:

-   **Check all channels**: be sure to check adjacent channels before
    making annotations to mitigate the number of marked/predicted false
    positives.

    -   Due to the nature of the spectral unmixing, you will see a lot
        of overlap between adjacent channels, most notably between CD8 &
        CD66b and CD3 & CD163/CD68.

-   **Disregarding crosstalk for markers of the same lineage**: we
    usually do not look for crosstalk between markers that belong to the
    same lineage (e.g. the T cell markers).

    -   For example, CD3 and CD8 may seem to have some cases of overlap,
        however we would just count these cases as CD3+CD8+ T cells.

-   **Determining the true positive**: if there is signal in multiple
    lineage channels, the user should choose the one with brighter
    staining if there's [both]{.underline}...

    -   **(a)** specificity (i.e. it is one of the few cells in the
        area, less dense that the other channel, etc.).

    -   **(b)** different staining pattern (i.e. different shape;
        different areas are brighter/fainter, etc.).

        -   This is very important. If the staining looks dimmer as a
            whole or that the overall shape is the same but it just
            \'shrunk\', likely this indicates a false-positive due to
            crosstalk. However, if the staining shape is different (not
            just shrinkage though) and/or different areas are brighter,
            then this could indicate specificity (thus, a true positive)
            for that particular marker channel.

    -   **Otherwise**: The user should refrain from making any
        annotation at all if the channels look too similar and/or if
        they are predominantly unsure.

[Stopping Point]{.underline}

1.  *Individual Markers:* stop providing annotations in the live
    predictions when [either]{.underline}...

<!-- -->

a)  After an annotation is placed, the resulting number of detections is
    within ± 5% for any 10 of the previous counts/annotations (**not
    including** Round 1 annotations).

    i.  Reference the excel workbook

b)  The user cannot make any more confident and/or meaningful
    annotations.

    i.  Although there may be some edge cases, you may not see any more
        obvious misclassifications.

    ii. If placing an annotation for an edge case produces (in the
        surrounding area) more predictions that don't align with what
        you would expect and/or the cell's prediction does not change
        after correcting it, then that is not a meaningful annotation.

    iii. You can keep re-annotating cells that are +/-

<!-- -->

2.  *Lineage Markers:* stop providing annotations in the live
    predictions when [either]{.underline}...

<!-- -->

a)  After an annotation is placed, the resulting number of detections is
    within ± 10% for any 10 of the previous counts/annotations (**not
    including** Round 1 annotations).

b)  The user make any more confident and/or meaningful annotations.

    i.  Although there may be some edge cases, you may not see any more
        obvious misclassifications.

    ii. If placing an annotation for an edge case produces (in the
        surrounding area) more predictions that don't align with what
        you would expect and/or the cell's prediction does not change
        after correcting it, then that is not a meaningful annotation.

<!-- -->

3.  *Other*:

-   **Total annotation count**: usually, the stopping point comes after
    making about 10-15 annotations total in Round 2 for the single
    markers.

    -   However, sometimes if a user make 'good' annotations or if the
        marker is well-behaved, it can definitely take less.

    -   It can also take more if the counts tend to oscillate.

    -   *Note: these numbers are a guide, not a goal*

**\
**

**D: CD8 CLASSIFIER**

> *General*:

-   CD8 tends to be relatively brighter and well-behaved.

-   There is observed crosstalk between CD8 and CD66b.

-   Because areas surrounding the tumors tend to have high lymphocyte
    infiltration, the user should focus their initial annotations in
    these dense regions + near tumors

    -   A large portions of the annotations; don't exclusively make it
        in dense regions

-   For the sake of phenotyping, we will assume that CD3+CD8+ T cells
    **absolutely** **cannot** co-express with CD4.

-   Always cross-check with CD3 & CD4 channels before making an
    annotation (see below in 'other notes').

> *Positive annotations*:

-   **Consider CD3 positivity**: for CD8, the user should only make CD8+
    annotations where the cell also exhibits CD3+. (see Positive
    Annotations section for Lineage Classifier: CD3)

> *Ignore annotations*:

-   **Dense regions**: the user should place some ignore annotations in
    areas of dense infiltration near the tumor(s)

    -   Since regions with dense T cell populations are likely to result
        in false positives due to residual staining from adjacent cells,
        comparing the predictions with the CD4 channel has shown to be
        useful in mitigating overlaps and helps guide the user in making
        annotations/corrections (e.g. where there is a CD4+ cell in a
        dense region, we can assume it is automatically a CD8- cell).

-   **False positives from adjacent CD8+ cells**: oftentimes during the
    live update, the classifier will identify false positive cells due
    to staining from adjacent CD8+ cells. Be sure to correct these cases
    to be CD8- as necessary.

> *Other notes*:

-   **Avoiding grouped segmentations**: after training, the user may
    observe single-cell segmentations containing multiple T cells that
    were grouped together, including some that are seemingly CD8+ on at
    least one of the cells.

    -   These grouped segmentations were sometimes classified as CD8+ or
        CD8-, but the user should avoid annotating/correcting these
        unless the staining was super off.

-   The user **SHOULD NOT** fix a prediction if...

    -   there is a predicted CD8+ cell with questionable CD8 stain but
        the CD3 stain was strong in that same area/cell 🡪 leave as CD8+

    -   there is a predicted CD8+ cell that looks like it has a strong
        and/or specific and complete CD8 stain but there was
        questionable/no corresponding CD3 stain 🡪 leave as CD8+

    -   there is a predicted CD8- cell that may be considered CD8+ (or
        as an edge case) but there was no corresponding CD3 stain (even
        if the CD8 stain was specific) 🡪 leave as CD8+

    -   there is a predicted CD8- cell that had some diffuse/bright
        staining but the staining was (both) neither specific nor
        complete ($< 30 - 40\%$) 🡪 leave as CD8-

**E: CD4 CLASSIFIER**

> *General*:

-   CD4 in general was much more diffuse and not as bright.

-   Because areas surrounding the tumors tend to have high lymphocyte
    infiltration, I aimed to make my initial annotations near dense
    regions + near tumors

-   For the sake of phenotyping, we will assume that CD3+CD4+ T cells
    **absolutely** **cannot** co-express with CD8.

-   Always cross-check with CD3 & CD8 channels before making an
    annotation (see below).

> *Positive Annotations*:

-   **Consider CD3 positivity**: for CD4, the user should only make CD4+
    annotations where the cell also exhibits CD3+. (see Positive
    Annotations section for Lineage Classifier: CD3)

> *Ignore Annotations*:

-   **Dense regions**: the user should place some ignore annotations in
    areas of dense infiltration near the tumor(s)

    -   Since regions with dense T cell populations are likely to result
        in false positives due to residual staining from adjacent cells,
        comparing the predictions with the CD4 channel has shown to be
        useful in mitigating overlaps and helps guide the user in making
        annotations/corrections (e.g. where there is a CD4+ cell in a
        dense region, we can assume it is automatically a CD8- cell).

-   **False positives from adjacent CD4+ cells**: oftentimes during
    Round 2, the classifier will identify false positive cells next to
    CD4+ cells due to their residual staining. Be sure to correct these
    cases to be CD4- as necessary.

> *Other Notes*:

-   The user **SHOULD NO**T fix a prediction if...

    -   there is a predicted CD4+ cell with questionable CD4 stain but
        the CD3 stain was strong in that same area/cell 🡪 leave as CD4+

    -   there is a predicted CD4+ cell that looked like it had a strong
        and/or specific and complete CD4 stain but there was
        questionable/no corresponding CD3 stain 🡪 leave as CD4+

    -   there is a predicted CD4- cell that may be considered CD4+ (or
        as an edge case) but there was no corresponding CD3 stain (even
        if the CD4 stain was specific) 🡪 leave as CD4+

    -   there is a predicted CD4- cell that had some diffuse/bright
        staining but the staining was neither specific nor complete
        ($< 30 - 40\%$) 🡪 leave as CD4-

**F: CD45RO CLASSIFIER**

> *General*:

-   We are looking strictly at CD3+CD45RO+ T cells.

-   T cells may coexpress CD45RO and CD8 or CD45RO and CD4.

> *Positive Annotations*:

-   **Consider CD3 positivity**: for CD4, the user should only make CD4+
    annotations where the cell also exhibits CD3+. (see Positive
    Annotations section for Lineage Classifier: CD3)

> *Ignore Annotations*:

-   **Dense regions**: the user should place some ignore annotations in
    areas of dense infiltration near the tumor(s).

-   **False positives from adjacent CD45RO+ cells**: oftentimes during
    Round 2, the classifier will identify false positive cells next to
    CD45RO+ cells due to their residual staining. Be sure to correct
    these cases to be CD45RO- as necessary.

> *Other Notes*:

-   The user **SHOULD NO**T fix a prediction if...

    -   there is a predicted CD45RO+ cell with questionable CD45RO stain
        but the CD3 stain was strong in that same area/cell 🡪 leave as
        CD45RO+

    -   there is a predicted CD45RO + cell that looked like it had a
        strong and/or specific and complete CD45RO stain but there was
        questionable/no corresponding CD3 stain 🡪 leave as CD45RO+

    -   there is a predicted CD45RO- cell that may be considered CD45RO+
        (or as an edge case) but there was no corresponding CD3 stain
        (even if the CD45RO stain was specific) 🡪 leave as CD45RO+

    -   there is a predicted CD45RO- cell that had some diffuse/bright
        staining but the staining was neither specific nor complete
        ($< 30 - 40\%$) 🡪 leave as CD45RO-

**G: LINEAGE CLASSIFIER: CD3**

> *General*:

-   Staining for CD3+ cells can range from super bright to **very**
    faint.

-   There is observed crosstalk between CD3 and CD163/68.

> *Positive Annotations*:

-   **Very diffuse staining**: If the CD3 signal seems very
    faint/diffuse (edge case), the user can still annotate the cell to
    be CD3+ if (all):

    -   the user can determine that the staining is complete AND
        specific.

    -   there is also $\mathbf{\geq 50\%\ }$complete AND specific
        staining in CD8, CD4, and/or CD45RO\*\*

        -   \*\*CAVEAT: this is not a requirement for CD3+ cells since
            CD8, CD4, and CD45RO can appear on non-T cells, but rather
            they can be used as a guide to increase the user's
            confidence in the identity of a CD3+ cell WHEN THE STAINING
            IS SUPER DIFFUSE.

        -   If CD3 is not diffuse, however, then the user does not need
            to take into account the other T cell marker channels (in
            that case your only concern is crosstalk).

    -   the cell can be differentiated as a true positive for CD3 after
        checking for crosstalk in other channels

> *Ignore Annotations*:

-   **Dense regions**: the user should place some ignore annotations in
    dense regions near the tumor(s)

> *Other Notes*:

-   **Very faint CD3 signal without other T cell markers**: if the CD3
    signal was very faint/diffuse (with or without specificity and
    completeness) and cell is CD8-, CD4-, and/or CD45RO-, the cell
    should be left unannotated.

-   **Dealing with crosstalk**: If the crosstalk between CD3 and
    CD163/68 cannot be differentiated, the user should refrain from
    annotating the cell.

    -   This holds true regardless even if the cell is CD4+, CD8+,
        and/or CD45RO+.

**H: LINEAGE CLASSIFIER: CD163+CD68**

> *General*:

-   There is observed crosstalk between CD163/68 and CD3.

-   Co-expression for CD4 and CD163/68 is not a cause for concern.

> *Positive Annotations*:

-   **Grouped segmentations and specific staining**: the user may notice
    many instances where the nuclear segmentation appears incorrect and
    groups a macrophage with adjacent cells. This is likely because
    macrophages/monocytes are in the process of phagocytosis. However,
    these grouped segmentations may still be annotated as CD163/68+ if
    [all]{.underline} are true:

    -   there is no crosstalk with other channels OR the user can tell
        that the cell is true positive for CD163/68.

    -   there is complete AND specific staining along the nuclear
        perimeter of *all the grouped cells* (i.e., there is staining
        around the entire grouped segmentation itself). (brightness?)

        -   If the staining does not manifest for all cells in the
            grouped segmentations, the user should not annotate the cell
            at all.

> *Ignore Annotations:*

-   **Mitigating the effects of crosstalk**: the user should place
    ignore annotations where there is no/less CD163/68 staining relative
    to CD3 so the classifier knows to eliminate false positive cases. 🡪
    move to section F

> *Other Notes*:

-   **Dealing with crosstalk**: If the crosstalk between CD3 and
    CD163/68 cannot be differentiated, the user should refrain from
    annotating the cell.

**I: LINNEAGE CLASSIFIER: CD66b**

> *General*:

-   There is (significant) observed crosstalk between CD66b and CD8,
    resulting in many false positives for CD66b.

-   CD66b can be a messier and blotchier marker than others.

    -   Define blotchy

> *Positive Annotations*:

-   **Grouped segmentations and specific staining**: the user may notice
    many instances where the nuclear segmentation appears incorrect and
    groups neutrophils with adjacent cells and/or with other
    neutrophils. This is likely because the neutrophils are in the
    process of phagocytosis. However, these grouped segmentations may
    still be annotated as CD66b+ if [all]{.underline} are true:

    -   there is **no crosstalk** with other channels OR the user can
        tell that the cell is **true positive** for CD66b.

    -   there is **complete AND specific** staining along the nuclear
        perimeter of *all the grouped cells* (i.e., there is staining
        around the entire grouped segmentation itself). (brightness?)

        -   If the staining does not manifest for all cells in the
            grouped segmentations, the user should not annotate the cell
            at all.

> *Ignore Annotations*:

-   **Blotchy areas**: There are three main types of blotchy areas: (1)
    bright, sparser blotchiness, (2) continuous, more uniform areas of
    blotchiness (mix of bright and diffuse staining), and (3) areas with
    very condensed and relatively brighter staining.

    -   **(1)**: the user may be able to still identify CD66b+ cells if
        the staining is specific AND complete for a particular cell.
        There should also not be staining in the immediate surroundings
        of this cell that overlap with other cells.

> ![](media/image1.png){width="1.8470592738407698in"
> height="1.4148939195100612in"}

-   **(2)**: in these areas, it is usually very hard to determine
    specificity. The user should avoid making annotations or fixing
    predictions in these areas with the exception\...(hard to define
    exceptions)

> ![A close-up of a black and white image Description automatically
> generated](media/image2.png){width="1.849905949256343in"
> height="1.3510640857392826in"}

-   **(3)**: in these areas, it is usually very hard to determine
    specificity. The user should avoid making annotations or fixing
    predictions in these areas.

> ![](media/image3.png){width="1.8510629921259842in"
> height="1.4167749343832021in"}

-   **Mitigating the effects of crosstalk**: the user should place
    ignore annotations where there is CD3 positivity so the classifier
    knows to eliminate false positive cases with respect to CD8+CD3+
    cells.

> *Other Notes*:

-   **Annotating in blotchy areas**: since CD66b staining can be very
    blotchy, the staining can appear non-specific. Thus, the user should
    be careful in annotating in these areas.

-   **False positive predictions with CD3 positivity (Round 2)**: if a
    cell is predicted to be CD66b+ and appears to be CD8+ as well, BUT
    the cell is CD3+ (i.e. the CD3 staining is questionable or
    nonexistent), then the user should re-annotate the cell to be CD3+.

-   **False positive predictions with CD3 negativity (Round 2)**: if a
    cell is predicted to be CD66b+ and appears to be CD8+ as well, BUT
    there is very little to no CD3 staining (i.e. the CD3 staining is
    questionable or nonexistent), then the user should refrain from
    'fixing' this prediction.

    -   Although this is still considered a false positive, the
        classifier has no information from CD8 to differentiate between
        a neutrophil and a T cell within the Lineage Classifier if there
        is also no clear CD3 positivity.

**I: LINNEAGE CLASSIFIER: IGNORE**
