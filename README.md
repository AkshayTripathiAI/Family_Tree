# Family Tree

An experimental family-tree visualizer built with D3.js. It reads people from `data.json` and draws them as a horizontal tree with draggable, colour-coded nodes.

> Status: work-in-progress prototype. The editing buttons are partly implemented.

## Features

- Loads family members from `data.json` and builds the hierarchy with `d3.stratify` (linked through the `mother` field)
- Horizontal tree layout with curved links (`d3.tree` + `d3.linkHorizontal`)
- Nodes coloured by sex (`M` / `F`), labelled with `display_name`
- Drag nodes to rearrange the layout
- Click a node to select it, then use the toolbar to add a child, parent, partner, stepbrother or stepsister, or delete the node
- Undo / Redo buttons (experimental)

`index_2.html` is an alternate version of the editor with Add Brother / Sister / Anonymous buttons and a stub for an edit popup. `familyTree.js` holds earlier iterations (static tree, drag, undo/redo); it is not loaded by the current `index.html`.

## Data format

`data.json` is an array of people:

```json
{ "name": "1", "display_name": "Name", "sex": "M", "age": "28", "mother": "3", "father": "2" }
```

`name` is the unique id; `mother` points to the parent node's id. Exactly one entry must have no `mother` (the root).

## Tech stack

- HTML, CSS, vanilla JavaScript
- [D3.js v7](https://d3js.org/) (loaded from CDN)

## Run locally

The page loads `data.json` with `fetch`, so it must be served over HTTP (opening the file directly will not work):

```bash
git clone https://github.com/AkshayTripathiAI/Family_Tree.git
cd Family_Tree
npx serve .
```

Then open the printed URL (or `/index_2.html` for the alternate version).

## Project structure

```
index.html     # current editor (D3 tree + toolbar)
index_2.html   # alternate editor variant
familyTree.js  # earlier iterations of the tree code
data.json      # family data
styles.css     # styles for the earlier static version
```
