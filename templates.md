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
