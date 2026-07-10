# DatoCMS-Schema erichkeller.ch — Referenz

<!-- GENERIERT aus scripts/schema/ im Website-Repo — nicht von Hand editieren. Regenerieren: npm run editors-plugin:refs -->

Sprachen: `de` (Hauptsprache), `en`, `fr`. **Lok ✓** = lokalisiertes Feld: beim Schreiben immer alle drei Locale-Keys angeben (Wert darf `null` sein). **Pflicht ✓** = required-Validator. Feldtyp `rich_text` = Modular Content (Block-Liste), `file` = einzelnes Asset, `links`/`link` = Verweis(e) auf Records. CMA-Wert-Formate und fertige Scripts: siehe `docs/cma-rezepte.md` im Plugin.

## Modelle (Records)

| api_key | Art | Label |
| --- | --- | --- |
| `home_page` | singleton | 🏠 Homepage |
| `cms_page` | tree (Seitenbaum) | 📄 CMS Page |
| `solution` | collection | 💡 Solution |
| `product` | collection | 🛋️ Product |
| `characteristic` | collection | ✨ Characteristic |
| `industry` | collection | 🏭 Industry |
| `project_type` | collection | 🏷️ Project Type |
| `reference` | collection | 🏗️ Reference |
| `person` | collection | 👤 Person |
| `translation` | collection | 🌐 Translation |
| `website` | singleton | ⚙️ Website |
| `redirect` | collection | ↪️ Redirect |

### `home_page` — 🏠 Homepage

singleton

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `seo` | seo |  | ✓ |  |
| `header` | rich_text |  | ✓ | Blöcke: `hero_slider`, `page_intro`, `statement_media_section` · max. 1 |
| `sections` | rich_text |  | ✓ | Blöcke: `statement_media_section`, `content_with_media_section`, `sticky_scroll_section`, `tabs_with_media_section`, `text_columns_section`, `richtext_block`, `accordion`, `stats_section`, `facts_figures_section`, `pikto_section`, `media_block`, `reference_teasers_section`, `teaser_collection_section`, `collection_section`, `card_grid`, `contact_cta`, `link_list`, `quote_section`, `hubspot_form_section`, `job_listing_section`, `image_marquee`, `airflow_animation`, `solution_slider`, `product_detail_section`, `downloads_section`, `pcon_configurator_section`, `product_carousel_section`, `color_slider_section` |

### `cms_page` — 📄 CMS Page

tree (Seitenbaum)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `title` |
| `seo` | seo |  | ✓ |  |
| `header` | rich_text |  | ✓ | Blöcke: `hero_slider`, `page_intro`, `statement_media_section` · max. 1 |
| `sections` | rich_text |  | ✓ | Blöcke: `statement_media_section`, `content_with_media_section`, `sticky_scroll_section`, `tabs_with_media_section`, `text_columns_section`, `richtext_block`, `accordion`, `stats_section`, `facts_figures_section`, `pikto_section`, `media_block`, `reference_teasers_section`, `teaser_collection_section`, `collection_section`, `card_grid`, `contact_cta`, `link_list`, `quote_section`, `hubspot_form_section`, `job_listing_section`, `image_marquee`, `airflow_animation`, `solution_slider`, `product_detail_section`, `downloads_section`, `pcon_configurator_section`, `product_carousel_section`, `color_slider_section` |

### `solution` — 💡 Solution

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |
| `icon` | file |  |  |  |

### `product` — 🛋️ Product

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `subtitle` | string |  | ✓ | Short tagline under the title, e.g. "Effizienter Kaltwassersatz" or "Für 1 Person". |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |
| `solution` | link | ✓ |  | → `solution` |
| `teaser_image` | file |  |  |  |
| `body` | structured_text |  | ✓ | Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |
| `specs` | text |  |  | E.g. "Für 1 Person / Aussenmasse: … / Innenmasse: …" |
| `links` | rich_text |  |  | Blöcke: `nav_link` — Optional inline links, e.g. "Verfügbare Modelle", "Konfigurator". |
| `accordion_items` | rich_text |  |  | Blöcke: `accordion_item` |
| `gallery` | gallery |  |  |  |
| `seo` | seo |  | ✓ |  |

### `characteristic` — ✨ Characteristic

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `solution` | link | ✓ |  | → `solution` — The solution this characteristic belongs to. |

### `industry` — 🏭 Industry

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |

### `project_type` — 🏷️ Project Type

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |

