# HTML Boilerplate with Tailwindcss

<p>
  <a href="https://github.com/acfatah/tailwindcss-no-build/commits/head">
  <img alt="GitHub last commit (by committer)" src="https://img.shields.io/github/last-commit/acfatah/tailwindcss-no-build?display_timestamp=committer&style=flat-square"></a>
</p>

Minimal, copy-paste configuration for building [TailwindCSS](https://tailwindcss.com) websites without a Node.js environment and using a CDN setup

## Usage

1. Add Tailwindcss config,

```html
<script src="https://cdn.tailwindcss.com?plugins=forms,typography,aspect-ratio,line-clamp,container-queries"></script>
<script>
  tailwind.config = {
    darkMode: 'class', // Remove this line to use `prefers-color-scheme` CSS media feature
    theme: {
      extend: {
        fontFamily: {
          sans: ['Inter', 'sans-serif'],
        },
        colors: {
          background: {
            DEFAULT: 'hsl(var(--background))',
            dark: 'hsl(var(--background))',
          },
          foreground: {
            DEFAULT: 'hsl(var(--foreground))',
            dark: 'hsl(var(--foreground))',
          },
          border: 'hsl(var(--border))',
          input: 'hsl(var(--input))',
          ring: 'hsl(var(--ring))',
        },
        borderRadius: {
          xl: 'calc(var(--radius) + 4px)',
          lg: 'var(--radius)',
          md: 'calc(var(--radius) - 2px)',
          sm: 'calc(var(--radius) - 4px)',
        },
      },
    },
  }
</script>
```

2. Add the basic styling for forms,

```html
<style type="text/tailwindcss">
  :root {
    --background: 0 0% 100%;
    --foreground: 0 0% 3.9%;
    --border: 0 0% 89.8%;
    --input: 0 0% 89.8%;
    --ring: 0 0% 3.9%;
    --radius: 0.3rem;
  }

  .dark {
    --background: 0 0% 3.9%;
    --foreground: 0 0% 98%;
    --border: 0 0% 14.9%;
    --input: 0 0% 14.9%;
    --ring: 0 0% 14.9%;
  }

  body {
    @apply p-2 sm:p-4 text-foreground bg-background;
  }

  h1 > small,
  h2 > small,
  h3 > small,
  h4 > small,
  h5 > small,
  h6 > small {
    @apply font-light;
  }

  blockquote > cite {
    @apply block text-sm font-light;
  }

  h1 > hr,
  h2 > hr,
  h3 > hr,
  h4 > hr,
  h5 > hr,
  h6 > hr {
    @apply !mt-2 !mb-0;
  }

  table > caption {
    @apply text-neutral-500 dark:text-neutral-400 caption-bottom;
  }

  fieldset {
    @apply p-2 sm:p-4 border-2 border-border rounded-xl;
  }

  legend {
    @apply p-2 text-lg font-bold;
  }

  fieldset,
  form {
    @apply flex flex-col gap-2;
  }

  form > [role='help'] {
    @apply relative -top-1 text-neutral-500 dark:text-neutral-400;
  }

  form > [role='alert'] {
    @apply relative -top-1 text-red-500;
  }

  fieldset > [role='button'],
  form > [role='button'] {
    @apply flex gap-2 justify-end;
  }

  label {
    @apply relative -bottom-1 flex items-center;
  }

  label[for]:has(input[type='checkbox']),
  label[for]:has(input[type='radio']),
  label[for]:has(input[type='color']) {
    @apply gap-2;
  }

  label[for]:has(+ input:required)::before {
    content: ' *';
    @apply relative -top-1 text-red-500;
  }

  input[type='text'],
  input[type='password'],
  input[type='number'],
  input[type='email'],
  input[type='date'],
  select,
  textarea {
    @apply border rounded-xl border-neutral-300 text-foreground bg-background hover:border-blue-500 hover:bg-opacity-50 focus:bg-neutral-50 dark:focus:bg-neutral-900;
  }

  .dark input[type='date']::-webkit-calendar-picker-indicator {
    filter: invert(1);
  }

  input::placeholder {
    @apply text-neutral-500;
  }

  input:disabled,
  select:disabled,
  textarea:disabled {
    @apply opacity-50 cursor-not-allowed hover:border-neutral-300 hover:bg-none;
  }

  button[type='reset'],
  button[type='submit'] {
    @apply border rounded-xl sm:px-4 sm:max-w-min border-neutral-300 hover:bg-neutral-50 hover:border-blue-500 dark:hover:bg-neutral-900;
  }

  button[type='reset'] {
    @apply text-neutral-500 dark:text-neutral-400;
  }
</style>
```

3. Add the `container` class.

```html
<body>
  <div class="prose prose-neutral dark:prose-invert container mx-auto">
    <!-- other elements -->
  </div>
</body>
```

4. Optionally, add `Inter` font before the previous script

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link
  rel="stylesheet"
  href="https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&family=Roboto+Mono:ital,wght@0,100..700;1,100..700&display=swap"
/>
```

5. Optionally, add `lucide-icon`

```html
<script src="https://unpkg.com/lucide@latest"></script>
<script defer>
  lucide.createIcons()
</script>
```

Using external files for Tailwindcss while using CDN is not possible since:

1. PostCSS is not available.
2. The browser has no way to process external files.

So, we need to use the `style` tag with `type="text/tailwindcss"` attribute.
