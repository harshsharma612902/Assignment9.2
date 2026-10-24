The HTML File (index.html)
HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Responsive Typography & Images Article</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <!-- Step 1 & 5: Content Container with Optimal Max-Width -->
    <main class="article-container">
        
        <!-- Article Header -->
        <header class="article-header">
            <span class="category">Web Standards</span>
            <!-- Steps 2 & 3: Fluid Heading using clamp() -->
            <h1>Mastering Responsive Typography and Fluid Images</h1>
            <p class="byline">By Sarah Jenkins • Published October 26, 2026</p>
        </header>

        <!-- Featured Image (Steps 2 & 4) -->
        <div class="image-wrapper">
            <img 
                src="https://images.unsplash.com/photo-1499750310107-5fef28a66643?auto=format&fit=crop&q=80&w=800" 
                alt="Developer workspace with laptop and notebook"
            >
            <figcaption>Photo by benchmark workspace design.</figcaption>
        </div>

        <!-- Article Body Content (Steps 2 & 6: Optimized Line Length & Spacing) -->
        <section class="article-body">
            <p class="lead">
                Creating a seamless reading experience across mobile phones, tablets, and widescreen desktop monitors requires more than just media queries. It demands fluid typographic scales and resilient media containers.
            </p>

            <h2>The Evolution of Fluid Sizing</h2>
            <p>
                In the past, developers relied heavily on rigid pixel values or cumbersome media query breakpoints to adjust font sizes between viewports. Today, modern CSS functions like <code>clamp()</code> allow text to scale smoothly and proportionally based on the viewport width.
            </p>

            <p>
                Similarly, images must never be locked to fixed pixel dimensions. By applying fundamental rules like <code>max-width: 100%</code> and <code>height: auto</code>, graphics scale down cleanly inside smaller viewports without overflowing or distorting their aspect ratios.
            </p>

            <h2>Optimizing Line Lengths for Readability</h2>
            <p>
                Typography experts have long noted that lines of text exceeding 75 characters become fatiguing for readers to track across wide desktop screens. Restricting paragraph containers using character units (like <code>ch</code>) or controlled maximum widths keeps reading comfortable at any screen size.
            </p>

            <!-- Secondary Image Example -->
            <div class="image-wrapper">
                <img 
                    src="https://images.unsplash.com/photo-1507238691740-187a5b1d37b8?auto=format&fit=crop&q=80&w=800" 
                    alt="Team collaboration on web design"
                >
                <figcaption>Collaboration fuels modern responsive design systems.</figcaption>
            </div>

            <p>
                By combining fluid typographic scales, fluid media blocks, and robust container constraints, your web pages will maintain professional polish and pristine legibility across every device your users bring to the web.
            </p>
        </section>

    </main>

</body>
</html>
2. The CSS File (style.css)
CSS
/* ==========================================================================
   Global Reset & Root Variables
   ========================================================================== */
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

:root {
    --text-main: #1e293b;
    --text-muted: #475569;
    --bg-page: #f8fafc;
    --bg-card: #ffffff;
    --border-color: #cbd5e1;
    --accent-color: #2563eb;
}

body {
    font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
    background-color: var(--bg-page);
    color: var(--text-main);
    line-height: 1.7;
    padding: 40px 16px;
    overflow-x: hidden; /* Step 7: Prevents horizontal screen overflow */
}

/* ==========================================================================
   Step 5: Content Container Max-Width & Centering
   ========================================================================== */
.article-container {
    max-width: 720px; /* Optimal reading width container */
    margin: 0 auto;
    background-color: var(--bg-card);
    border: 1px solid var(--border-color);
    border-radius: 12px;
    padding: 32px 24px;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
}

@media (min-width: 640px) {
    .article-container {
        padding: 56px 48px;
    }
}

/* ==========================================================================
   Step 3: Responsive Typography (rem, em, clamp)
   ========================================================================== */
.article-header {
    margin-bottom: 32px;
    border-bottom: 1px solid #e2e8f0;
    padding-bottom: 24px;
}

.category {
    display: inline-block;
    font-size: 0.85rem;
    font-weight: 700;
    text-transform: uppercase;
    color: var(--accent-color);
    letter-spacing: 0.5px;
    margin-bottom: 8px;
}

/* Fluid Heading using clamp(min, preferred, max) */
h1 {
    font-size: clamp(1.75rem, 4vw + 1rem, 2.75rem);
    font-weight: 800;
    color: #0f172a;
    line-height: 1.2;
    margin-bottom: 12px;
}

.byline {
    font-size: 0.9rem;
    color: var(--text-muted);
}

h2 {
    font-size: clamp(1.35rem, 2vw + 0.75rem, 1.85rem);
    font-weight: 700;
    color: #0f172a;
    margin-top: 40px;
    margin-bottom: 16px;
}

/* Step 6: Improved Line Length & Spacing for Paragraphs */
.article-body p {
    font-size: 1.05rem; /* Base size in rem relative to root */
    color: var(--text-main);
    margin-bottom: 24px;
    max-width: 65ch; /* Keeps line length optimal for readability */
}

.article-body p.lead {
    font-size: 1.2rem;
    color: #334155;
    font-weight: 500;
}

/* Code snippet styling */
code {
    background-color: #f1f5f9;
    color: #0f172a;
    padding: 2px 6px;
    border-radius: 4px;
    font-size: 0.9em;
    font-family: monospace;
}

/* ==========================================================================
   Step 4: Responsive Images (max-width: 100%, height: auto)
   ========================================================================== */
.image-wrapper {
    margin: 32px 0;
}

.image-wrapper img {
    width: 100%;          /* Step 4: Scales down to fit container width */
    height: auto;         /* Step 4: Maintains pristine aspect ratio without stretching */
    display: block;
    border-radius: 8px;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.05);
}

.image-wrapper figcaption {
    font-size: 0.85rem;
    color: var(--text-muted);
    text-align: center;
    margin-top: 8px;
    font-style: italic;
}
Key Requirements Checklist
Fluid Typography (clamp()): Headings scale dynamically and smoothly between mobile and desktop sizes without sudden breakpoint jumps.

Resilient Images (max-width: 100%, height: auto): Prevents images from stretching or breaking out of their parent containers on narrow mobile viewports.

Optimal Line Lengths (max-width: 65ch): Constrains paragraph text width so readers don't experience eye fatigue on wide screens.

Would you like to proceed to Assignment 9.3 (Responsive Navigation / Hamburger Menu), or would you like to review any specific concepts from this assignment first?