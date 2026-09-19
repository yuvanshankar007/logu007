# ULAGANATHAN MS — Engineering meets digital precision

A premium, dark architectural portfolio for **Ulaganathan MS**, BIM Engineer and **Assistant Manager at Pinnacle Infotech Solutions**, based in Salem, Tamil Nadu, India. Its central idea is a scroll-driven journey through a digital building: person, capabilities, career, work, model, connection.

## Completed features

- React 18 component-based frontend, authored in TypeScript/TSX, with Tailwind utilities and a custom responsive CSS design system.
- Original user-uploaded PNG at `images/ulaganathan-ms.png`, used in the hero, About and Contact. The face is not generated, retouched or replaced. CSS crops away the supplied outer matte into a circular portrait.
- Full-screen hero with architectural grid, portrait ring, technical annotations, real profile information, two anchor CTAs and career facts.
- GSAP 3 + ScrollTrigger: five pinned desktop experiences (hero, active skills, horizontal career, horizontal projects, model chamber), scrubbed rotation, horizontal translation, masked line reveals, image reveals, layered parallax, milestone line fill and responsive typography.
- Lenis smooth wheel scrolling, real document-percentage progress, active-section indicators, fixed glass navigation, mobile menu, accessible anchor navigation and back-to-top.
- Interactive skills index with eight capability panels, click/scroll-controlled active selection, sequential entrances and desktop hover details.
- Complete career history with all five supplied positions, employers and exact dates. No invented project metrics or software credentials.
- Four clearly labeled illustrative project placeholders with original SVG architectural diagrams, hover parallax, custom view cursor and accessible project dialogs.
- Lightweight procedural Three.js buildings with floors, instanced structural columns, translucent surfaces, edges, axes and grid. Rotation follows scroll in either direction. Structure, wireframe and levels buttons change the live model.
- WebGL failure fallback uses original vector architectural drawings. No external model downloads are required.
- Mobile uses stacked career/project cards instead of horizontal pinning, reduced parallax, no hero WebGL renderer, no magnetic cursor, lower canvas pixel ratio and lower render frequency.
- Reduced-motion preference removes cinematic pinning, transform animations and smooth scrolling; all career/project content remains available vertically.
- Short identity loader, semantic sections, portrait alt text, focus outlines, skip link, keyboard-operable dialogs with focus trap, Escape dismissal and focus restoration.
- Page title, description, Open Graph metadata, theme color and SVG favicon.

## Functional entry points

| URI | Purpose |
| --- | --- |
| `/` or `/index.html` | Complete portfolio |
| `/#hero` | Introduction and original portrait |
| `/#about` | Introduction, location, education and professional metadata |
| `/#skills` | Interactive skill showcase and capability cards |
| `/#experience` | Five-stage career timeline |
| `/#projects` | Four-project illustrative gallery; cards open dialogs |
| `/#inside-model` | Interactive BIM massing, with three display modes |
| `/#contact` | Professional contact actions and location |
| `/tests/integration.html` | Developer browser checks against the real portfolio in a 1280px iframe |
| `/tests/section.html` | Developer redirect to the actual project section, retaining the device viewport |

No application query parameters are needed. Modal selection and the model display mode are transient React state, not URLs.

## Content configuration

Edit `js/config.js` to finish the personal contact details and replace project placeholders:

```js
window.PORTFOLIO_CONFIG = {
  email: 'yuvanshankar920@gmail.com',
  linkedin: 'https://www.linkedin.com/in/ulaganathan-ms-b41258253/',
  instagram: 'https://www.instagram.com/messi_logan264',
  whatsapp: '919360582237',
  emailUrl: 'mailto:yuvanshankar920@gmail.com?subject=Portfolio%20Project%20Inquiry&body=Hi%20Ulaganathan%2C%20I%20visited%20your%20portfolio%20and%20would%20like%20to%20discuss%20a%20project.',
  whatsappUrl: 'https://wa.me/919360582237?text=Hi%20Ulaganathan%2C%20I%20visited%20your%20portfolio%20and%20would%20like%20to%20discuss%20a%20project.',
  projects: [
    {
      id: '01',
      title: 'Your approved project title',
      category: 'Your project category',
      description: 'Your verified scope and contribution',
      role: 'Your actual role',
      tools: 'Tools actually used',
      image: 'images/your-approved-project.webp',
      status: 'Your verified project status'
    }
  ]
};
```

### Important content boundaries

