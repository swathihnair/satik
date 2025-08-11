<script>
  import { onMount } from 'svelte';
  import { Heart, Award, Users, Sparkles } from 'lucide-svelte';
  
  let storiesRef;
  let isVisible = false;
  
  const stories = [
    {
      icon: Heart,
      title: "Passion for Fashion",
      description: "Every piece in our collection is chosen with love and attention to detail, ensuring that you receive only the finest quality garments.",
      color: "text-rose-500"
    },
    {
      icon: Award,
      title: "Excellence in Quality",
      description: "We partner with renowned designers and manufacturers to bring you clothing that stands the test of time while staying ahead of trends.",
      color: "text-primary-500"
    },
    {
      icon: Users,
      title: "Community First",
      description: "Our customers are at the heart of everything we do. We listen, we care, and we continuously evolve to meet your fashion needs.",
      color: "text-pink-500"
    },
    {
      icon: Sparkles,
      title: "Sustainable Beauty",
      description: "We're committed to ethical fashion practices, supporting sustainable production methods and fair trade partnerships.",
      color: "text-purple-500"
    }
  ];
  
  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          isVisible = true;
        }
      });
    }, { threshold: 0.3 });
    
    if (storiesRef) {
      observer.observe(storiesRef);
    }
    
    return () => observer.disconnect();
  });
</script>

<section id="stories" bind:this={storiesRef} class="py-20 bg-white">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="text-center mb-16 {isVisible ? 'animate-slide-up' : 'opacity-0'}">
      <h2 class="text-4xl lg:text-5xl font-serif font-bold text-gray-900 mb-6">
        Our <span class="bg-gradient-to-r from-primary-600 to-rose-500 bg-clip-text text-transparent">Stories</span>
      </h2>
      <p class="text-lg text-gray-600 max-w-3xl mx-auto leading-relaxed">
        Behind every collection lies a story of passion, dedication, and the relentless pursuit of beauty. 
        Discover what makes Zion Collection more than just a fashion brand.
      </p>
    </div>
    
    <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
      {#each stories as story, index}
        <div class="{isVisible ? 'animate-fade-in' : 'opacity-0'} bg-gradient-to-br from-white to-gray-50 p-8 rounded-2xl shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-2 border border-gray-100"
             style="animation-delay: {index * 0.1}s">
          <div class="w-16 h-16 {story.color} bg-opacity-10 rounded-2xl flex items-center justify-center mb-6">
            <svelte:component this={story.icon} size={32} class="{story.color}" />
          </div>
          <h3 class="text-xl font-bold text-gray-900 mb-4">{story.title}</h3>
          <p class="text-gray-600 leading-relaxed">{story.description}</p>
        </div>
      {/each}
    </div>
    
    <!-- Featured Story -->
    <div class="mt-20 {isVisible ? 'animate-slide-up' : 'opacity-0'}">
      <div class="bg-gradient-to-r from-primary-600 to-rose-500 rounded-3xl p-1">
        <div class="bg-white rounded-3xl p-8 lg:p-12">
          <div class="grid lg:grid-cols-2 gap-12 items-center">
            <div>
              <h3 class="text-3xl lg:text-4xl font-serif font-bold text-gray-900 mb-6">
                The Journey Continues
              </h3>
              <p class="text-lg text-gray-600 mb-6 leading-relaxed">
                From a small boutique dream to a beloved fashion destination, our journey has been filled with 
                memorable moments, loyal customers, and the constant drive to redefine elegance.
              </p>
              <p class="text-lg text-gray-600 mb-8 leading-relaxed">
                As we look to the future, we remain committed to our core values while embracing innovation 
                and expanding our reach to serve fashion-forward women everywhere.
              </p>
              <button class="bg-gradient-to-r from-primary-600 to-rose-500 text-white px-8 py-3 rounded-full font-semibold hover:shadow-lg transition-all duration-300 transform hover:scale-105">
                Join Our Journey
              </button>
            </div>
            <div class="relative">
              <img 
                src="https://images.pexels.com/photos/3965548/pexels-photo-3965548.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1" 
                alt="Fashion Journey" 
                class="rounded-2xl shadow-2xl w-full h-80 object-cover"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-primary-600/20 to-transparent rounded-2xl"></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>