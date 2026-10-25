# Contributing to FlowViz

Thank you for your interest in contributing! FlowViz is a community project, and we welcome all contributions.

## How to Contribute

### Reporting Bugs

Found a bug? Please open an [issue](https://github.com/yourname/FlowViz/issues) with:
- **Title**: Clear, specific description
- **Steps to reproduce**: Exact steps to trigger the bug
- **Expected behavior**: What should happen
- **Actual behavior**: What actually happens
- **Screenshots**: If relevant
- **Environment**: Browser, OS, device (desktop/mobile)

### Suggesting Features

Have an idea? Open an issue with the **enhancement** label:
- **Title**: Clear feature description
- **Motivation**: Why this feature would be useful
- **Implementation ideas**: How you might build it (optional)
- **Examples**: Related tools or effects you like

### Adding Visual Styles

This is the easiest way to contribute! Visual styles are self-contained functions.

#### Create a New Style

1. Open `FlowViz.html` in a text editor
2. Find the `Styles = {}` section (around line 800)
3. Add your style:

```javascript
Styles.myNewStyle = {
  name: 'My Style Name',
  
  enter() {
    // Called when the style loads
    // Initialize state, random seeds, etc.
    this.particles = [];
    this.angle = 0;
  },
  
  setup(w, h) {
    // Called on canvas resize
    // Optional: set up cached data
    this.width = w;
    this.height = h;
  },
  
  draw(ctx, w, h, dt, s) {
    // Called every frame
    // ctx: Canvas 2D context
    // w, h: Canvas width/height
    // dt: Delta time in seconds
    // s: Scale factor (2 on retina, 1 on standard)
    
    // Access audio data
    const bassLevel = F.bass;      // 0–1
    const midsLevel = F.mid;       // 0–1
    const treb = F.treb;           // 0–1
    const energySpike = F.beat;    // true on beat
    const spectrum = F.spec;       // 0–63 frequency bins
    
    // Access user parameters
    const amp = P.amplitude;
    const motion = P.motion;
    const trails = P.trails;
    const density = P.density;
    const complexity = P.complexity;
    
    // Get theme-aware colors
    const color1 = Mood.c(0, 70, 0.6);    // hue, sat, bright
    const color2 = Mood.c(120, 80, 0.8);
    
    // Draw
    ctx.fillStyle = color1;
    ctx.fillRect(0, 0, w, h);
    
    ctx.strokeStyle = color2;
    ctx.beginPath();
    ctx.arc(w/2, h/2, 100 * bassLevel, 0, Math.PI * 2);
    ctx.stroke();
  }
};
```

4. Add your style name to the `ORDER` array (line ~900):

```javascript
const ORDER = [
  'existing1', 'existing2',
  'myNewStyle',  // ← Add here
  // ...
];
```

5. Test:
   - Open `index.html` in your browser
   - Load an audio file
   - Look for your style in the grid
   - See if it animates correctly

#### Style Tips

**Respond to Audio**:
- Use `F.beat` for beat-synced effects
- Use `F.bass`, `F.mid`, `F.treb` for frequency-dependent behavior
- Use `F.spec[]` for detailed spectrum analysis

**Use Colors**:
- Always use `Mood.c(hue, saturation, brightness)` for colors
- This ensures dark/light theme compatibility
- Hue: 0–360° (red=0, green=120, blue=240)
- Saturation: 0–100
- Brightness: 0–1 (0 = black, 1 = white)

**Performance**:
- Avoid heavy computations per frame
- Pre-compute in `setup()` if possible
- Use low-res canvas: `s` is 0.5–1.0, don't ignore it
- Limit particle count; use `P.density` to scale

**Visual Variety**:
- Use randomness in `enter()` to vary the effect
- Different random seeds = different look each time
- Avoid hard-coded colors; use Mood system

**Examples to Learn From**:
Look at existing styles like:
- `Galaxy`: Orbital particles, attractors
- `Ribbon Fountain`: Curves and path rendering
- `Kaleidoscope`: Geometric patterns
- `Fractal Tree`: Recursive structures

### Improving Documentation

Found a typo or unclear section? Submit a pull request to:
- Update `README.md` with clarifications
- Expand `docs/USER_MANUAL.md` with tips
- Add `docs/DEVELOPER_GUIDE.md` with API details

### Code Quality

Before submitting a PR:

1. **Test thoroughly**:
   - Test in Chrome, Firefox, and Safari
   - Test on mobile (iPad, iPhone)
   - Test with file and microphone input
   - Test export functionality

2. **Keep it simple**:
   - FlowViz is intentionally a single HTML file
   - Avoid adding external dependencies
   - Write readable code with comments

3. **Maintain browser compatibility**:
   - Use ES2020 features (no experimental APIs)
   - Test on older browser versions if possible
   - Use `-webkit-` prefixes where needed

4. **Follow the code style**:
   - 2-space indentation
   - camelCase for variables
   - UPPERCASE for constants
   - Comments for non-obvious logic

## Pull Request Process

1. **Fork** the repository
2. **Create a branch**: `git checkout -b feature/my-feature`
3. **Make your changes**: Add styles, fix bugs, improve docs
4. **Test thoroughly**: Verify everything works
5. **Commit**: Clear, descriptive commit messages
6. **Push**: `git push origin feature/my-feature`
7. **Open a PR**: Describe what you changed and why

### PR Checklist

- [ ] Changes are tested (Chrome, Firefox, Safari, mobile)
- [ ] Code follows the style guide
- [ ] No new external dependencies added
- [ ] Documentation updated (if needed)
- [ ] Commit messages are clear and descriptive

## Development Tips

### Running Locally

```bash
git clone https://github.com/yourname/FlowViz.git
cd FlowViz
# Open index.html in your browser
```

No build step needed! FlowViz is a single HTML file.

### Debugging

Enable developer tools (`F12` in most browsers):

**Console**: Check for errors
```javascript
// View current style
console.log(Flow.current);

// Check audio analysis
console.log(F);

// View user parameters
console.log(P);
```

**Performance**: Use the DevTools Performance tab to profile rendering.

**Network**: Ensure no resources are failing to load.

### Making Style Variations

Each style can have multiple variations. Techniques:

**1. Randomize on Load**:
```javascript
enter() {
  this.variant = Math.random();
  this.seed = rand(0, 1000);
}
```

**2. Use Different Colors**:
```javascript
const hue = Mood.hue + rand(-30, 30);  // Shift within range
ctx.fillStyle = Mood.c(hue, 70, 0.6);
```

**3. Change Complexity**:
```javascript
const complexity = P.complexity * rand(0.5, 1.5);
```

## Recognition

Contributors are recognized:
- Mention in the README
- Credit in GitHub contributors list
- Shout-out in release notes

## Questions?

- Check the [README](README.md)
- Read the [USER_MANUAL](docs/USER_MANUAL.md)
- Open a [discussion](https://github.com/yourname/FlowViz/discussions)

---

**Thank you for making FlowViz better!** 🎵✨
