# HTML Boilerplate with Tailwindcss

<p>
  <a href="https://github.com/acfatah/tailwindcss-no-build/commits/head">
  <img alt="GitHub last commit (by committer)" src="https://img.shields.io/github/last-commit/acfatah/tailwindcss-no-build?display_timestamp=committer&style=flat-square"></a>
</p>

Minimal, copy-paste configuration for building [TailwindCSS](https://tailwindcss.com) websites using a CDN setup without Node.js environment.

## Usage

1. Add the Tailwindcss config,

```html
<script src="https://cdn.tailwindcss.com?plugins=forms,typography,aspect-ratio,container-queries"></script>
<script>
  tailwind.config = {
    darkMode: 'class',
    theme: {
      container: {
        center: true,
      },
      extend: {
        fontFamily: {
          sans: ['Inter', 'sans-serif'],
        },
        colors: {
          primary: {
            DEFAULT: 'hsl(var(--primary))',
            dark: 'hsl(var(--primary))',
          },
          background: {
            DEFAULT: 'hsl(var(--background))',
            dark: 'hsl(var(--background))',
          },
          foreground: {
            DEFAULT: 'hsl(var(--foreground))',
            dark: 'hsl(var(--foreground))',
          },
          border: {
            DEFAULT: 'hsl(var(--border))',
            dark: 'hsl(var(--border))',
          },
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
    --primary: 217 91% 60%;
    --background: 0 0% 100%;
    --foreground: 0 0% 3.9%;
    --border: 0 0% 45%;
    --input: 0 0% 89.8%;
    --ring: 0 0% 3.9%;
    --radius: 0.3rem;
  }

  .dark {
    --background: 0 0% 3.9%;
    --foreground: 0 0% 98%;
    --input: 0 0% 14.9%;
    --ring: 0 0% 14.9%;
  }

  @layer base {
    body {
      @apply text-foreground bg-background p-2 sm:p-4;
    }
  }

  @layer components {
    .semantic-tailwind :not(input[type='checkbox'], a):focus {
      @apply rounded-xl;
    }

    .semantic-tailwind :not(input[type='submit']):focus {
      @apply bg-background/10 dark:bg-background/90;
    }

    .semantic-tailwind :focus {
      @apply border-primary ring-primary outline-none ring-2;
    }

    /* Typography */
    .semantic-tailwind .container {
      @apply prose prose-neutral dark:prose-invert;
    }

    .semantic-tailwind .container > header,
    .semantic-tailwind .container > article,
    .semantic-tailwind .container > section {
      h1 {
        @apply relative text-5xl;
      }

      h2 {
        @apply relative text-3xl;
      }

      h3 {
        @apply relative text-2xl;
      }

      h4 {
        @apply relative text-xl;
      }

      h5 {
        @apply relative text-lg;
      }

      h6 {
        @apply relative;
      }
    }

    .semantic-tailwind h1 > small,
    .semantic-tailwind h2 > small,
    .semantic-tailwind h3 > small,
    .semantic-tailwind h4 > small,
    .semantic-tailwind h5 > small,
    .semantic-tailwind h6 > small {
      @apply font-light;
    }

    .semantic-tailwind blockquote > cite {
      @apply block text-sm font-light;
    }

    /* link */
    .semantic-tailwind a[role='button'] {
      @apply inline-block py-4 no-underline;
    }

    /* hr */
    .semantic-tailwind hr {
      @apply border-border !important;
    }

    .semantic-tailwind h1 > hr,
    .semantic-tailwind h2 > hr,
    .semantic-tailwind h3 > hr,
    .semantic-tailwind h4 > hr,
    .semantic-tailwind h5 > hr,
    .semantic-tailwind h6 > hr {
      @apply !mb-0 !mt-2;
    }

    /* meter */
    .semantic-tailwind meter {
      @apply h-6 overflow-hidden rounded-xl;
    }

    /* progress */
    .semantic-tailwind progress {
      @apply border-border overflow-hidden rounded-xl border-2;
    }

    /* table */
    .semantic-tailwind table > caption {
      @apply caption-bottom text-neutral-500 dark:text-neutral-400;
    }

    /* form and fieldset */
    .semantic-tailwind fieldset {
      @apply border-border rounded-xl border-2 p-2 sm:p-4;
    }

    .semantic-tailwind legend {
      @apply p-2 text-lg font-bold;
    }

    .semantic-tailwind fieldset,
    .semantic-tailwind form {
      @apply flex flex-col gap-2;
    }

    .semantic-tailwind form > [role='help'] {
      @apply relative -top-1 text-neutral-500 dark:text-neutral-400;
    }

    .semantic-tailwind form > [role='alert'] {
      @apply relative -top-1 text-red-500;
    }

    .semantic-tailwind fieldset > [role='button'],
    .semantic-tailwind form > [role='button'] {
      @apply flex justify-end gap-2;
    }

    /* form label */
    .semantic-tailwind label {
      @apply relative -bottom-1 flex items-center;
    }

    .semantic-tailwind label[for]:has(input[type='checkbox']),
    .semantic-tailwind label[for]:has(input[type='radio']),
    .semantic-tailwind label[for]:has(input[type='color']) {
      @apply select-none gap-2 hover:cursor-pointer;
    }

    /* form required input label */
    .semantic-tailwind label[for]:has(+ input:required)::before {
      content: ' *';
      @apply relative -top-1 text-red-500;
    }

    /* form input */
    .semantic-tailwind a[role='button'],
    .semantic-tailwind button,
    .semantic-tailwind input[type='submit'],
    .semantic-tailwind input[type='reset'],
    .semantic-tailwind input[type='text'],
    .semantic-tailwind input[type='password'],
    .semantic-tailwind input[type='number'],
    .semantic-tailwind input[type='email'],
    .semantic-tailwind input[type='url'],
    .semantic-tailwind input[type='date'],
    .semantic-tailwind select,
    .semantic-tailwind textarea {
      @apply border-border rounded-xl border font-normal;
    }

    .semantic-tailwind a[role='button'],
    .semantic-tailwind button,
    .semantic-tailwind input[type='reset'],
    .semantic-tailwind input[type='text'],
    .semantic-tailwind input[type='password'],
    .semantic-tailwind input[type='number'],
    .semantic-tailwind input[type='email'],
    .semantic-tailwind input[type='url'],
    .semantic-tailwind input[type='date'],
    .semantic-tailwind select,
    .semantic-tailwind textarea {
      @apply border-border text-foreground bg-background hover:border-primary hover:ring-primary rounded-xl border font-normal hover:outline-none;
    }

    /* form input placeholder */
    .semantic-tailwind input::placeholder {
      @apply text-neutral-500;
    }

    /* form checkbox and radio input */
    .semantic-tailwind input[type='checkbox'],
    .semantic-tailwind input[type='radio'] {
      @apply cursor-pointer;
    }

    .semantic-tailwind input[type='checkbox']:checked,
    .semantic-tailwind input[type='radio']:checked {
      @apply bg-primary focus:bg-primary;
    }

    .semantic-tailwind input[type='checkbox']:not(:checked),
    .semantic-tailwind input[type='radio']:not(:checked) {
      @apply focus:bg-white;
    }

    .semantic-tailwind input[type='checkbox'] {
      @apply rounded;
    }

    /* form color input */
    .semantic-tailwind input[type='color']:focus {
      @apply rounded;
    }

    /* from date input */
    .semantic-tailwind input[type='date']::-webkit-calendar-picker-indicator {
      @apply cursor-pointer;
    }

    .dark
      .semantic-tailwind
      input[type='date']::-webkit-calendar-picker-indicator {
      filter: invert(1);
      @apply cursor-pointer;
    }

    .dark
      .semantic-tailwind
      input[type='date']::-webkit-calendar-picker-indicator:focus {
      filter: invert(1) hue-rotate(180deg);
    }

    .semantic-tailwind
      input[type='date']::-webkit-calendar-picker-indicator:focus {
      @apply ring-primary outline-none ring-2;
    }

    /* form input submit and reset button */
    .semantic-tailwind form input[type='submit'],
    .semantic-tailwind form button[type='submit'],
    .semantic-tailwind input[type='submit'] {
      @apply border-primary bg-primary hover:bg-primary/80 focus:border-primary/80 focus:bg-primary/80 text-white;
    }

    .semantic-tailwind a[role='button'],
    .semantic-tailwind button,
    .semantic-tailwind input[type='submit'],
    .semantic-tailwind input[type='reset'] {
      @apply px-4 py-1 no-underline hover:cursor-pointer;
    }

    /* form disabled input */
    .semantic-tailwind button:disabled,
    .semantic-tailwind input:disabled,
    .semantic-tailwind select:disabled,
    .semantic-tailwind textarea:disabled {
      @apply hover:bg-background opacity-50 hover:cursor-not-allowed hover:border-neutral-500;
    }

    /* @layer components */
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
