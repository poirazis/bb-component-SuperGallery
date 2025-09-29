<script>
  import { getContext } from "svelte";
  import {
    CellAttachmentExpanded,
    CellAttachmentSlider,
  } from "@poirazis/supercomponents-shared";

  const { styleable, Provider, builderStore } = getContext("sdk");
  const component = getContext("component");

  export let value;
  export let mode = "grid"; // grid | carousel
  export let imageRatio = "landscape"; // landscape | square
  export let gridColumns = 4; // 1-6
  export let onClickAction = "view";
  export let onItemClick; // (item) => {}

  // Carousel settings
  export let carouselItemsToShow = 3;
  export let carouselItemsToScroll = 1;
  export let carouselAutoplay = false;
  export let carouselAutoplaySpeed = 3000;
  export let carouselDots = true;
  export let carouselArrows = true;
  export let carouselInfinite = true;

  $: cellOptions = {
    readonly: true,
    disabled: $builderStore.inBuilder,
    controlType: mode,
    height: $component.styles.normal.height || "15rem",
    isGallery: true,
    imageRatio,
    gridColumns,
    onClickAction,
    onItemClick,
    // Add carousel settings when in carousel mode
    ...((mode === "carousel" || mode == "marquee") && {
      carouselMode: mode,
      carouselItemsToShow,
      carouselItemsToScroll,
      carouselAutoplay,
      carouselAutoplaySpeed,
      carouselDots,
      carouselArrows,
      carouselInfinite,
    }),
  };

  $: safeValue = Array.isArray(value) ? value : safeParse(value);
  $: height = $component.styles.normal.height || "15rem";
  $: inBuilder = $builderStore.inBuilder;
  $: $component.styles.normal = {
    height: "20rem",
    ...$component.styles.normal,
  };

  const safeParse = (val) => {
    try {
      return JSON.parse(val);
    } catch (e) {
      return [];
    }
  };
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
<div class="super-gallery" use:styleable={$component.styles}>
  <Provider data={{ value }} />
  {#if safeValue.length}
    {#if mode === "carousel" || mode === "marquee"}
      <CellAttachmentSlider value={safeValue} {cellOptions} {height} />
    {:else if mode === "grid"}
      <CellAttachmentExpanded value={safeValue} {cellOptions} {height}>
        <slot />
      </CellAttachmentExpanded>
    {/if}
  {:else if inBuilder}
    <div class="empty-state">No Images to show</div>
  {/if}
</div>

<style>
  .super-gallery {
    display: flex;
    align-items: stretch;
  }

  .empty-state {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    border: 1px dashed var(--spectrum-global-color-blue-400);
    border-radius: 0.25rem;
    font-style: italic;
    padding: 1rem;
  }
</style>
