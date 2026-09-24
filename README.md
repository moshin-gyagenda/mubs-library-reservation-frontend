# MUBS Library Reservations — Frontend Template

Static HTML + CSS screens for the BUC3131 coursework (MUBS Library book reservations). No Laravel, no Tailwind, and no CDN. Styles live in `assets/css/styles.css`, so the pages work with the internet off. Students copy these markup files into Blade views and wire them to routes, a controller, a model, and a migration.

## Design

A warm library look, distinct from the Campus Service Portal:

- Cream page (`#faf4eb`), ink header/footer (`#1a1512`)
- **Orange** (`#ea580c`) as the brand colour — buttons, accents, focus rings
- Georgia (headings) + Segoe UI / system sans (body), so fonts load without the internet
- Official MUBS crest: `assets/img/logo.png`
- Key blocks are marked with `<!-- Start: … -->` / `<!-- End: … -->` comments

## Pages (3)

| File | Purpose | Suggested Blade file |
| --- | --- | --- |
| `index.html` | Library home / welcome | `resources/views/welcome.blade.php` |
| `create.html` | Collect a reservation | `resources/views/reservations/create.blade.php` |
| `reservations.html` | List reservations already made | `resources/views/reservations/index.blade.php` |

Open `index.html` in a browser. No install and no internet are required.

## Form fields → database columns

The reservation form already uses these `name` attributes. Use the same names as migration columns and `$fillable` fields:

| Form `name` | Type |
| --- | --- |
| `student_name` | string |
| `registration_number` | string |
| `programme` | string |
| `book_title` | string |
| `pickup_date` | date |

## In Laravel (during the exam)

1. Copy the HTML into the Blade files above. Copy `assets/` into `public/assets/` (or point `asset()` at the CSS and `logo.png`).
2. Change the form to `method="POST"`, set `action` to your store route, and add `@csrf`.
3. Replace the sample table rows with a `@forelse ($reservations as $reservation)` loop.
4. Split the repeated header and footer into Blade layouts or `@include` partials if you have time.
