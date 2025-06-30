<script lang="ts">

  import { type Icon as IconType, UserCheck, Layers, PenTool, Package, Factory, Truck, Headset } from "@lucide/svelte";

  interface Step {
    icon: typeof IconType;
    title: string;
    description: string;
  }

  const steps: Step[] = [
    {
      icon: UserCheck,
      title: "Konsultasi Desain",
      description: "Langkah pertama adalah sesi konsultasi antara pelanggan dan tim desain kami. Di sini, ide dan kebutuhan Anda didiskusikan secara mendalam untuk menghasilkan desain yang sesuai dengan keinginan."
    },
    {
      icon: Layers,
      title: "Pilihan Bahan",
      description: "Setelah desain disepakati, saatnya memilih bahan terbaik. Kami menyediakan berbagai jenis kain dan material dengan kualitas premium yang dapat disesuaikan dengan anggaran dan fungsi produk."
    },
    {
      icon: PenTool,
      title: "Desain Produk",
      description: "Tim desain kami mulai memvisualisasikan desain ke dalam format digital atau mockup, memastikan setiap detail sesuai dengan ekspektasi Anda."
    },
    {
      icon: Package,
      title: "Sample Produk",
      description: "Sebelum produksi massal, kami buatkan sample produk untuk memastikan Anda puas dengan hasil awal. Perubahan dan koreksi masih bisa dilakukan di tahap ini."
    },
    {
      icon: Factory,
      title: "Produksi",
      description: "Setelah sample disetujui, proses produksi dimulai. Kami mengutamakan ketepatan waktu dan kualitas jahitan, dengan tenaga kerja berpengalaman dan mesin modern."
    },
    {
      icon: Truck,
      title: "Pengiriman Produk",
      description: "Produk selesai diproduksi dan langsung dikirim ke alamat Anda. Kami bekerja sama dengan jasa pengiriman tepercaya agar produk sampai dengan aman dan tepat waktu."
    },
    {
      icon: Headset,
      title: "Pelayanan Purna Jual",
      description: "Kami tetap hadir untuk Anda setelah produk diterima. Jika ada keluhan, saran, atau kebutuhan tambahan, tim customer service kami siap membantu!"
    },
  ];

</script>

<section class="py-[6rem] px-6 md:px-8 bg-accent text-primary">
  <h2 class="text-3xl text-center font-bold md:text-4xl mb-[1em]">Alur Kerja Kami</h2>
  <ol class="relative border-s border-dashed border-primary max-w-lg mx-auto">
    {#each steps as step}
      <li class="mb-10 ms-6">
        <span class="abolute flex items-center justify-center w-4 h-4 bg-primary rounded-full -ms-8 ring-8 ring-primary">
          <step.icon class="w-4 h-4 text-accent" />
        </span>
        <h3 class="flex items-center mb-1 -mt-6 text-lg font-semibold text-primary">{step.title}</h3>
        <p class="mb-4 text-base font-normal text-white">{step.description}</p>
      </li>
    {/each}
  </ol>
</section>