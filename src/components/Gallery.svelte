<script>
  import { onMount } from 'svelte';
  import { ChevronLeft, ChevronRight, X } from 'lucide-svelte';
  
  let galleryRef;
  let isVisible = false;
  let selectedImage = null;
  let lightboxIndex = 0;
  
  const galleryImages = [
    {
      id: 1,
      src: "/image/i1.jpg",
      alt: "Elegant Evening Dress",
      category: "Evening Wear"
    },
    {
      id: 2,
      src: "/image/i2.jpg",
      alt: "Casual Chic Outfit",
      category: "Casual"
    },
    {
      id: 3,
      src: "/image/i3.jpg",
      alt: "Professional Attire",
      category: "Professional"
    },
    {
      id: 4,
      src: "/image/i4.jpg",
      alt: "Summer Collection",
      category: "Summer"
    },
    {
      id: 5,
      src: "/image/i5.jpg",
      alt: "Accessories",
      category: "Accessories"
    },
    {
      id: 6,
      src: "/image/i6.jpg",
      alt: "Designer Collection",
      category: "Designer"
    },
    
  ];
  
  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          isVisible = true;
        }
      });
    }, { threshold: 0.3 });
    
    if (galleryRef) {
      observer.observe(galleryRef);
    }
    
    return () => observer.disconnect();
  });
  
  function openLightbox(image, index) {
    selectedImage = image;
    lightboxIndex = index;
    document.body.style.overflow = 'hidden';
  }
  
  function closeLightbox() {
    selectedImage = null;
    document.body.style.overflow = 'auto';
  }
  
  function prevImage() {
    lightboxIndex = lightboxIndex === 0 ? galleryImages.length - 1 : lightboxIndex - 1;
    selectedImage = galleryImages[lightboxIndex];
  }
  
  function nextImage() {
    lightboxIndex = (lightboxIndex + 1) % galleryImages.length;
    selectedImage = galleryImages[lightboxIndex];
  }
</script>

<section id="gallery" bind:this={galleryRef} class="py-20 bg-gradient-to-b from-primary-50 to-white">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="text-center mb-16 {isVisible ? 'animate-slide-up' : 'opacity-0'}">
      <h2 class="text-4xl lg:text-5xl font-serif font-bold text-gray-900 mb-6">
        Our <span class="bg-gradient-to-r from-primary-600 to-rose-500 bg-clip-text text-transparent">Gallery</span>
      </h2>
      <p class="text-lg text-gray-600 max-w-3xl mx-auto leading-relaxed">
        Explore our stunning collection through carefully curated images that showcase the beauty, 
        elegance, and versatility of our fashion pieces.
      </p>
    </div>
    
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
      {#each galleryImages as image, index}
        <div class="{isVisible ? 'animate-fade-in' : 'opacity-0'} relative group cursor-pointer overflow-hidden rounded-xl {index % 7 === 0 || index % 7 === 3 ? 'md:col-span-2 md:row-span-2' : ''}"
             style="animation-delay: {index * 0.1}s"
             on:click={() => openLightbox(image, index)}>
          <img 
            src={image.src} 
            alt={image.alt}
            class="w-full h-64 {index % 7 === 0 || index % 7 === 3 ? 'md:h-full' : ''} object-cover transition-transform duration-700 group-hover:scale-110"
          />
          <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300">
            <div class="absolute bottom-4 left-4 text-white">
              <p class="font-semibold">{image.alt}</p>
              <p class="text-sm opacity-90">{image.category}</p>
            </div>
          </div>
          <div class="absolute inset-0 ring-1 ring-inset ring-black/10 rounded-xl"></div>
        </div>
      {/each}
    </div>
  </div>
</section>

<!-- Lightbox -->
{#if selectedImage}
  <div class="fixed inset-0 z-50 bg-black bg-opacity-90 flex items-center justify-center p-4"
       on:click={closeLightbox}>
    <div class="relative max-w-4xl max-h-full" on:click|stopPropagation>
      <img 
        src={selectedImage.src} 
        alt={selectedImage.alt}
        class="max-w-full max-h-full object-contain rounded-lg"
      />
      <button 
        on:click={closeLightbox}
        class="absolute top-4 right-4 text-white bg-black bg-opacity-50 rounded-full p-2 hover:bg-opacity-75 transition-colors"
      >
        <X size={24} />
      </button>
      <button 
        on:click={prevImage}
        class="absolute left-4 top-1/2 transform -translate-y-1/2 text-white bg-black bg-opacity-50 rounded-full p-2 hover:bg-opacity-75 transition-colors"
      >
        <ChevronLeft size={24} />
      </button>
      <button 
        on:click={nextImage}
        class="absolute right-4 top-1/2 transform -translate-y-1/2 text-white bg-black bg-opacity-50 rounded-full p-2 hover:bg-opacity-75 transition-colors"
      >
        <ChevronRight size={24} />
      </button>
      <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 text-white text-center">
        <p class="font-semibold">{selectedImage.alt}</p>
        <p class="text-sm opacity-75">{selectedImage.category}</p>
      </div>
    </div>
  </div>
{/if}