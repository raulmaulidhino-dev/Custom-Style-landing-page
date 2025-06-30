<script lang="ts">

  import { Lightbulb, Star, ScissorsLineDashed, Handshake, type Icon as IconType } from "@lucide/svelte";

  interface Feature {
    title: string;
    description: string;
    icon: typeof IconType;
  };

  const features: Feature[] = [
    {
      title: "Gratis Desain & Konsultasi",
      description: "Ekpresikan gaya unik Anda tanpa batas. Nikmati layanan ini secara gratis. Kami bantu wujudkan ide Anda jadi nyata.",
      icon: Lightbulb
    }, {
      title: "Bahan Berkualitas Tinggi",
      description: "Kami hanya menggunakan material premium yang nyaman, tahan lama, dan tampil menawan.",
      icon: Star,
    }, {
      title: "Presisi Produksi",
      description: "Didukung teknologi modern, setiap detail produksi kami kerjakan dengan akurasi tinggi untuk hasil yang terbaik.",
      icon: ScissorsLineDashed
    }, {
      title: "Desain Fleksibel, Produk Beragam",
      description: "Butuh seragam, apparel olahraga, atau merchandise? Kami siap bantu dengan desain custom dan pilihan produk yang fleksibel sesuai dengan kebutuhan Anda.",
      icon: Handshake
    }
  ];
</script>

<section class="py-[6rem] px-4 md:px-6">
  <h2 class="text-3xl text-center font-bold md:text-4xl mb-[1em]">Mengapa Pilih Custom Style?</h2>
  <section class="flex flex-wrap gap-4 justify-center h-full">
    {#each features as feature}
      <div class="flex flex-col items-center max-w-sm px-4 py-6 bg-primary odd:bg-accent text-accent odd:text-primary border-2 border-accent rounded-lg shadow-md w-full transition duration-500 ease-in-out hover:scale-[1.05]">
        <feature.icon class="text-innherit mb-2" size={50} />
        <h3 class="text-xl text-inherit text-center font-semibold mb-2">{feature.title}</h3>
        <p class="text-inherit text-center">{feature.description}</p>
      </div>
    {/each}
  </section>
</section>
