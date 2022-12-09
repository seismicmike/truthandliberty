# Node Architecture
### Table of contents
- [Global Field Declarations](#global-field-declarations)
- [Content-Types](#content-types-bundles)
  - [Page](#page)
  - [Article](#article)
- [View-Modes](#view-modes)
  - [Default](#default)
  - [Full](#full)
  - [Search Result](#search-result)
- [Paragraph Types](#paragraph-types)
- [Taxonomy Vocabularies](#taxonomies)


## Global Field Declarations
| Machine Name       | Label          | Type                        | Required | Cardinality | Help text                                                                                                        | Field Settings                                                                                            | Notes    |
|--------------------|----------------|-----------------------------|----------|-------------|------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|----------|
| title              | Title          |                             |Yes       |1            |                                                                                                                  |                                                                                                           |          |
| body               | Intro/Summary  | Text long, with summary     |No        |1            | Used as introductory text on the page, or for a summary of the content used in listings.                         | Allowed formats: [Limited HTML](filter_format.md#limited-html), [Plain text](filter_format.md#plain-text) |          |
| field_media_item   | Featured Image | Entity Reference (media)    |No        |1            | This image will be used for the page header and any teaser renderings of this content.                           | Bundles: [Image](./media.md#image)                                                                        |          |
| field_media_teaser | Teaser Image   | Entity Reference (media)    |No        |1            | This image will be used for teasers renderings of this content, will fallback to Featured Image if not provided. | Bundles: [Image](./media.md#image)                                                                        |          |
| field_meta_tags    | Meta tags      | Meta tags                   |No        |1            |                                                                                                                  |                                                                                                           |          |
| field_tags         | Tags           | Entity Reference (taxonomy) |No        |Unlimited    | Tag this content with tags to allow for adhoc grouping. Ex: "COVID19", "2021 Holiday Party"                      | Bundles: [Tags](./taxonomy.md#tags)                                                                       |          |

## Content-Types (bundles)

### Page
###### [machine_name: page]
A _Page_ is used to display generic content.

| Machine Name     | Label           | Type                        | Required | Cardinality | Help text                              | Field Settings | Notes    |
|------------------|-----------------|-----------------------------|----------|-------------|----------------------------------------|----------------|----------|
|body              |(inherit)        |(inherit)                    |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_media_item  |(inherit)        |(inherit)                    |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_media_teaser|(inherit)        |(inherit)                    |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_meta_tags   |(inherit)        |(inherit)                    |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_tags        |(inherit)        |(inherit)                    |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|title             |(inherit)        |(inherit)                    |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|components        |Content          |Entity Reference (paragraph) |No        |Unlimited    |Content components to show on this page |(inherit)       |(inherit) |

#### Notes
- N/A/

### Article
###### [machine_name: article]
An _Article_ is an entry in a blog.

| Machine Name     | Label    | Type                       | Required | Cardinality | Help text                                   | Field Settings | Notes                                                                                 |
|------------------|----------|----------------------------|----------|-------------|---------------------------------------------|----------------|---------------------------------------------------------------------------------------|
|body              |(inherit) |(inherit)                   |(inherit) |(inherit)    |(inherit)                                    |(inherit)       |(inherit)                                                                              |
|field_media_item  |(inherit) |(inherit)                   |(inherit) |(inherit)    |(inherit)                                    |(inherit)       |(inherit)                                                                              |
|field_media_teaser|(inherit) |(inherit)                   |(inherit) |(inherit)    |(inherit)                                    |(inherit)       |(inherit)                                                                              |
|field_meta_tags   |(inherit) |(inherit)                   |(inherit) |(inherit)    |(inherit)                                    |(inherit)       |(inherit)                                                                              |
|field_tags        |(inherit) |(inherit)                   |(inherit) |(inherit)    |(inherit)                                    |(inherit)       |(inherit)                                                                              |
|title             |(inherit) |(inherit)                   |(inherit) |(inherit)    |(inherit)                                    |(inherit)       |(inherit)                                                                              |
|field_date        |Date      |Date                        |Yes       |1            |The date the article was authored.           |                | Defaults to date of creation of the article node, but not necessarily the same thing. |
|field_author      |Author    |Entity Reference (node)     |Yes       |Unlimited    |The author(s) who contributed to the article.|                |                                                                                       |
|field_category    |Category  |Entity Reference (category) |Yes       |1            |Article Category                             |                |                                                                                       |

### Author
###### [machine_name: author]
An _Author_ is the profile of a person who writes entries on the blog.
| Machine Name      | Label       | Type                         | Required | Cardinality | Help text                              | Field Settings | Notes    |
|-------------------|-------------|------------------------------|----------|-------------|----------------------------------------|----------------|----------|
|body               |(inherit)    |(inherit)                     |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_media_item   |(inherit)    |(inherit)                     |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_media_teaser |(inherit)    |(inherit)                     |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_meta_tags    |(inherit)    |(inherit)                     |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_tags         |(inherit)    |(inherit)                     |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|title              |(inherit)    |(inherit)                     |(inherit) |(inherit)    |(inherit)                               |(inherit)       |(inherit) |
|field_social_links |Social Links |Entity Reference (paragraphs) |No        |Unlimited    |A component containing links to socials |                |          |


## View-Modes

### Default
All content types have a default view mode.

__All fields will be disabled on every Default view-mode.__

### Full
###### [machine_name: full]
**Layout**: Customizable. No default.

### Full (fields)
###### [machine_name: full_fields]
**Layout**: N/A. Uses field display.

#### Full (fields): Page
| Machine Name    |Formatter  |Settings       |Notes |
|-----------------| :-------- | :------------ | :--- |
|body             |Default    |Label: none    |      |
|components       |Default    |Label: none    |      |

#### Full (fields): Article
| Machine Name    |Formatter       |Settings                       |Notes |
|-----------------| :--------      | :------------                 | :--- |
|body             |Default         |Label: none                    |      |
|date             |Default         |Label: Date                    |      |
|author           |Rendered Entity |Label: none; View mode: Credit |      |

### Credit
###### [machine_name: credit]
**Layout**: Customizable. No default.

#### Credit (Author): 
| Machine Name  |Formatter |Settings                             |Notes |
|---------------| :------- | :------------                       | :--- |
|field_media    |Default   |Label: none                          |      |
|title          |Default   |Label: Date                          |      |
|body           |SmartTrim |Strip HTML, 200 characters, ellipses |      |


### Search Result
###### [machine_name: search_result]
**Layout**: [Search Result](./layout.md#search-result)

|Region | Machine Name    |Content Types             |Formatter    |Settings                            |Notes                                                      |
|-------|-----------------| :----------------------: | :--------   | :------------                      | :---                                                      |
|Eyebrow|Bundle           |All                       |Pseudo Field |                                    |Shows bundle title for all bundles other than [Page](#page)|
|Title  |title            |All                       |Default      |Tag: h4                             |                                                           |
|Content|search excerpt   |All                       |Default      |                                    |                                                           |
|Content|body             |All                       |SmartTrim    |Strip HTML, 200 characters, ellipses|Show if excerpt is empty.                                  |

## Paragraph Types

### Social Link
###### [machine_name: social_link]
| Machine Name      | Label | Type                       | Required | Cardinality | Help text        | Field Settings                      | Notes |
|-------------------|-------|----------------------------|----------|-------------|------------------|-------------------------------------|-------|
|type               |Type   |Entity Reference (taxonomy) |Yes       |1            |Social Media Type | Vocabulary: Social Media            |       |
|field_link         |Link   |Link                        |Yes       |1            |Link              | External links only; Title optional |       |


## Taxonomy Vocabularies

### Tags
| Machine Name | Label | Type | Required | Cardinality | Help text | Field Settings | Notes |
|--------------|-------|------|----------|-------------|-----------|----------------|-------|
|name          |Name   |text  |Yes       |1            |Name       |                |       |


### Social Media
| Machine Name | Label | Type                    | Required | Cardinality | Help text        | Field Settings | Notes |
|--------------|-------|-------------------------|----------|-------------|------------------|----------------|-------|
|name          |Name   |text                     |Yes       |1            |Name              |                |       |
|field_icon    |Icon   |Entity Reference (media) |Yes       |1            |Social Media Icon |                |       |
