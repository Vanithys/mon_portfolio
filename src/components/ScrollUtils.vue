<template>
</template>

<script>
export default {
  methods: {
    scrollTo(targetSelector, offset = 10, duration = 300) {
      const targetElement = document.querySelector(targetSelector);
      if (!targetElement) return;

      const headerHeight = document.querySelector('.header')?.offsetHeight || 0;
      const targetPosition = targetElement.getBoundingClientRect().top + window.pageYOffset - headerHeight - offset;
      const startPosition = window.pageYOffset;
      const distance = targetPosition - startPosition;
      let start = null;

      const step = (timestamp) => {
        if (!start) start = timestamp;
        const progress = timestamp - start;
        const scrollProgress = Math.min(progress / duration, 1);
        window.scrollTo(0, startPosition + distance * scrollProgress);

        if (progress < duration) {
          window.requestAnimationFrame(step);
        }
      };

      window.requestAnimationFrame(step);
    },

    scrollToTop() {
      this.scrollTo(0);
    },
  },
};
</script>