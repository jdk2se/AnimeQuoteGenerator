<template>
  <section class="quote">
    <div class="quote__content">
      {{ quote.content }}
    </div>
    <div class="quote__info">
      <div class="quote__anime">
        {{ quote.anime }}
      </div>
      <div class="quote__author">
        {{ quote.character }}
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ['quote']
}
</script>

<style lang="scss" scoped>
.quote {
  position: relative;
  margin: 0 auto;
  padding: 32px;
  max-width: 720px;

  &__content {
    position: relative;
    font-size: 29px;
    font-weight: 600;
    background-color: var(--dark);
    color: var(--light);
    padding: 48px 32px;
    border-radius: 16px;

    &:before, &:after {
      content: '"';
      color: var(--grey);
      margin: 0 2px;
    }
  }

  &__info {
    position: absolute;
    top: 0;
    left:0;
    right: 0;
    bottom: 0;
    padding: 32px;
  }

  &__author, &__anime {
    position: absolute;
    padding: 12px 16px;
    font-size: 24px;
    font-weight: 700;
    border-radius: 99px;
    color: var(--light);
  }

  &__author {
    top: calc(100% - 32px);
    right: 0;
    transform: translateY(-50%);
    background-color: var(--secondary);
  }

  &__anime {
    top: 0;
    left: 0;
    background-color: var(--tertiary);
    color: var(--dark);
  }
}
</style>