### `reference` — 🏗️ Reference

collection · Titel-Feld: `title`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `title` |
| `teaser_image` | file |  |  |  |
| **Fieldset «Reference attributes»** | | | | Drives the reference index filters. |
| `project_types` | links |  |  | → `project_type` |
| `industries` | links |  |  | → `industry` |
| `solutions` | links |  |  | → `solution` |
| `characteristics` | links |  |  | → `characteristic` — Pick from the characteristics of the selected solutions. |
| `products` | links |  |  | → `product` — Products featured in this reference — keeps references↔products filterable. |
| `volume` | string |  |  | Werte: `up_to_50k` · `50k_to_250k` · `250k_to_1m` · `over_1m` |
| `seo` | seo |  | ✓ |  |
| `header` | rich_text |  | ✓ | Blöcke: `hero_slider`, `page_intro`, `statement_media_section` · max. 1 |
| `sections` | rich_text |  | ✓ | Blöcke: `statement_media_section`, `content_with_media_section`, `sticky_scroll_section`, `tabs_with_media_section`, `text_columns_section`, `richtext_block`, `accordion`, `stats_section`, `facts_figures_section`, `pikto_section`, `media_block`, `reference_teasers_section`, `teaser_collection_section`, `collection_section`, `card_grid`, `contact_cta`, `link_list`, `quote_section`, `hubspot_form_section`, `job_listing_section`, `image_marquee`, `airflow_animation`, `solution_slider`, `product_detail_section`, `downloads_section`, `pcon_configurator_section`, `product_carousel_section`, `color_slider_section` |

### `person` — 👤 Person

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ |  |  |
| `role` | string |  | ✓ |  |
| `phone` | string |  |  |  |
| `portrait` | file |  |  |  |

### `translation` — 🌐 Translation

collection · Titel-Feld: `key`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `key` | string | ✓ |  | unique |
| `text` | string | ✓ | ✓ |  |

### `website` — ⚙️ Website

singleton

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string |  | ✓ |  |
| `reference_parent` | link |  |  | → `cms_page` — References are published under this page: {parent-path}/{reference-slug}. Their URLs and sitemap entries depend on it. |
| `job_parent` | link |  |  | → `cms_page` — Job pages (from the Dualoo feed) are published under this page: {parent-path}/{job-slug}. |
| `header_navigation` | rich_text |  | ✓ | Blöcke: `menu_group` |
| `footer_info` | structured_text |  | ✓ | Headings:  · Marks: strong, underline, strikethrough · Nodes: list, link |
| `footer_navigation` | rich_text |  | ✓ | Blöcke: `menu_group` |
| `legal_links` | rich_text |  | ✓ | Blöcke: `nav_link` |

### `redirect` — ↪️ Redirect

collection · manuell sortierbar

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `source` | string | ✓ |  |  |
| `target_type` | string | ✓ |  | Werte: `page` · `url` · `path` |
| `target_page` | link |  |  | → `cms_page`, `home_page` |
| `target_url` | string |  |  |  |
| `target_path` | string |  |  |  |
| `status_code` | string | ✓ |  | Werte: `301` · `302` |

## Blöcke

Einsatz: **Header** = erlaubt im `header`-Feld (genau 1 Block) · **Section** = erlaubt im `sections`-Feld · **Baustein** = nur innerhalb anderer Blöcke/Felder (siehe Detail).

