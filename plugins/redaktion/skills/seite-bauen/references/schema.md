# DatoCMS-Schema erichkeller.ch — Referenz

<!-- GENERIERT aus scripts/schema/ im Website-Repo — nicht von Hand editieren. Regenerieren: npm run editors-plugin:refs -->

Sprachen: `de` (Hauptsprache), `en`, `fr`. **Lok ✓** = lokalisiertes Feld: beim Schreiben immer alle drei Locale-Keys angeben (Wert darf `null` sein). **Pflicht ✓** = required-Validator. Feldtyp `rich_text` = Modular Content (Block-Liste), `file` = einzelnes Asset, `links`/`link` = Verweis(e) auf Records. CMA-Wert-Formate und fertige Scripts: siehe `docs/cma-rezepte.md` im Plugin.

## Modelle (Records)

| api_key | Art | Label |
| --- | --- | --- |
| `home_page` | singleton | 🏠 Startseite |
| `cms_page` | tree (Seitenbaum) | 📄 CMS-Seite |
| `solution` | collection | 💡 Geschäftsbereich |
| `product_family` | collection | 🧩 Produktfamilie |
| `product` | collection | 🛋️ Produkt |
| `available_model` | collection | 📦 Verfügbares Modell |
| `industry` | collection | 🏭 Branche |
| `project_type` | collection | 🏷️ Raum- / Objekttyp |
| `project_kind` | collection | 🔨 Projektart |
| `project_volume` | collection | 💰 Projektvolumen |
| `reference` | collection | 🏗️ Referenz |
| `person` | collection | 👤 Person |
| `location_type` | collection | 🏷️ Standort-Typ |
| `location` | collection | 📍 Standort |
| `translation` | collection | 🌐 Übersetzung |
| `website` | singleton | ⚙️ Website |
| `redirect` | collection | ↪️ Redirect |
| `slide_deck` | collection | 🎞️ Slide-Deck |

### `home_page` — 🏠 Startseite

singleton

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `seo` | seo |  | ✓ |  |
| `header` | rich_text |  | ✓ | Blöcke: `hero_slider`, `page_intro`, `statement_media_section` · max. 1 |
| `sections` | rich_text |  | ✓ | Blöcke: `anchor`, `spacer_section`, `statement_media_section`, `content_with_media_section`, `sticky_scroll_section`, `tabs_with_media_section`, `text_columns_section`, `richtext_block`, `accordion`, `stats_section`, `facts_figures_section`, `pikto_section`, `media_block`, `external_video_block`, `media_slider_section`, `reference_teasers_section`, `available_models_section`, `teaser_collection_section`, `image_text_grid_section`, `collection_section`, `contact_cta`, `link_list`, `quote_section`, `quotes_slider_section`, `hubspot_form_section`, `job_listing_section`, `locations_section`, `image_marquee`, `airflow_animation`, `solution_slider`, `product_detail_section`, `downloads_section`, `pcon_configurator_section`, `product_carousel_section`, `color_slider_section`, `content_tab_nav_section`, `flexible_image_section` |

### `cms_page` — 📄 CMS-Seite

tree (Seitenbaum)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `title` |
| `seo` | seo |  | ✓ |  |
| `header` | rich_text |  | ✓ | Blöcke: `hero_slider`, `page_intro`, `statement_media_section` · max. 1 |
| `sections` | rich_text |  | ✓ | Blöcke: `anchor`, `spacer_section`, `statement_media_section`, `content_with_media_section`, `sticky_scroll_section`, `tabs_with_media_section`, `text_columns_section`, `richtext_block`, `accordion`, `stats_section`, `facts_figures_section`, `pikto_section`, `media_block`, `external_video_block`, `media_slider_section`, `reference_teasers_section`, `available_models_section`, `teaser_collection_section`, `image_text_grid_section`, `collection_section`, `contact_cta`, `link_list`, `quote_section`, `quotes_slider_section`, `hubspot_form_section`, `job_listing_section`, `locations_section`, `image_marquee`, `airflow_animation`, `solution_slider`, `product_detail_section`, `downloads_section`, `pcon_configurator_section`, `product_carousel_section`, `color_slider_section`, `content_tab_nav_section`, `flexible_image_section` |

