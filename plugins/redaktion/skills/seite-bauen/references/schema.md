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
| `available_model` | collection | 📦 Available model |
| `industry` | collection | 🏭 Industry |
| `project_type` | collection | 🏷️ Project Type |
| `project_kind` | collection | 🔨 Project Kind |
| `project_volume` | collection | 💰 Project Volume |
| `reference` | collection | 🏗️ Reference |
| `person` | collection | 👤 Person |
| `location_type` | collection | 🏷️ Location Type |
| `location` | collection | 📍 Location |
| `translation` | collection | 🌐 Translation |
| `website` | singleton | ⚙️ Website |
| `redirect` | collection | ↪️ Redirect |
| `slide_deck` | collection | 🎞️ Slide deck |

### `home_page` — 🏠 Homepage

singleton

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `seo` | seo |  | ✓ |  |
| `header` | rich_text |  | ✓ | Blöcke: `hero_slider`, `page_intro`, `statement_media_section` · max. 1 |
| `sections` | rich_text |  | ✓ | Blöcke: `anchor`, `spacer_section`, `statement_media_section`, `content_with_media_section`, `sticky_scroll_section`, `tabs_with_media_section`, `text_columns_section`, `richtext_block`, `accordion`, `stats_section`, `facts_figures_section`, `pikto_section`, `media_block`, `media_slider_section`, `reference_teasers_section`, `available_models_section`, `teaser_collection_section`, `image_text_grid_section`, `collection_section`, `contact_cta`, `link_list`, `quote_section`, `hubspot_form_section`, `job_listing_section`, `locations_section`, `image_marquee`, `airflow_animation`, `solution_slider`, `product_detail_section`, `downloads_section`, `pcon_configurator_section`, `product_carousel_section`, `color_slider_section`, `content_tab_nav_section`, `flexible_image_section` |

### `cms_page` — 📄 CMS Page

tree (Seitenbaum)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `title` |
| `seo` | seo |  | ✓ |  |
| `header` | rich_text |  | ✓ | Blöcke: `hero_slider`, `page_intro`, `statement_media_section` · max. 1 |
| `sections` | rich_text |  | ✓ | Blöcke: `anchor`, `spacer_section`, `statement_media_section`, `content_with_media_section`, `sticky_scroll_section`, `tabs_with_media_section`, `text_columns_section`, `richtext_block`, `accordion`, `stats_section`, `facts_figures_section`, `pikto_section`, `media_block`, `media_slider_section`, `reference_teasers_section`, `available_models_section`, `teaser_collection_section`, `image_text_grid_section`, `collection_section`, `contact_cta`, `link_list`, `quote_section`, `hubspot_form_section`, `job_listing_section`, `locations_section`, `image_marquee`, `airflow_animation`, `solution_slider`, `product_detail_section`, `downloads_section`, `pcon_configurator_section`, `product_carousel_section`, `color_slider_section`, `content_tab_nav_section`, `flexible_image_section` |

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
| `body` | structured_text |  | ✓ | Blöcke: `spec_table`, `download_item` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |
| `specs` | text |  |  | E.g. "Für 1 Person / Aussenmasse: … / Innenmasse: …" |
| `links` | rich_text |  |  | Blöcke: `nav_link` — Optional inline links, e.g. "Verfügbare Modelle", "Konfigurator". |
| `accordion_items` | rich_text |  |  | Blöcke: `accordion_item` |
| `gallery` | gallery |  |  |  |
| `seo` | seo |  | ✓ |  |

