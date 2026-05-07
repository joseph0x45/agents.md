here is a description of how I do HTML templating with Go.
I always use Tailwind for the styling. I embed the tailwind script directly in my Go binary and serve it as javascript at `/tailwindcss` so always include
`<script src="/tailwindcss"></script>` in the templates head

Each template is rendered by a custom function that uses the templates 'name'. A typical template looks like this

```html
{{define "template_name"}}
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title></title>
  <script src="/tailwindcss"></script>
  <style>
  </style>
</head>

<body class="">
</body>

</html>
{{end}}

```
I always use `autocomplete="off"` on inputs.
I don't like placeholders that are too obvious. Always prefer labels to placeholders inside forms.
On login forms always add a block with '{{.Error}}' that will contain an error message.
I prefer inline confirmation on "dangerous" actions like deletions, so instead of using modals I'd do something like this
```html
<button type="submit" onclick="return confirm('Delete {{.Name}}?')"
```
I always limit Javascript but in case we need reactivity I'd reach for AlpineJS. I also embed the whole script inside my binary and serve it as javascript at `/alpinejs` so in case
we need to use Alpine just include the script tag pointing to that path.
