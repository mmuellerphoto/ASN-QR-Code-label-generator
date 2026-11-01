# QR Code Label Generator for Paperless-ngx ASN

A web-based tool for generating printable QR code labels for Paperless-ngx ASN (Archival Serial Numbers). Based on the original implementation by Tobias Maier, this tool has been enhanced and improved to provide more precise control over layout and print quality. While originally designed for ASN labels, it can now be used to create QR code labels of various sizes for any purpose, supporting multiple page formats and orientations.

## Features

- Generation of QR codes for ASN numbers with customizable prefixes
- Precise control over page margins and label spacing
- Target/Actual value comparison for exact print adjustments
- Multiple page format support (A4, A5, US Letter, Legal)
- Portrait and landscape orientation
- Configurable text formatting (font family, size, weight)
- Visual page preview with margin indicators
- Save and load configurations
- Print-optimized output
- Responsive design
- No installation required - runs in browser
- QR codes are generated locally in the browser (no external QR service)
- Flexible label sizing for various applications

## Technical Details

- Default label size: 25.35mm × 10mm (customizable)
- QR code size: 9mm × 9mm
- Supported page formats:
  - A4 (210mm × 297mm)
  - A5 (148mm × 210mm)
  - US Letter (215.9mm × 279.4mm)
  - US Legal (215.9mm × 355.6mm)
- Default labels per page: 7 × 27 = 189 labels (adjustable based on format)
- Default page margins:
  - Top: 13.14mm
  - Bottom: 13.7mm
  - Left: 8.4mm
  - Right: 8.5mm

## Understanding Target and Actual Values and Scaling

The generator uses a sophisticated target and actual value system to ensure precise label printing:

### Target Values
- These are your desired measurements, which can come from:
  - Manufacturer specifications for your label sheets
  - Measurements from existing label sheets
  - Your own requirements for custom labels
  - Standard label dimensions
- Examples:
  - If your label sheet specifies 25.4mm × 10mm labels, use these as target values
  - If you measured an existing label sheet with 25.35mm × 10mm labels, use these measurements
  - For custom labels, use your required dimensions

### Actual Values
- These are the real measurements from your test prints
- Process to determine:
  1. Start with your target values as initial actual values
  2. Generate and print a test page
  3. Measure the actual printed dimensions carefully
  4. Enter these measured values as your new actual values
  5. The generator will automatically calculate scaling factors to compensate for differences

For example:
- Target value: 25.4mm × 10mm
- Initial actual value: Same as target (25.4mm × 10mm)
- After test print measurement: 25.8mm × 10.2mm
- Enter 25.8mm × 10.2mm as actual values
- System calculates scaling: 25.4/25.8 = 0.984 (width), 10/10.2 = 0.980 (height)

### Automatic Scaling
The system automatically calculates scaling factors to compensate for printer variations:
- Horizontal scaling: Adjusts for width differences
- Vertical scaling: Adjusts for height differences
- These calculations ensure that your labels will print at the correct size

## Setup and Usage

### Initial Configuration

1. Basic Setup
   - Open `index.html` in your web browser
   - Select page format (A4, A5, Letter, Legal)
   - Choose orientation (portrait/landscape)
   - Configure QR code basics:
     * Start number and prefix (e.g., "ASN")
     * Number of leading zeros
     * Display options (show/hide prefix, borders)

2. Label Dimensions
   - Enter target values from:
     * Manufacturer specifications
     * Measured existing labels
     * Custom requirements
   - Configure text formatting:
     * Font family and size
     * Font weight
     * QR code spacing
   - Set initial spacing between labels
   - Review the preview layout

### Calibration Process

1. First Print Adjustment
   - Start with target values as initial actual values
   - Print a test page
   - Measure all dimensions carefully:
     * Label width and height
     * Horizontal and vertical spacing
     * Page margins on all sides
   - Enter measured values as actual values
   - System automatically calculates scaling factors

2. Verification
   - Print another test page with scaling applied
   - Verify all measurements are now correct
   - Make minor adjustments if needed
   - Test with a full page of labels

3. Save Your Settings
   - Once everything is perfect, save your configuration
   - Document printer settings used
   - Keep measurements for future reference
   - Consider creating a printer preset

### Regular Usage

1. Daily Operation
   - Load your saved configuration if needed
   - Enter starting ASN number
   - Verify preview looks correct
   - Print labels as needed

2. Maintenance
   - Periodically verify measurements
   - Update actual values if printer behavior changes
   - Keep backup of working configurations

### Tips for Success
- Always use 100% scaling in printer settings
- Select appropriate media type (Labels/Thick Paper)
- Perform test prints on plain paper first
- Verify QR code readability
- Document successful printer settings

### Tips for Saving Toner and Label Sheets

When fine-tuning your print layout, you can save toner and label sheets:
- Use the Print Testing function
- Initially print only the label outlines
- Enable only the corner labels for optimal alignment control
- Use Toner Save Mode during the testing phase

### Toner Save Mode
The Toner Save Mode is a feature that helps reduce toner consumption during test prints:
- When enabled, QR codes and text are printed with reduced density
- The feature is accessible via the checkbox in the Print Testing section
- Recommended for initial layout and alignment testing
- Should be disabled for final production prints to ensure optimal QR code readability

## Printing Setup and Configuration

### Critical Print Settings
- Ensure printer scaling is set to 100% (no automatic scaling)
- Set appropriate media type:
  - "Labels" if available
  - "Thick Paper" or "Card Stock" as alternative
  - Avoid "Plain Paper" setting
- Disable any automatic adjustments or "Fit to Page" options
- For duplex printers: Select single-sided printing

### Browser Print Settings
- Use the browser's print dialog (⌘P or Ctrl+P)
- Set margins to "None" or "Minimum"
- Ensure "Scale" is set to 100%
- Disable headers and footers
- Select "Color" even for black/white printing to ensure proper QR code contrast

### Tested Configurations

#### Example Setup 1 (Verified Working)
- Operating System: macOS 15.3.2 (24D81)
- Browser: Safari
- Printer: Brother MFC-L2740DW series
- Labels: Avery L4731REV-25
- Print Settings:
  - Media Type: Labels
  - Resolution: HQ 1200dpi
  - Scaling: 100%
  - Toner Save Mode: Off

#### Additional Tips
- Perform a test print on plain paper first
- Hold test print against label sheet to verify alignment
- Save working printer settings for future use
- Consider creating a dedicated printer preset

## Dependencies

- [Alpine.js](https://alpinejs.dev/) - For reactive functionality
- [Tailwind CSS](https://tailwindcss.com/) - For styling
- [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) by Kazuhiko Arase (MIT, bundled as `lib/qrcode.js`) - For local QR code generation. QR codes are created in the browser as SVG, so no ASN numbers are sent to an external service.

## License

MIT License - See LICENSE file for details

## Author

Enhanced version by Murat Güven
GitHub Repository: [muguu](https://github.com/muguu/ASN-QR-Code-label-generator)

Based on the original implementation by Tobias Maier
