---
title: "{{ replace .File.ContentBaseName "-" " " | title }}"
description: "Describe this collection of co-op interviews."
summary: "Write a short homepage summary, not the full interviews."
date: {{ .Date }}
draft: true
# Credit the writer/editor here, not everyone who was interviewed.
authors: []
tags: ["careers"]
---

Introduce this collection of interviews in ordinary Markdown.

{{ `{{< coop
  member="member-profile-slug"
  program="Year and program"
  formula-role="Role with Formula uOttawa"
  coop-role="Co-op position and employer"
  image="portrait.jpg"
  image-alt="Describe the member's photo"
  intro="A short introduction to this member's experience."
  quote="An exact quote from the member's answers."
  quote-context="Full name, on the topic of the quote"
>}}` }}

> **What do you work on at your co-op?**
>
> Write the answer here. Normal Markdown, including links and emphasis, is supported.

> **What have you learned through Formula?**
>
> Write the answer here.

{{ `{{< /coop >}}` }}

Copy the complete member block above for another person in this same article.
