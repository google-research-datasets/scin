# SCIN Dataset Description

What follows are a description of the fields in the different CSV files.

## `scin_cases.csv`

*   **case_id** (`string`, always present): Identifier for the case
    *   This id should typically be stable across releases
*   **source** (`string`, always present): Value is "SCIN"
*   **release** (`string`, always present): Identifier for the release this case
    is included from.

    *   The format of this string will be "major.minor.patch"

        *   Major: Large number of new cases
        *   Minor: Providing a small number of new categories or labels for
            existing images
        *   Patch: Bug fixes

    *   The first version will be "1.0.0"

*   **year** (`int`, always present): Year closest to the bulk of the data
    released

*   **age_group** (`enum`, sometimes present): The age provided by the user is
    an integer.

    *   This value is mapped into the following age ranges:
        *   AGE_18_TO_29
        *   AGE_30_TO_39
        *   AGE_40_TO_49
        *   AGE_50_TO_59
        *   AGE_60_TO_69
        *   AGE_70_TO_79
        *   AGE_80_OR_ABOVE

*   **sex_at_birth** (`enum`, sometimes present): User-reported sex at birth

    *   Values in the dataset:

        *   FEMALE
        *   MALE
        *   OTHER_OR_UNSPECIFIED

    *   The SCIN UX also included answers for "OTHER" and "PREFER_NOT_TO_SAY".
        There were not enough answers in those categories to publish so this
        field is grouped into the "OTHER_OR_UNSPECIFIED" category for those
        cases.

*   **fitzpatrick_skin_type** (`enum`, sometimes present): User-reported skin
    type

    *   Possible values: FST1-6, NONE_SELECTED
    *   Note that in application, users were asked questions about how their
        skin responds to sun exposure and those responses were mapped to these
        FST values.
        *   NEVER_TANS
        *   TANS_MINIMALLY
        *   TANS_UNIFORMLY
        *   ALWAYS_TANS_WELL
        *   TANS_EASILY
        *   ALWAYS_TANS
        *   NONE_OF_THE_ABOVE
    *   Note that NONE_SELECTED means that the user selected none of the above
        available options matched their skin type. This may indicate it's hard
        for users to self-assess Fitzpatrick skin type with the limited
        information provided. (See scin_questions.csv for the full provided
        text)

*   **race_ethnicity_\*** (`bool`, sometimes present): User-reported race and/or
    ethnicity demographic

    *   Column suffixes:
        *   AMERICAN_INDIAN_OR_ALASKA_NATIVE
        *   ASIAN
        *   BLACK_OR_AFRICAN_AMERICAN
        *   HISPANIC_LATINO_OR_SPANISH_ORIGIN
        *   MIDDLE_EASTERN_OR_NORTH_AFRICAN
        *   NATIVE_HAWAIIAN_OR_PACIFIC_ISLANDER
        *   WHITE
        *   OTHER_RACE
        *   PREFER_NOT_TO_ANSWER
        *   TWO_OR_MORE_AFTER_MITIGATION: As part of data processing, some
            race/ethnicity combinations with low numbers of contributions were
            grouped into this category.
    *   Users may have selected more than one of the above categories.

*   **textures_\*** (`bool`, sometimes present): User-reported texture of the
    skin condition

    *   Column suffixes:
        *   TEXTURE_UNSPECIFIED
        *   RAISED_OR_BUMPY
        *   FLAT
        *   ROUGH_OR_FLAKY
        *   FLUID_FILLED

*   **body_parts_\*** (`bool`, sometimes present): User-reported body parts
    affected by the skin condition

    *   Column suffixes:
        *   HEAD_OR_NECK
        *   ARM
        *   PALM
        *   BACK_OF_HAND
        *   TORSO_FRONT
        *   TORSO_BACK
        *   GENITALIA_OR_GROIN
        *   BUTTOCKS
        *   LEG
        *   FOOT_TOP_OR_SIDE
        *   FOOT_SOLE
        *   OTHER

*   **condition_symptoms_\*** (`bool`, sometimes present): User-reported
    symptoms related to the appearance and sensation of the skin condition

    *   Column suffixes:
        *   BOTHERSOME_APPEARANCE
        *   BLEEDING
        *   INCREASING_SIZE
        *   DARKENING
        *   ITCHING
        *   BURNING
        *   PAIN
        *   NO_RELEVANT_EXPERIENCE

*   **other_symptoms_\*** (`bool`, sometimes present): User-reported symptoms
    that may also be related to the skin condition

    *   Column suffixes:
        *   FEVER
        *   CHILLS
        *   FATIGUE
        *   JOINT_PAIN
        *   MOUTH_SORES
        *   SHORTNESS_OF_BREATH
        *   NO_RELEVANT_SYMPTOMS

*   **related_category** (`enum`, sometimes present): User-reported category
    that may be related

    *   Possible values:
        *   ACNE
        *   GROWTH_OR_MOLE
        *   HAIR_LOSS
        *   OTHER_HAIR_PROBLEM
        *   NAIL_PROBLEM
        *   PIGMENTARY_PROBLEM
        *   RASH
        *   LOOKS_HEALTHY
        *   OTHER_ISSUE_DESCRIPTION

*   **condition_duration** (`enum`, sometimes present): User-reported duration
    of the skin condition

    *   Values (based on current UI question):
        *   ONE_DAY
        *   LESS_THAN_ONE_WEEK
        *   ONE_TO_FOUR_WEEKS
        *   ONE_TO_THREE_MONTHS
        *   THREE_TO_TWELVE_MONTHS
        *   MORE_THAN_ONE_YEAR
        *   MORE_THAN_FIVE_YEARS
        *   SINCE_CHILDHOOD
        *   UNKNOWN

