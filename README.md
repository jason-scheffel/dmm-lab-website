![on-push](../../actions/workflows/on-push.yaml/badge.svg)
![on-pull-request](../../actions/workflows/on-pull-request.yaml/badge.svg)
![on-schedule](../../actions/workflows/on-schedule.yaml/badge.svg)

# Data Management and Mining Lab Website

Visit **[jason-scheffel.github.io/dmm-lab-website](https://jason-scheffel.github.io/dmm-lab-website)**.

Built with the [Lab Website Template](https://greene-lab.gitbook.io/lab-website-template-docs).

## Updating Publications

The template supports more citation workflows than this README covers. The full docs are here: [Citations](https://greene-lab.gitbook.io/lab-website-template-docs/basics/citations).

The easiest paths are identifier entries and manual entries.

For normal publication updates, edit **only** this file:

```text
_data/sources.yaml
```

Do **not** edit `_data/citations.yaml`. That file is generated automatically by GitHub Actions and will be overwritten.

The publications page itself is here, but usually does not need edits:

```text
publications/index.md
```

### Option 1: Identifier

Use this when the paper has a DOI, arXiv ID, or another identifier supported by [Manubot](https://github.com/manubot/manubot/blob/main/manubot/cite/handlers.py#L155). Add one entry to `_data/sources.yaml`:

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

After the change is committed and pushed, GitHub Actions asks Manubot to fill in the title, authors, journal/conference, and date.

### Option 2: Manual Entry

Add the full details yourself in `_data/sources.yaml`:

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

then commit.
