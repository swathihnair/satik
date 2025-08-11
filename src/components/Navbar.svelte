<script>
  import { onMount } from 'svelte';
  import { Menu, X, ShoppingBag, User, Search } from 'lucide-svelte';
 
  let isMenuOpen = false;
  let scrolled = false;
 
  onMount(() => {
    const handleScroll = () => {
      scrolled = window.scrollY > 50;
    };
   
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  });
 
  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }
</script>

<nav class="fixed top-0 w-full z-50 transition-all duration-300 {scrolled ? 'bg-white/95 backdrop-blur-sm shadow-lg' : 'bg-transparent'}">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between items-center h-16 lg:h-20">
      <!-- Logo -->
      <div class="flex-shrink-0">
        <a href="/" class="text-2xl lg:text-3xl font-serif font-bold bg-gradient-to-r from-primary-600 to-rose-500 bg-clip-text text-transparent">
          Zion Collection
        </a>
      </div>
     
      <!-- Desktop Navigation -->
      <div class="hidden lg:block">
        <div class="flex items-center space-x-8">
          <a href="/" class="text-gray-800 hover:text-primary-600 transition-colors duration-200 font-medium">Home</a>
          <a href="#about" class="text-gray-800 hover:text-primary-600 transition-colors duration-200 font-medium">About</a>
          <a href="#team" class="text-gray-800 hover:text-primary-600 transition-colors duration-200 font-medium">Team</a>
          <a href="#stories" class="text-gray-800 hover:text-primary-600 transition-colors duration-200 font-medium">Our Stories</a>
          <a href="#gallery" class="text-gray-800 hover:text-primary-600 transition-colors duration-200 font-medium">Gallery</a>
          <a href="#contact" class="text-gray-800 hover:text-primary-600 transition-colors duration-200 font-medium">Contact</a>
        </div>
      </div>
     
      <!-- Desktop Actions -->
      <div class="hidden lg:flex items-center space-x-4">
        <button class="p-2 text-gray-600 hover:text-primary-600 transition-colors">
          <Search size={20} />
        </button>
        <button class="p-2 text-gray-600 hover:text-primary-600 transition-colors">
          <User size={20} />
        </button>
        <button class="p-2 text-gray-600 hover:text-primary-600 transition-colors relative">
          <ShoppingBag size={20} />
          <span class="absolute -top-1 -right-1 bg-primary-500 text-white text-xs rounded-full h-5 w-5 flex items-center justify-center">0</span>
        </button>
      </div>
     
      <!-- Mobile Menu Button -->
      <div class="lg:hidden">
        <button on:click={toggleMenu} class="p-2 text-gray-600">
          {#if isMenuOpen}
            <X size={24} />
          {:else}
            <Menu size={24} />
          {/if}
        </button>
      </div>
    </div>
  </div>
 
  <!-- Mobile Menu -->
  {#if isMenuOpen}
    <div class="lg:hidden bg-white border-t">
      <div class="px-4 pt-2 pb-3 space-y-1">
        <a href="/" class="block px-3 py-2 text-gray-800 hover:text-primary-600 transition-colors">Home</a>
        <a href="#about" class="block px-3 py-2 text-gray-800 hover:text-primary-600 transition-colors">About</a>
        <a href="#team" class="block px-3 py-2 text-gray-800 hover:text-primary-600 transition-colors">Team</a>
        <a href="#stories" class="block px-3 py-2 text-gray-800 hover:text-primary-600 transition-colors">Our Stories</a>
        <a href="#gallery" class="block px-3 py-2 text-gray-800 hover:text-primary-600 transition-colors">Gallery</a>
        <a href="#contact" class="block px-3 py-2 text-gray-800 hover:text-primary-600 transition-colors">Contact</a>
      </div>
      <div class="border-t pt-4 pb-3 px-4">
        <div class="flex items-center space-x-3">
          <button class="p-2 text-gray-600 hover:text-primary-600 transition-colors">
            <Search size={20} />
          </button>
          <button class="p-2 text-gray-600 hover:text-primary-600 transition-colors">
            <User size={20} />
          </button>
          <button class="p-2 text-gray-600 hover:text-primary-600 transition-colors relative">
            <ShoppingBag size={20} />
            <span class="absolute -top-1 -right-1 bg-primary-500 text-white text-xs rounded-full h-5 w-5 flex items-center justify-center">0</span>
          </button>
        </div>
      </div>
    </div>
  {/if}
</nav>