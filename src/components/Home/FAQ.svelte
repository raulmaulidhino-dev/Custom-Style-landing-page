<script lang="ts">
  import { onMount } from "svelte";
  import { ChevronDown, ChevronUp } from "@lucide/svelte";

  interface FAQ {
    question: string;
    answer: string;
    isOpen: boolean;
  }

  const faqs: FAQ[] = [
    {
      question: "Apa jenis pakaian yang bisa saya pesan dari konveksi Custom Style?",
      answer:
        "Kami menyediakan berbagai jenis pakaian, termasuk konveksi Seragam Kantor, Seragam Sekolah, Pakaian Olahraga, Seragam Industri, Kaos, Polo Shirt, Rompi, Jaket, Almamater, Merchandise dan lain-lain.",
      isOpen: false,
    },
    {
      question: "Berapa lama waktu yang dibutuhkan untuk memproses pesanan?",
      answer:
        "Waktu pemesanan standar kami 14 hari kerja (2 minggu). Waktu proses pesanan kami bervariasi tergantung pada kompleksitas desain dan jumlah pesanan. Kami akan memberikan perkiraan waktu yang lebih jelas saat pemesanan.",
      isOpen: false,
    },
    {
      question: "Berapa minimum order dan apakah Anda menerima pesanan dalam jumlah besar?",
      answer:
        "Ya, kami menerima pesanan dalam jumlah besar untuk keperluan perusahaan, organisasi, atau acara khusus lainnya. Untuk minimum order kami yaitu 1 lusin (12 pcs) untuk 1 desain.",
      isOpen: false,
    },
    {
      question: "Bagaimana cara melakukan pemesanan?",
      answer:
        "Anda dapat melakukan pemesanan melalui website kami atau dengan menghubungi tim layanan pelanggan kami.",
      isOpen: false,
    },
    {
      question: "Apakah Anda memberikan diskon untuk pesanan dalam jumlah besar?",
      answer:
        "Kami memberikan diskon khusus untuk pesanan dalam jumlah besar. Mohon hubungi kami untuk informasi lebih lanjut tentang diskon dan penawaran spesial lainnya. Nantikan promo-promo menarik dari kami di website ini.",
      isOpen: false,
    },
    {
      question: "Apakah Anda menerima pesanan dengan desain custom serta mendapatkan \"FREE DESIGN\"?",
      answer:
        "Ya, kami menerima pesanan dengan desain custom. Tim desain kami akan membantu Anda mewujudkan ide Anda menjadi kenyataan tanpa mengeluarkan biaya tambahan lagi.",
      isOpen: false,
    },
    {
      question: "Bagaimana saya bisa mendapatkan sampel produk sebelum melakukan pemesanan?",
      answer:
        "Anda dapat meminta sampel produk sebelum melakukan pemesanan jika pesanan anda lebih dari 5 lusin untuk 1 desain. Silakan hubungi kami untuk informasi lebih lanjut.",
      isOpen: false,
    },
    {
      question: "Apakah ada biaya tambahan yang perlu saya bayarkan?",
      answer:
        "Kami tidak memberikan biaya tambahan apapun, seluruh biaya kami sudah hitung didalam penawaran kami. Termasuk *Free Ongkir diseluruh wilayah Jabodetabek. *(untuk pemesanan diatas 5 lusin)",
      isOpen: false,
    },
    {
      question: "Apakah ada kebijakan pengembalian atau penukaran barang?",
      answer:
        "Kami menerima pengembalian atau penukaran barang jika terdapat cacat produksi atau kesalahan dari pihak kami. Mohon hubungi kami untuk informasi lebih lanjut.",
      isOpen: false,
    },
    {
      question: "Apakah Anda memiliki katalog produk yang bisa saya lihat?",
      answer:
        "Ya, kami memiliki katalog produk yang bisa Anda lihat di halaman produk pada navigasi di atas.",
      isOpen: false,
    },
    {
      question: "\"Pengerjaan Kilat\" Apakah Anda menyediakan layanan pengerjaan ekspres?",
      answer:
        "Ya, kami menyediakan layanan pengerjaan ekspres dengan nama “Pengerjaan Kilat” untuk memenuhi kebutuhan Anda yang membutuhkan pengerjaan dan pengiriman cepat. Hubungi kami untuk informasi lebih lanjut tentang layanan ini.",
      isOpen: false,
    },
    {
      question: "Bagaimana saya bisa mengetahui perkembangan pesanan saya?",
      answer:
        "Kami akan memberikan pembaruan tentang perkembangan pesanan Anda melalui admin kami, Kami selalu meng-update posisi pekerjaan agar klien merasa lebih aman bekerja sama dengan kami.",
      isOpen: false,
    },
  ];

  const toggleFAQ = (index: number) => {
    faqs[index].isOpen = !faqs[index].isOpen;
  };

  onMount(() => {
    const faqItems = document.querySelectorAll(".faq-item");
    faqItems.forEach((item, index) => {
      item.addEventListener("click", () => {
        toggleFAQ(index);
      });
    });
  });
</script>

<section class="py-[6rem] px-6 md:px-8 bg-primary text-secondary">
  <h2 class="text-3xl text-center font-bold md:text-4xl mb-[1em]">FAQ</h2>
  {#each faqs as faq}
  <div class="flex flex-col max-w-xl mx-auto">
    <button
      class="faq-item bg-accent text-primary mb-4 border border-accent rounded-lg bg-primary-light"
    >
      <div
        class="question p-4 flex justify-between items-center gap-2 font-bold text-inherit cursor-pointer"
      >
        <span class="text-left text-inherit">{faq.question}</span>
        {#if faq.isOpen}
          <ChevronUp class="text-inherit transition-transform duration-300 min-w-10" />
        {:else}
          <ChevronDown class="text-inherit transition-transform duration-300 min-w-10" />
        {/if}
      </div>
      <div
        class="answer bg-primary text-left text-secondary rounded-b-lg overflow-hidden transition-all duration-300"
        style="max-height: {faq.isOpen ? '500px' : '0'}"
      >
        {#if faq.isOpen}
          <p class="mt-2 p-4">{faq.answer}</p>
        {/if}
      </div>
    </button>
  </div>
  {/each}
</section>
