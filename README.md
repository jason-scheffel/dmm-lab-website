![on-push](../../actions/workflows/on-push.yaml/badge.svg)
![on-pull-request](../../actions/workflows/on-pull-request.yaml/badge.svg)
![on-schedule](../../actions/workflows/on-schedule.yaml/badge.svg)

# Data Management and Mining Lab Website

Visit **[jason-scheffel.github.io/dmm-lab-website](https://jason-scheffel.github.io/dmm-lab-website)**.

Built with the [Lab Website Template](https://greene-lab.gitbook.io/lab-website-template-docs).

## Table of Contents

- [Modify Content](#modify-content)
- [People](#people)
- [Research](#research)
- [Publications](#publications)
- [Grants](#grants)
- [Software](#software)

## Modify Content

Most site content lives in small Markdown or YAML files. Edit the file for the item you want to change, then commit and push. GitHub Pages rebuilds the live site.

### People

Each person gets one file in `_members/`. The filename becomes the lookup name, so `_members/jane-doe.md` is used as `jane-doe`.

Photos go in `images/people/`. If no photo is available, leave out `image`.

#### Add Faculty

Create a file like `_members/jane-doe.md`:

```yaml
---
name: Prof. Jane Doe
image: images/people/jane-doe.jpg
description: Associate Professor
role: principal-investigator
affiliation: University at Albany - SUNY
links:
  home-page: https://example.com
---

Short bio goes here.
```

Then add this line under `## Faculty` in `people/index.md`:

```liquid
{% include person.html lookup="jane-doe" %}
```

#### Add PhD Student

Use the same pattern, with:

```yaml
description: PhD Student
role: phd
```

Then add the include under `## PhD Students` in `people/index.md`.

#### Add Undergraduate Student

Use:

```yaml
description: Undergraduate Student
role: undergrad
```

Then add the include under `## Undergraduate Students` in `people/index.md`.

#### Add Alumni

Use:

```yaml
description: PhD, 2024
role: alum
group: alum
```

Then add the include under `## Alumni` in `people/index.md`:

```liquid
{% include person.html lookup="jane-doe" style="compact" %}
```

### Research

Each research project gets one file in `_research/`. The research page lists these files automatically by `order`.

Create a file like `_research/06-example-project.md`:

```yaml
---
title: Example Research Project
image: images/research/example-project.jpg
order: 6
---

Project description goes here.
```

Use `order` to control the display order. Images are optional.

### Publications

The template supports more citation workflows than this README covers. Details are in the [citation docs](https://greene-lab.gitbook.io/lab-website-template-docs/basics/citations).

For this site, publications are pulled from Petko Bogdanov's Google Scholar profile:

```text
_data/google-scholar.yaml
```

The Google Scholar pull uses SerpAPI. The GitHub repository must have an Actions repository secret named `GOOGLE_SCHOLAR_API_KEY`.

Do **not** edit `_data/citations.yaml`. That file is generated automatically by GitHub Actions.

#### Add or Correct a Publication

Use `_data/sources.yaml` for manual additions, corrections, or removals.

If Google Scholar misses a paper and the paper has a DOI, arXiv ID, or another identifier supported by [Manubot](https://github.com/manubot/manubot/blob/main/manubot/cite/handlers.py#L155), add one entry:

Add one entry to `_data/sources.yaml`:

```yaml
- id: doi:10.xxxx/example
  type: paper
  link: https://publisher-page-for-the-paper
```

or:

```yaml
- id: arxiv:2309.09717
  type: paper
  link: https://arxiv.org/abs/2309.09717
```

If the automatic citation does not work, add the details manually:

```yaml
- title: Example Paper Title
  authors:
    - First Author
    - Petko Bogdanov
  publisher: Example Conference or Journal
  date: 2024-01-01
  link: https://link-to-paper
  type: paper
```

### Grants

Each grant gets one file in `_grants/`. The grants page lists these files automatically by `status` and `order`.

Create a file like `_grants/09-example-grant.md`:

```yaml
---
title: Example Grant Title
status: current
order: 90
funder: National Science Foundation
funder_url: https://www.nsf.gov/
amount: $500k
award_number: 1234567
award_url: https://www.nsf.gov/awardsearch/showAward?AWD_ID=1234567
duration: 9/24-8/27
project_url: https://example.com/project
---

Short grant summary goes here.
```

Use `status: current` or `status: past`. To hide a grant without deleting it, add `hidden: true`.

### Software

Each software entry gets one file in `_software/`. The software page lists these files automatically by `order`.

Images go in `images/software/`.

Create a file like `_software/17-example-software.md`:

```yaml
---
title: "Example Software [KDD'24]"
order: 170
image: images/software/example-software.png
image_width: 240px
links:
  - text: Matlab Code
    url: https://example.com/software.zip
    icon: fa-solid fa-code
citation: >-
  First Author and Petko Bogdanov,
  ["Example Paper Title"](https://example.com/paper.pdf),
  Conference Name, 2024.
---
```

Images and citations are optional. To hide a software entry without deleting it, add `hidden: true`.
