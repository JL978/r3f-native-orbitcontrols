# r3f-native-orbitcontrols

OrbitControls for React Three Fiber in React Native

## Example

```jsx
import useControls from "r3f-native-orbitcontrols"

function Canvas1() {
  const [OrbitControls, events] = useControls()

  const camera = new PerspectiveCamera()

  return (
    <Show {...events}>
      <Canvas camera={camera}>
        {/* you can set the camera here */}
        <OrbitControls camera={camera} />
      </Canvas>
    </Show>
  )
}

function Canvas2() {
  // or use the default camera
  const [OrbitControls, events, camera] = useControls()

  return (
    <Show {...events}>
      <Canvas camera={camera}>
        <OrbitControls />
      </Canvas>
    </Show>
  )
}

function Canvas3() {
  const [OrbitControls, events] = useControls()
  // or set the camera once the canvas is created
  const [camera, setCamera] = useState(null)

  return (
    <Show {...events}>
      <Canvas
        onCreated={(state) => {
          setCamera(state.camera)
        }}
      >
        <OrbitControls camera={camera} />
      </Canvas>
    </Show>
  )
}

function Canvases() {
  const [OrbitControls, events] = useControls()
  const [camera, setCamera] = useState(null)

  const orbitControls = () => <OrbitControls camera={camera} />

  // you also can use the same OrbitControls for multiple canvases
  // creating and effect like the game
  // The Medium (https://store.steampowered.com/app/1293160)

  return (
    <Show {...events}>
      <Canvas
        // in this case, the frameloop must be "always" (the default)
        onCreated={(state) => {
          setCamera(state.camera)
        }}
      >
        <orbitControls />
      </Canvas>
      <Canvas>
        <orbitControls />
      </Canvas>
    </Show>
  )
}
```

## Options

The `<OrbitControls />` element _may_ receive the following properties:

| Property        |       Type        |                                     Description |
| :-------------- | :---------------: | ----------------------------------------------: |
| camera          | PerspectiveCamera |                                                 |
| enabled         |      boolean      |                                                 |
| target          |      Vector3      |                                                 |
| minDistance     |      number       |                                                 |
| maxDistance     |      number       |                                                 |
| minZoom         |      number       |                                                 |
| maxZoom         |      number       |                                                 |
| minPolarAngle   |      number       |              how close you can orbit vertically |
| maxPolarAngle   |      number       |                how far you can orbit vertically |
| minAzimuthAngle |      number       |            how close you can orbit horizontally |
| maxAzimuthAngle |      number       |              how far you can orbit horizontally |
| dampingFactor   |      number       |                                  inertia factor |
| enableZoom      |      boolean      |                                                 |
| zoomSpeed       |      number       |                                                 |
| enableRotate    |      boolean      |                                                 |
| rotateSpeed     |      number       |                                                 |
| enablePan       |      boolean      |                                                 |
| panSpeed        |      number       |                                                 |
| onChange        |  (event) => void  | receives an event with all the properties above |