- Verified contact integrations are configured for LinkedIn, Instagram, Gmail, and WhatsApp in `#contact`. External links open securely in a new tab with `target="_blank"` and `rel="noopener noreferrer"`, email opens the default mail client with pre-filled project inquiry details, and WhatsApp opens a direct chat using India's country code (`91`).
- All four current project visuals are **illustrative placeholders**, not client work. Project roles/tools remain explicitly unprovided. Add only permitted, verified project materials.
- When replacing the placeholders with verified work, also update the placeholder disclosures in `js/app.tsx` (gallery labels, introductions and dialog notes). The current disclosures are deliberately explicit rather than automatically removed by an image change.
- Role descriptions are conservative summaries of the supplied progression, not claims of quantified achievements or named project responsibilities.
- About education uses only the provided institution; no degree or graduation date has been invented.

## Implementation and files

```
index.html                  Entry document, SEO and CDN dependencies
css/style.css               Architectural design system and responsive/reduced-motion rules
js/app.tsx                  React/TypeScript components, content layouts and dialogs
js/config.js                Verified contact destinations and replaceable project records
js/experience.js            GSAP/ScrollTrigger/Lenis, procedural Three.js and diagnostics
images/ulaganathan-ms.png    Exact original uploaded portrait
images/favicon.svg          Custom architectural monogram
 tests/integration.html     Developer interaction test harness
 tests/integration.js       Programmatic DOM/scroll integration checks
 tests/section.html         Actual-page deep-link visual test entry
 tests/section.js           Redirect for visual checks
```

### Runtime and production considerations

This editing environment serves static files without a Node build pipeline. The portfolio uses React, TSX transformed in the browser by Babel Standalone, Tailwind's browser CDN, and pinned CDN versions of GSAP, Lenis and Three.js. It is a **static React website, not a Next.js server application**. Babel and Tailwind emit expected development-CDN warnings, and the compatible Three.js UMD build emits a legacy-build warning. These are not application exceptions.

For an optimized production build, the recommended next engineering step is to precompile TSX with Vite/esbuild or a Next.js static export, compile Tailwind ahead of time, switch Three.js to ESM and bundle/cache the dependencies. This removes browser compilation and the development-CDN warnings. Do not add a server solely to run this frontend.

All rendering is browser-side. WebGL work is visibility-gated and pauses when the document is hidden; canvas dimensions react to container resizing. Images below the hero are lazy-loaded. Fonts use `display=swap`.

## Data models and storage

- `PORTFOLIO_CONFIG`: `{ email: string, linkedin: string, projects: Project[] }`.
- `Project`: `{ id, title, category, description, role, tools, image, status }`, all strings.
- Career and skill arrays are public static content in `js/app.tsx`.
- React state: active skill, active modal, mobile navigation visibility, model mode and intro progress.
- Animation/model state exists only in browser memory.
- **No database, Table API, authentication, cookies, analytics, uploaded-file storage, form submissions or personal-message collection.**
- Assets reside in the project repository. Dependencies use jsDelivr, the Tailwind CDN and Google Fonts.

## Verification

- Desktop and actual mobile hero rendering visually checked.
- Developer integration harness checks original portrait loading, all five desktop pin triggers, horizontal career/project motion driven by vertical scrolling, project modal/disclosure, focus, Escape handling, contact availability notice, model control state, active skill selection, page percentage, mobile menu logic and document overflow.
- The harness also verifies direct `#projects` navigation after pinned-section layout measurement.
- `window.portfolioDiagnostics()` returns current trigger IDs, model count, content counts and responsive settings for debugging.
- Software-rendered test browsers can emit WebGL GPU/readback warnings. The page includes a vector fallback for browsers without WebGL.

## Not yet implemented / awaiting owner input

1. Verified email address and LinkedIn URL.
2. Actual project imagery, scope, role, tools and permission to publish.
3. Optimized precompiled production bundle (current environment uses browser TSX compilation).
4. Optional downloadable CV, only if a real approved PDF is provided.
5. Deployment, canonical URL and final absolute Open Graph image URL.
6. Server messaging/contact-form delivery — not part of this static website.

## Public URLs and publishing

- **Production URL:** Not deployed in this session; no production URL is available yet.
- **API endpoints:** None.
- Publish using the project's **Publish tab**. Hosted Deploy requires an explicit request and user approval.
- After publication, configure a canonical URL and an absolute Open Graph portrait/image URL for reliable social previews.

## Recommended next steps

1. Supply the verified email and LinkedIn profile URL.
2. Replace the four disclosed placeholders with approved project case studies.
3. Precompile/bundle the frontend for a lean production delivery.
4. Publish, then verify scroll interactions on real touch devices and common browsers.
5. Optionally add a real CV download and verified impact metrics.
