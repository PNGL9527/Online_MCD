# Mediation Composition Lab

A browser-based editor for the Mediation Composition Diagram (MCD), based on Peng Lu's NordiCHI 2026 paper:

**Granularity as Analytical Cut: A Diagrammatic Approach to Situated Mediation Analysis in Postphenomenological Design Research.**

https://doi.org/10.1145/3821402.3830102

## Run

Open `index.html` in a modern browser. There are no dependencies, build steps, accounts, API keys, or application server. For local HTTP serving, run `python3 -m http.server 8000` from this folder and open `http://localhost:8000`.

## Create an MCD

1. Select **New project**.
2. Name the project and define its **analytical focus** and **mediation granularity / analytical cut**. Describe what is distinguished, grouped, or left in the background. Add a rationale and situated context where useful.
3. Create the empty MCD, then add mediation relations.
4. Name each relation, select its dominant relation type, and adjust its relative impact, transparency, forefronting, and position. Drag markers or use the position controls.
5. Optionally assign a sedimentation assessment or a diffuse field-compositional influence, and record evidence or uncertainty.
6. Download **SVG** or **PNG** for a visual record; download **project JSON** to preserve editable data.

The original manual-driving and NoA-driving cases are retained as **Example A** and **Example B**. Duplicate a project to explore an independent configuration. Fresh examples can be added from Project details.

## Save and import

- The app automatically saves projects in browser local storage when available.
- Local storage belongs to the browser and page origin; it does not sync between devices, browsers, or hosting addresses. Clearing browser data may remove projects.
- **Save project** downloads one `.mcd.json` file containing the granularity definition, context, relations, notes, positions, and visual settings.
- **Import project** restores this file as a separate project; it does not replace an existing one.
- SVG and PNG exports include the current diagram, its granularity description, and its visual legend. They are visual snapshots rather than editable project backups.
- PNG output is generated at twice the SVG's pixel dimensions.
- User-created diagrams are not transmitted to a server. The DOI link opens the external paper page only when selected.

## Static hosting

The repository root should contain:

```
index.html
README.md
.nojekyll
```

These files can be served by a static host, including GitHub Pages. No backend is needed. GitHub hosts the application files; visitors' MCD projects remain in their own browsers or downloaded files.

For GitHub Pages, upload the contents of this folder to a repository. In the repository's **Settings → Pages**, choose **Deploy from a branch**, select the branch containing these files and **/(root)**, then save. GitHub's current guide is the authoritative reference:

https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## Theoretical scope

The paper's encoding is retained: shape indicates dominant relation type; size indicates relative impact; opacity indicates transparency; position indicates forefronting. Mediation granularity is a selective analytical cut, not a universal artifact hierarchy or a numeric zoom level.

**Exploratory additions in this implementation:** the granularity-definition workflow, radial positioning controls, editable field-influence regions, and sedimentation colour encoding. Sedimentation uses light sand to deep brick red, independently of transparency. Grey dashed markers indicate unassessed sedimentation. Example scores and positions are illustrative drawing conventions, not empirical measurements; the paper does not provide sedimentation ratings.

This is an editor for situated configurations. It does not model how sedimentation develops through time or automatically verify the analytical cut. Revised cuts require the analyst to review the relation units.

## Implementation

Single self-contained HTML file with inline CSS and JavaScript; native SVG rendering, Canvas PNG export, browser local storage, and JSON import/export. Version 0.2. Data files identify themselves as `mcd-lab-project`, version `2`.

Validation covered new-project prerequisites, empty diagrams, relation editing and dragging, independent dimension storage, browser reload, JSON roundtrip, invalid imports, SVG/PNG downloads, and mobile page overflow.
