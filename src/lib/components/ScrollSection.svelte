<script>
  import { onMount, onDestroy, createEventDispatcher } from 'svelte';

  export let stepClass = 'scroll-step';
  export let offset = 0.3;        // 0..1 (fracción de la altura de viewport)
  export let once = false;         // true: dispara una sola vez por paso
  export let debug = false;

  // Nuevas clases configurables para estados
  export let visibleClass = 'is-visible';
  export let activeClass  = 'is-active';
  export let pastClass    = 'is-past';

  // Si vuelves hacia arriba, ¿quieres ocultar de nuevo?
  export let hideOnScrollUp = false;

  const dispatch = createEventDispatcher();

  let scroller;
  let removeListeners = () => {};

  // throttle con rAF para evitar recálculos excesivos en resize
  const rafThrottle = (fn) => {
    let rAF = 0;
    return (...args) => {
      if (rAF) return;
      rAF = requestAnimationFrame(() => {
        fn(...args);
        rAF = 0;
      });
    };
  };

  function revealInView() {
    const steps = document.querySelectorAll(`.${stepClass}`);
    steps.forEach((el) => {
      const r = el.getBoundingClientRect();
      const inView = r.top < window.innerHeight * (offset + 0.1) && r.bottom > 0;
      if (inView) el.classList.add(visibleClass);
    });
  }

  onMount(async () => {
    const { default: scrollama } = await import('scrollama');
    scroller = scrollama();

    scroller
      .setup({ step: `.${stepClass}`, offset, once, debug })
      .onStepEnter(({ element, index, direction }) => {
        element.classList.add(visibleClass, activeClass);
        dispatch('enter', { element, index, direction });
      })
      .onStepExit(({ element, index, direction }) => {
        element.classList.remove(activeClass);

        if (direction === 'down') {
          element.classList.add(pastClass);
        } else {
          element.classList.remove(pastClass);
          if (hideOnScrollUp && !once) {
            element.classList.remove(visibleClass);
          }
        }
        dispatch('exit', { element, index, direction });
      });

    revealInView();

    const onResize = rafThrottle(() => scroller && scroller.resize());
    const onLoad   = () => scroller && scroller.resize();

    window.addEventListener('resize', onResize);
    window.addEventListener('load', onLoad);
    removeListeners = () => {
      window.removeEventListener('resize', onResize);
      window.removeEventListener('load', onLoad);
    };
  });

  onDestroy(() => {
    removeListeners();
    if (scroller && scroller.destroy) scroller.destroy();
  });
</script>

<slot />

<style>
  :global(.scroll-step) {
    opacity: 0;
    transform: translateY(12px);
    transition: opacity 0.6s ease, transform 0.6s ease;
    will-change: opacity, transform;
  }
  :global(.scroll-step.is-visible) {
    opacity: 1;
    transform: translateY(0);
  }
</style>
