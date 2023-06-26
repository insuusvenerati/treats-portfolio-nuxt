<template>
  <div class="m-4">
    <div class="mr-4 float-left sticky top-4">
      <nav
        style="background-image: url(/images/sidebar-bg.png)"
        class="float-left w-96 p-4 text-black rounded-md h-96">
        <ul>
          <li>
            <a href="/">bg</a>
          </li>
          <li>
            <a href="/about">sketchbook</a>
          </li>
          <li>
            <a href="/contact">contact</a>
          </li>
        </ul>
      </nav>
    </div>
    <slot />
  </div>
</template>
