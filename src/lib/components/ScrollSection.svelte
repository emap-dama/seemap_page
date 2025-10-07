<script>
  import { onMount } from "svelte";
  import scrollama from "scrollama";

  export let stepClass = "scroll-step";
  export let offset = 0.3;

  function revealInView() {
    const steps = document.querySelectorAll(`.${stepClass}`);
    steps.forEach((el) => {
      const r = el.getBoundingClientRect();
      const inView = r.top < window.innerHeight * 0.9 && r.bottom > 0;
      if (inView) el.classList.add("visible");
    });
  }

  onMount(() => {
    const scroller = scrollama();

    scroller
      .setup({ step: `.${stepClass}`, offset, once: false })
      .onStepEnter(({ element }) => element.classList.add("visible"))
      .onStepExit(({ element, direction }) => {
        // si no quieres que se oculten al volver hacia arriba, comenta la línea siguiente:
        if (direction === 'up') element.classList.remove("visible");
      });

    revealInView();
    const onR = () => { scroller.resize(); revealInView(); };
    window.addEventListener('resize', onR);
    window.addEventListener('load', onR);
  });
</script>

<slot />
