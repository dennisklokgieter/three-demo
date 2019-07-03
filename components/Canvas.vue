<template>
  <div id="canvas"></div>
</template>

<style >
#canvas {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
</style>


<script>
import * as THREE from "three";
import { GLTFLoader } from "three/examples/jsm/loaders/GLTFLoader.js";

export default {
  mounted: function() {
    this.canvas();
  },
  methods: {
    canvas() {
      var container;
      var camera, scene, renderer;
      var geometry, material, mesh;

      init();
      animate();

      function init() {
        camera = new THREE.PerspectiveCamera(
          70,
          window.innerWidth / window.innerHeight,
          0.01,
          10
        );
        camera.position.z = 1;

        scene = new THREE.Scene();

        // geometry = new THREE.BoxGeometry(0.2, 0.2, 0.2);

        // material = new THREE.MeshNormalMaterial();

        // mesh = new THREE.Mesh(geometry, material);
        // scene.add(mesh);

        //gltf

        const loader = new GLTFLoader();
        // Load a glTF resource
        loader.load(
          // resource URL
          "Duck.gltf",
          // called when the resource is loaded
          function(gltf) {
            scene.add(gltf.scene);
          }
        );
        // renderer

        container = document.getElementById("canvas");
        document.body.appendChild(container);

        renderer = new THREE.WebGLRenderer({ antialias: true });
        renderer.setSize(window.innerWidth, window.innerHeight);
        container.appendChild(renderer.domElement);
      }

      function animate() {
        // requestAnimationFrame(animate);

        // mesh.rotation.x += 0.01;
        // mesh.rotation.y += 0.02;

        renderer.render(scene, camera);
      }
    }
  }
};
</script>

