<script>
  import { onMount } from 'svelte';
  import { Linkedin, Instagram, Twitter } from 'lucide-svelte';
 
  let teamRef;
  let isVisible = false;
 
  const teamMembers = [
    {
      id: 1,
      name: "Sarah Johnson",
      role: "Founder & Creative Director",
      image: "https://images.pexels.com/photos/3785079/pexels-photo-3785079.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      bio: "With over 15 years in fashion design, Sarah founded Zion Collection to empower women through elegant, timeless pieces.",
      social: {
        linkedin: "#",
        instagram: "#",
        twitter: "#"
      }
    },
    {
      id: 2,
      name: "Emily Chen",
      role: "Head of Design",
      image: "https://images.pexels.com/photos/3756679/pexels-photo-3756679.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      bio: "Emily brings innovative design concepts to life, blending contemporary trends with classic sophistication.",
      social: {
        linkedin: "#",
        instagram: "#",
        twitter: "#"
      }
    },
    {
      id: 3,
      name: "Maria Rodriguez",
      role: "Style Consultant",
      image: "https://images.pexels.com/photos/3785077/pexels-photo-3785077.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      bio: "Maria helps our customers find their perfect style, offering personalized fashion advice and styling services.",
      social: {
        linkedin: "#",
        instagram: "#",
        twitter: "#"
      }
    },
    {
      id: 4,
      name: "Jessica Williams",
      role: "Brand Manager",
      image: "https://images.pexels.com/photos/3756681/pexels-photo-3756681.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      bio: "Jessica oversees our brand strategy and ensures every customer experience reflects our commitment to excellence.",
      social: {
        linkedin: "#",
        instagram: "#",
        twitter: "#"
      }
    },
    {
      id: 5,
      name: "Amanda Thompson",
      role: "Quality Assurance",
      image: "https://images.pexels.com/photos/3785078/pexels-photo-3785078.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      bio: "Amanda ensures every piece meets our high standards of quality, from material selection to final finishing.",
      social: {
        linkedin: "#",
        instagram: "#",
        twitter: "#"
      }
    },
    {
      id: 6,
      name: "Lisa Park",
      role: "Customer Relations",
      image: "https://images.pexels.com/photos/3756680/pexels-photo-3756680.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
      bio: "Lisa leads our customer service team, ensuring every interaction is warm, helpful, and memorable.",
      social: {
        linkedin: "#",
        instagram: "#",
        twitter: "#"
      }
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
   
    if (teamRef) {
      observer.observe(teamRef);
    }
   
    return () => observer.disconnect();
  });
</script>

<section id="team" bind:this={teamRef} class="py-20 bg-gradient-to-b from-white to-primary-50">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="text-center mb-16 {isVisible ? 'animate-slide-up' : 'opacity-0'}">
      <h2 class="text-4xl lg:text-5xl font-serif font-bold text-gray-900 mb-6">
        Meet Our <span class="bg-gradient-to-r from-primary-600 to-rose-500 bg-clip-text text-transparent">Team</span>
      </h2>
      <p class="text-lg text-gray-600 max-w-3xl mx-auto leading-relaxed">
        Behind every beautiful collection is a passionate team of professionals dedicated to bringing you
        the finest in women's fashion. Get to know the talented individuals who make Zion Collection special.
      </p>
    </div>
   
    <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
      {#each teamMembers as member, index}
        <div class="{isVisible ? 'animate-fade-in' : 'opacity-0'} bg-white rounded-2xl shadow-lg hover:shadow-xl transition-all duration-300 transform hover:-translate-y-2 overflow-hidden group"
             style="animation-delay: {index * 0.1}s">
          <div class="relative overflow-hidden">
            <img
              src={member.image}
              alt={member.name}
              class="w-full h-64 object-cover transition-transform duration-700 group-hover:scale-110"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-transparent to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              <div class="absolute bottom-4 left-1/2 transform -translate-x-1/2 flex space-x-3">
                <a href={member.social.linkedin} class="w-10 h-10 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center text-white hover:bg-white/30 transition-colors">
                  <Linkedin size={18} />
                </a>
                <a href={member.social.instagram} class="w-10 h-10 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center text-white hover:bg-white/30 transition-colors">
                  <Instagram size={18} />
                </a>
                <a href={member.social.twitter} class="w-10 h-10 bg-white/20 backdrop-blur-sm rounded-full flex items-center justify-center text-white hover:bg-white/30 transition-colors">
                  <Twitter size={18} />
                </a>
              </div>
            </div>
          </div>
          <div class="p-6">
            <h3 class="text-xl font-bold text-gray-900 mb-2">{member.name}</h3>
            <p class="text-primary-600 font-semibold mb-3">{member.role}</p>
            <p class="text-gray-600 leading-relaxed">{member.bio}</p>
          </div>
        </div>
      {/each}
    </div>
   
    <!-- Team Values -->
    <div class="mt-20 {isVisible ? 'animate-slide-up' : 'opacity-0'}">
      <div class="bg-gradient-to-r from-primary-600 to-rose-500 rounded-3xl p-1">
        <div class="bg-white rounded-3xl p-8 lg:p-12 text-center">
          <h3 class="text-3xl lg:text-4xl font-serif font-bold text-gray-900 mb-6">
            Our Team Values
          </h3>
          <div class="grid md:grid-cols-3 gap-8 mt-12">
            <div class="text-center">
              <div class="w-16 h-16 bg-primary-100 rounded-full flex items-center justify-center mx-auto mb-4">
                <span class="text-2xl">💎</span>
              </div>
              <h4 class="text-xl font-bold text-gray-900 mb-2">Excellence</h4>
              <p class="text-gray-600">We strive for perfection in every detail, from design to customer service.</p>
            </div>
            <div class="text-center">
              <div class="w-16 h-16 bg-rose-100 rounded-full flex items-center justify-center mx-auto mb-4">
                <span class="text-2xl">🤝</span>
              </div>
              <h4 class="text-xl font-bold text-gray-900 mb-2">Collaboration</h4>
              <p class="text-gray-600">Together, we create magic through teamwork and shared vision.</p>
            </div>
            <div class="text-center">
              <div class="w-16 h-16 bg-pink-100 rounded-full flex items-center justify-center mx-auto mb-4">
                <span class="text-2xl">✨</span>
              </div>
              <h4 class="text-xl font-bold text-gray-900 mb-2">Innovation</h4>
              <p class="text-gray-600">We embrace creativity and innovation to stay ahead of fashion trends.</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>