### `available_model` — 📦 Available model

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string |  | ✓ | Optional — defaults to the linked product's name if left empty. |
| `product` | link | ✓ |  | → `product` |
| `external_id` | string |  |  | E.g. an ERP/Dualoo article number. Written into the request form's hidden "talky_produkt_id" field when this model's CTA is clicked. |
| `teaser_image` | file |  |  | Optional — defaults to the linked product's teaser image if left empty. |
| `gallery` | gallery |  |  |  |
| `specs` | rich_text |  | ✓ | Blöcke: `spec_table` — Attribute rows, e.g. Aussenfarbe: weiss / Stofffarbe: hellgrau / Bodenbelag: Teppich dunkel / ... |
| `description` | structured_text |  | ✓ | Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote — Free text, e.g. condition, location, delivery note. |

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

### `project_kind` — 🔨 Project Kind

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |

### `project_volume` — 💰 Project Volume

collection · manuell sortierbar · Titel-Feld: `name`

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
| `intro` | text |  | ✓ | Lead paragraph of the generated reference header. |
| **Fieldset «Reference attributes»** | | | | Drives the reference index filters and the attribute list in the header. |
| `project_types` | links |  |  | → `project_type` |
| `industries` | links |  |  | → `industry` |
| `solutions` | links |  |  | → `solution` |
| `products` | links |  |  | → `product` — Products featured in this reference — keeps references↔products filterable. |
| `project_kinds` | links |  |  | → `project_kind` — Neubau, Umbau, … — combinations allowed. |
| `year` | integer |  |  | Year of completion. |
| `volume` | link |  |  | → `project_volume` |
| `location` | string |  | ✓ | Free text, e.g. {Zürich}. |
| `rating` | string |  |  | Werte: `1` · `2` · `3` — Internal editorial ranking — not shown on the website. |
| `specs` | single_block | ✓ | ✓ | Free attribute rows rendered as a spec table at the end of the page, e.g. Architekt, Planer, Bauherrschaft. |
| `seo` | seo |  | ✓ |  |
| `sections` | rich_text |  | ✓ | Blöcke: `richtext_block`, `media_block` |

### `person` — 👤 Person

