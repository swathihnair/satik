<script>
  import { Facebook, Instagram, Twitter, Youtube, MapPin, Phone, Mail } from 'lucide-svelte';
</script>

<footer class="bg-gray-900 text-white">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
    <div class="grid lg:grid-cols-4 md:grid-cols-2 gap-8">
      <!-- Brand -->
      <div class="lg:col-span-1">
        <h3 class="text-3xl font-serif font-bold bg-gradient-to-r from-primary-400 to-rose-400 bg-clip-text text-transparent mb-4">
          Zion Collection
        </h3>
        <p class="text-gray-300 mb-6 leading-relaxed">
          Empowering women through fashion with elegant, timeless pieces that celebrate individuality and confidence.
        </p>
        <div class="flex space-x-4">
          <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-primary-600 transition-colors">
            <Facebook size={20} />
          </a>
          <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-primary-600 transition-colors">
            <Instagram size={20} />
          </a>
          <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-primary-600 transition-colors">
            <Twitter size={20} />
          </a>
          <a href="#" class="w-10 h-10 bg-gray-800 rounded-full flex items-center justify-center hover:bg-primary-600 transition-colors">
            <Youtube size={20} />
          </a>
        </div>
      </div>
      
      <!-- Quick Links -->
      <div>
        <h4 class="text-lg font-semibold mb-6">Quick Links</h4>
        <ul class="space-y-3">
          <li><a href="/" class="text-gray-300 hover:text-primary-400 transition-colors">Home</a></li>
          <li><a href="#about" class="text-gray-300 hover:text-primary-400 transition-colors">About Us</a></li>
          <li><a href="#stories" class="text-gray-300 hover:text-primary-400 transition-colors">Our Stories</a></li>
          <li><a href="#gallery" class="text-gray-300 hover:text-primary-400 transition-colors">Gallery</a></li>
          <li><a href="#contact" class="text-gray-300 hover:text-primary-400 transition-colors">Contact</a></li>
        </ul>
      </div>
      
      <!-- Collections -->
      <div>
        <h4 class="text-lg font-semibold mb-6">Collections</h4>
        <ul class="space-y-3">
          <li><a href="#" class="text-gray-300 hover:text-primary-400 transition-colors">New Arrivals</a></li>
          <li><a href="#" class="text-gray-300 hover:text-primary-400 transition-colors">Evening Wear</a></li>
          <li><a href="#" class="text-gray-300 hover:text-primary-400 transition-colors">Casual Wear</a></li>
          <li><a href="#" class="text-gray-300 hover:text-primary-400 transition-colors">Accessories</a></li>
          <li><a href="#" class="text-gray-300 hover:text-primary-400 transition-colors">Sale Items</a></li>
        </ul>
      </div>
      
      <!-- Contact Info -->
      <div>
        <h4 class="text-lg font-semibold mb-6">Contact Info</h4>
        <div class="space-y-3">
          <div class="flex items-center space-x-3">
            <MapPin size={16} class="text-primary-400" />
            <span class="text-gray-300">123 Fashion Ave, NY 10001</span>
          </div>
          <div class="flex items-center space-x-3">
            <Phone size={16} class="text-primary-400" />
            <span class="text-gray-300">+1 (555) 123-4567</span>
          </div>
          <div class="flex items-center space-x-3">
            <Mail size={16} class="text-primary-400" />
            <span class="text-gray-300">hello@zioncollection.com</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  
  <!-- Bottom Bar -->
  <div class="border-t border-gray-800">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6">
      <div class="flex flex-col md:flex-row justify-between items-center">
        <p class="text-gray-400 text-sm">
          © 2024 Zion Collection. All rights reserved.
        </p>
        <div class="flex space-x-6 mt-4 md:mt-0">
          <a href="#" class="text-gray-400 hover:text-primary-400 text-sm transition-colors">Privacy Policy</a>
          <a href="#" class="text-gray-400 hover:text-primary-400 text-sm transition-colors">Terms of Service</a>
          <a href="#" class="text-gray-400 hover:text-primary-400 text-sm transition-colors">Shipping Info</a>
        </div>
      </div>
    </div>
  </div>
</footer>