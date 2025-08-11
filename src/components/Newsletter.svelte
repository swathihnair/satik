<script>
  import { Mail } from 'lucide-svelte';
  
  let email = '';
  
  function handleSubscribe(event) {
    event.preventDefault();
    if (email) {
      alert('Thank you for subscribing to our newsletter!');
      email = '';
    }
  }
</script>

<section class="py-16 bg-gradient-to-r from-primary-600 to-rose-500">
  <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
    <div class="animate-fade-in">
      <div class="w-16 h-16 bg-white/20 rounded-full flex items-center justify-center mx-auto mb-6">
        <Mail size={32} class="text-white" />
      </div>
      <h2 class="text-3xl lg:text-4xl font-serif font-bold text-white mb-4">
        Stay in Style
      </h2>
      <p class="text-lg text-white/90 mb-8 max-w-2xl mx-auto">
        Subscribe to our newsletter and be the first to know about new collections, 
        exclusive offers, and fashion tips from our style experts.
      </p>
      
      <form on:submit={handleSubscribe} class="max-w-md mx-auto">
        <div class="flex">
          <input 
            type="email" 
            bind:value={email}
            placeholder="Enter your email"
            required
            class="flex-1 px-4 py-3 rounded-l-full border-0 focus:ring-2 focus:ring-white focus:outline-none"
          />
          <button 
            type="submit"
            class="bg-white text-primary-600 px-6 py-3 rounded-r-full font-semibold hover:bg-gray-100 transition-colors"
          >
            Subscribe
          </button>
        </div>
      </form>
      
      <p class="text-sm text-white/70 mt-4">
        No spam, unsubscribe anytime. Your privacy is important to us.
      </p>
    </div>
  </div>
</section>