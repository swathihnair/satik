<script>
  import { onMount } from 'svelte';
  import { ChevronLeft, ChevronRight } from 'lucide-svelte';
 
  let currentSlide = 0;
  let autoPlay;
 
  const slides = [
    {
      id: 1,
      title: "Spring Collection 2024",
      subtitle: "Elegance Redefined",
      description: "Discover our latest spring collection featuring elegant  accessories and timeless pieces.",
      image: "/image/i1.jpg",
      cta: "Shop Now"
    },
    {
      id: 2,
      title: "Summer Essentials",
      subtitle: "Bright & Beautiful",
      description: "Light, airy and vibrant colors perfect for the summer season.",
      image: "/image/i4.jpg",
      cta: "Explore"
    },
    {
      id: 3,
      title: "Premium Accessories",
      subtitle: "Complete Your Look",
      description: "Handpicked accessories to complement your style and elevate your wardrobe.",
      image: "/image/i5.jpg",
      cta: "View Collection"
    }
  ];
 
  onMount(() => {
    startAutoPlay();
    return () => clearInterval(autoPlay);
  });
 
  function startAutoPlay() {
    autoPlay = setInterval(() => {
      currentSlide = (currentSlide + 1) % slides.length;
    }, 5000);
  }
 
  function goToSlide(index) {
    currentSlide = index;
    clearInterval(autoPlay);
    startAutoPlay();
  }
 
  function prevSlide() {
    currentSlide = currentSlide === 0 ? slides.length - 1 : currentSlide - 1;
    clearInterval(autoPlay);
    startAutoPlay();
  }
 
  function nextSlide() {
    currentSlide = (currentSlide + 1) % slides.length;
    clearInterval(autoPlay);
    startAutoPlay();
  }
</script>

<section class="relative h-screen overflow-hidden">
  {#each slides as slide, index}
    <div class="absolute inset-0 transition-transform duration-700 ease-in-out {index === currentSlide ? 'translate-x-0' : index < currentSlide ? '-translate-x-full' : 'translate-x-full'}">
      <div class="relative h-full">
        <img src={slide.image} alt={slide.title} class="w-full h-full object-cover" />
        <div class="absolute inset-0 bg-black bg-opacity-30"></div>
        <div class="absolute inset-0 flex items-center justify-center">
          <div class="text-center text-white px-4 max-w-4xl mx-auto">
            <h2 class="text-lg md:text-xl font-medium mb-2 opacity-90 animate-fade-in">{slide.subtitle}</h2>
            <h1 class="text-4xl md:text-6xl lg:text-7xl font-serif font-bold mb-6 animate-slide-up">{slide.title}</h1>
            <p class="text-lg md:text-xl mb-8 max-w-2xl mx-auto opacity-95 animate-fade-in">{slide.description}</p>
            <button class="bg-primary-600 hover:bg-primary-700 text-white px-8 py-3 rounded-full font-semibold transition-all duration-300 transform hover:scale-105 animate-slide-up">
              {slide.cta}
            </button>
          </div>
        </div>
      </div>
    </div>
  {/each}
 
  <!-- Navigation Buttons -->
  <button on:click={prevSlide} class="absolute left-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/30 backdrop-blur-sm text-white p-3 rounded-full transition-all duration-200">
    <ChevronLeft size={24} />
  </button>
  <button on:click={nextSlide} class="absolute right-4 top-1/2 transform -translate-y-1/2 bg-white/20 hover:bg-white/30 backdrop-blur-sm text-white p-3 rounded-full transition-all duration-200">
    <ChevronRight size={24} />
  </button>
 
  <!-- Slide Indicators -->
  <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 flex space-x-3">
    {#each slides as _, index}
      <button
        on:click={() => goToSlide(index)}
        class="w-3 h-3 rounded-full transition-all duration-200 {index === currentSlide ? 'bg-white' : 'bg-white/50 hover:bg-white/75'}"
      ></button>
    {/each}
  </div>
</section>