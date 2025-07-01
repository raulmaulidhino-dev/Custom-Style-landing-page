<script lang="ts">

  interface Service {
    title: string;
    bgImage: string;
  }

  const services: Service[] = [
    {
      title: "Sablon Manual",
      bgImage: "/images/services/Sablon-Manual.webp"
    },
    {
      title: "Sablon DTF",
      bgImage: "/images/services/Sablon-DTF.webp"
    },
    {
      title: "Bordir Sublimasi",
      bgImage: "/images/services/Sablon-Sublimasi.webp"
    },
    {
      title: "Dan Banyak Lagi!",
      bgImage: "/images/services/Clothing-Display.webp"
    },
  ];

</script>

<section class="py-[6rem] px-4 md:px-6">
  <h2 class="text-3xl text-center font-bold md:text-4xl mb-[1em]">Kami Bisa Bantu ...</h2>
  <div class="flex gap-4 overflow-x-auto">
    {#each services as service}
      <article class={`relative w-full min-w-xs max-w-md aspect-[3/4] md:aspect-[4/3] rounded-sm overflow-hidden`}>
        <img src={service.bgImage} alt={service.title} class="w-full h-full object-cover rounded-[inherit] shadow-lg transition-all duration-500 hover:scale-125 hover:brightness-75" />
        <h3 class="absolute bottom-8 left-8 md:bottom-6 md:left-6 text-lg font-bold text-accent bg-primary rounded-md px-4 py-2 shadow-xl">{service.title}</h3>
      </article>
    {/each}
  </div>
</section>