# Testing wiki links

Input: `This is a [[wiki-link]].`

Output: This is a [[wiki-link]].

---

This works by creating a footnote section with markdown references at the end of the file

```
[wiki-link]: wiki-link.md "Wiki link"
```

[wiki-link]: wiki-link "Wiki Link"

Output: (None)

---

Generates this html:

```html
<a href="wiki-link.md" title="Wiki Link">wiki-link.md</a>
```

---

But this CSS makes it display the title instead of the content

```css
a[title] {
  font-size: 0;
}

a[title]:after {
  content: attr(title);
  font-size: initial;
}
```

--

Output: This is a [[wiki-link]].
