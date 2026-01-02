# Web-Projects
  This is a vanilla HTML/CSS/JS project demonstrating an interactive card UI with smooth expand/collapse animations.

  Project Structure

  expanding-cards/
  ├── index.html    # Page structure
  ├── style.css     # Layout & animations
  └── script.js     # Click interactivity

  ---
  Core Concepts

  1. CSS Flexbox Layout

  The panels are arranged using flexbox with a flex property trick:

  .panel {
    flex: 0.5;              /* Default: equal small size */
    transition: flex 700ms ease-in;
  }

  .panel.active {
    flex: 5;                /* Active: 10x larger than inactive */
  }

  When one card becomes active (flex: 5), it takes ~10x more space than others (flex: 0.5), creating the expansion effect.

  2. CSS Transitions

  Two animations work together:
  - Panel expansion: 700ms transition on flex
  - Title fade-in: 0.4s delay so text appears after expansion completes

  .panel h3 {
    opacity: 0;
  }
  .panel.active h3 {
    opacity: 1;
    transition: opacity 0.3s ease-in 0.4s;  /* 0.4s delay */
  }

  3. JavaScript State Management

  Simple class toggling pattern (script.js:1-13):

  panels.forEach(panel => {
    panel.addEventListener('click', () => {
      removeActiveClasses();       // Clear all
      panel.classList.add('active'); // Set clicked
    });
  });

  No framework needed—just classList.add() and classList.remove().

  4. Responsive Design

  Media query hides last two cards on mobile:

  @media (max-width: 480px) {
    .panel:nth-of-type(4),
    .panel:nth-of-type(5) {
      display: none;
    }
  }

  ---
  Key Takeaways for Learning

  | Concept              | Implementation                         |
  |----------------------|----------------------------------------|
  | Flexbox distribution | flex values control relative sizing    |
  | Smooth animations    | transition on properties that change   |
  | Delayed animations   | Transition delay for sequenced effects |
  | State via classes    | Toggle .active class for state changes |
  | Event handling       | forEach + addEventListener pattern     |
  | Responsive hiding    | display: none in media queries         |

  ---
  External Dependencies

  - Google Fonts: Muli font family
  - Unsplash: Background images via direct URL

  No build tools, bundlers, or npm packages—pure browser-native code.
