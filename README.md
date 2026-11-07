# Eagle Generation Bible School

A static replica of the public marketing site at `eaglegenbibleschool.com` —
hand-written HTML, CSS and vanilla JavaScript. No framework, no build step,
nothing to install.

## Run it

```
python3 -m http.server 8000
```

Open `http://localhost:8000`. You do need a server: a few pages `fetch` their
data, which `file://` blocks.

## What's here

```
*.html        10 pages, plus course.html (one programme, by ?id=) and 404.html
css/          tokens → base → layout → components, in that order
js/           header/footer, icons, forms, reveal-on-scroll, the map loader
data/         courses, faculty, FAQs, resources, legal copy — as JSON
assets/       logo, icons, photographs

The brand colour is gold (`--accent: #a87e1e` in `css/tokens.css`). The live
site's stylesheet also declares a red accent, but never renders it — it's a
leftover shadcn default. `plan.md` has the story.

## Editing content

Most copy lives in `data/*.json`. Two different things happen with it:

- **`courses.html` and `course.html` fetch it at runtime.** Edit the JSON, reload
  the page, done.
- **`our-faculty.html`, `faq.html`, `resources.html` and the programme cards on
  `index.html` have it baked into the HTML** so it's there for search engines and
  for readers with JavaScript off. Editing the JSON alone won't change those
  pages — update the markup too, and keep the two in step.

Same for `sitemap.xml`: it lists the 10 pages plus one URL per programme. Add a
programme and it needs a line.

**The map is click-to-load.** `contact.html` shows a placeholder with a *Show
map* button; `js/map.js` builds the Google Maps iframe only when it's pressed.
Nothing is requested from Google until a visitor asks. Google Fonts is the one
third party that does load on every page.

## Attribution

Icon geometry is from [Lucide](https://lucide.dev) 1.70.0, under the 
