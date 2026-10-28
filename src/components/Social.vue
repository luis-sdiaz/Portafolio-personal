<script setup lang="ts">
import Github from "./icons/Github.vue";
import Linkedin from "./icons/Linkedin.vue";
import Mail from "./icons/Mail.vue";
import X from "./icons/X.vue";
import ButtonRound from "./ButtonRound.vue";

const props = defineProps<{
  variant?: "theme" | "background";
}>();

const socialIcons = [
  { name: "Correo", icon: Mail },
  { name: "GitHub", icon: Github },
  { name: "LinkedIn", icon: Linkedin },
  { name: "X", icon: X },
] as const;
</script>

<template>
  <div class="social">
    <div v-for="item in socialIcons" :key="item.name" :aria-label="item.name" class="social-link">
      <ButtonRound
        renderAs="div"
        :variant="props.variant ?? 'theme'"
        class="children-unclickable"
      >
        <component :is="item.icon" aria-hidden="true" />
      </ButtonRound>
    </div>
  </div>
</template>

<style scoped lang="scss">
.social {
  display: flex;
  gap: var(--space-md);
}
</style>
