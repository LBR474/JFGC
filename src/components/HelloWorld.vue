<script setup lang="ts">
import { shallowRef, Ref, ref } from 'vue';
import { TresCanvas, useRenderLoop, TresObject3D } from '@tresjs/core';
import { OrbitControls } from '@tresjs/cientos';

import { useLoader } from '@tresjs/core'
//@ts-ignore

import { GLTFLoader } from 'three/addons/loaders/GLTFLoader'

const { scene } = await useLoader(GLTFLoader, '/tree_also.glb')

const boxRef: Ref<TresObject3D | null> = ref(null);

const { onLoop } = useRenderLoop();



onLoop(({ delta, elapsed }) => {
  if (boxRef.value) {
    boxRef.value.rotation.y += delta;
    //boxRef.value.rotation.z = elapsed * 0.2;
  }
});
</script>

<template>
  <TresCanvas clear-color="#82DBC5" shadows alpha window-size>
    <OrbitControls />
      <TresPerspectiveCamera
        :position="[1, 2, 5]"
        :fov="45"
        :aspect="1"
        :near="0.1"
        :far="1000"
      />
      <TresDirectionalLight
        ref="directionalRef"
        :args="['white', 1]"
        :position="[-2, 4, 0]"
      />
     
      <primitive :object="scene" :scale="0.1" ref="boxRef"
      :position="[0, -1, 0]"
      />

      
      <!-- <TresMesh ref="boxRef" :scale="1" cast-shadow>
        <TresBoxGeometry :args="[1, 1, 1]" />
        <TresMeshNormalMaterial />
      </TresMesh> -->
  </TresCanvas>
  
</template>