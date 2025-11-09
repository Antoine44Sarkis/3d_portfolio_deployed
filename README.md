# 🚀 Antoine Sarkis - Adaptive 3D/2D Portfolio

> **An innovative, dual-experience portfolio that intelligently adapts between immersive 3D graphics and modern 2D design based on device capabilities.**

**Hi, I'm Antoine Sarkis** | Full Stack Developer | 42 Beirut - Level 7 | Physics Background

click to see : [![🚀 Live Demo – Visit My Portfolio!](https://img.shields.io/badge/demo-live-brightgreen)](https://antoine-sarkis.vercel.app)

---

## 🌐 My Portfolio is Live!

- [Project Structure](#-project-structure)
  Organized 100+ components into a clean, scalable structure:

**Why this matters**: Any developer can understand and extend this codebase immediately.

### 3. **Performance Engineering** ⚡

Achieved **81% asset size reduction** through:

| Optimization             | Before   | After   | Impact             |
| ------------------------ | -------- | ------- | ------------------ |
| **3D Model Compression** | 23.37 MB | 3.48 MB | **-85.1%** 🔥      |
| **Image Optimization**   | ~3.5 MB  | ~1.2 MB | **-66%**           |
| **Particle Count**       | 4,000    | 1,500   | **-62%**           |
| **Initial Load Time**    | 3-8s     | 1-3s    | **~70% faster** ⚡ |
| **Lighthouse Score**     | 40-60    | 80-95   | **+40 points** 📈  |

**Techniques I Implemented**:

- ✅ Draco mesh compression for 3D models
- ✅ WebP image conversion with Sharp
- ✅ LocalStorage caching for instant repeat visits
- ✅ Dynamic imports & code splitting
- ✅ Optimized Three.js rendering pipeline
- ✅ Bundle size optimization (tree shaking, minification)

**Why this matters**: Shows I don't just build features — I optimize them for production.

### 4. **Advanced State Management** 🔄

Refactored from messy useState to **Redux Toolkit** architecture:

- **Migrated 35+ useState** → Centralized Redux store
- **Created 8 specialized slices** for different concerns
- **Type-safe hooks** throughout (`useAppDispatch`, `useAppSelector`)
- **Predictable state** across 2D and 3D modes

```typescript
store/slices/
├── uiSlice.ts              // Menu, modals, UI state
├── projectsSlice.ts        // Project interactions
├── feedbackSlice.ts        // Form management (15+ fields)
├── musicSlice.ts           // Audio player state
├── languageSlice.ts        // i18n state
├── heroSlice.ts            // Hero section (11 states!)
├── hero3DButtonsSlice.ts   // 3D button animations
└── skillsSlice.ts          // Skills selection & visibility
```

**Why this matters**: Demonstrates enterprise-level state management at scale.

---

## 🏗️ Technical Architecture

### How the Responsive System Works

```
┌─────────────────────────────────────────────────┐
│           ResponsivePortfolio.tsx               │
│    (Main component with layout switcher)        │
│                                                 │
│  useResponsiveLayout() → Detects screen size    │
│            ↓                                    │
│     Is screen ≤1024px?                          │
│            ↓                                    │
│      ┌─────┴─────┐                              │
│      ↓           ↓                              │
│   Layout2D    Layout3D                          │
│   (Mobile)    (Desktop)                         │
│      ↓           ↓                              │
│   2D/ui/     3D/ + ui/                          │
│   components  components                        │
└─────────────────────────────────────────────────┘
```

### Custom Hooks I Built

#### 1. **useMediaQuery** - Media Query Detection

```typescript
// Handles media queries with SSR safety
const isMobile = useMediaQuery("(max-width: 768px)");
const isTablet = useMediaQuery("(min-width: 768px) and (max-width: 1023px)");
const isDesktop = useMediaQuery("(min-width: 1024px)");
```

**Features**:

- ✅ SSR-safe (prevents hydration mismatches)
- ✅ Automatic cleanup
- ✅ Modern & legacy browser support
- ✅ TypeScript typed

#### 2. **useResponsiveLayout** - Layout Mode Logic

```typescript
// Determines which experience to show
const {
  layoutMode, // "2d" | "3d"
  is2DMode, // boolean
  is3DMode, // boolean
  isSmallScreen, // ≤767px
  isMediumScreen, // 768-1023px
  isLargeScreen, // ≥1024px
} = useResponsiveLayout();
```

**Why I built this**: Centralized responsive logic, no prop drilling, type-safe.

---

## ✨ Key Features & Achievements

### 🎮 3D Desktop Experience (>1024px)

**What I Built**:

- **Interactive 3D Hero** with animated alien character
- **Orbital Project System** - Planets that orbit and respond to clicks
- **Real-time Particle System** - 1,500 optimized particles
- **3D Modals & Holos** - HoloGem effects, project modals
- **Speech Synthesis** - Alien character "speaks" portfolio content
- **Matrix Aesthetic** - Green-on-black terminal theme

**Technical Highlights**:

```typescript
// 3D Model with LocalStorage caching
const cachedModel = await ModelCache.loadModel(modelPath);
// 85% size reduction + instant repeat loads!

// Optimized Three.js setup
<Canvas
  gl={{ powerPreference: "high-performance", antialias: false }}
  dpr={[1, 1.5]}  // Limit pixel ratio
>
```

### 📱 2D Mobile Experience (≤1024px)

**What I Built**:

- **Gradient Hero** with animated stats and CTAs
- **Glass Morphism Cards** for About section
- **Filterable Skills** with animated progress bars
- **Card-Based Projects** with modal details
- **Vertical Timeline** for Experience
- **Contact Cards** with animated interactions

**Technical Highlights**:

```typescript
// Glass morphism styling
className="bg-white/5 backdrop-blur-sm border border-white/10"

// Animated progress bars
<motion.div
  initial={{ width: 0 }}
  whileInView={{ width: `${skill.level}%` }}
  transition={{ duration: 1, ease: "easeOut" }}
/>
```

### 🌍 Internationalization

**3 Languages Supported**:

- 🇬🇧 **English** - Full content
- 🇫🇷 **French** - Translated sections
- 🇰🇷 **Korean** - Shows my passion for South Korea!

**Implementation**:

```typescript
// i18next integration
const { t } = useTranslation();
<h1>{t("hero.title")}</h1>

// Dynamic language switching
<LanguageSwitcher />  // Multiple variants available
```

### 💾 Feedback System

**Full-Stack Feature**:

- MongoDB database integration
- API routes (`/api/feedback`)
- Form validation (15+ fields)
- Like/Dislike system
- Optional fields (name, email, phone, country, gender)
- Feedback display with pagination

```typescript
// Redux-managed form state
feedbackSlice.ts:
- Form fields (feedback, name, email, etc)
- Validation errors
- Submission status
- Feedbacks list with pagination
```

---

## 📦 Project Structure

I organized the codebase for **maximum clarity and maintainability**:

```
src/
├── app/                              # Next.js 15 App Router
│   ├── api/feedback/route.ts        # Feedback API endpoint
│   ├── ClientLayout.tsx             # Redux Provider wrapper
│   ├── layout.tsx                   # Root layout + metadata
│   └── page.tsx                     # Entry point (uses ResponsivePortfolio)
│
├── components/
│   ├── 2d/                          # 📱 MOBILE/TABLET EXPERIENCE
│   │   ├── layouts/
│   │   │   └── Layout2D.tsx         # 2D layout wrapper
│   │   └── ui/                      # 2D UI Components
│   │       ├── Hero2D.tsx           # Gradient hero + stats
│   │       ├── About2D.tsx          # Glass morphism cards
│   │       ├── Skills2D.tsx         # Progress bars + filters
│   │       ├── Projects2D.tsx       # Card-based projects
│   │       ├── Experience2D.tsx     # Vertical timeline
│   │       ├── Contact2D.tsx        # Contact cards + CTA
│   │       └── index.ts             # Clean exports
│   │
│   ├── 3d/                          # 💻 DESKTOP EXPERIENCE
│   │   ├── layouts/
│   │   │   └── Layout3D.tsx         # 3D layout wrapper
│   │   ├── GlobalParticleBackground.tsx  # 1,500 particles
│   │   ├── HoloGem.tsx              # 3D holographic effects
│   │   ├── SphereList.tsx           # Planetary spheres
│   │   ├── ProjectModal.tsx         # 3D project modals
│   │   ├── InteractivePortfolio.tsx # Interactive 3D canvas
│   │   └── index.ts                 # Clean exports
│   │
│   ├── shared/                      # 🤝 SHARED BETWEEN BOTH
│   │   ├── Navbar.tsx               # Adaptive navigation
│   │   ├── Footer.tsx               # Responsive footer
│   │   ├── MusicProvider.tsx        # Audio context + controls
│   │   ├── AnimatedSection.tsx      # Scroll animations
│   │   └── index.ts                 # Clean exports
│   │
│   ├── language-switchers/          # 🌍 LANGUAGE VARIANTS
│   │   ├── LanguageSwitcher.tsx     # Default switcher
│   │   ├── LanguageSwitcherCards.tsx
│   │   ├── LanguageSwitcherCarousel.tsx
│   │   ├── LanguageSwitcherOrbiting.tsx
│   │   └── index.ts
│   │
│   ├── ui/                          # 🎮 ORIGINAL 3D COMPONENTS
│   │   ├── About.tsx                # 3D about section
│   │   ├── Contact.tsx              # 3D contact
│   │   ├── Experience.tsx           # 3D experience
│   │   ├── Feedback.tsx             # Feedback form (shared)
│   │   ├── Hero.tsx                 # 3D hero with alien
│   │   ├── Hero3DButtons.tsx        # Interactive 3D buttons
│   │   ├── Navbar.tsx               # Original navbar
│   │   ├── Projects.tsx             # Planetary projects
│   │   └── Skills.tsx               # 3D skill spheres
│   │
│   ├── ResponsivePortfolio.tsx      # 🎯 MAIN SWITCHER
│   └── LazyComponents.tsx           # Lazy loading utilities
│
├── hooks/                           # 🪝 CUSTOM REACT HOOKS
│   ├── useMediaQuery.ts             # Media query detection
│   ├── useResponsiveLayout.ts       # Layout mode logic
│   └── index.ts                     # Clean exports
│
├── store/                           # 🔄 REDUX STATE MANAGEMENT
│   ├── index.ts                     # Store configuration
│   ├── hooks.ts                     # Type-safe hooks
│   └── slices/                      # 8 Redux slices
│       ├── uiSlice.ts               # UI state (menu, modals)
│       ├── projectsSlice.ts         # Project interactions
│       ├── feedbackSlice.ts         # Feedback form (15+ fields)
│       ├── musicSlice.ts            # Audio player
│       ├── languageSlice.ts         # i18n state
│       ├── heroSlice.ts             # Hero interactions (11 states)
│       ├── hero3DButtonsSlice.ts    # 3D button animations
│       └── skillsSlice.ts           # Skills selection
│
├── lib/
│   ├── three/                       # 🎨 THREE.JS UTILITIES
│   │   ├── ModelCache.ts            # 3D model caching system
│   │   ├── ParticleSystem.ts        # Particle generation
│   │   └── PlanetSphere.ts          # Planet rendering
│   ├── i18n.ts                      # i18next configuration
│   └── mongodb.ts                   # Database connection
│
├── locales/                         # 🌍 TRANSLATIONS
│   ├── en.json                      # English
│   ├── fr.json                      # French
│   └── ko.json                      # Korean (🇰🇷 My dream!)
│
├── data/
│   └── projects.ts                  # Project data with icons
│
└── types/
    └── project.ts                   # TypeScript interfaces
```

**Folder Organization Principles**:

- ✅ **Clear separation** of 2D and 3D concerns
- ✅ **Shared components** in dedicated folder
- ✅ **Clean exports** with index files
- ✅ **Feature-based** organization
- ✅ **Easy to navigate** and extend

---

## 🛠️ Tech Stack

### Frontend Core

| Technology        | Version | Purpose                         |
| ----------------- | ------- | ------------------------------- |
| **Next.js**       | 15.5.4  | React framework with App Router |
| **React**         | 19.0.0  | UI library with latest features |
| **TypeScript**    | 5.x     | Type-safe development           |
| **Tailwind CSS**  | 4.x     | Utility-first styling           |
| **Framer Motion** | 12.x    | Advanced animations             |

### 3D Graphics Stack

| Technology            | Purpose                     |
| --------------------- | --------------------------- |
| **Three.js**          | 3D rendering engine         |
| **React Three Fiber** | React renderer for Three.js |
| **@react-three/drei** | Useful Three.js helpers     |
| **Draco Decoder**     | 3D model compression        |

### State & Data Management

| Technology        | Purpose                      |
| ----------------- | ---------------------------- |
| **Redux Toolkit** | Centralized state management |
| **React-Redux**   | React bindings for Redux     |
| **MongoDB**       | NoSQL database for feedback  |
| **i18next**       | Internationalization         |
| **react-i18next** | React i18n bindings          |

### Performance & Optimization

| Tool                | Purpose                      |
| ------------------- | ---------------------------- |
| **Sharp**           | Image optimization           |
| **gltf-pipeline**   | 3D model compression         |
| **Next.js Image**   | Automatic image optimization |
| **Dynamic Imports** | Code splitting               |

### Development Tools

| Tool       | Purpose                |
| ---------- | ---------------------- |
| **pnpm**   | Fast package manager   |
| **ESLint** | Code quality & linting |
| **Vercel** | Deployment platform    |

---

## ⚡ Performance Optimization

### What I Optimized

#### 1. **3D Model Compression** (HUGE WIN! 🔥)

**Problem**: Original alien model was 23.37 MB
**Solution**:

```bash
# Custom compression script
pnpm compress-model

# Result: 3.48 MB (85.1% reduction!)
```

**Techniques**:

- ✅ Draco mesh compression with highest quality
- ✅ LocalStorage caching for instant repeat visits
- ✅ Reduced loading delay from 2s → 500ms
- ✅ Disabled shadows & antialiasing for performance

**Implementation**:

```typescript
// lib/three/ModelCache.ts
export class ModelCache {
  static async loadModel(path: string) {
    // Try cache first
    const cached = localStorage.getItem(cacheKey);
    if (cached && !isExpired) {
      return JSON.parse(cached);
    }

    // Load and cache
    const model = await loadGLTF(path);
    localStorage.setItem(cacheKey, JSON.stringify(model));
    return model;
  }
}
```

#### 2. **Image Optimization**

**Automated with custom script**:

```bash
pnpm optimize-images
```

| Image  | Before | After  | Savings   |
| ------ | ------ | ------ | --------- |
| Earth  | 980 KB | 330 KB | **66.3%** |
| Mars   | 653 KB | 217 KB | **66.8%** |
| Saturn | 431 KB | 85 KB  | **80.2%** |
| Venus  | 488 KB | 214 KB | **56.2%** |
| Pluton | 955 KB | 360 KB | **62.3%** |

**Techniques**:

- ✅ WebP conversion
- ✅ Quality optimization
- ✅ Responsive sizing
- ✅ Lazy loading

#### 3. **Particle System Optimization**

**Reduced from 4,000 → 1,500 particles** while maintaining visual quality

```typescript
// Before: 4000 particles (laggy on mobile)
const particleCount = 4000;

// After: 1500 particles (smooth 60fps)
const particleCount = 1500;

// Plus rendering optimizations
gl={{ antialias: false, powerPreference: "high-performance" }}
dpr={[1, 1.5]}  // Limit device pixel ratio
```

#### 4. **Code Splitting & Lazy Loading**

**Every major component lazy loaded**:

```typescript
// LazyComponents.tsx
export const LazyGlobalParticleBackground = dynamic(
  () => import("@/components/3d/GlobalParticleBackground"),
  { loading: () => null, ssr: false }
);

export const LazyAbout = dynamic(() => import("@/components/ui/About"), {
  loading: () => <LoadingSection />,
  ssr: true,
});
```

**Benefits**:

- ✅ Faster initial load
- ✅ Smaller JavaScript bundle
- ✅ Better First Contentful Paint (FCP)
- ✅ On-demand loading as user scrolls

#### 5. **Next.js Configuration**

```typescript
// next.config.ts
export default {
  compress: true, // Gzip compression
  images: {
    formats: ["image/avif", "image/webp"], // Modern formats
  },
  experimental: {
    optimizePackageImports: ["lucide-react", "framer-motion"],
  },
};
```

#### 6. **Vercel Deployment Optimization**

```json
// vercel.json
{
  "headers": [
    {
      "source": "/models/(.*)",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=2592000, must-revalidate"
        }
      ]
    }
  ]
}
```

### Performance Results

| Metric                     | Before    | After     | Improvement          |
| -------------------------- | --------- | --------- | -------------------- |
| **Initial Load Time**      | 3-8s      | 1-3s      | **60-70% faster** ⚡ |
| **Repeat Visit**           | 2-4s      | 0.5s      | **80% faster** 🚀    |
| **Total Asset Size**       | ~27 MB    | ~5 MB     | **81% smaller** 🔥   |
| **Lighthouse Performance** | 40-60     | 80-95     | **+40 points** 📈    |
| **Core Web Vitals**        | ❌ Failed | ✅ Passed | **Production Ready** |

**Core Web Vitals**:

- **LCP** (Largest Contentful Paint): < 1.8s ✅
- **FID** (First Input Delay): < 50ms ✅
- **CLS** (Cumulative Layout Shift): < 0.05 ✅

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18+ installed
- **pnpm** package manager (or npm)
- **MongoDB** connection string

## 🎨 Design Philosophy

### 2D Design System (Mobile/Tablet - ≤1024px)

**Visual Language**:

- **Modern & Clean**: Glass morphism with backdrop blur
- **Gradient-Heavy**: Purple-to-blue gradients for depth
- **Card-Based**: Everything in rounded, bordered cards
- **Touch-First**: Large touch targets (min 44x44px)
- **Vertical Flow**: Single column, scroll-based

**Color Palette**:

```css
/* Primary Gradients */
from-purple-600 to-blue-600   /* CTAs, buttons */
from-purple-500 to-pink-600   /* Accent elements */
from-emerald-500 to-teal-600  /* Success states */

/* Backgrounds */
bg-slate-950                  /* Main background */
bg-slate-900                  /* Section backgrounds */
bg-white/5                    /* Glass morphism cards */

/* Text */
text-white                    /* Primary text */
text-gray-300                 /* Secondary text */
text-gray-400                 /* Tertiary text */
```

**Component Patterns**:

```tsx
// Glass morphism card
<div className="p-6 rounded-2xl bg-white/5 backdrop-blur-sm border border-white/10 hover:border-white/30">

// Gradient heading
<h2 className="text-4xl font-bold bg-linear-to-r from-white to-gray-400 bg-clip-text text-transparent">

// Animated button
<button className="px-8 py-4 bg-linear-to-r from-purple-600 to-blue-600 rounded-full shadow-lg hover:scale-105">
```

### 3D Design System (Desktop - >1024px)

**Visual Language**:

- **Immersive**: Full-screen 3D canvas experiences
- **Matrix Theme**: Green-on-black terminal aesthetic
- **Interactive**: Mouse-driven hover & click interactions
- **Space Theme**: Planets, particles, cosmic elements
- **Cyberpunk**: Glowing effects, neon accents

**Color Palette**:

```css
/* Primary */
--green-400: #00ff41      /* Matrix green */
--black: #000000          /* Deep black background */

/* Accents */
--green-300: #00ff88      /* Lighter green */
--green-500: #00cc33      /* Darker green */
```

**3D Patterns**:

```tsx
// Three.js Canvas setup
<Canvas
  camera={{ position: [0, 0, 5], fov: 75 }}
  shadows={false}
  gl={{
    alpha: true,
    antialias: false,
    powerPreference: "high-performance",
  }}
  dpr={[1, 1.5]}
>

// Particle system
<ParticleSystem count={1500} />

// Interactive planets
<PlanetSphere
  texture="/images/earth.png"
  onClick={handleClick}
  onHover={handleHover}
/>
```

### Responsive Breakpoints

```typescript
// Custom breakpoints
const breakpoints = {
  small: "≤767px", // Mobile phones
  medium: "768-1023px", // Tablets
  large: "≥1024px", // Desktops
};

// Layout switching
const LAYOUT_BREAKPOINT = 1024; // px
```

---

## 🔄 State Management

### Redux Architecture

I refactored the entire state from scattered `useState` to **centralized Redux Toolkit**:

**Before** (Messy):

```tsx
// Scattered across 13+ components
const [isMenuOpen, setIsMenuOpen] = useState(false);
const [selectedProject, setSelectedProject] = useState(null);
const [feedback, setFeedback] = useState("");
// ... 32 more useState calls!
```

**After** (Clean):

```tsx
// Centralized in Redux slices
const isMenuOpen = useAppSelector((state) => state.ui.isMenuOpen);
const dispatch = useAppDispatch();
dispatch(setMenuOpen(true));
```

### Redux Slices

#### 1. **uiSlice.ts** - UI State

```typescript
interface UIState {
  isMenuOpen: boolean; // Mobile menu
  showModal: boolean; // Modal visibility
  theme: "light" | "dark"; // Theme mode
}
```

#### 2. **projectsSlice.ts** - Project Interactions

```typescript
interface ProjectsState {
  selectedProject: ProjectData | null; // Selected project
  hoveredProject: string | null; // Hovered project ID
  projectsVisible: boolean; // Section visibility
}
```

#### 3. **feedbackSlice.ts** - Feedback Form (15+ fields!)

```typescript
interface FeedbackState {
  // Form fields
  feedback: string;
  name: string;
  email: string;
  phone: string;
  education: string;
  country: string;
  gender: string;
  like: boolean;
  dislike: boolean;

  // UI state
  clicked: boolean;
  submitted: boolean;
  error: string;

  // Feedbacks list
  feedbacks: Feedback[];
  feedbacksLoading: boolean;
  feedbacksToShow: number;
  allFeedbacksLoaded: boolean;
}
```

#### 4. **musicSlice.ts** - Audio Player

```typescript
interface MusicState {
  isPlaying: boolean;
  volume: number;
  currentTrack: string;
}
```

#### 5. **languageSlice.ts** - i18n State

```typescript
interface LanguageState {
  currentLanguage: "en" | "fr" | "ko";
  availableLanguages: string[];
}
```

#### 6. **heroSlice.ts** - Hero Section (11 states!)

```typescript
interface HeroState {
  isTyping: boolean;
  showButtons: boolean;
  isSpeaking: boolean;
  speechText: string;
  currentButtonIndex: number;
  currentIndex: number;
  alienMessage: string;
  clickedButtons: boolean[];
  modelLoaded: boolean;
  modelLoading: boolean;
  loadingProgress: number;
}
```

#### 7. **hero3DButtonsSlice.ts** - 3D Button Animations

```typescript
interface Hero3DButtonsState {
  hoveredButton: string | null;
  activeButton: string | null;
  buttonStates: Record<string, ButtonState>;
}
```

#### 8. **skillsSlice.ts** - Skills Selection

```typescript
interface SkillsState {
  selectedSkill: string | null;
  hoveredSkill: string | null;
  skillsInView: boolean;
}
```

### Benefits of Redux Migration

| Before (useState) | After (Redux)  | Benefit               |
| ----------------- | -------------- | --------------------- |
| Scattered state   | Centralized    | Easy debugging        |
| Prop drilling     | Direct access  | Less boilerplate      |
| No DevTools       | Redux DevTools | Time travel debugging |
| Hard to test      | Easy to test   | Better testing        |
| No persistence    | Can persist    | Better UX             |

---

## 👨‍💼 For Recruiters & Companies

### Why This Portfolio Stands Out

**This is not just a portfolio — it's a demonstration of production-level engineering.**

#### 1. **Problem-Solving Skills** 🧠

**Problem**: Traditional portfolios perform poorly on mobile
**Solution**: Built two distinct experiences that switch automatically
**Impact**: Perfect UX on any device, 81% data reduction

#### 2. **Architecture Skills** 🏗️

- Organized 100+ components into scalable folder structure
- Created reusable custom hooks
- Implemented clean separation of concerns
- Built with future maintenance in mind

#### 3. **Performance Engineering** ⚡

- **85% model compression** through Draco encoding
- **66% image optimization** via WebP conversion
- **LocalStorage caching** for instant repeat visits
- **70% faster load times** through optimization techniques

#### 4. **State Management at Scale** 🔄

- Migrated **35+ useState** to Redux Toolkit
- Created **8 specialized slices** for different concerns
- Type-safe throughout with **custom hooks**
- Demonstrates **enterprise-level** state architecture

#### 5. **Full-Stack Capabilities** 🌐

- **Backend**: MongoDB integration, API routes
- **Frontend**: React 19, Next.js 15, TypeScript
- **3D Graphics**: Three.js, React Three Fiber
- **Performance**: Optimization scripts, caching strategies
- **DevOps**: Vercel deployment, cache headers

#### 6. **Modern Tech Stack** 💻

- Next.js 15 (App Router)
- React 19 (latest features)
- TypeScript (full type safety)
- Redux Toolkit (state management)
- Three.js (3D graphics)
- Framer Motion (animations)
- MongoDB (database)
- i18next (i18n)

### What I Can Bring to Your Team

✅ **Write clean, maintainable code** that other developers can easily understand  
✅ **Optimize for performance** from day one, not as an afterthought  
✅ **Think about scalability** and future maintenance  
✅ **Solve complex problems** with creative solutions  
✅ **Work with modern tech stacks** and learn new ones quickly  
✅ **Build full-stack applications** from database to UI  
✅ **Care about user experience** across all devices  
✅ **Document and communicate** technical decisions clearly

### Technical Skills Demonstrated

**Frontend**:

- React (advanced hooks, context, performance)
- Next.js (App Router, SSR, optimization)
- TypeScript (type-safe development)
- Tailwind CSS (utility-first styling)
- Framer Motion (complex animations)

**3D Graphics**:

- Three.js fundamentals
- React Three Fiber
- 3D model optimization
- WebGL rendering
- Performance tuning

**State Management**:

- Redux Toolkit (slices, thunks)
- Custom hooks (useAppDispatch, useAppSelector)
- Complex state architecture
- Type-safe state access

**Backend**:

- MongoDB integration
- Next.js API routes
- RESTful API design
- Database operations

**Performance**:

- Asset optimization (images, models)
- Caching strategies (LocalStorage, HTTP)
- Code splitting & lazy loading
- Bundle size optimization
- Lighthouse optimization

**DevOps**:

- Vercel deployment
- Environment configuration
- Build optimization
- Cache headers

---

## 🇰🇷 My Dream: Working in South Korea

### Why This Portfolio Includes Korean

This portfolio is **personal** to me. I didn't just build it to show off skills — I built it to show **who I am** and **what I dream of**.

**I want to live and work in South Korea as a Full Stack Developer.**

#### What I've Done to Show This:

- ✅ **Korean language support** (한국어) - Full translation
- ✅ **Dedicated sections** about my South Korea dream
- ✅ **Cultural consideration** in design
- ✅ **Genuine passion** visible throughout

#### Why South Korea?

- 🇰🇷 **Tech innovation** - World-leading tech industry
- 🇰🇷 **Work culture** - Dedicated, ambitious, growth-focused
- 🇰🇷 **Personal dream** - More than just a job, it's where I want to build my life

#### What I Offer:

- ✅ **Genuine motivation** - Not just for the job, but for the experience
- ✅ **Willing to relocate** - Ready to move immediately
- ✅ **Salary is secondary** - The opportunity matters more
- ✅ **Long-term commitment** - Want to build my career there
- ✅ **Cultural respect** - Learning language and customs

**For South Korean companies**: I'm not just another applicant. I'm someone who has dreamed of working in your country and has the skills and passion to contribute meaningfully to your team.

---

## 📞 Contact Me

I'm currently **open to new opportunities**, especially in **South Korea**! 🇰🇷

### Get In Touch

- 📧 **Email**: antoinesarkis44@gmail.com
- 🌐 **Portfolio**: [your-portfolio-url.vercel.app](https://your-portfolio-url.vercel.app)
- 📱 **Phone**: +961 76 409 440

### About Me

**Antoine Sarkis**

- 🎓 **Education**: 42 Beirut - Level 7 | Physics Background
- 💼 **Current**: Full Stack Developer Intern at CMA CGM The Hub
- 🌍 **Languages**: Arabic (native), English, French, Korean (learning)
- 🇰🇷 **Dream**: Work as Full Stack Developer in South Korea

### What I'm Looking For

- ✅ **Full Stack Developer** roles
- ✅ **Frontend/Backend Engineer** positions
- ✅ **Opportunities in South Korea** (preferred)
- ✅ **Growth-oriented companies**
- ✅ **Modern tech stacks**

**Availability**: Immediate (can relocate)

---

## 📄 License

This project is **proprietary** - created by Antoine Sarkis as a portfolio showcase.

**Want to collaborate or hire me? Let's talk!** 🚀

---

## 🙏 Attribution

### Resources Used

- **Background Music**: "Celestial Drift" by lofdreams ([Pixabay License](https://pixabay.com/music/))
- **3D Model**: Alien Mecha character model
- **Icons**: [Lucide React](https://lucide.dev/)
- **Fonts**: System fonts for optimal performance
- **Technologies**: Open-source libraries from the amazing developer community

---

## 📊 Project Stats

| Metric                  | Value          |
| ----------------------- | -------------- |
| **Lines of Code**       | ~15,000+       |
| **Components**          | 100+           |
| **Redux Slices**        | 8              |
| **Custom Hooks**        | 2              |
| **Languages Supported** | 3 (EN, FR, KO) |
| **Asset Reduction**     | 81%            |
| **Performance Gain**    | 70% faster     |
| **Lighthouse Score**    | 80-95          |
| **Development Time**    | 2+ months      |
| **Coffee Consumed**     | ∞ ☕           |

---

## 🎉 Summary

### What I Built

This portfolio demonstrates:

1. **Adaptive Architecture** - Two complete experiences in one app
2. **Performance Engineering** - 81% asset reduction, 70% faster loads
3. **Enterprise State Management** - Redux with 8 slices, 35+ migrated states
4. **3D Graphics Mastery** - Three.js, WebGL, optimized rendering
5. **Modern Full-Stack Skills** - Next.js 15, React 19, TypeScript, MongoDB
6. **Clean Code** - Scalable architecture, type-safe, well-organized
7. **UX Thinking** - Device-appropriate experiences, accessibility
8. **Passion Project** - Shows my dream to work in South Korea 🇰🇷

### Ready for Production

✅ **81% smaller** assets  
✅ **70% faster** load times  
✅ **Zero TypeScript** errors  
✅ **Lighthouse 80-95** score  
✅ **Fully responsive** (2D/3D)  
✅ **Multi-language** support  
✅ **Production-optimized** deployment  
✅ **Maintainable** codebase

---

**Built with ❤️ and countless hours of coding by Antoine Sarkis**

_42 Beirut - Level 7 | Full Stack Developer | Physics Background | South Korea Enthusiast 🇰🇷_

**⭐ If you're interested in working together, please reach out!**

---

