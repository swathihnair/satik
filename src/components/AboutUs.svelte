<script>
  import { onMount } from 'svelte';
  
  let aboutRef;
  let isVisible = false;
  
  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          isVisible = true;
        }
      });
    }, { threshold: 0.3 });
    
    if (aboutRef) {
      observer.observe(aboutRef);
    }
    
    return () => observer.disconnect();
  });
</script>

<section id="about" bind:this={aboutRef} class="py-20 bg-gradient-to-b from-white to-primary-50">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="grid lg:grid-cols-2 gap-12 lg:gap-20 items-center">
      <div class="{isVisible ? 'animate-slide-up' : 'opacity-0'}">
        <h2 class="text-4xl lg:text-5xl font-serif font-bold text-gray-900 mb-6">
          About <span class="bg-gradient-to-r from-primary-600 to-rose-500 bg-clip-text text-transparent">Zion Collection</span>
        </h2>
        <p class="text-lg text-gray-600 mb-6 leading-relaxed">
           ZION Collections is not just a store — it’s an experience crafted especially for women who love to express themselves through the little details that complete a look. As a dedicated ladies’ accessories boutique, ZION celebrates the art of elegance, offering a thoughtfully curated selection of stylish, high-quality accessories that blend tradition with contemporary flair. Our collection includes everything from delicately crafted earrings, bracelets, and statement necklaces to sophisticated handbags, trendy clutches, vibrant scarves, stylish sunglasses, and daily-use essentials like scrunchies, pouches, and hair accessories. Each product is handpicked or designed with care, keeping in mind the modern woman’s desire for individuality, beauty, and comfort
        </p>
        
        <div class="flex flex-col sm:flex-row gap-4">
          <div class="flex items-center space-x-3">
            <div class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center">
              <span class="text-primary-600 font-bold text-xl">5+</span>
            </div>
            <div>
              <p class="font-semibold text-gray-900">Years of Excellence</p>
              <p class="text-sm text-gray-600">Serving fashionable women</p>
            </div>
          </div>
          <div class="flex items-center space-x-3">
            <div class="w-12 h-12 bg-rose-100 rounded-full flex items-center justify-center">
              <span class="text-rose-600 font-bold text-xl">10k+</span>
            </div>
            <div>
              <p class="font-semibold text-gray-900">Happy Customers</p>
              <p class="text-sm text-gray-600">Worldwide satisfaction</p>
            </div>
          </div>
        </div>
      </div>
      
      <div class="{isVisible ? 'animate-fade-in' : 'opacity-0'} relative">
        <div class="relative">
          <img 
            src="https://images.pexels.com/photos/1036622/pexels-photo-1036622.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" 
            alt="Fashion Designer at Work" 
            class="rounded-2xl shadow-2xl w-full h-96 object-cover"
          />
          <div class="absolute -bottom-6 -right-6 w-32 h-32 bg-gradient-to-br from-primary-500 to-rose-500 rounded-2xl opacity-20"></div>
          <div class="absolute -top-6 -left-6 w-24 h-24 bg-gradient-to-br from-rose-400 to-primary-400 rounded-full opacity-30"></div>
        </div>
        <div class="absolute top-4 right-4 bg-white/90 backdrop-blur-sm rounded-lg p-4 shadow-lg">
          <p class="text-sm font-semibold text-gray-800">Premium Quality</p>
          <p class="text-xs text-gray-600">Handpicked Materials</p>
        </div>
      </div>
    </div>
  </div>
</section>