| api_key | Label | Einsatz |
| --- | --- | --- |
| `nav_link` | 🔗 Link | Baustein |
| `menu_link` | 🧭 Menu Link | Baustein |
| `menu_group` | 🧭 Menu Group | Baustein |
| `hero_slide` | 🖼️ Hero Slide | Baustein |
| `hero_slider` | 🦸 Hero Slider | Header |
| `page_intro` | 🦸 Page Intro | Header |
| `statement_media_section` | 💬 Statement Media | Header + Section |
| `content_with_media_section` | 📰 Content with Media | Section |
| `sticky_scroll_entry` | 🗓️ Sticky Scroll Entry | Baustein |
| `sticky_scroll_section` | 📜 Sticky Scroll Text-Media | Section |
| `media_tab` | 🗂️ Media Tab | Baustein |
| `tabs_with_media_section` | 🗂️ Tabs with Media | Section |
| `text_column` | 📑 Text Column | Baustein |
| `text_columns_section` | 📑 Text Columns | Section |
| `richtext_block` | 📝 Richtext Block | Section |
| `accordion_item` | ➕ Accordion Item | Baustein |
| `accordion` | ➕ Accordion | Section |
| `stat_item` | 📊 Stat | Baustein |
| `stats_section` | 📊 Stats | Section |
| `fact_item` | 🔢 Fact | Baustein |
| `facts_figures_section` | 🔢 Facts & Figures | Section |
| `icon_element` | 🔣 Icon Element | Baustein |
| `pikto_section` | 🔣 Pikto | Section |
| `media_block` | 🖼️ Media Block | Section |
| `reference_teasers_section` | 🏗️ Reference Teasers | Section |
| `teaser_link` | 🧲 Teaser Link | Baustein |
| `teaser_collection_section` | 🧲 Teaser Collection | Section |
| `collection_section` | 🗂️ Collection | Section |
| `card` | 🃏 Card | Baustein |
| `card_grid` | 🃏 Card Grid | Section |
| `contact_cta` | 📞 Contact CTA | Section |
| `link_list` | 🔗 Link List | Section |
| `quote_section` | ❝ Quote | Section |
| `hubspot_form_section` | HubSpot Form | Section |
| `job_listing_section` | 💼 Job Listing | Section |
| `image_marquee` | 🎞️ Image Marquee | Section |
| `airflow_animation` | 🌬️ Airflow Animation | Section |
| `solution_slide` | 🧩 Solution Slide | Baustein |
| `solution_slider` | 🧩 Solution Slider | Section |
| `product_detail_section` | 🛋️ Product Detail Section | Section |
| `download_item` | 📄 Download | Baustein |
| `downloads_section` | 📄 Downloads | Section |
| `pcon_configurator_section` | 🛋️ Konfigurator (pCon) | Section |
| `product_carousel_section` | 🎠 Product Carousel | Section |
| `color_slider_slide` | 🎨 Color Slider Slide | Baustein |
| `color_slider_section` | 🎨 Color Slider | Section |

### `nav_link` — 🔗 Link

