<template>
    <div id="viewport" class="flex flex-col p-4">
        <button class="bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 
        hover:border-blue-500 rounded" @click="initThreeJSScene">do something with threejs</button>
        <div id="threejs-container" class="py-5"></div>
    </div>

    <div id="viewport" class="flex flex-col p-4">
        <button class="bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 border-b-4 border-blue-700 
        hover:border-blue-500 rounded" @click="initRhinoScene">do something with rhino</button>
        <div id="rhino-container" class="py-5"></div>
    </div>




</template>

<script setup>
import { ref } from 'vue'
import * as THREE from 'three'
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls'
import { Rhino3dmLoader } from 'three/examples/jsm/loaders/3DMLoader'


// for threejs
let renderer = ref(null)
let camera = ref(null)
let scene = ref(null)
let controls = null


let width = 500
let heigh = 700

// for rhino vierwport
let rendererRH = null
let cameraRH = null
let sceneRH = null
let controlsRH = null

function initRhinoScene() {

    // rendeder
    rendererRH = new THREE.WebGLRenderer()
    rendererRH.setSize(width, heigh)
    rendererRH.setPixelRatio(window.devicePixelRatio)
    document.getElementById('rhino-container').appendChild(rendererRH.domElement)

    // camera
    cameraRH = new THREE.PerspectiveCamera(75, width / heigh, 0.1, 1000)
    cameraRH.position.set(0, -20, 40)

    // scene
    sceneRH = new THREE.Scene()
    sceneRH.background = new THREE.Color('#f5f6fa');


    // orbit controls
    controlsRH = new OrbitControls(cameraRH, rendererRH.domElement)

    const loader = new Rhino3dmLoader()
    loader.setLibraryPath( 'https://cdn.jsdelivr.net/npm/rhino3dm@0.15.0-beta/' );

    loader.load('https://files.mcneel.com/rhino3dm/models/RhinoLogo.3dm', function (object) {
        sceneRH.add(object)
    })

    animateRh()

}

function animateRh() {
    requestAnimationFrame(animateRh);
    controlsRH.update();
    rendererRH.render(sceneRH, cameraRH);
}


function initThreeJSScene() {

    // rendeder
    renderer = new THREE.WebGLRenderer()
    renderer.setSize(width, heigh)
    renderer.setPixelRatio(window.devicePixelRatio)
    document.getElementById('threejs-container').appendChild(renderer.domElement)

    // camera
    camera = new THREE.PerspectiveCamera(75, width / heigh, 0.1, 1000)
    camera.position.set(0, 0, 40)

    // scene
    scene = new THREE.Scene()
    scene.background = new THREE.Color('#f5f6fa');


    // orbit controls
    controls = new OrbitControls(camera, renderer.domElement)

    // geometry to the scene
    const geometry = new THREE.TorusKnotGeometry(8, 3, 150, 16)
    const material = new THREE.MeshNormalMaterial()
    const cube = new THREE.Mesh(geometry, material)
    scene.add(cube)

    animate()
}

function animate() {

    requestAnimationFrame(animate);
    controls.update();
    renderer.render(scene, camera);
}

</script>

<style scoped>
#viewport {
    border-style: dashed;
    border-color: #d2dfe8;
    border-width: 4px;
    border-radius: 10px;
    margin: 12px;
    height: calc(100vh - 105px);
    width: 600px;
    min-width: 200px;
}
</style>