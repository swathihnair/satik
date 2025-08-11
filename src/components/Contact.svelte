<script>
  import { onMount } from 'svelte';
  import { MapPin, Phone, Mail, Clock, Send } from 'lucide-svelte';
  
  let contactRef;
  let isVisible = false;
  let formData = {
    name: '',
    email: '',
    subject: '',
    message: ''
  };
  
  onMount(() => {
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          isVisible = true;
        }
      });
    }, { threshold: 0.3 });
    
    if (contactRef) {
      observer.observe(contactRef);
    }
    
    return () => observer.disconnect();
  });
  
  function handleSubmit(event) {
    event.preventDefault();
    // Handle form submission here
    alert('Thank you for your message! We\'ll get back to you soon.');
    formData = { name: '', email: '', subject: '', message: '' };
  }
</script>

<section id="contact" bind:this={contactRef} class="py-20 bg-gray-50">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="text-center mb-16 {isVisible ? 'animate-slide-up' : 'opacity-0'}">
      <h2 class="text-4xl lg:text-5xl font-serif font-bold text-gray-900 mb-6">
        Get In Touch
      </h2>
      <p class="text-lg text-gray-600 max-w-3xl mx-auto leading-relaxed">
        We'd love to hear from you! Whether you have questions about our collections, 
        need styling advice, or want to share feedback, we're here to help.
      </p>
    </div>
    
    <div class="grid lg:grid-cols-2 gap-12">
      <!-- Contact Information -->
      <div class="{isVisible ? 'animate-slide-up' : 'opacity-0'}">
        <div class="bg-white rounded-2xl p-8 shadow-lg">
          <h3 class="text-2xl font-bold text-gray-900 mb-8">Contact Information</h3>
          
          <div class="space-y-6">
            <div class="flex items-start space-x-4">
              <div class="w-12 h-12 bg-primary-100 rounded-full flex items-center justify-center flex-shrink-0">
                <MapPin size={20} class="text-primary-600" />
              </div>
              <div>
                <h4 class="font-semibold text-gray-900">Visit Our Store</h4>
                <p class="text-gray-600">123 Fashion Avenue<br>New York, NY 10001<br>United States</p>
              </div>
            </div>
            
            <div class="flex items-start space-x-4">
              <div class="w-12 h-12 bg-rose-100 rounded-full flex items-center justify-center flex-shrink-0">
                <Phone size={20} class="text-rose-600" />
              </div>
              <div>
                <h4 class="font-semibold text-gray-900">Call Us</h4>
                <p class="text-gray-600">+1 (555) 123-4567<br>Toll-free: +1 (800) 123-4567</p>
              </div>
            </div>
            
            <div class="flex items-start space-x-4">
              <div class="w-12 h-12 bg-pink-100 rounded-full flex items-center justify-center flex-shrink-0">
                <Mail size={20} class="text-pink-600" />
              </div>
              <div>
                <h4 class="font-semibold text-gray-900">Email Us</h4>
                <p class="text-gray-600">hello@zioncollection.com<br>support@zioncollection.com</p>
              </div>
            </div>
            
            <div class="flex items-start space-x-4">
              <div class="w-12 h-12 bg-purple-100 rounded-full flex items-center justify-center flex-shrink-0">
                <Clock size={20} class="text-purple-600" />
              </div>
              <div>
                <h4 class="font-semibold text-gray-900">Opening Hours</h4>
                <p class="text-gray-600">Monday - Saturday: 10:00 AM - 8:00 PM<br>Sunday: 12:00 PM - 6:00 PM</p>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Contact Form -->
      <div class="{isVisible ? 'animate-fade-in' : 'opacity-0'}">
        <div class="bg-white rounded-2xl p-8 shadow-lg">
          <h3 class="text-2xl font-bold text-gray-900 mb-8">Send Us a Message</h3>
          
          <form on:submit={handleSubmit} class="space-y-6">
            <div class="grid md:grid-cols-2 gap-6">
              <div>
                <label for="name" class="block text-sm font-medium text-gray-700 mb-2">Full Name</label>
                <input 
                  type="text" 
                  id="name" 
                  bind:value={formData.name}
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent transition-colors"
                  placeholder="Your Name"
                />
              </div>
              <div>
                <label for="email" class="block text-sm font-medium text-gray-700 mb-2">Email</label>
                <input 
                  type="email" 
                  id="email" 
                  bind:value={formData.email}
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent transition-colors"
                  placeholder="your@email.com"
                />
              </div>
            </div>
            
            <div>
              <label for="subject" class="block text-sm font-medium text-gray-700 mb-2">Subject</label>
              <input 
                type="text" 
                id="subject" 
                bind:value={formData.subject}
                required
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent transition-colors"
                placeholder="How can we help you?"
              />
            </div>
            
            <div>
              <label for="message" class="block text-sm font-medium text-gray-700 mb-2">Message</label>
              <textarea 
                id="message" 
                bind:value={formData.message}
                required
                rows="6"
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-transparent transition-colors resize-none"
                placeholder="Tell us more about your inquiry..."
              ></textarea>
            </div>
            
            <button 
              type="submit"
              class="w-full bg-gradient-to-r from-primary-600 to-rose-500 text-white py-3 px-6 rounded-lg font-semibold hover:shadow-lg transition-all duration-300 transform hover:scale-105 flex items-center justify-center space-x-2"
            >
              <Send size={20} />
              <span>Send Message</span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</section>