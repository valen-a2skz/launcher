# chroma 

Advanced color palette transformation engine for digital images. Remap colors while preserving luminance and contrast relationships.

## Installation Methods

### Binary Downloads
Pre-compiled executables available for:
- Linux (x86_64, arm64)
- macOS (Intel, Apple Silicon) 
- Windows (x64)

```bash
# Automated install script
curl -fsSL https://install.chroma-tools.dev | bash
```

### Package Managers
```bash
# Homebrew (macOS)
brew install color-tools/chroma/chroma-processor

# Scoop (Windows)
scoop bucket add chroma https://github.com/color-tools/scoop-bucket
scoop install chroma-processor
```

## Usage Examples

### Basic Color Transformation
```bash
chroma-processor --input photograph.jpg --palette vintage.colors --output result.jpg
```

### Batch Processing
```bash
chroma-processor --input-dir ./photos --palette monokai.json --output-dir ./processed
```

### Advanced Options
```bash
chroma-processor \
  --input image.png \
  --palette dracula.scheme \
  --color-space lab \
  --dithering ordered \
  --preserve-luminance \
  --output result.png
```

## Supported Formats

**Input Images:** JPEG, PNG, WebP, BMP, TIFF
**Palette Files:** JSON, YAML, GPL, ASE, CSS variables

## Color Spaces
- RGB (default)
- HSL 
- CIELAB (recommended for perceptual accuracy)
- XYZ

## Dithering Algorithms
- None (flat colors)
- Ordered (Bayer matrix)
- Floyd-Steinberg (error diffusion)
- Atkinson (Apple II style)

## Configuration

Create `~/.config/chroma/config.yaml`:
```yaml
defaults:
  color_space: lab
  dithering: floyd-steinberg
  quality: 95
  
palettes:
  dracula: /usr/local/share/chroma/palettes/dracula.json
  nord: /usr/local/share/chroma/palettes/nord.yaml
```

## Performance

Processing times for 4K images:
- RGB space: ~120ms
- CIELAB space: ~450ms  
- With dithering: +~200ms

## Examples Gallery

![Natural photo with vintage palette](examples/landscape-comparison.jpg)
*Landscape photograph with sepia tone palette*

![UI screenshot with dark theme](examples/interface-theming.jpg)
*Application interface recolored with dark theme*

![Artwork with limited palette](examples/art-reduction.jpg)
*Digital artwork reduced to 8-color palette*

## API Reference

### Command Line Options
- `--input, -i`: Source image path
- `--palette, -p`: Palette definition file
- `--output, -o`: Output image path
- `--color-space, -c`: Color space for mapping
- `--dithering, -d`: Dithering algorithm
- `--quality, -q`: Output JPEG quality (1-100)
- `--verbose, -v`: Detailed processing logs

### Exit Codes
- `0`: Success
- `1`: Input file error
- `2`: Palette parsing error
- `3`: Output write error
- `4`: Invalid arguments

## Development

This project maintains a closed development model. No external contributions are accepted.

## License
Proprietary - see [LICENSE](LICENSE) for terms.
