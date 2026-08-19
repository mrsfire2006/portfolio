<script lang="ts">
  import { Dot, MoveDownRight, X } from "@lucide/svelte";
  import Button from "@/components/ui/button/button.svelte";
  let isMoblieOpen = $state(false);
  let navLinks = [
    { id: "#about", label: "about" },
    { id: "#work", label: "work" },
    { id: "#contact", label: "contact" },
  ];
</script>

<div id="top"></div>

<div class="fixed top-0 left-0 w-full z-10">
  <nav
    class="max-w-[90%] w-full p-5 mx-auto flex flex-row justify-between items-center"
  >
    <a href="#top" class="flex flex-row justify-center items-center">
      <span class="text-navy text-4xl font-black">M</span>
      <Dot size={35} strokeWidth={10} class="text-orange" />
    </a>
    <div class="hidden md:flex felx-row gap-10 justify-center items-center">
      {#each navLinks as link}
        <a
          href={link.id}
          class="text-navy uppercase font-bold hover:text-orange text-sm"
          >{link.label}</a
        >
      {/each}
    </div>
    <!-- {mobile opend} -->
    <div class="relative md:hidden">
      <Button
        onclick={() => {
          isMoblieOpen = !isMoblieOpen;
        }}
        class="flex flex-row text-sm font-bold justify-center items-center"
      >
        {#if isMoblieOpen}
          <X class="size-5  " strokeWidth={5} />
        {:else}
          <span class="uppercase text-navy">Menu</span>
          <MoveDownRight size={15} />
        {/if}
      </Button>
      <div
        class={`absolute -bottom-30 shadow-[5px_6px_0_#172342] -left-15 px-5 py-3 gap-5 text-sm  border-navy border-2 bg-orange/50 backdrop-blur-xs  flex-col ${isMoblieOpen ? "flex" : "hidden"}`}
      >
        {#each navLinks as link}
          <a
            href={link.id}
            class="text-navy uppercase font-bold hover:text-orange text-sm"
            >{link.label}</a
          >
        {/each}
      </div>
    </div>
  </nav>
</div>
