# RealityKit-import-multiple-models-
RealityKit SwiftUI import multiple models
# The first part
![IMG_0143](https://github.com/S-way520/RealityKit-import-multiple-models-/assets/95877651/8d621c4a-2e45-4752-8efa-7f400b636e99)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import RealityKit
struct ContentView: View {
    var body: some View {
        ARViewContainer()
            .edgesIgnoringSafeArea(.all)
    }
}
struct ARViewContainer: UIViewRepresentable {
    func makeUIView(context: UIViewRepresentableContext<ARViewContainer>) -> ARView {
        let arView = ARView(frame: .zero)
        let anchorEntity = AnchorEntity(plane: .horizontal)
        guard let toyEntity = try? Entity.load(named: "toy_biplane_idle"),
              let tutorialEntity = try? Entity.load(named: "tutorial") else {
            fatalError("models is not!")
        }
        anchorEntity.addChild(toyEntity)
        anchorEntity.addChild(tutorialEntity)
        arView.scene.addAnchor(anchorEntity)
        return arView
    }
    func updateUIView(_ uiView: ARView, context: Context) {}
}
```
