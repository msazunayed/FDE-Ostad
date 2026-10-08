# Observation: AI-Assisted Landing Page Development for FDE Service

## 1. AI Models Used

Model 1: Claude Haiku 5.5 (folder: `Claude-Haiku 5.5/`, files: `index.html` and `style.css`)

Model 2: Kimi K3 (folder: `kimi-k3/`, files: `index.html` and `styles.css`)

## 2. Prompt Used

I gave the same prompt to both models:

"Create a responsive landing page for an FDE service using HTML and CSS."

## 3. Code Quality Observation

| Area | Model 1 (Claude Haiku 5.5) | Model 2 (Kimi K3) |
|---|---|---|
| Code structure | The code is one HTML file and one CSS file. The sections come in a clear order: header, hero, stats, services, process, testimonial, contact, and footer. The CSS starts with a small set of color and spacing variables, which keeps things easy to change. | Also one HTML file and one CSS file, but the layout is bigger. It has a hero panel, a proof strip, and separate sections for the operating model, capabilities, signals, engagement, and consultation. The HTML is a bit more deeply nested. |
| Readability | Very easy to read. Class names are short, there is a comment above each section, and the indentation is consistent. | Also easy to read. The class names are descriptive, like `hero__copy` and `capability--accent`. Some progress bars use inline style attributes such as `--value: 82%`, which is a little harder to scan. |
| Component design | Buttons, cards, and process steps reuse the same few classes, so the page feels consistent. | The pieces are well named and fit the FDE topic closely. The page feels written for this service, not like a generic template. |
| Documentation | There are helpful comments in the HTML, and the page has a meta description. There is no README. | The comments are lighter. Most interactive areas have an aria-label, and there is a meta description. There is no README. |
| Error handling | The form uses `required` and `type="email"` on the right fields. The mobile menu has a visible focus outline for keyboard users. The page uses a system font, so there is nothing to fall back from. | The page has a skip link, aria-labels on the navigation and menu toggle, and aria-hidden on decoration. It loads Google Fonts, which adds an outside dependency, though the CSS has a fallback font list. The contact form is replaced by a mailto link, so there is no validation. |
| Responsiveness | Breakpoints at 1024px, 860px, and 600px. The mobile menu slides down. | Breakpoints at 1060px, 780px, and 460px. The mobile menu works with the checkbox trick. It also respects reduced motion settings. |

Both files are clean and work without any JavaScript. Model 1 is simpler and easier to maintain. Model 2 has better accessibility and a fuller page, but it is bigger and depends on an external font.

## 4. AI Hallucination Observation

Both models made up facts that are not true. If someone published these pages without checking, the made-up details could mislead visitors.

Observation 1 (Model 1): The page has a testimonial from an "Operations Lead" at a "Mid-sized logistics company," saying the solution went live within two months. This client does not exist.

Observation 2 (Model 1): The stats look like real numbers: "50+ projects delivered," "98% client retention," and "6 wks average time to first release." The hero card also says "40% faster ticket resolution." None of these come from any real source.

Observation 3 (Model 1): The footer says the company is in "Dhaka, Bangladesh." I never asked for a location, so the model guessed it.

Observation 4 (Model 2): The hero panel shows a "Field operations copilot" marked as Production with an 87% readiness score. The signals panel shows scores of 82, 94, and 68. These look like live data, but they are invented.

Observation 5 (Model 2): The page states service promises as facts, such as "14 days to first production workflow," "6 to 12 weeks embedded build cycles," and "100% handoff documentation." They sound like normal marketing copy, but the model had no business details to base them on.

Observation 6 (Model 2): The page loads Google Fonts from an outside server. This is not a made-up fact, but the prompt did not ask for it, and the page now depends on that outside service.

The main pattern is this: neither model asked for real business details. Both filled the gaps with confident, specific numbers. A person needs to review and replace all of this before the page goes live.

## 5. Final Decision

Answer: Model 2 (Kimi K3) gave the better result overall, mainly because of its structure, its wording, and its accessibility.

My reasoning:

- Code quality: Both pages are valid and work on phones and laptops. Model 2 is better for accessibility, with a skip link, aria-labels, and reduced motion support. It also has a fuller page structure. Model 1 is simpler and easier to keep up, which matters for a small project.
- Accuracy: Both models make things up. Model 1 invents a client testimonial and a set of stats, which is the bigger problem, because a fake testimonial suggests a real customer said something they never said. Model 2's invented numbers look like dashboard placeholders, but they are still shown as if they were live data.
- Maintainability: Model 1 is easier to edit. Model 2 uses more inline styles and an outside font, so changing it takes more work.
- Understanding of the task: Model 2 seemed to understand what an FDE service does. It talks about embedded engineers, operating models, and handing skills over to the client team, and it ends with a clear call to book a consultation. Model 1 wrote a more general landing page with a standard service pitch.

Conclusion: I chose Model 2 because it understood the FDE idea better and made a fuller, more accessible page. Model 1 would be the better pick if you care more about simple code than about depth. Either way, every invented number, testimonial, and service claim needs to be replaced with real information before the page is used.
