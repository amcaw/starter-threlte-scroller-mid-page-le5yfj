<script>
  import { T, useFrame } from '@threlte/core';
  import { Grid } from '@threlte/extras';
  import { tweened } from 'svelte/motion';
  import { cubicInOut } from 'svelte/easing';
  import { generateRingSteps } from '$lib/utils';
  import { injectLookAtPlugin } from '$lib/lookAt';
  
  export let index;
  export let stepCount;

  injectLookAtPlugin(); // Custom plugin to add `lookAt` prop to all <T> components

  let r = 0;
  let meshRef;
  const cameraPosition = tweened(null, { duration: 1000, easing: cubicInOut });

  useFrame((_, delta) => {
    r += 0.5 * delta;
  });

  // Predefined locations for camera movement
  const cameraSteps = [
    ...generateRingSteps(stepCount, 20)
  ];

  // Update camera position based on scroller index
  $: cameraPosition.set(cameraSteps[index] ?? cameraSteps[0]);
</script>

<T.PerspectiveCamera 
    makeDefault
    position.x={$cameraPosition.x}
    position.y={$cameraPosition.y}
    position.z={$cameraPosition.z}
    fov={55}
    lookAt={meshRef}
/>

<T.HemisphereLight color="#00ff00" groundColor="#0000ff" intensity={0.5}/>

<T.Mesh rotation.x={r} rotation.y={r} bind:ref={meshRef}>
  <T.SphereGeometry radius={1} widthSegments={32} heightSegments={32} />
  <T.MeshStandardMaterial color="#ffffff" />
</T.Mesh>

<Grid 
  infiniteGrid 
  fadeDistance={50} 
  cellColor="#ffffff"
  sectionColor="#ff0500"
/>
