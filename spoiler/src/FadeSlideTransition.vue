<template>
    <Transition name="fadeSlide" mode="out-in"> <!--Avec mode="out-in", on évite le petit décalage d'animation, la suivante commence quand la première est finie-->
        <slot></slot>
    </Transition>
</template>

<style>
.fadeSlide-enter-active,
.fadeSlide-leave-active {
    transition: .5s;
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