block · Einsatz: Baustein (`product.links`, `website.legal_links`, `hero_slide.link`, `page_intro.link`, `statement_media_section.link`, `content_with_media_section.links`, `text_column.link`, `text_columns_section.link`, `reference_teasers_section.link`, `teaser_collection_section.link`, `card.link`, `link_list.link`, `link_list.items`, `job_listing_section.link`, `solution_slide.link`, `downloads_section.link`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Pick a page OR fill the external URL below — not both. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optional #anchor on the target page. |

### `menu_link` — 🧭 Menu Link

block · Einsatz: Baustein (`menu_group.overview_link`, `menu_group.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Pick a page OR fill the external URL below — not both. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optional #anchor on the target page. |
| `image` | file |  |  | Optional. Shown on hover in the header mega-menu. |

### `menu_group` — 🧭 Menu Group

block · Einsatz: Baustein (`website.header_navigation`, `website.footer_navigation`, `menu_group.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `overview_link` | rich_text |  |  | Blöcke: `menu_link` · max. 1 — Optional. The group's landing page (the "Zur Übersicht" row). |
| `items` | rich_text |  |  | Blöcke: `menu_link`, `menu_group` |

### `hero_slide` — 🖼️ Hero Slide

block · Einsatz: Baustein (`hero_slider.slides`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `media` | file | ✓ |  |  |
| `headline` | string | ✓ |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `hero_slider` — 🦸 Hero Slider

block · Einsatz: Header (`home_page.header`, `cms_page.header`, `reference.header`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `slides` | rich_text |  |  | Blöcke: `hero_slide` |

### `page_intro` — 🦸 Page Intro

block · Einsatz: Header (`home_page.header`, `cms_page.header`, `reference.header`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `lead` | text |  |  |  |
| `lead_style` | string |  |  | Werte: `hero` · `plain` · `statement` · Default: `plain` — hero: large with link · plain: smaller grey, optional CTA button · statement: display size (Portrait) |
| `logo` | string |  |  | Werte: `none` · `talky` · `riotherm` · Default: `none` — Optional brand logo shown above the title. |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` — Band background. Consecutive blocks of the same colour merge into one band. |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `media` | file |  |  | Optional contained media (~12:7). |

### `statement_media_section` — 💬 Statement Media

block · Einsatz: Header + Section (`home_page.header`, `home_page.sections`, `cms_page.header`, `cms_page.sections`, `reference.header`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `media` | file | ✓ |  |  |
| `statement` | text | ✓ |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `content_with_media_section` — 📰 Content with Media

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `kicker` | string |  |  | Optional second title line, e.g. "Der Design Tisch". |
| `heading` | string | ✓ |  |  |
| `body` | structured_text |  |  | Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |
| `links` | rich_text |  |  | Blöcke: `nav_link` · max. 2 |
| `media` | file | ✓ |  | Roughly square. Videos play muted/autoplay without controls. |
| `media_position` | string |  |  | Werte: `left` · `right` · Default: `right` |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` |

### `sticky_scroll_entry` — 🗓️ Sticky Scroll Entry

block · Einsatz: Baustein (`sticky_scroll_section.entries`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `year` | string |  |  | Optional milestone year, e.g. "2025". |
| `heading` | string | ✓ |  |  |
| `body` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |
| `media` | file | ✓ |  | Shown in the sticky column while this entry is in view. |

### `sticky_scroll_section` — 📜 Sticky Scroll Text-Media

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `entries` | rich_text |  |  | Blöcke: `sticky_scroll_entry` |

### `media_tab` — 🗂️ Media Tab

block · Einsatz: Baustein (`tabs_with_media_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes:  |
| `media` | file |  |  |  |

### `tabs_with_media_section` — 🗂️ Tabs with Media

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `items` | rich_text |  |  | Blöcke: `media_tab` |
| `media_position` | string |  |  | Werte: `left` · `right` · Default: `right` |

### `text_column` — 📑 Text Column

block · Einsatz: Baustein (`text_columns_section.columns`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `text_columns_section` — 📑 Text Columns

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `columns` | rich_text |  |  | Blöcke: `text_column` |

### `richtext_block` — 📝 Richtext Block

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `body` | structured_text |  |  | Blöcke: `accordion` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |

### `accordion_item` — ➕ Accordion Item

block · Einsatz: Baustein (`product.accordion_items`, `accordion.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ |  |  |
| `content` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |

### `accordion` — ➕ Accordion

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`, `richtext_block.body`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `items` | rich_text |  |  | Blöcke: `accordion_item` |

### `stat_item` — 📊 Stat

block · Einsatz: Baustein (`stats_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `value` | string | ✓ |  |  |
| `caption` | string |  |  |  |
| `color` | string |  |  | Werte: `black` · `green` · `blue` · `red` · Default: `green` — Accent colour of the big value. |

### `stats_section` — 📊 Stats

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `items` | rich_text |  |  | Blöcke: `stat_item` |

### `fact_item` — 🔢 Fact

block · Einsatz: Baustein (`facts_figures_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `value` | string | ✓ |  |  |

### `facts_figures_section` — 🔢 Facts & Figures

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `items` | rich_text |  |  | Blöcke: `fact_item` |

### `icon_element` — 🔣 Icon Element

block · Einsatz: Baustein (`pikto_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `icon` | file |  |  | Monochrome line icon (SVG), ~64×64. |
| `title` | string | ✓ |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |

### `pikto_section` — 🔣 Pikto

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `items` | rich_text |  |  | Blöcke: `icon_element` |

### `media_block` — 🖼️ Media Block

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `media` | file | ✓ |  |  |
| `layout` | string |  |  | Werte: `full_bleed` · `contained` · Default: `contained` |
| `caption` | string |  |  |  |

### `reference_teasers_section` — 🏗️ Reference Teasers

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `references` | links |  |  | → `reference` — Leave empty to show the latest references. |
| `layout` | string |  |  | Werte: `editorial_rows` · `grid_3` · `grid_2` · `slider` · Default: `editorial_rows` |

### `teaser_link` — 🧲 Teaser Link

block · Einsatz: Baustein (`teaser_collection_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Pick a page OR fill the external URL below — not both. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optional #anchor on the target page. |
| `title` | string |  |  | Defaults to the linked target's title. |
| `image` | file |  |  | Defaults to the linked target's teaser image. |

### `teaser_collection_section` — 🧲 Teaser Collection

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `items` | rich_text |  |  | Blöcke: `teaser_link` |
| `layout` | string |  |  | Werte: `editorial_rows` · `grid_3` · `grid_2` · `slider` · Default: `grid_3` |

### `collection_section` — 🗂️ Collection

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `source` | string | ✓ |  | Werte: `references` · Default: `references` — Which collection to list. More sources can be added later. |
| `show_filters` | boolean |  |  | Default: `true` — Render the visitor-facing facet filters above the list. |
| `layout` | string |  |  | Werte: `grid` · `editorial_rows` · Default: `grid` |

### `card` — 🃏 Card

block · Einsatz: Baustein (`card_grid.cards`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file |  |  |  |
| `title` | string | ✓ |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `card_grid` — 🃏 Card Grid

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `cards` | rich_text |  |  | Blöcke: `card` |
| `layout` | string |  |  | Werte: `grid_3` · `grid_4` · `feature` · Default: `grid_3` — feature: two stacked cards + one tall card. |

### `contact_cta` — 📞 Contact CTA

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string | ✓ |  |  |
| `subline` | string |  |  |  |
| `person` | link |  |  | → `person` |
| `background` | string |  |  | Werte: `white` · `black` · Default: `white` — white: light section · black: inverted dark section. |

### `link_list` — 🔗 Link List

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `items` | rich_text |  |  | Blöcke: `nav_link` |

### `quote_section` — ❝ Quote

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `quote` | text | ✓ |  |  |
| `attribution` | string |  |  |  |

### `hubspot_form_section` — HubSpot Form

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `embed` | text | ✓ |  | Einfach aus HubSpot kopieren: Einbettungscode (Standard oder Entwickler) oder eine Formular-URL aus der HubSpot-App — Portal-ID, Formular-ID und Region werden automatisch erkannt. |

### `job_listing_section` — 💼 Job Listing

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `empty_note` | string |  |  | Shown instead of the list when no jobs are published. |

### `image_marquee` — 🎞️ Image Marquee

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file | ✓ |  |  |
| `marquee_texts` | text |  |  | One phrase per line. |

### `airflow_animation` — 🌬️ Airflow Animation

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `anchor` | string |  |  | Werte: `up` · `center` · `down` · Default: `up` — Bleed direction out of the 0px anchor. |
| `palette` | string |  |  | Werte: `thermal` · `ice` · `aqua` · `magma` · `viridis` · `mono` · Default: `thermal` — Speed → colour ramp (slow = blue … fast = red). |
| `config` | text |  |  | Optional: paste an exported JSON from the /dev/airflow playground to override the defaults (particle count, turbulence, height, mouse behaviour …). |

### `solution_slide` — 🧩 Solution Slide

block · Einsatz: Baustein (`solution_slider.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `image` | file |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `logo` | file |  |  |  |

### `solution_slider` — 🧩 Solution Slider

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string | ✓ |  |  |
| `items` | rich_text |  |  | Blöcke: `solution_slide` |

### `product_detail_section` — 🛋️ Product Detail Section

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  | Optional section title above the product nav, e.g. "Grössen im Überblick". Only shown in the Stacked variant. |
| `variant` | string |  |  | Werte: `stacked` · `tabs` · Default: `stacked` — Stacked: sticky product nav + all products below each other. Tabs: one product at a time (not built yet). |
| `products` | links |  |  | → `product` |

### `download_item` — 📄 Download

block · Einsatz: Baustein (`downloads_section.files`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `file` | file | ✓ |  |  |

### `downloads_section` — 📄 Downloads

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `files` | rich_text |  |  | Blöcke: `download_item` |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `pcon_configurator_section` — 🛋️ Konfigurator (pCon)

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `article` | string | ✓ |  | pCon-Basisartikelnummer («ban»), z. B. «Talky S109». |
| `manufacturer` | string |  |  | pCon-Herstellerkürzel («moc»). Leer lassen für den Standard «ERKE». |

### `product_carousel_section` — 🎠 Product Carousel

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`) · Zwei gegenläufige Bildbänder unter einer Überschrift (Produkt-Hero). Nur als erste Section direkt nach einem page_intro-Header.

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `top_images` | gallery |  |  | Läuft von rechts nach links. |
| `bottom_images` | gallery |  |  | Läuft gegenläufig von links nach rechts. Leer lassen für nur eine Reihe. |

### `color_slider_slide` — 🎨 Color Slider Slide

block · Einsatz: Baustein (`color_slider_section.slides`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file | ✓ |  |  |
| `color` | string | ✓ |  | Hex-Farbe, z.B. {#B5BF9C} — färbt das Header-Band, wenn dieses Bild in der Mitte steht. |

### `color_slider_section` — 🎨 Color Slider

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`) · Farbwechsel-Slider: durchlaufende Produktbilder, die das Header-Band einfärben. Nur als erste Section direkt nach einem page_intro-Header.

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `slides` | rich_text |  |  | Blöcke: `color_slider_slide` |
