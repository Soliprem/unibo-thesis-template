# Unibo Thesis

This is an unofficial thesis template for unibo. While I made it by looking at
the requirements from the Economics department, it's made to be highly
configurable, and hopefully fine for any programme. If not, feel free to open a
PR.

Provides two public functions:

- `thesis_cover`: renders a standalone cover page
- `thesis`: full document setup (cover + abstract + ToC + body)

Typical usage:

```typst
#import "template.typ": thesis

#show: thesis.with(
    title: "My Dissertation",
    author: "Jane Doe",
    student_number: "1234567",
    supervisor: "Prof. John Smith",
    program: "Economics",
    degree: "Master's Degree",
    department: "Department of Economics",
    academic_year: "2024/2025",
    graduation_month: "March",
    abstract: [Your abstract text here.],
    locale: "en", // can also be "it"
)

= Introduction
...
#bibliography("references.bib", style: "apa")
```

If you only need the cover page (e.g. to prepend to an existing document), you
can use thesis_cover directly:

```typst
#import "@preview/unibo-thesis:0.1.0": thesis_cover

#thesis_cover(
  title: "My Dissertation",
  author: "Jane Doe",
  ...
)
```

## Configuration

All parameters have what I think are sensible defaults and can be omitted if not
needed.

| Parameter          | Description                                                              | Default                 |
| ------------------ | ------------------------------------------------------------------------ | ----------------------- |
| `title`            | Dissertation title                                                       | —                       |
| `author`           | Candidate's full name                                                    | —                       |
| `student_number`   | Matriculation number                                                     | —                       |
| `supervisor`       | Supervisor's name and title                                              | —                       |
| `program`          | Degree programme name                                                    | —                       |
| `degree`           | Degree type (e.g. `"Master's Degree"`)                                   | —                       |
| `department`       | Full department name                                                     | —                       |
| `academic_year`    | Academic year (e.g. `"2024/2025"`)                                       | —                       |
| `graduation_month` | Month of the graduation session                                          | —                       |
| `abstract`         | Abstract content block; omit to skip                                     | `none`                  |
| `abstract_title`   | Override the abstract heading text                                       | locale default          |
| `toc`              | Whether to render a table of contents                                    | `true`                  |
| `font`             | Body font                                                                | `"New Computer Modern"` |
| `cover_font`       | Cover page font (can differ from body)                                   | `"New Computer Modern"` |
| `locale`           | `"en"` or `"it"` (controls built-in label translations, and lang option) | `"en"`                  |
| `labels`           | Override the template's localised strings manually (see below)           | `none`                  |

### Localisation

Setting `locale: "it"` switches the cover labels to Italian (`CANDIDATO`,
`RELATORE`, etc.). For any other language, pass a `labels` dict directly:

```typst
#show: thesis.with(
  locale: "de",
  labels: (
    defended_by: "VORGELEGT VON",
    supervisor: "BETREUER",
    in_word: "in",
    graduation_session: "Abschlussprüfung",
    academic_year: "Akademisches Jahr",
    abstract_title: "Zusammenfassung",
  ),
  ...
)
```

## License

GPL-3.0-or-later