*   **image_\d_path** (`string`, sometimes present): Path to the image storage
    location. Up to 3 images per case

*   **image_\d_shot_type** (`enum`, sometimes present): Enum indicating under
    which image question the user submitted this image.

    *   Possible values: CLOSE_UP, AT_AN_ANGLE, AT_DISTANCE

## `scin_labels.csv`

### Labeling example

In the condition labeling process, each labeller provides up to 3 conditions
with a confidence value of 1-5 for each condition. A case may be labeled up by
up to 3 labelers. This final list of condition names and confidence values are
combined into a list of condition names. For each condition, there is a rank and
weight. These values are combined in the `weighted_skin_condition_label` column.

**Example (fictional)**:

Dermatologist labels:

*   Dermatologist 1's label: Nummular eczema with confidence 3, Acute and
    chronic dermatitis with confidence 2, Psoriasis vulgaris with confidence 1

*   Dermatologist 2's label: Eczematous dermatitis with confidence 3

*   Dermatologist 3's label: Eczematous dermatitis with confidence 4,
    Post-inflammatory hyperpigmentation with confidence 3

The labels would be as follows:

*   `dermatologist_skin_condition_label_name`: `Nummular eczema, Acute and chronic
    dermatitis, Psoriasis vulgaris, Eczematous dermatitis, Eczematous
    dermatitis, Post-inflammatory hyperpigmentation`

*   `dermatologist_skin_condition_confidence`: `[3, 2, 1, 3, 4, 3]`

*   `weighted_skin_condition_label`: `{'Eczema': 0.69, 'Acute and chronic
    dermatitis': 0.11, 'Post-Inflammatory hyperpigmentation: 0.11, 'Psoriasis':
    0.08}` (Note that the condition names change. In particular, both "Nummular
    eczema" and "Eczematous dermatitis" are mapped to "Eczema". See the
    `weighted_skin_condition_label` description below for more details.)

### CSV schema:

*   **case_id**: Same id as the `scin_cases.csv`
*   **dermatologist_gradable_for_skin_condition_\d** (`bool`, sometimes
    present): Label from a dermatologist indicating if the skin condition can be
    determined from the case's images.
    *   The last digit is a value in range `[1, 3]`(inclusive), indicating one
        of 3 dermatologists.
    *   This may be false for a number of reasons, including: there's no
        discernible pathology (e.g. typical skin), there's insufficient
        information, there are multiple conditions present, or the image quality
        is an issue.
*   **dermatologist_skin_condition_label_name** (`List[string]`, sometimes
    present): List of condition names derived from dermatologist-provided labels
    of what condition(s) may be present in the case.
    *   Note that these condition names are the original values used by the
        labeling.
    *   There may be duplicate entries in this list. A duplicate entry means
        more than 1 dermatologist labeller included that condition in their
        response.
    *   Example value: `[Nummular eczema, Psoriasis vulgaris, ...]`
*   **dermatologist_skin_condition_confidence** (`List[int]`, sometimes present)
    A list of confidence scores. Each confidence score is in range
    `[1,5]`(inclusive). 1 means lowest confidence and 5 means highest confidence
    *   The entries in this list represent the confidence value for the
        corresponding entry in the previous
        `dermatologist_skin_condition_label_name` column.
    *   Example value: `[1, 3, …]`
        *   Combined with the `dermatologist_skin_condition_label_name` column,
            this would mean a dermatologist labeled the case with "Nummular
            eczema" with confidence 1 and "Psoriasis vulgaris" with
            confidence 3.
*   **weighted_skin_condition_label** (`Dict[string, float]`, sometimes
    present): This column represents a final differential label that is
    generated as follows:

    *   These are generated as follows:
        *   For each dermatologist label (list of condition name and confidence
            value), the label is reweighted to the inverse of the rank within
            each labeler. For example, a label with values `'Condition A': 4,
            'Condition B': 3, 'Condition C': 1` would have a reweighted value of
            `'Condition A': 1, 'Condition B': 0.5, 'Condition C': 0.3`
        *   These weights are then summed by condition across all dermatologist
            labels.
        *   Then the results are normalized so the weights sum to 1.

*   **dermatologist_gradable_for_fitzpatrick_skin_type_\d** (`string`, sometimes
    present): Label from a dermatologist indicating if the Fitzpatrick skin type
    can be estimated from the case

    *   Values: "YES", "NO"
    *   There may be up to 3 of these labels for a case.

*   **dermatologist_fitzpatrick_skin_type_label_\d** (`enum`, sometimes
    present): Label from a dermatologist estimating the Fitzpatrick skin type

    *   There may be up to 3 of these labels for a case.

*   **gradable_for_monk_skin_tone_india** (`bool`, sometimes present): Label
    from a trained lay person from a pool of graders in India indicating if the
    Monk skin tone label can be determined from the case's images.

*   **gradable_for_monk_skin_tone_us** (`bool`, sometimes present): Label from a
    trained lay person from a pool of graders in the United States indicating if
    the Monk skin tone label can be determined from the case's images.

*   **monk_skin_tone_label_india** (`enum`, sometimes present): Label from a
    trained lay person from a pool of graders in India indicating the Monk skin
    tone label value.

    *   Possible values: 1-10

*   **monk_skin_tone_label_us** (`enum`, sometimes present): Label from a
    trained lay person from a pool of graders in United States indicating the
    Monk skin tone label value.

    *   Possible values: 1-10

