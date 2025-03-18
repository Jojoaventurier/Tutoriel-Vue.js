<template>
    <Transition name="fadeSlide">
        <slot></slot>
    </Transition>
</template>

<style>
.fadeSlide-enter-active,
fadeSlide-leave-active {
    transition: .5;
}

.fadeSlide-enter-from {
  opacity: 0;
  transform: translateX(10px);
}

.fadeSlide-leave-to {
  opacity: 0;
  transform: translateX(-10px);
}
</style>