### `solution` — 💡 Geschäftsbereich

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |
| `icon` | file |  |  |  |

### `product_family` — 🧩 Produktfamilie

collection · manuell sortierbar · Titel-Feld: `label`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `label` |
| `solution` | link | ✓ |  | → `solution` |
| `page` | link |  |  | → `cms_page` — Die Produkt-Detailseite, auf der diese Familie vorgestellt wird. |

### `product` — 🛋️ Produkt

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `subtitle` | string |  | ✓ | Kurze Zeile unter dem Titel, z. B. {Effizienter Kaltwassersatz} oder {Für 1 Person}. |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |
| `product_family` | link |  |  | → `product_family` — Die Familie, zu der dieses Produkt gehört — definiert auch den Geschäftsbereich. |
| `solution` | link |  |  | → `solution` — DEPRECATED — der Geschäftsbereich ergibt sich neu aus der Produktfamilie. Feld wird nach der Umstellung entfernt. |
| `teaser_image` | file |  |  |  |
| `body` | structured_text |  | ✓ | Blöcke: `spec_table`, `download_item` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |
| `specs` | text |  |  | Z. B. {Für 1 Person / Aussenmasse: … / Innenmasse: …} |
| `links` | rich_text |  |  | Blöcke: `nav_link` — Optionale Links im Text, z. B. {Verfügbare Modelle} oder {Konfigurator}. |
| `accordion_items` | rich_text |  |  | Blöcke: `accordion_item` |
| `gallery` | gallery |  |  |  |
| `seo` | seo |  | ✓ |  |

### `available_model` — 📦 Verfügbares Modell

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string |  | ✓ | Optional — leer lassen: es gilt der Name des verlinkten Produkts. |
| `product` | link | ✓ |  | → `product` |
| `external_id` | string |  |  | Z. B. eine ERP- oder Dualoo-Artikelnummer. Wird beim Klick auf den CTA dieses Modells in das versteckte Feld {talky_produkt_id} des Anfrageformulars geschrieben. |
| `teaser_image` | file |  |  | Optional — leer lassen: es gilt das Teaser-Bild des verlinkten Produkts. |
| `gallery` | gallery |  |  |  |
| `specs` | rich_text |  | ✓ | Blöcke: `spec_table` — Attributzeilen, z. B. Aussenfarbe: weiss / Stofffarbe: hellgrau / Bodenbelag: Teppich dunkel / … |
| `description` | structured_text |  | ✓ | Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote — Freitext, z. B. Zustand, Standort, Lieferhinweis. |

### `industry` — 🏭 Branche

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |

### `project_type` — 🏷️ Raum- / Objekttyp

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |

### `project_kind` — 🔨 Projektart

collection · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |

### `project_volume` — 💰 Projektvolumen

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `name` |

### `reference` — 🏗️ Referenz

collection · Titel-Feld: `title`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `slug` | slug |  | ✓ | abgeleitet aus `title` |
| `teaser_image` | file |  |  |  |
| `intro` | text |  | ✓ | Lead-Absatz im generierten Referenz-Header. |
| **Fieldset «Referenz-Attribute»** | | | | Steuert die Filter in der Referenzübersicht und die Attributliste im Header. |
| `project_types` | links |  |  | → `project_type` |
| `industries` | links |  |  | → `industry` |
| `product_families` | links |  |  | → `product_family` — Produktfamilien, die in dieser Referenz eingesetzt sind — definieren auch den Geschäftsbereich. |
| `solutions` | links |  |  | → `solution` — DEPRECATED — der Geschäftsbereich ergibt sich neu aus den Produktfamilien. Feld wird nach der Umstellung entfernt. |
| `products` | links |  |  | → `product` — DEPRECATED — Referenzen verlinken neu Produktfamilien statt einzelne Produkte. Feld wird nach der Umstellung entfernt. |
| `project_kinds` | links |  |  | → `project_kind` — Neubau, Umbau, … — Kombinationen möglich. |
| `year` | integer |  |  | Jahr der Fertigstellung. |
| `volume` | link |  |  | → `project_volume` |
| `location` | string |  | ✓ | Freitext, z. B. {Zürich}. |
| `rating` | string |  |  | Werte: `1` · `2` · `3` — Interne redaktionelle Bewertung — erscheint nicht auf der Website. |
| `specs` | single_block | ✓ | ✓ | Freie Attributzeilen, die am Seitenende als Tabelle erscheinen, z. B. Architekt, Planer, Bauherrschaft. |
| `related_references` | links |  |  | → `reference` — Optional. Leer lassen — verwandte Referenzen werden automatisch aus den Attributen ermittelt. Hier gesetzte Referenzen stehen zuoberst, der Rest wird automatisch aufgefüllt (max. 3 Karten). |
| `seo` | seo |  | ✓ |  |
| `sections` | rich_text |  | ✓ | Blöcke: `richtext_block`, `media_block`, `external_video_block` |

