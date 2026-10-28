# Writing co-op spotlight articles

Co-op spotlights are ordinary Hugo posts. One Markdown article can contain several
member interviews. The homepage and tag pages show the normal clickable post card,
not the full interviews. Technical, software, business and other posts are unchanged.

The current collection is `content/posts/summer-coop-spotlights/index.md`.
Edit that file to change the introductions, quotes and interview answers. Put its
photos beside it. There is no separate post or YAML question list for each member.

## Author credit and member profiles

Use the existing `authors` taxonomy for the people who wrote or edited the article:

```yaml
authors: ["Jiyun Chen"]
tags: ["careers", "member stories", "mechanical"]
```

The plural `authors` field produces linked author credit on the homepage card and
article. Create the writer's profile at `content/authors/jiyun-chen/_index.md`.
Do not list the interviewees as article authors unless they also helped write it.

Every featured person also needs a profile. Copy
`content/authors/BASIC-TEMPLATE/_index.md` into a new, lowercase, hyphenated folder,
then enter their full name, role and a short factual biography. For example:

```markdown
---
title: "Alex Example"
draft: true
---

**Mechanical team member**

Add a brief, approved biography here.
```

The profile folder, for example `alex-example`, is the `member` value used below.
The interview heading automatically uses the profile's full `title` and links to
that profile. Keep the folder slug stable when correcting someone's display name.
Only add LinkedIn, GitHub or other personal links supplied or approved by the member.
Set a completed profile to `draft: false` before publishing the article.

## Add another member to the same article

1. Create or update their member profile as described above.
2. Add their approved photo beside the article's `index.md`.
3. Copy one whole `coop` block in that same article, including its closing line.
4. Change the member slug, program, roles, introduction, quote and photo settings.
5. Replace the questions and answers inside the block with the member's own content.

```markdown
{{< coop
  member="alex-example"
  program="Third-year Mechanical Engineering student"
  formula-role="Mechanical team member"
  coop-role="Engineering Intern at Example Company"
  image="alex.jpg"
  image-alt="Alex working on a Formula uOttawa component"
  intro="A short introduction explaining this member's experience."
  quote="Use an exact quote from the member's interview."
  quote-context="Alex Example, on learning with the team"
>}}

> **What do you work on at your co-op?**
>
> Write the answer using ordinary Markdown.
>
> Keep the `>` prefix on extra paragraphs that belong to the same answer.

> **What have you learned through Formula?**
>
> Write the next answer here.

{{< /coop >}}
```

Each Markdown blockquote (`>`) groups one question and its answer. Separate question
blocks with a blank line that has no `>` prefix. The design places these blocks in
two columns on desktop and one column on phones. Any number of questions is allowed.
Use the member's exact words for the pull quote; introductions may be edited summaries.

Do not use the same member slug twice in one article: it is also their jump-link ID.
For a contents list, link to `#member-alex-example`.

## Start a new collection

From the repository folder, run:

```powershell
hugo new content posts/summer-coop-2027/index.md --kind coop
```

Fill in the title, description, short homepage summary, date, writer's `authors`
entry and tags. Create member profiles and replace the starter values before previewing.
The starter is a draft. Copy its member block to add more people to the same article.
If copying an older article instead, remove its `aliases` so old URLs do not redirect
to the wrong collection. Ordinary non-interview blog posts need no `coop` shortcode.

## Photos

- Use real, approved photos. Never substitute a generated person's portrait.
- Put all member photos beside this article's `index.md` and reference their exact filenames.
- Recommended size: 1200 x 1500 pixels (4:5 portrait); 800 x 1000 is sufficient.
- Use JPG or WebP, preferably below 500 KB. Keep the face centred with headroom;
  the card crops the photo to fit its available space.
- `image-alt` should describe the actual photo, not just say "image".
- `image=""` displays a pending-photo box only in a draft preview.

Published interviews must have real image files. A missing/misspelled image, a
missing member profile, an unfinished draft profile, or missing article author
credit stops the build with an explanation. This prevents placeholders from
accidentally reaching the published blog.

## Preview and publishing checklist

Hugo templates are not standalone HTML pages. Do not open `layouts/index.html`
directly in a browser. From the repository folder, use:

```powershell
hugo server --buildDrafts --baseURL http://localhost:1313/uOpenBlog/ --port 1313
```

Open `http://localhost:1313/uOpenBlog/`, click the article card, and check:

- The homepage contains one summary card for the whole collection, not full interviews.
- Homepage tag buttons and Browse Tags work; existing categories still appear.
- The article has the writer's linked byline, the correct tags and all interviews.
- Each person has a confirmed full name, working profile link and an approved photo.
- Quotes match the interviews and desktop/mobile layouts remain readable.

Set the completed member profiles and article to `draft: false`, then run:

```powershell
hugo --minify
```

The deployment uses Hugo 0.146.0. A regular build does not include draft posts.
Do not merge a post that still needs names, permissions or photos.

### Current article's content

The collection features Jacob Thomas, Benjamin Marceau and Maire Levin, with their
real photos included beside the article as `jacob.jpg`, `benji.jpg` and `maire.jpg`.
All three photos are 1200 x 1500 pixels (4:5 portrait). Jiyun Chen is credited as
the writer/editor. The article and all featured profiles have `draft: false`.

Jacob's profile keeps the existing `jacob` folder slug; its title displays the
confirmed full name, Jacob Thomas, without breaking existing profile links.

## Where the reusable design lives

- `layouts/_shortcodes/coop.html`: member profile lookup, card markup and publishing checks.
- `assets/css/extended/coop.css`: interview-only styling, loaded by PaperMod's existing
  stylesheet pipeline. It does not hide navigation, bylines or tags.
- `archetypes/coop.md`: copyable starter for another collection.
- `layouts/index.html`: normal homepage cards, unchanged by the interview design.

Keep ordinary contribution steps in the main README. Changes to these design files
are only needed to change the shared appearance, not to add a person or edit answers.
