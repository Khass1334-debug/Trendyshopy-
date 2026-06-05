# Trendyshopy

A modern, animated portfolio landing page built with React and TypeScript. Features smooth scroll-based animations, video scrubbing, gesture controls, and advanced visual effects for an immersive user experience.

## 🌟 Features

- **Smooth Scroll Animations** - Advanced lerping system for fluid scroll progress tracking
- **Video Scrubbing** - Interactive video playback synchronized with scroll position
- **Gesture Controls** - Full support for mouse wheel and touch gestures
- **Smooth Transitions** - Eased navigation between sections with custom animation curves
- **Advanced Effects** - Blur effects, transforms, and text animations
- **Responsive Design** - Tailored for desktop and mobile experiences
- **Section-Based Navigation** - Dynamic header navigation with smooth transitions
- **Custom Components** - Reusable animated components (SoapTiles, CylindricalTextDrum, Marquee, etc.)

## 🛠️ Tech Stack

- **React 18** - UI framework
- **TypeScript** - Type-safe development
- **Tailwind CSS** - Utility-first styling
- **Vite** - Fast build tool and development server
- **Web APIs** - RequestAnimationFrame for smooth animations

## 📦 Project Structure

```
src/
├── components/
│   ├── Header.tsx              # Navigation header
│   ├── VideoScrubber.tsx       # First screen video scrubber
│   ├── SecondVideoScrubber.tsx # Second screen video scrubber
│   ├── ScrollExitSplitText.tsx # Text animation component
│   ├── SoapTiles.tsx           # Tile animation effects
│   ├── CylindricalTextDrum.tsx # Cylindrical text animation
│   ├── Marquee.tsx             # Scrolling marquee component
│   ├── Logos.tsx               # Logo components (Google, Github)
│   └── ...other components
├── data/
│   └── index.ts                # Navigation items and constants
├── types/
│   └── index.ts                # TypeScript type definitions
├── App.tsx                     # Main application component
└── main.tsx                    # Application entry point
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/Khass1334-debug/Trendyshopy-.git
   cd Trendyshopy-
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Start the development server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

4. **Open your browser**
   Navigate to `http://localhost:5173` (or the port shown in your terminal)

### Build for Production

```bash
npm run build
# or
yarn build
```

The optimized build will be in the `dist/` directory.

## 📖 Usage

### Main App Component

The `App.tsx` file is the core of the application. It manages:

- **Scroll Progress** - Tracks vertical scroll position (0 to 3.5)
- **Lerped Progress** - Smoothly interpolated scroll value for animations
- **Active Section** - Determines which navigation section is active based on scroll progress
- **Navigation Handling** - Smooth animated navigation to specific sections

### Key Functions

#### `updateActiveSection(progress: number): string`
Determines which section should be highlighted based on scroll progress:
- `0.00 - 0.18` → Hero section
- `0.18 - 0.45` → Projects section
- `0.45 - 0.68` → Expertise section
- `0.68 - 1.15` → About section
- `1.15+` → Contact section

#### `easeInOutCubic(p: number): number`
Cubic easing function for smooth navigation animations.

#### `clamp(v, min, max)`
Utility to constrain values within a range.

### Scroll-Based Animations

Scroll progress is synchronized with all animated components:

```tsx
<VideoScrubber scrollProgress={Math.min(1, lerpedScrollProgress)} />
<SecondVideoScrubber scrollProgress={lerpedScrollProgress} />
<CylindricalTextDrum scrollProgress={lerpedScrollProgress} />
```

### Navigation

Navigate to sections programmatically:

```tsx
handleNavigateToSection({ scrollRatio: 1.5 })
```

This will smoothly animate to the specified scroll ratio over 1200ms.

## 🎨 Key Sections

### Hero Section (0.0 - 0.18)
- Welcome video with scroll scrubbing
- Split text animation for "INNER CIRCLE" title
- Soap tile effects

### Projects Section (0.18 - 0.45)
- Featured projects display
- Project showcase with animations

### Expertise Section (0.45 - 0.68)
- Skills and expertise showcase
- Interactive expertise display

### About Section (0.68 - 1.15)
- About information with video scrubber
- Cylindrical text drum animation

### Contact Section (1.15+)
- Contact information
- Company logo marquee
- Social links

## ⚙️ Configuration

### Colors
- Primary: `#FF005E` (Bright Pink)
- Background: `#11010a` (Dark Purple)
- Text: White with opacity variations

### Animation Speeds
- Lerp amount: `0.08` (higher = snappier, lower = smoother)
- Navigation duration: `1200ms`
- Scroll sensitivity: `0.0006` (wheel) / `0.0015` (touch)

### Scroll Ranges
- Maximum scroll progress: `3.5`
- Customizable per component

## 🔧 Development

### Adding New Sections

1. Add navigation item to `NAVIGATION_ITEMS` in `data/index.ts`
2. Create a new component for the section
3. Update `updateActiveSection()` with new progress ranges
4. Import and include the component in `App.tsx`

### Creating Custom Animations

Use the `scrollProgress` and `lerpedScrollProgress` values to drive animations:

```tsx
style={{
  transform: `translateY(${scrollProgress * 100}px)`,
  opacity: Math.max(0, 1 - scrollProgress * 2),
}}
```

## 🎯 Performance Optimization

- Scroll events use `requestAnimationFrame` for 60fps animations
- Event listeners use `passive: false` for wheel and touch (enables `preventDefault`)
- Lerp loop only updates when values change significantly (`> 0.0001`)
- CSS `will-change` property applied to animated elements

## 📱 Browser Support

- Chrome/Edge (latest)
- Firefox (latest)
- Safari (latest)
- Mobile browsers with touch support

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the MIT License.

## 👤 Author

**Khass1334-debug**

- GitHub: [@Khass1334-debug](https://github.com/Khass1334-debug)

## 🙋 Support

If you have any questions or issues, please feel free to:
- Open an issue on GitHub
- Check existing issues for solutions

---

**Happy coding! 🚀**
