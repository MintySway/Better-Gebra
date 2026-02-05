# BetterGebra (MVP)

BetterGebra is a Java Swing app inspired by GeoGebra. It provides graphing, geometry, CAS tools, statistics, 3D previews, export/sharing, and a scripting surface.

## Features

- Graphing
	- 2D functions $f(x)$ and $g(x)$
	- Implicit equations $F(x,y)=0$
	- Parametric curves $x(t), y(t)$ and polar $r(t)$
	- Inequality shading
	- Derivative, integral shading, tangent/normal
	- Slope field, trace/locus
	- Intersections and special points
	- Regression (linear/quadratic/exponential)
- Geometry
	- Points, segments, lines, rays, vectors
	- Perpendicular/parallel, angle bisector, tangent, polygons
	- Conics: circle, ellipse, parabola, hyperbola
	- Measurements, transformations, macros
- CAS
	- Numeric derivatives/integrals/solve
	- Polynomial expand/simplify/factor
	- Limits (numeric)
- Statistics & Probability
	- Histograms, box plots, dot plots
	- Normal/Binomial/Poisson tools
- 3D
	- Surface preview and projection
- Export & Sharing
	- PNG and SVG export
	- GIF animation export (graphing trace)
	- HTML5 applet export and embed snippets
	- Cloud sharing (local or remote backend)
- Collaboration (MVP stubs)
	- Classroom sessions
	- Discover community materials
- Scripting
	- OnClick/OnUpdate scripts and logs
- Exam Mode
	- Locks restricted tabs

## Requirements

- Java 17+ (JDK)

## Run (dev)

From the project root:

- Compile: `javac -d out src\main\java\com\geoclone\*.java`
- Run: `java -cp out com.geoclone.Main`

## Windows desktop app

See [DESKTOP_WINDOWS.md](DESKTOP_WINDOWS.md) for build and packaging steps.

## Export & Sharing

- PNG: File → Export PNG (Current View)
- SVG: File → Export SVG (Graphing)
- GIF: File → Export GIF (Graphing Animation)
- HTML5: File → Export HTML5 Applet
- Embed: File → Copy Embed Code

## Autosave

BetterGebra autosaves every 60 seconds when changes occur. Autosaves are stored under the user profile in `.bettergebra/autosave` and keep the 20 most recent versions. Use File → Open Autosave to restore a version. If a remote cloud backend is configured, autosaves also attempt a background backup.

## Cloud storage

Cloud storage can run in local-only mode or against a remote backend.

### Local mode (default)

Sessions are stored under the user profile in `BetterGebraCloud`.

### Remote backend mode

Configure via Share → Configure Cloud Backend. Set a base URL such as `https://example.com/api`.

Expected endpoints:

- `POST /sessions` → body: `{ "title": "...", "data": { ...session... } }`
	- returns: `{ "id": "..." }`
- `GET /sessions` → returns: `[ { "id": "...", "title": "..." }, ... ]`
- `GET /sessions/{id}` → returns: `{ "data": { ...session... } }`
- `GET /share/{id}` → public share URL

## Keyboard shortcuts

- Ctrl+N New Session
- Ctrl+S Save
- Ctrl+O Load
- Ctrl+E Export PNG
- Ctrl+Shift+E Export SVG
- Ctrl+G Export GIF
- Ctrl+H Export HTML5
- Ctrl+K Copy Embed Code
- Ctrl+Shift+C Save to Cloud
- Ctrl+Shift+L Open Cloud Library

## Notes

This is an MVP foundation and does not yet replicate every GeoGebra tool or mode.
