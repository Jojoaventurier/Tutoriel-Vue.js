<template>
    <div class="relative">
        <Transition name="fadeSlide" mode="out-in"> <!--Avec mode="out-in", on évite le petit décalage d'animation, la suivante commence quand la première est finie-->
            <slot></slot>
        </Transition>
<!--On a aussi appear :
    <Transition name="fadeSlide" appear>
        <slot></slot>
    </Transition>
-->
    </div>
</template>

<style>
.relative {
    position: relative;
}

.fadeSlide-enter-active,
.fadeSlide-leave-active {
    transition: .5s;
}

.fadeSlide-leave-active {
    position: absolute;
    width: 100%;
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