collection · Titel-Feld: `internal_label`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `internal_label` | string | ✓ |  | Editor-only title for this record, shown in listings and pickers. |
| `name` | string | ✓ |  |  |
| `role` | string |  | ✓ |  |
| `phone` | string |  |  | International format, e.g. {+41 71 644 88 88} — rendered as a tel: link. |
| `email` | string |  |  | Personal or team address, e.g. {vorname.nachname@erichkeller.com} — rendered as a mailto: link. |
| `contact_url` | string |  |  | Optional link for the contact slide, e.g. a booking or profile page. Full URL incl. {https://}. |
| `portrait` | file |  |  |  |
| `solution` | link |  |  | → `solution` — Main solution this person covers — filters the contact picker in the deck configurator. |
| **Fieldset «Contact languages»** | | | | Languages this person can be contacted in. |
| `lang_de` | boolean |  |  | Default: `true` |
| `lang_en` | boolean |  |  |  |
| `lang_fr` | boolean |  |  |  |

### `location_type` — 🏷️ Location Type

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ | Tab label in the locations section, e.g. {Arbeitsplatzlösungen Showrooms}. |

### `location` — 📍 Location

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ |  |  |
| `types` | links | ✓ |  | → `location_type` — Which groups this location is listed under. Pick several when it belongs in more than one tab. |
| `image` | file |  |  | Interior shot for a showroom, company logo for a partner. |
| `street` | string |  |  | e.g. {Romanshornstrasse 17} |
| `postal_code` | string |  |  | e.g. {8583} |
| `city` | string |  |  | e.g. {Sulgen} |
| `country` | string |  | ✓ | Only for locations abroad — leave empty for Swiss addresses. e.g. {Niederlande}. |
| `phone` | string |  |  | International format, e.g. {+41 71 644 88 88} — rendered as a tel: link. |
| `email` | string |  |  | Optional address for this location, e.g. {info@partner.ch} — rendered as a mailto: link. |
| `website_url` | string |  |  | Optional link to this location's own site (mainly for partners). Full URL incl. {https://}. |
| `coordinates` | lat_lon |  |  | The map pin. Search the address, then drag the pin to fine-tune it. |
| `directions_url` | string |  |  | Optional, full URL incl. {https://}. Leave empty to link to Google Maps directions for the address above. |
| `solutions` | links |  |  | → `solution` — Which product lines this location covers. Not filtered on — kept for later. |
| `kind` | string |  |  | Werte: `showroom` · `partner` · Default: `showroom` — DEPRECATED — replaced by {Types} above and no longer rendered. Don't edit; the field will be deleted. |

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
| `contact_page` | link |  |  | → `cms_page` — Global contact/form page — the fallback target for Contact CTA buttons without an own contact page. |
| `header_navigation` | rich_text |  | ✓ | Blöcke: `menu_group` |
| `footer_info` | structured_text |  | ✓ | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: list, link |
| `footer_navigation` | rich_text |  | ✓ | Blöcke: `menu_group` |
| `legal_links` | rich_text |  | ✓ | Blöcke: `nav_link` |
| `pcon_contact_form` | rich_text |  | ✓ | Blöcke: `hubspot_form_section` · max. 1 — HubSpot-Formular, das nach einer Konfigurationsanfrage im pCon-Konfigurator eingeblendet wird. |

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

### `slide_deck` — 🎞️ Slide deck

collection · manuell sortierbar · Titel-Feld: `title`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `solution` | link |  |  | → `solution` — Groups the deck in the configurator picker. Leave empty for general decks. |
| `slides` | gallery |  | ✓ | One image per slide, 16:9 {1920x1080px or larger}. Export from PowerPoint via Save As > PNG. |

## Blöcke

Einsatz: **Header** = erlaubt im `header`-Feld (genau 1 Block) · **Section** = erlaubt im `sections`-Feld · **Baustein** = nur innerhalb anderer Blöcke/Felder (siehe Detail).

| api_key | Label | Einsatz |
| --- | --- | --- |
| `nav_link` | 🔗 Link | Baustein |
| `menu_link` | 🧭 Menu Link | Baustein |
| `menu_group` | 🧭 Menu Group | Baustein |
| `anchor` | ⚓ Anchor | Section |
| `spacer_section` | ↕️ Spacer | Section |
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
| `spec_row` | ▸ Spec Row | Baustein |
| `spec_table` | 📋 Spec Table | Baustein |
| `stat_item` | 📊 Stat | Baustein |
| `stats_section` | 📊 Stats | Section |
| `fact_item` | 🔢 Fact | Baustein |
| `facts_figures_section` | 🔢 Facts & Figures | Section |
| `icon_element` | 🔣 Icon Element | Baustein |
| `pikto_section` | 🔣 Pikto | Section |
| `media_block` | 🖼️ Media Block | Section |
| `media_slider_slide` | 🖼️ Media Slider Slide | Baustein |
| `media_slider_section` | 🎞️ Media Slider | Section |
| `reference_teasers_section` | 🏗️ Reference Teasers | Section |
| `available_models_section` | 📦 Available models | Section |
| `teaser_link` | 🧲 Teaser Link | Baustein |
| `teaser_collection_section` | 🧲 Teaser Collection | Section |
| `image_text_item` | 🖼️ Image Text Item | Baustein |
| `image_text_grid_section` | 🖼️ Image Text Grid | Section |
| `collection_section` | 🗂️ Collection | Section |
| `contact_cta` | 📞 Contact CTA | Section |
| `link_list` | 🔗 Link List | Section |
| `quote_section` | ❝ Quote | Section |
| `hubspot_form_section` | HubSpot Form | Section |
| `job_listing_section` | 💼 Job Listing | Section |
| `locations_section` | 📍 Locations | Section |
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
| `content_tab` | 📑 Content Tab | Baustein |
| `content_tab_nav_section` | 🎛️ Content Tab Nav | Section |
| `flexible_image_setting` | 🎛️ Image Settings | Baustein |
| `flexible_image_viewport` | 📐 Viewport Setting | Baustein |
| `flexible_image_section` | 🖼️ Flexible Image | Section |

### `nav_link` — 🔗 Link

block · Einsatz: Baustein (`product.links`, `website.legal_links`, `hero_slide.link`, `page_intro.link`, `statement_media_section.link`, `content_with_media_section.links`, `text_column.link`, `text_columns_section.link`, `reference_teasers_section.link`, `teaser_collection_section.link`, `link_list.link`, `link_list.items`, `job_listing_section.link`, `solution_slide.link`, `downloads_section.link`, `content_tab.link`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Pick a page OR fill the external URL below — not both. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optional anchor on the target page, without leading {#} — e.g. {oeffnungszeiten}. |

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

### `anchor` — ⚓ Anchor

block · Titel-Feld: `anchor_id` · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `richtext_block.body`, `accordion_item.content`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `anchor_id` | string | ✓ |  | Kleinbuchstaben, Zahlen, Bindestriche — z.B. "oeffnungszeiten". Achtung: nachträgliches Umbenennen bricht bestehende Links auf diesen Anker. |

### `spacer_section` — ↕️ Spacer

block · Titel-Feld: `size` · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `size` | string |  |  | Werte: `medium` · `large` · Default: `medium` — Zusätzlicher Abstand zum nächsten Abschnitt. |
| `background` | string |  |  | Werte: `auto` · `white` · `grey` · Default: `auto` — {auto} takes the colour of the next section and never splits a band; {white}/{grey} force the gap's colour. |

### `hero_slide` — 🖼️ Hero Slide

block · Einsatz: Baustein (`hero_slider.slides`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `media` | file | ✓ |  |  |
| `headline` | string | ✓ |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `hero_slider` — 🦸 Hero Slider

block · Einsatz: Header (`home_page.header`, `cms_page.header`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `slides` | rich_text |  |  | Blöcke: `hero_slide` |

### `page_intro` — 🦸 Page Intro

block · Einsatz: Header (`home_page.header`, `cms_page.header`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  | Optional heading shown above the lead text. |
| `lead` | text |  |  |  |
| `logo` | string |  |  | Werte: `none` · `talky` · `riotherm` · Default: `none` — Optional brand logo shown above the title. |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` — Band background. Consecutive blocks of the same colour merge into one band. |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `gallery` | gallery |  |  | Optional contained media (~12:7). A single item renders like the old single image; multiple items render as a slider with the same spacing. |
| `autoplay` | boolean |  |  | Default: `true` — Auto-advance the media slider. Only relevant when the gallery has more than one item; off means slides change on manual navigation only. |

### `statement_media_section` — 💬 Statement Media

block · Einsatz: Header + Section (`home_page.header`, `home_page.sections`, `cms_page.header`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `media` | file | ✓ |  |  |
| `statement` | text | ✓ |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `content_with_media_section` — 📰 Content with Media

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `kicker` | string |  |  | Optional second title line, e.g. "Der Design Tisch". |
| `heading` | string | ✓ |  |  |
| `body` | structured_text |  |  | Blöcke: `spec_table` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote — Format a paragraph as a quote to render it as large lead text. |
| `links` | rich_text |  |  | Blöcke: `nav_link` · max. 1 — A single link. Choose its appearance below. |
| `link_style` | string |  |  | Werte: `link` · `cta` · Default: `link` — "link" = inline text with arrow, "cta" = solid button. |
| `media` | file | ✓ |  | Roughly square. Videos play muted/autoplay without controls. |
| `media_position` | string |  |  | Werte: `left` · `right` · Default: `right` |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` |

### `sticky_scroll_entry` — 🗓️ Sticky Scroll Entry

block · Einsatz: Baustein (`sticky_scroll_section.entries`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `year` | string |  |  | Optional milestone year, e.g. "2025". |
| `heading` | string | ✓ |  |  |
| `body` | structured_text |  |  | Blöcke: `spec_table` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |
| `media` | file | ✓ |  | Shown in the sticky column while this entry is in view. |

### `sticky_scroll_section` — 📜 Sticky Scroll Text-Media

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

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
| `downloads` | rich_text |  |  | Blöcke: `download_item` — Optionale Download-Links, die unter dem Text des aktiven Tabs erscheinen. |

### `tabs_with_media_section` — 🗂️ Tabs with Media

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

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

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `columns` | rich_text |  |  | Blöcke: `text_column` |

### `richtext_block` — 📝 Richtext Block

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `body` | structured_text |  |  | Blöcke: `accordion`, `spec_table`, `anchor`, `download_item` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |

### `accordion_item` — ➕ Accordion Item

block · Einsatz: Baustein (`product.accordion_items`, `accordion.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ |  |  |
| `content` | structured_text |  |  | Blöcke: `spec_table`, `anchor`, `download_item` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |

### `accordion` — ➕ Accordion

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `richtext_block.body`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `items` | rich_text |  |  | Blöcke: `accordion_item` |

### `spec_row` — ▸ Spec Row

block · Einsatz: Baustein (`spec_table.rows`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `value` | text | ✓ |  |  |

### `spec_table` — 📋 Spec Table

block · Einsatz: Baustein (`product.body`, `available_model.specs`, `content_with_media_section.body`, `sticky_scroll_entry.body`, `richtext_block.body`, `accordion_item.content`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `rows` | rich_text |  |  | Blöcke: `spec_row` |

### `stat_item` — 📊 Stat

block · Einsatz: Baustein (`stats_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `value` | string | ✓ |  |  |
| `caption` | string |  |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `color` | string |  |  | Werte: `black` · `green` · `blue` · `red` · Default: `green` — Accent colour of the big value. |

### `stats_section` — 📊 Stats

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

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

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

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

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

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

### `media_slider_slide` — 🖼️ Media Slider Slide

block · Einsatz: Baustein (`media_slider_section.slides`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `media` | file | ✓ |  |  |

### `media_slider_section` — 🎞️ Media Slider

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `slides` | rich_text |  |  | Blöcke: `media_slider_slide` |
| `autoplay` | boolean |  |  | Default: `true` |
| `autoplay_duration` | integer |  |  | Default: `6` — Seconds each slide stays before auto-advancing (video slides run at least their own duration). |

### `reference_teasers_section` — 🏗️ Reference Teasers

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `references` | links |  |  | → `reference` — Leave empty to show the latest references. |
| `layout` | string |  |  | Werte: `editorial_rows` · `grid_3` · `grid_2` · `slider` · Default: `editorial_rows` |

### `available_models_section` — 📦 Available models

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `products` | links |  |  | → `product` — Optional — restrict to specific products. Leave empty to show all. |
| `solutions` | links |  |  | → `solution` — Optional — restrict to available models whose product belongs to these solutions. Leave empty to show all. |
| `layout` | string |  |  | Werte: `editorial_rows` · `grid_3` · `grid_2` · `slider` · Default: `grid_3` |
| `form` | rich_text |  |  | Blöcke: `hubspot_form_section` · max. 1 — Rendered once, below every model row — each model's CTA scrolls to it. |

### `teaser_link` — 🧲 Teaser Link

block · Einsatz: Baustein (`teaser_collection_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Pick a page OR fill the external URL below — not both. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optional #anchor on the target page. |
| `title` | string |  |  | Defaults to the linked target's title. |
| `text` | text |  |  | Optional short description shown under the title. |
| `image` | file |  |  | Defaults to the linked target's teaser image. |

### `teaser_collection_section` — 🧲 Teaser Collection

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `items` | rich_text |  |  | Blöcke: `teaser_link` |
| `layout` | string |  |  | Werte: `editorial_rows` · `grid_3` · `grid_2` · `slider` · Default: `grid_3` |

### `image_text_item` — 🖼️ Image Text Item

block · Einsatz: Baustein (`image_text_grid_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file | ✓ |  |  |
| `title` | string | ✓ |  |  |
| `text` | text |  |  |  |

### `image_text_grid_section` — 🖼️ Image Text Grid

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `items` | rich_text |  |  | Blöcke: `image_text_item` |
| `layout` | string |  |  | Werte: `grid_3` · `grid_2` · Default: `grid_3` |

### `collection_section` — 🗂️ Collection

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `source` | string | ✓ |  | Werte: `references` · Default: `references` — Which collection to list. More sources can be added later. |
| `show_filters` | boolean |  |  | Default: `true` — Render the visitor-facing facet filters above the list. |

### `contact_cta` — 📞 Contact CTA

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string | ✓ |  |  |
| `subline` | string |  |  |  |
| `person` | link |  |  | → `person` |
| `contact_page` | link |  |  | → `cms_page` — Target page for the CTA button, e.g. the contact form. Empty: falls back to the global contact page from the Website settings. |
| `background` | string |  |  | Werte: `white` · `black` · Default: `white` — white: light section · black: inverted dark section. |

### `link_list` — 🔗 Link List

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `items` | rich_text |  |  | Blöcke: `nav_link` |

### `quote_section` — ❝ Quote

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `quote` | text | ✓ |  |  |
| `attribution` | string |  |  |  |

### `hubspot_form_section` — HubSpot Form

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `website.pcon_contact_form`, `available_models_section.form`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `embed` | text | ✓ |  | Einfach aus HubSpot kopieren: Einbettungscode (Standard oder Entwickler) oder eine Formular-URL aus der HubSpot-App — Portal-ID, Formular-ID und Region werden automatisch erkannt. |

### `job_listing_section` — 💼 Job Listing

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `empty_note` | string |  |  | Shown instead of the list when no jobs are published. |

### `locations_section` — 📍 Locations

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `types` | links |  |  | → `location_type` — Limit the section to these groups — they also become its tabs. Leave empty to list every location. |

### `image_marquee` — 🎞️ Image Marquee

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file | ✓ |  |  |
| `marquee_texts` | text |  |  | One phrase per line. |

### `airflow_animation` — 🌬️ Airflow Animation

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `anchor` | string |  |  | Werte: `up` · `center` · `down` · Default: `up` — Bleed direction out of the 0px anchor. |

### `solution_slide` — 🧩 Solution Slide

block · Einsatz: Baustein (`solution_slider.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `image` | file |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `logo` | file |  |  |  |

### `solution_slider` — 🧩 Solution Slider

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string | ✓ |  |  |
| `items` | rich_text |  |  | Blöcke: `solution_slide` |

### `product_detail_section` — 🛋️ Product Detail Section

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  | Optional section title, e.g. "Grössen im Überblick". Stacked: above the product nav. Tabs: centered display title on the grey band. |
| `subtitle` | string |  |  | Optional line under the heading, e.g. "Für moderne Kontrollraumarbeitsplätze". Only shown in the Tabs variant. |
| `intro` | text |  |  | Optional short intro paragraph under the subtitle. Only shown in the Tabs variant. |
| `variant` | string |  |  | Werte: `stacked` · `plain` · `tabs` · Default: `stacked` — Stacked: sticky product nav + all products below each other. Plain: all products below each other, no nav. Tabs: pill tab nav, one product at a time. |
| `products` | links |  |  | → `product` |

### `download_item` — 📄 Download

block · Einsatz: Baustein (`product.body`, `media_tab.downloads`, `richtext_block.body`, `accordion_item.content`, `downloads_section.files`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `file` | file | ✓ |  |  |

### `downloads_section` — 📄 Downloads

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `description` | text |  |  | Optional intro paragraph under the heading. |
| `files` | rich_text |  |  | Blöcke: `download_item` |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |

### `pcon_configurator_section` — 🛋️ Konfigurator (pCon)

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `article` | string | ✓ |  | pCon-Basisartikelnummer («ban»), z. B. «Talky S109». |
| `manufacturer` | string |  |  | pCon-Herstellerkürzel («moc»). Leer lassen für den Standard «ERKE». |

### `product_carousel_section` — 🎠 Product Carousel

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`) · Zwei gegenläufige Bildbänder unter einer Überschrift (Produkt-Hero). Nur als erste Section direkt nach einem page_intro-Header.

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

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`) · Farbwechsel-Slider: durchlaufende Produktbilder, die das Header-Band einfärben. Nur als erste Section direkt nach einem page_intro-Header.

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `slides` | rich_text |  |  | Blöcke: `color_slider_slide` |

### `content_tab` — 📑 Content Tab

block · Einsatz: Baustein (`content_tab_nav_section.tabs`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `operator` | string |  |  | Optional decorative connector shown before this tab in the nav, e.g. {=} or {+} (Talky Village case). |
| `title` | string |  |  |  |
| `text` | text |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `image` | file | ✓ |  | Hotspots variant: the image's focal point marks where this tab's marker sits on the base image — all tab images must share the base image's canvas. |
| `image_mobile` | file |  |  | Optional art-directed image for narrow portrait screens. |

### `content_tab_nav_section` — 🎛️ Content Tab Nav

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `variant` | string |  |  | Werte: `tab_nav` · `hotspots` · Default: `tab_nav` — {tab_nav} = pill navigation pinned over the visual. {hotspots} = tab labels sit as markers on the base image (at each tab image's focal point) and open a flyout card. |
| `legend` | string |  |  | Accessible name for the tab group (visually hidden). Falls back to a default when empty. |
| `base_image` | file |  |  | Hotspots variant only: the neutral image shown while no marker is selected. Tab images swap in over it and must share its canvas. |
| `base_image_mobile` | file |  |  | Optional art-directed base image for narrow portrait screens (hotspots variant). |
| `tabs` | rich_text |  |  | Blöcke: `content_tab` |

### `flexible_image_setting` — 🎛️ Image Settings

block · Einsatz: Baustein (`flexible_image_section.base_settings`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `crop` | string |  |  | Percent cut off each side. Negative = the image bleeds outward past the container as margin-inline. |
| `margin_top` | string |  |  | Spacing above in pixels, negative allowed (overlaps the previous element). |
| `margin_bottom` | string |  |  | Spacing below in pixels, negative allowed. |

### `flexible_image_viewport` — 📐 Viewport Setting

block · Titel-Feld: `breakpoint` · Einsatz: Baustein (`flexible_image_section.viewport_settings`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `breakpoint` | string | ✓ |  | Werte: `xs` · `sm` · `md` · `lg` · `xl` · `xxl` — The values below apply beneath this width (desktop-first: the base settings apply above). Empty fields inherit from the next-wider setting. One entry per width — with duplicates the last one wins. |
| `crop` | string |  |  | Percent cut off each side. Negative = the image bleeds outward past the container as margin-inline. |
| `margin_top` | string |  |  | Spacing above in pixels, negative allowed (overlaps the previous element). |
| `margin_bottom` | string |  |  | Spacing below in pixels, negative allowed. |

### `flexible_image_section` — 🖼️ Flexible Image

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file | ✓ |  |  |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` — Color of the band behind this section. |
| `base_settings` | rich_text | ✓ |  | Blöcke: `flexible_image_setting` · max. 1 — Crop/margins for all viewports (the desktop view). Empty values = full width, no extra spacing. |
| `viewport_settings` | rich_text |  |  | Blöcke: `flexible_image_viewport` — Optional: deviations below a width (desktop-first, e.g. a tighter crop on mobile). |
