# Super Gallery

A versatile image gallery component for Budibase applications with grid, carousel, and marquee display modes for showcasing image collections.

## 🚀 Features

### Display Modes

- **Grid Mode**: Responsive grid layout with configurable columns and image ratios
- **Carousel Mode**: Interactive sliding carousel with navigation controls
- **Marquee Mode**: Continuous scrolling marquee display

### Image Management

- **Array Input**: Accepts arrays of image data from Budibase data sources
- **Image Ratios**: Landscape, square, and portrait aspect ratios
- **Responsive Design**: Adapts to different screen sizes and container widths

### Interactive Features

- **Click Actions**: None, view (lightbox), select, or custom event handling
- **Lightbox Viewing**: Full-screen image viewing with navigation
- **Touch Support**: Mobile-friendly touch gestures for carousel navigation

### Carousel Controls

- **Navigation Arrows**: Previous/next slide controls
- **Dot Indicators**: Visual slide position indicators
- **Autoplay**: Automatic slide progression with configurable timing
- **Infinite Loop**: Seamless continuous scrolling
- **Items Configuration**: Control visible items and scroll behavior

### User Experience

- **Builder Integration**: Visual placeholder in design mode
- **Event Handling**: Custom click events for advanced interactions
- **Performance Optimized**: Efficient rendering for large image collections
- **Accessibility**: Keyboard navigation and screen reader support

## 📝 Usage Instructions

### Basic Setup

1. Add the Super Gallery component to your screen
2. Bind the `value` property to an array field containing image data
3. Choose your preferred display mode (grid, carousel, or marquee)
4. Configure image ratio and grid columns for grid mode
5. Set up carousel settings for carousel/marquee modes

### Display Mode Configuration

#### Grid Mode

- Set `Mode` to "Grid"
- Choose `Image Ratio` (landscape, square, portrait)
- Configure `Grid Columns` (1-12 columns)
- Images will automatically arrange in responsive grid

#### Carousel Mode

- Set `Mode` to "Carousel"
- Configure `Items to Show` (1-6 visible items)
- Set `Items to Scroll` (items to advance per navigation)
- Enable/disable autoplay, dots, and infinite loop

#### Marquee Mode

- Set `Mode` to "Marquee"
- Same carousel settings apply with continuous scrolling behavior

### Advanced Configuration

- **Click Actions**: Choose what happens when users click images
  - `None`: No action on click
  - `View`: Opens image in lightbox
  - `Select`: Triggers selection event
  - `Custom`: Fires custom event for advanced handling

### Common Use Cases

- **Photo Galleries**: Showcase product images or portfolios
- **Image Carousels**: Featured content sliders on dashboards
- **Media Browsers**: Browse through collections of images
- **Content Showcases**: Display user-generated content
- **Marketing Banners**: Rotating promotional images

## 🔧 Configuration Options

| Setting      | Type   | Description                              | Default   |
| ------------ | ------ | ---------------------------------------- | --------- |
| Value        | Array  | Array of image data                      | -         |
| Mode         | Select | Display mode (grid/carousel/marquee)     | grid      |
| Image Ratio  | Select | Aspect ratio (landscape/square/portrait) | landscape |
| Grid Columns | Number | Number of columns in grid (1-12)         | 4         |
| On Click     | Select | Click behavior (none/view/select/custom) | view      |

### Carousel Settings (Carousel/Marquee Mode)

| Setting         | Type    | Description                    | Default |
| --------------- | ------- | ------------------------------ | ------- |
| Items to Show   | Number  | Visible items in carousel      | 3       |
| Items to Scroll | Number  | Items to advance per scroll    | 1       |
| Autoplay        | Boolean | Enable automatic progression   | false   |
| Speed (ms)      | Number  | Autoplay interval (1000-10000) | 3000    |
| Show Dots       | Boolean | Display navigation dots        | true    |
| Infinite Loop   | Boolean | Seamless continuous scrolling  | true    |

## 📋 Events

### On Click (Custom Action)

Triggered when `On Click` is set to "Custom" and user clicks an image.

**Context:**

- `item`: The clicked image data
- `index`: Index of clicked item in array
- `value`: Complete array of images

```javascript
// Example: Handle custom click action
function handleGalleryClick(context) {
  const { item, index } = context;
  // Custom logic here
  console.log(`Clicked image ${index}:`, item);
}
```

## 🎨 Styling

The component supports Budibase's styling system with:

- **Size**: Control overall component dimensions
- **Border**: Customize border appearance
- **Background**: Set background colors and images
- **Grid Spacing**: Automatic responsive spacing in grid mode
- **Carousel Theming**: Consistent styling with carousel controls

## 🔍 Best Practices

- Choose appropriate image ratios based on your content type
- Consider mobile users when setting grid columns and carousel items
- Use carousel mode for featured content, grid for browsing
- Enable autoplay sparingly to avoid user distraction
- Test with various image counts to ensure performance
- Provide meaningful alt text for accessibility
- Consider image loading performance with large collections
