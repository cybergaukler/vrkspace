<script setup>
import { ref } from 'vue'

</script>

<template>
  <a-scene embedded style="width:100%; height:100%">
      <a-assets>
          <img id="branding" src="vrkspace/assets/branding.png">
          <!-- this gets generated by the vrkSpace server -->
          {{assetList}}
          <!-- place your own/ additional asset-items below -->
          <a-asset-item id="myPlant" src="vrkspace/myspace/plant.glb"></a-asset-item>
      </a-assets>
      <a-entity id="camera2DBox" position="0 0 5" rotation="-5 0 0">
          <a-camera id="camera2D" fov="20" active="true"></a-camera>
      </a-entity>
      <a-camera id="cameraVR" active="false">

      </a-camera>

      <!-- this spawns a random environment from the aframe-environment-component by feiss  -->
      {{environment}}

      <!-- if you want your own environment, just remove the line above. To just add your own object, place them as a-frame entities below-->
      <!--<a-entity gltf-model="#myPlant" shadow="" position="3 0.06 -2" scale="0.1 0.1 0.1" rotation="0 -60 0"></a-entity>-->
      <!--<a-video position="-0.8 1 -0.2" src="vrkspace/myspace/girl.mov" width="0.16" height="0.198" rotation="0 65 0"></a-video>-->

      <a-entity id="ambientLight" light="type: ambient; color:ffcc00; intensity: 0.6;"></a-entity>
      <!--<a-entity id="directionalLight" light="type: directional; intensity: 0.2; shadowCameraVisible: false;" position="-5 3 1.5"></a-entity>-->
      <a-entity id="directionalLight" light="type: spot; target:vrkspace; castShadow: true; intensity: 0.3; shadowCameraVisible: false;" position="3 2 2">
      </a-entity>

      <a-vrk-space id="vrkspace" theme="cybergaukler" controlScheme="HTCViveBasic">

          <!--hand controls including raycasters used for detecting interaction-->
          <a-entity id="vrkspace-leftHand" hand-controls="left">
              <a-box id="vrkspace-leftHand-fingertip"
                      depth="0.02" height="0.02" width="0.02"
                      position="0.035 0.01 -0.09"
                      color="blue"
                      raycaster="objects: .vrkspace-collisionArea; showLine: true; near: 0; far: 0.02"
              ></a-box>
              <a-box id="vrkspace-leftHand-palm"
                      depth="0.01" height="0.05" width="0.05"
                      position="0 -0.01 0.03"
                      rotation="-90 0 0"
                      color="blue"
                      raycaster="objects: .vrkspace-collisionArea; showLine: true; near: 0; far: 0.02"
              ></a-box>
          </a-entity>
          <a-entity id="vrkspace-rightHand" hand-controls="right">
              <a-box id="vrkspace-rightHand-fingertip"
                      depth="0.02" height="0.02" width="0.02"
                      position="-0.035 0.01 -0.09"
                      color="red"
                      raycaster="objects: .vrkspace-collisionArea; showLine: true; near: 0; far: 0.02"
              ></a-box>
              <a-box id="vrkspace-rightHand-palm"
                      depth="0.01" height="0.05" width="0.05"
                      position="0 -0.01 0.03"
                      rotation="-90 0 0"
                      color="red"
                      raycaster="objects: .vrkspace-collisionArea; showLine: true; near: 0; far: 0.02"
              ></a-box>
          </a-entity>

          <!--the virtual desk that will be aligned with your physical desk-->
          <a-vrk-desk>
              <a-vrk-grid>
                  <a-entity id="vrkspace-screenFront"
                            class="vrkspace-grid"
                            geometry="primitive: plane; width: 1; height:0.8; "
                            material="shader: html; fps:1; target: #vrkspace-backLayer; width:1280; height: 1024; alphaTest: 0.1"
                            position="0 1 -0.5"
                            rotation="-5 0 0"
                            visible="false">
                  </a-entity>
              </a-vrk-grid>
              <a-vrk-deskTop gltf-model = "#vrkSpaceDeskTop" shadow="receive: true" position="0 0.7 -0.5">
                  <a-entity gltf-model = "#vrkSpaceKeyboard" shadow="receive: true" position="0, 0.03, 0.36"></a-entity>
                  <a-vrk-browser isMain = "true" gltf-model = "#vrkSpaceBrowser" shadow="receive: true" position="0.10, 0.01, 0.12">
                      <a-entity class="vrkspace-collisionArea" id="vrkspace-browser-left" gltf-model = "#vrkSpaceBrowserAreaLeft"></a-entity>
                      <a-entity class="vrkspace-collisionArea" id="vrkspace-browser-right" gltf-model = "#vrkSpaceBrowserAreaRight"></a-entity>
                      <a-entity class="vrkspace-collisionArea" id="vrkspace-browser-front" gltf-model = "#vrkSpaceBrowserAreaFront"></a-entity>
                      <a-entity class="vrkspace-collisionArea" id="vrkspace-browser-inFront" gltf-model = "#vrkSpaceBrowserAreaInFront"></a-entity>
                      <a-entity class="vrkspace-collisionArea" id="vrkspace-browser-back" gltf-model = "#vrkSpaceBrowserAreaBack"></a-entity>
                      <a-entity class="vrkspace-collisionArea" id="vrkspace-browser-top" gltf-model = "#vrkSpaceBrowserAreaTop"></a-entity>
                      <a-entity id="vrkspaceBrowserIconWheel" model-opacity ="1"></a-entity>
                  </a-vrk-browser>
              </a-vrk-deskTop>
              <a-vrk-deskBack id="vrkspace-deskBack" gltf-model = "#vrkSpaceDeskBack"
                              shadow="receive: true"
                              position="0 -0.3 -0.5" >
                  <a-entity id="vrkspace-branding"
                            geometry="primitive: plane; height: 0.6; width: 0.6"
                            material="shader: flat; opacity:0.3; repeat:1; src: #branding; width:512; height: 512; alphaTest: 0.1"
                            position="0.06 1.65 0.01" >
                  </a-entity>
              </a-vrk-deskBack>
          </a-vrk-desk>
      </a-vrk-space>

      <!-- config items, only needed in 2d view to visualize initial setup -->
      <a-entity id="vrkspace-HTCViveBasicElements" visible="false">
          <a-entity gltf-model = "#vrkSpaceConfigViveLeft" shadow="receive: true" position="-0.5 0.75 0.01" rotation="85 0 -180"></a-entity>
          <a-entity gltf-model = "#vrkSpaceConfigViveRight" shadow="receive: true" position="0.5 0.75 0.01" rotation="85 0 180"></a-entity>
      </a-entity>

  </a-scene>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
