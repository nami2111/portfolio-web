# AIMSOMNIA Portfolio Website

A modern, responsive portfolio website built with Svelte to showcase Web3 NFT projects.

## Features

- Responsive design that works on all devices
- Project filtering by year and technology
- Search functionality
- Project details modal
- Contact form
- Animated hero section
- Accessibility features

## Project Structure

portfolio-web

├─ public

│ ├─ images

│ │ └─ [project images]

│ ├─ favicon.png

│ ├─ global.css

│ └─ index.html

├─ src

│ ├─ components

│ │ ├─ AboutSection.svelte

│ │ ├─ ContactSection.svelte

│ │ ├─ HeroSection.svelte

│ │ ├─ ProjectCard.svelte

│ │ └─ ProjectModal.svelte

│ ├─ data

│ │ └─ projects.js

│ ├─ App.svelte

│ └─ main.js

├─ package.json

└─ rollup.config.js

## Getting Started

### Prerequisites

- Node.js (v14 or later)
- npm or yarn

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/nami2111/portfolio-web.git
   cd portfolio-web
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the development server:
   ```bash
   npm run dev
   ```

4. Open your browser and navigate to `http://localhost:5000`

## Building for Production

To create a production build:

```bash
npm run build
```

The built files will be in the `public/build` directory.

## Customization

### Updating Project Data

Edit the `src/data/projects.js` file to update your project information.

### Changing Styles

Global styles are in `public/global.css`. Component-specific styles are within each Svelte component.

### Adding New Pages

1. Create a new Svelte component in the `src/components` directory
2. Import and use it in `App.svelte`

## Deployment

This site can be deployed to any static hosting service:

- Netlify
- Vercel
- GitHub Pages
- AWS S3
- etc.

## Accessibility Features

- Semantic HTML
- ARIA attributes
- Keyboard navigation
- Focus management
- Screen reader friendly content

## Performance Optimizations

- Lazy loading images
- Responsive image loading
- Minimal dependencies
- Efficient Svelte reactivity

## License

MIT

## Acknowledgments

- Svelte - https://svelte.dev/
- Space Mono font - https://fonts.google.com/specimen/Space+Mono