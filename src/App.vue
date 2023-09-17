<template>
  <nav class="flex items-center justify-between flex-wrap bg-black/70 p-1">
    <div class="flex items-center flex-shrink-0 text-white mr-6">
      <img class="p-2 h-13" alt="Iaac logo" src="./assets/iaac-white.png">
      <h2 class="font-semibold text-xl tracking-tight">
        Digital Tools for Cloud-based Data Management
      </h2>
    </div>
  </nav>

  <h2>Moj tytul</h2>
  <nav class="flex">
    <Sidebar/>
  <GeometryView/>
  </nav>

 
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Sidebar from './components/Sidebar.vue'
import GeometryView from './components/GeometryView.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Sidebar,
    GeometryView
  }
}
</script>

<style>
:root {
  --sidebar-bg-color: #d0ddd7;
  --sidebar-item-hover: #a5ae9e;
  --sidebar-item-active: #A26769;
  --primary: #4ade80;
	--primary-alt: #22c55e;
	--grey: #64748b;
	--dark: #1e293b;
	--dark-alt: #334155;
	--light: #f1f5f9;

}

</style>
