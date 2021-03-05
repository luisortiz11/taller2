<template>
  <a-layout id="components-layout-demo-fixed">
    <a-layout-header :style="{ position: 'fixed', zIndex: 1, width: '100%' }">
      <div class="logo" />
      <a-menu
        theme="dark"
        mode="horizontal"
        :default-selected-keys="['2']"
        :style="{ lineHeight: '64px' }"
      >
        <a-menu-item key="1">
          <NuxtLink to="/Productos"> Productos </NuxtLink>
        </a-menu-item>
        <a-menu-item key="2">
          <NuxtLink to="/Vacantes"> Vacantes </NuxtLink>
        </a-menu-item>
        <a-menu-item key="3">
          <NuxtLink to="/Login"> Login </NuxtLink>
        </a-menu-item>
      </a-menu>
    </a-layout-header>
    <a-layout-content :style="{ padding: '0 50px', marginTop: '64px'  }">

        <nuxt />

    </a-layout-content>
    <a-layout-footer :style="{ textAlign: 'center' }">
      Ant Design ©2018 Created by Ant UED
    </a-layout-footer>
  </a-layout>
</template>


<style>

</style>
