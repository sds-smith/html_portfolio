# HTML Portfolio

A lightweight, responsive portfolio website built almost entirely with HTML and CSS, featuring liquid glass styling effects. The project demonstrates modern CSS capabilities with minimal JavaScript usage.

## Intent

This portfolio showcases a minimalist approach to web development, emphasizing the power of pure CSS for creating sophisticated visual effects. The site serves as both a personal portfolio and a demonstration of liquid glass design principles without relying on heavy JavaScript frameworks or build tools.

## Construction

### Architecture

The project consists of three static HTML pages:

- `index.html` - Main portfolio entry point currently showcasing a featured project
- `about.html` - Personal philosophy and values
- `portfolio.html` - Links to a selection of projects

All pages share a single CSS file (`index.css`) and maintain consistent navigation and styling.

### Lightweight Nature

This project intentionally avoids:

- Build tools or bundlers
- JavaScript frameworks
- CSS preprocessors
- External dependencies or CDN resources

The entire application runs on vanilla HTML, CSS, and ~30 lines of JavaScript with zero external network requests.

## Components

### 100% HTML/CSS Components

**Card System**

- `.card` - Base glass morphism container
- `.card-elevated` - Enhanced elevation with borders
- `.card-outlined` - Subtle outlined variant
- All cards feature backdrop blur, transparency, and dynamic shadows

**Layout System**

- `.layout-fullscreen` - Full viewport layouts for hero sections
- `.layout-hero` - Centered content display
- `.layout-list` - Vertical stacking for content sections
- Fully responsive grid and flexbox implementations

**Navigation**

- Semantic header with responsive navigation
- Mobile-first responsive design
- No JavaScript required for basic navigation

**Typography & Content**

- System font stack for optimal performance and native appearance
- Responsive font sizing using `clamp()`
- Content truncation for mobile layouts
- Semantic HTML5 structure throughout

**Liquid Glass Styling (100% CSS)**

**Design Token System**

- Comprehensive CSS custom properties for glass physics
- Variable naming convention: `--lg-{group}-{subgroup}-{token}`
- Dark mode support via `prefers-color-scheme`
- Accessibility considerations for reduced motion/transparency

**Glass Physics Implementation**

```css
--lg-glass-blur: 20px;
--lg-glass-bg-opacity: 0.12;
--lg-glass-border-opacity: 0.2;
--lg-glass-surface: rgba(255, 255, 255, var(--lg-glass-bg-opacity));
--lg-glass-reflection: linear-gradient(135deg, ...);
```

**Visual Effects**

- Backdrop blur with webkit fallbacks
- Layered box shadows for depth perception
- Gradient reflections for glass-like surfaces
- Smooth transitions with custom easing curves

**Responsive Behavior**

- Mobile-optimized glass effects
- Touch-friendly interaction targets
- Adaptive background handling

## Minimal JavaScript Usage

Only one component requires JavaScript: the **SpeedDial** floating action button. This ~30-line script handles:

- Checkbox-based state management
- Click-to-toggle functionality
- Outside click detection
- Keyboard navigation (Escape key)
- Action button interactions

The JavaScript is vanilla, framework-agnostic, and progressively enhanced.

## Technical Highlights

### CSS Architecture

- CSS custom properties for theming
- Mobile-first responsive design
- Semantic class naming conventions
- Component-based organization
- Accessibility-first approach

### Performance

- Zero build process required
- Instant loading with no external dependencies
- No network requests for fonts or frameworks
- Optimized for mobile devices

### Browser Compatibility

- Modern CSS with graceful degradation
- Webkit prefixes for broader support
- Responsive images and layouts
- Touch-optimized interactions

## Design Philosophy

This portfolio demonstrates that sophisticated user interfaces can be achieved without complex tooling or external dependencies. The liquid glass effects are created entirely through CSS, showcasing the power of modern web standards while maintaining exceptional performance and accessibility.

The project serves as both a portfolio piece and a technical demonstration of zero-dependency web development principles, proving that beautiful, responsive interfaces can be built with pure HTML, CSS, and minimal JavaScript.
