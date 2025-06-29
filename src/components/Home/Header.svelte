<script lang="ts">
  import { onMount } from "svelte";
  import CartIcon from "@lucide/svelte/icons/shopping-cart";
  import MenuIcon from "@lucide/svelte/icons/menu";
  import XIcon from "@lucide/svelte/icons/x";

  interface NavItem {
    name: string;
    href: string;
    isActive?: boolean;
  }

  let isMobileNavOpen: boolean = $state(false);

  let navItems: NavItem[] = [
    { name: "Beranda", href: "/", isActive: true },
    { name: "Layanan", href: "/" },
    { name: "Produk", href: "/" },
    { name: "Tentang Kami", href: "/" },
    { name: "Blog", href: "/" },
    { name: "Hubungi Kami", href: "/" }
  ];

  onMount(() => {
    const handleResize = async () => {
      if (window.innerWidth > 768) {
        isMobileNavOpen = false;
      }
    };
    window.addEventListener("resize", handleResize);
    
    const hamburgerBtn: HTMLElement | null = document.getElementById("hamburger");

    if (hamburgerBtn) {
      hamburgerBtn.addEventListener("click", () => {
        isMobileNavOpen = !isMobileNavOpen;
      });
    }

    return () => window.removeEventListener("resize", handleResize);
  });
</script>

<header class="p-6 flex flex-wrap justify-between content-center items-center gap-8 md:gap-6">
  <section class="max-w-42">
    <img src="/images/logos/Custom-Style-logo_black.png" alt="Custom Style Logo" class="w-full" />
  </section>
  <!-- Desktop Navigation -->
  <nav class="hidden lg:block">
    <ul class="flex gap-4">
      {#each navItems as navItem}
        <li><a href={navItem.href} class={`text-secondary font-semibold ${ navItem.isActive ? "text-accent" : "hover:text-accent" } `}>{navItem.name}</a></li>
      {/each}
    </ul>
  </nav>

  <!-- Mobile Navigation -->
  <nav class="lg:hidden">
    <button
      id="hamburger"
      class="p-2 text-secondary rounded-lg hover:bg-slate-200 transition-colors duration-300"
      aria-label="Toggle Navigation"
    >
      {#if isMobileNavOpen}
        <XIcon size="30" />
      {:else}
        <MenuIcon size="30" />
      {/if}
    </button>

    <nav class={`fixed top-0 left-0 w-3/4 h-full bg-accent text-white p-6 z-50 shadow-lg shadow-black ${ isMobileNavOpen ? "translate-x-0" : "-translate-x-full" } transition ease-in-out duration-300`}>
      <img src="/images/logos/Custom-Style-logo_white.png" alt="Custom Style Logo" class="w-full max-w-42 py-6 mx-auto" />
      <hr class="max-w-32 mx-auto" />
      <ul class="py-8 flex flex-col items-center justify-center gap-1">
        {#each navItems as navItem}
          <li class="w-full"><a href={navItem.href} class={`text-center ${ navItem.isActive ? "text-accent font-bold bg-primary" : "text-primary hover:text-accent hover:font-bold hover:bg-primary" } w-full p-4 rounded-lg block`}>{navItem.name}</a></li>
        {/each}
      </ul>
    </nav>
  </nav>
  <section class="grow-1 md:grow-0 justify-center items-center gap-2 hidden lg:flex">
    <input type="text" placeholder="Cari Produk/Jasa" class="bg-slate-200 p-3 rounded-full" />
    <CartIcon size="38" class="text-primary bg-accent p-2 rounded-lg" />
  </section>
</header>
