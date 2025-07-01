<script lang="ts">

  import { ClockFading as ProcessingTimeIcon, Spool as MaterialIcon, ArrowRight as SeeMoreIcon } from "@lucide/svelte";

  interface Product {
    picturePath: string;
    name: string;
    fabricUsed: string;
    isDiscounted: boolean;
    originalPrice: number;
    discountedPrice: number;
    processingTime: number;
  }

  const products: Product[] = [
    {
      picturePath: "/images/products/Kaos-Oblong-Cotton-Combed-30s.webp",
      name: "Kaos Oblong & Sablon",
      fabricUsed: "Cotton Combed 30s",
      isDiscounted: true,
      originalPrice: 75000,
      discountedPrice: 50000,
      processingTime: 5
    },
    {
      picturePath: "/images/products/Kaos-Raglan-Cotton-Combed-30s.webp",
      name: "Kaos Raglan & Sablon",
      fabricUsed: "Cotton Combed 30s",
      isDiscounted: true,
      originalPrice: 95000,
      discountedPrice: 65000,
      processingTime: 5
    },
    {
      picturePath: "/images/products/Jersey-Olahraga-(Atasan).webp",
      name: "Jersey Olahraga (Atasan)",
      fabricUsed: "Jersey",
      isDiscounted: true,
      originalPrice: 140000,
      discountedPrice: 110000,
      processingTime: 5
    },
    {
      picturePath: "/images/products/Jersey-Olahraga-(1-Stel).webp",
      name: "Jersey Olahraga (1 Stel)",
      fabricUsed: "Jersey",
      isDiscounted: true,
      originalPrice: 175000,
      discountedPrice: 140500,
      processingTime: 5
    },
    {
      picturePath: "/images/products/Kaos-Polo-Lacoste-Cotton-PE.webp",
      name: "Kaos Polo & Bordir",
      fabricUsed: "Polo Lacoste Cotton PE",
      isDiscounted: true,
      originalPrice: 100000,
      discountedPrice: 80000,
      processingTime: 7
    },
    {
      picturePath: "/images/products/Kaos-Polo-Lacoste-CVC-Premium.webp",
      name: "Kaos Polo & Bordir",
      fabricUsed: "Polo Lacoste CVC Premium",
      isDiscounted: true,
      originalPrice: 140000,
      discountedPrice: 115000,
      processingTime: 7
    },
  ];
</script>

<section class="py-[6rem] px-6 md:px-8 bg-primary text-secondary">
  <h2 class="text-3xl text-center font-bold md:text-4xl mb-[1em]">Produk Unggulan Kami</h2>
  <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 2xl:grid-cols-6 gap-6">
    {#each products as product}
      <article class="bg-white rounded-lg shadow-md overflow-hidden hover:scale-[1.05] transition duration-500 ease-in-out flex flex-col">
        <img src={product.picturePath} alt={product.name} loading="lazy" class="w-full h-64 aspect-[3/4] object-cover" />
        <div class="p-4 flex flex-col grow">
          <h3 class="text-xl text-secondary font-extrabold mb-[0.25em]">{product.name}</h3>
          <p class="text-sm text-gray-600 mb-2 flex items-center">
            <MaterialIcon class="inline mr-1 text-amber-800" size={16} />
            <span>{product.fabricUsed}</span>
          </p>
          {#if product.isDiscounted}
            <p class="text-red-500 text-sm line-through mb-1">Rp{product.originalPrice.toLocaleString("id-ID")}</p>
            <p class="text-green-500 text-2xl font-bold mb-[0.5em]">Rp{product.discountedPrice.toLocaleString("id-ID")}</p>
          {:else}
            <p class="text-gray-800 text-2xl font-bold mb-[0.5em]">Rp{product.originalPrice.toLocaleString("id-ID")}</p>
          {/if}
          <p class="text-sm text-gray-500 flex items-center mb-3">
            <ProcessingTimeIcon class="inline mr-1 text-blue-800" size={16} />
            <span class="font-semibold">{product.processingTime} hari</span>
          </p>
          <button class="text-primary font-semibold bg-accent w-full border-2 border-accent py-2 px-4 rounded-lg mt-auto hover:text-accent hover:bg-primary">
            Beli Produk
          </button>
        </div>
      </article>
    {/each}

  </div>
  <div class="w-full py-8">
    <button class="text-secondary font-semibold bg-primary w-fit border-2 border-secondary py-2 px-4 rounded-lg mt-auto mx-auto hover:text-primary hover:bg-accent hover:border-accent flex items-center">
      <span>Lihat Produk Lainnya</span>
      <SeeMoreIcon class="inline ms-1" size={16} />
    </button>
  </div>
</section>