### `person` — 👤 Person

collection · Titel-Feld: `internal_label`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `internal_label` | string | ✓ |  | Nur für die Redaktion: Titel dieses Datensatzes in Listen und Auswahlfeldern. |
| `name` | string | ✓ |  |  |
| `role` | string |  | ✓ |  |
| `phone` | string |  |  | Internationales Format, z. B. {+41 71 644 88 88} — wird als tel:-Link ausgegeben. |
| `email` | string |  |  | Persönliche oder Team-Adresse, z. B. {vorname.nachname@erichkeller.com} — wird als mailto:-Link ausgegeben. |
| `contact_url` | string |  |  | Optionaler Link für den Kontakt-Slide, z. B. eine Buchungs- oder Profilseite. Vollständige URL inkl. {https://}. |
| `portrait` | file |  |  |  |
| `solution` | link |  |  | → `solution` — Hauptgeschäftsbereich dieser Person — filtert die Kontaktauswahl im Deck-Konfigurator. |
| **Fieldset «Kontaktsprachen»** | | | | Sprachen, in denen diese Person kontaktiert werden kann. |
| `lang_de` | boolean |  |  | Default: `true` |
| `lang_en` | boolean |  |  |  |
| `lang_fr` | boolean |  |  |  |

### `location_type` — 🏷️ Standort-Typ

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ | ✓ | Tab-Label in der Standort-Section, z. B. {Arbeitsplatzlösungen Showrooms}. |

### `location` — 📍 Standort

collection · manuell sortierbar · Titel-Feld: `name`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `name` | string | ✓ |  |  |
| `types` | links | ✓ |  | → `location_type` — Unter welchen Gruppen dieser Standort erscheint. Mehrere wählen, wenn er in mehr als einen Tab gehört. |
| `image` | file |  |  | Innenaufnahme bei einem Showroom, Firmenlogo bei einem Partner. |
| `street` | string |  |  | z. B. {Romanshornstrasse 17} |
| `postal_code` | string |  |  | z. B. {8583} |
| `city` | string |  |  | z. B. {Sulgen} |
| `country` | string |  | ✓ | Nur für Standorte im Ausland — bei Schweizer Adressen leer lassen. Z. B. {Niederlande}. |
| `phone` | string |  |  | Internationales Format, z. B. {+41 71 644 88 88} — wird als tel:-Link ausgegeben. |
| `email` | string |  |  | Optionale Adresse für diesen Standort, z. B. {info@partner.ch} — wird als mailto:-Link ausgegeben. |
| `website_url` | string |  |  | Optionaler Link auf die eigene Website dieses Standorts (vor allem bei Partnern). Vollständige URL inkl. {https://}. |
| `coordinates` | lat_lon |  |  | Der Kartenpunkt. Adresse suchen, danach den Pin für die Feinjustierung verschieben. |
| `directions_url` | string |  |  | Optional, vollständige URL inkl. {https://}. Leer lassen: es wird auf die Google-Maps-Route zur obigen Adresse verlinkt. |
| `solutions` | links |  |  | → `solution` — Welche Geschäftsbereiche dieser Standort abdeckt. Wird noch nicht gefiltert — für später erfasst. |
| `kind` | string |  |  | Werte: `showroom` · `partner` · Default: `showroom` — DEPRECATED — ersetzt durch {Typen} oben und wird nicht mehr ausgegeben. Nicht bearbeiten; das Feld wird gelöscht. |

### `translation` — 🌐 Übersetzung

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
| `reference_parent` | link |  |  | → `cms_page` — Referenzen werden unter dieser Seite publiziert: {pfad-der-seite}/{referenz-slug}. Ihre URLs und Sitemap-Einträge hängen davon ab. |
| `job_parent` | link |  |  | → `cms_page` — Jobseiten (aus dem Dualoo-Feed) werden unter dieser Seite publiziert: {pfad-der-seite}/{job-slug}. |
| `contact_page` | link |  |  | → `cms_page` — Globale Kontakt- bzw. Formularseite — Ziel für alle Contact-CTA-Buttons ohne eigene Kontaktseite. |
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

### `slide_deck` — 🎞️ Slide-Deck

collection · manuell sortierbar · Titel-Feld: `title`

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `title` | string | ✓ | ✓ |  |
| `solution` | link |  |  | → `solution` — Gruppiert das Deck in der Auswahl des Konfigurators. Leer lassen für allgemeine Decks. |
| `slides` | gallery |  | ✓ | Ein Bild pro Slide, 16:9 {1920x1080px oder grösser}. Aus PowerPoint über Speichern unter, Format PNG, exportieren. |

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
| `external_video_block` | ▶️ External Video | Section |
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
| `quotes_slider_section` | ❝ Quotes Slider | Section |
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
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Entweder eine Seite wählen ODER unten die externe URL ausfüllen — nicht beides. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optionaler Anker auf der Zielseite. Die Auswahl zeigt die Anker der verlinkten Seite; von Hand eingetippt ohne {#}, z. B. {oeffnungszeiten}. |

### `menu_link` — 🧭 Menu Link

block · Einsatz: Baustein (`menu_group.overview_link`, `menu_group.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Entweder eine Seite wählen ODER unten die externe URL ausfüllen — nicht beides. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optionaler Anker auf der Zielseite, ohne führendes {#} — z. B. {oeffnungszeiten}. |
| `image` | file |  |  | Optional. Erscheint beim Hover im Mega-Menü des Headers. |

### `menu_group` — 🧭 Menu Group

block · Einsatz: Baustein (`website.header_navigation`, `website.footer_navigation`, `menu_group.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `label` | string | ✓ |  |  |
| `overview_link` | rich_text |  |  | Blöcke: `menu_link` · max. 1 — Optional. Die Übersichtsseite der Gruppe (die Zeile {Zur Übersicht}). |
| `items` | rich_text |  |  | Blöcke: `menu_link`, `menu_group` |

### `anchor` — ⚓ Anchor

block · Titel-Feld: `anchor_id` · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `richtext_block.body`, `accordion_item.content`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `anchor_id` | string | ✓ |  | Kleinbuchstaben, Zahlen, Bindestriche — z. B. {oeffnungszeiten}. Achtung: nachträgliches Umbenennen bricht bestehende Links auf diesen Anker. |

### `spacer_section` — ↕️ Spacer

block · Titel-Feld: `size` · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `size` | string |  |  | Werte: `medium` · `large` · Default: `medium` — Zusätzlicher Abstand zum nächsten Abschnitt. |
| `background` | string |  |  | Werte: `auto` · `white` · `grey` · Default: `auto` — Weiss/Grau erzwingen die Farbe des Abstands. |

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
| `heading` | string |  |  | Optionale Überschrift über dem Lead-Text. |
| `lead` | text |  |  |  |
| `logo` | string |  |  | Werte: `none` · `talky` · `riotherm` · Default: `none` — Optionales Marken-Logo über dem Titel. |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` — Hintergrund des Farbbands. Aufeinanderfolgende Blöcke mit derselben Farbe verschmelzen zu einem Band. |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `gallery` | gallery |  |  | Optionale Medien im Satzspiegel (ca. 12:7). Ein einzelner Eintrag erscheint als einzelnes Bild, mehrere Einträge als Slider mit denselben Abständen. |
| `autoplay` | boolean |  |  | Default: `true` — Schaltet den Medien-Slider automatisch weiter. Nur relevant, wenn die Galerie mehr als einen Eintrag hat; aus heisst: nur manuelle Navigation. |

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
| `kicker` | string |  |  | Optionale zweite Titelzeile, z. B. {Der Design Tisch}. |
| `heading` | string | ✓ |  |  |
| `body` | structured_text |  |  | Blöcke: `spec_table` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote — Ein Absatz im Zitat-Format wird als grosser Lead-Text ausgegeben. |
| `links` | rich_text |  |  | Blöcke: `nav_link` · max. 1 — Ein einzelner Link. Das Erscheinungsbild wird unten gewählt. |
| `link_style` | string |  |  | Werte: `link` · `cta` · Default: `link` |
| `media` | file | ✓ |  | Ungefähr quadratisch. Videos laufen stumm und automatisch, ohne Bedienelemente. |
| `media_position` | string |  |  | Werte: `left` · `right` · Default: `right` |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` |

### `sticky_scroll_entry` — 🗓️ Sticky Scroll Entry

block · Einsatz: Baustein (`sticky_scroll_section.entries`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `year` | string |  |  | Optionale Jahreszahl, z. B. {2025}. |
| `heading` | string | ✓ |  |  |
| `body` | structured_text |  |  | Blöcke: `spec_table` · Record-Links: `cms_page`, `reference`, `product` · Headings: h3–h6 · Marks: strong, underline, strikethrough · Nodes: heading, list, link, blockquote |
| `media` | file | ✓ |  | Erscheint in der Sticky-Spalte, solange dieser Eintrag im Blickfeld ist. |

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
| `color` | string |  |  | Werte: `black` · `green` · `blue` · `red` · Default: `green` — Akzentfarbe der grossen Zahl. |

### `stats_section` — 📊 Stats

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `items` | rich_text |  |  | Blöcke: `stat_item` |
| `variant` | string |  |  | Werte: `standard` · `riotherm` · Default: `standard` |

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
| `icon` | file |  |  | Einfarbiges Linien-Icon (SVG), ca. 64×64. |
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

### `external_video_block` — ▶️ External Video

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `reference.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `video` | video | ✓ |  | Normale Watch-URL einfügen, z. B. {https://www.youtube.com/watch?v=…} oder {https://vimeo.com/…} — das Vorschaubild kommt automatisch vom Anbieter. |
| `layout` | string |  |  | Werte: `full_bleed` · `contained` · Default: `contained` |
| `autoplay` | boolean |  |  | Startet stumm und in Schleife, sobald das Video ins Blickfeld scrollt, statt einen Play-Button zu zeigen. Achtung: lädt den Player des Anbieters (und dessen Cookies) ohne Klick. |
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
| `autoplay_duration` | integer |  |  | Default: `6` — Sekunden, die ein Slide stehen bleibt, bevor automatisch weitergeschaltet wird (Video-Slides laufen mindestens ihre eigene Dauer). |

### `reference_teasers_section` — 🏗️ Reference Teasers

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `references` | links |  |  | → `reference` — Leer lassen, um automatisch die neusten Referenzen zu zeigen. |
| `layout` | string |  |  | Werte: `editorial_rows` · `grid_3` · `grid_2` · `slider` · Default: `editorial_rows` |

### `available_models_section` — 📦 Available models

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `products` | links |  |  | → `product` — Optional — nur diese Produkte zeigen. Leer lassen für alle. |
| `solutions` | links |  |  | → `solution` — Optional — nur Modelle zeigen, deren Produkt zu diesen Geschäftsbereichen gehört. Leer lassen für alle. |
| `layout` | string |  |  | Werte: `editorial_rows` · `grid_3` · `grid_2` · `slider` · Default: `grid_3` |
| `form` | rich_text |  |  | Blöcke: `hubspot_form_section` · max. 1 — Erscheint einmal unter allen Modellzeilen — der CTA jedes Modells scrollt dorthin. |

### `teaser_link` — 🧲 Teaser Link

block · Einsatz: Baustein (`teaser_collection_section.items`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `page` | link |  |  | → `cms_page`, `home_page`, `reference` — Entweder eine Seite wählen ODER unten die externe URL ausfüllen — nicht beides. |
| `external_url` | string |  |  |  |
| `anchor` | string |  |  | Optionaler Anker auf der Zielseite, ohne führendes {#} — z. B. {oeffnungszeiten}. |
| `title` | string |  |  | Leer lassen: es gilt der Titel des verlinkten Ziels. |
| `text` | text |  |  | Optionaler Kurztext unter dem Titel. |
| `image` | file |  |  | Leer lassen: es gilt das Teaser-Bild des verlinkten Ziels. |

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
| `source` | string | ✓ |  | Werte: `references` · Default: `references` — Welche Sammlung aufgelistet wird. Weitere Quellen können später dazukommen. |
| `show_filters` | boolean |  |  | Default: `true` — Blendet die Filterleiste über der Liste ein. |

### `contact_cta` — 📞 Contact CTA

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string | ✓ |  |  |
| `subline` | string |  |  |  |
| `person` | link |  |  | → `person` |
| `contact_page` | link |  |  | → `cms_page` — Zielseite des CTA-Buttons, z. B. das Kontaktformular. Leer: es gilt die globale Kontaktseite aus den Website-Einstellungen. |
| `background` | string |  |  | Werte: `white` · `black` · Default: `white` |

### `link_list` — 🔗 Link List

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `text` | structured_text |  |  | Record-Links: `cms_page`, `reference`, `product` · Headings:  · Marks: strong, underline, strikethrough · Nodes: link |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `items` | rich_text |  |  | Blöcke: `nav_link` |

### `quote_section` — ❝ Quote

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`, `quotes_slider_section.quotes`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `quote` | text | ✓ |  |  |
| `attribution` | string |  |  |  |

### `quotes_slider_section` — ❝ Quotes Slider

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `quotes` | rich_text | ✓ |  | Blöcke: `quote_section` · max. 5 — 1–5 Zitate, einzeln nacheinander gezeigt; beim Scrollen durch die Section wird zum nächsten Zitat übergeblendet. |

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
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 — Mit Link (z. B. auf die vollständige Jobseite) wird der Block zum Teaser: Es erscheinen nur die 3 neusten Jobs. Ohne Link werden alle offenen Stellen gelistet. |
| `empty_note` | string |  |  | Erscheint statt der Liste, wenn keine Jobs publiziert sind. |

### `locations_section` — 📍 Locations

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `heading` | string |  |  |  |
| `intro` | text |  |  |  |
| `types` | links |  |  | → `location_type` — Beschränkt die Section auf diese Gruppen — sie werden auch zu den Tabs. Leer lassen, um alle Standorte zu listen. |

### `image_marquee` — 🎞️ Image Marquee

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file | ✓ |  |  |
| `marquee_texts` | text |  |  | Ein Begriff pro Zeile. |

### `airflow_animation` — 🌬️ Airflow Animation

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `anchor` | string |  |  | Werte: `up` · `center` · `down` · Default: `up` — In welche Richtung die Animation aus ihrem 0px hohen Anker herausragt. |

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
| `heading` | string |  |  | Optionaler Titel der Section, z. B. {Grössen im Überblick}. Stacked: über der Produkt-Navigation. Tabs: zentriert auf dem grauen Band. |
| `subtitle` | string |  |  | Optionale Zeile unter der Überschrift, z. B. {Für moderne Kontrollraumarbeitsplätze}. Nur in der Variante Tabs sichtbar. |
| `intro` | text |  |  | Optionaler kurzer Einleitungstext unter dem Untertitel. Nur in der Variante Tabs sichtbar. |
| `variant` | string |  |  | Werte: `stacked` · `plain` · `tabs` · Default: `stacked` |
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
| `description` | text |  |  | Optionaler Einleitungstext unter der Überschrift. |
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
| `color` | string | ✓ |  | Hex-Farbe, z. B. {#B5BF9C} — färbt das Header-Band, wenn dieses Bild in der Mitte steht. |

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
| `operator` | string |  |  | Optionales dekoratives Verbindungszeichen vor diesem Tab in der Navigation, z. B. {=} oder {+} (Fall Talky Village). |
| `title` | string |  |  |  |
| `text` | text |  |  |  |
| `link` | rich_text |  |  | Blöcke: `nav_link` · max. 1 |
| `image` | file | ✓ |  | Variante Hotspots: Der Fokuspunkt des Bildes bestimmt, wo der Marker dieses Tabs auf dem Basisbild sitzt — alle Tab-Bilder brauchen denselben Bildausschnitt wie das Basisbild. |
| `image_mobile` | file |  |  | Optionales, eigens gewähltes Bild für schmale Hochformat-Bildschirme. |

### `content_tab_nav_section` — 🎛️ Content Tab Nav

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `variant` | string |  |  | Werte: `tab_nav` · `hotspots` · Default: `tab_nav` |
| `legend` | string |  |  | Bezeichnung der Tab-Gruppe für Screenreader (visuell nicht sichtbar). Leer: es gilt ein Standardtext. |
| `base_image` | file |  |  | Nur Variante Hotspots: das neutrale Bild, solange kein Marker gewählt ist. Die Tab-Bilder werden darüber eingeblendet und brauchen denselben Bildausschnitt. |
| `base_image_mobile` | file |  |  | Optionales, eigens gewähltes Basisbild für schmale Hochformat-Bildschirme (Variante Hotspots). |
| `tabs` | rich_text |  |  | Blöcke: `content_tab` |

### `flexible_image_setting` — 🎛️ Image Settings

block · Einsatz: Baustein (`flexible_image_section.base_settings`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `crop` | string |  |  | Prozent, die auf jeder Seite weggeschnitten werden. Negativ = das Bild ragt über den Container hinaus. |
| `margin_top` | string |  |  | Abstand nach oben in Pixel, negative Werte erlaubt (überlappt das vorherige Element). |
| `margin_bottom` | string |  |  | Abstand nach unten in Pixel, negative Werte erlaubt. |

### `flexible_image_viewport` — 📐 Viewport Setting

block · Titel-Feld: `breakpoint` · Einsatz: Baustein (`flexible_image_section.viewport_settings`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `breakpoint` | string | ✓ |  | Werte: `xs` · `sm` · `md` · `lg` · `xl` · `xxl` — Die Werte unten gelten unterhalb dieser Breite (Desktop first: darüber gelten die Basis-Einstellungen). Leere Felder erben von der nächstbreiteren Einstellung. Pro Breite ein Eintrag — bei Duplikaten gewinnt der letzte. |
| `crop` | string |  |  | Prozent, die auf jeder Seite weggeschnitten werden. Negativ = das Bild ragt über den Container hinaus. |
| `margin_top` | string |  |  | Abstand nach oben in Pixel, negative Werte erlaubt (überlappt das vorherige Element). |
| `margin_bottom` | string |  |  | Abstand nach unten in Pixel, negative Werte erlaubt. |

### `flexible_image_section` — 🖼️ Flexible Image

block · Einsatz: Section (`home_page.sections`, `cms_page.sections`)

| Feld | Typ | Pflicht | Lok | Details |
| --- | --- | :-: | :-: | --- |
| `image` | file | ✓ |  |  |
| `background` | string |  |  | Werte: `white` · `grey` · Default: `white` — Farbe des Bands hinter dieser Section. |
| `base_settings` | rich_text | ✓ |  | Blöcke: `flexible_image_setting` · max. 1 — Beschnitt und Abstände für alle Viewports (die Desktop-Ansicht). Leere Werte = volle Breite, keine zusätzlichen Abstände. |
| `viewport_settings` | rich_text |  |  | Blöcke: `flexible_image_viewport` — Optional: Abweichungen unterhalb einer bestimmten Breite (Desktop first, z. B. ein engerer Beschnitt auf Mobile). |
