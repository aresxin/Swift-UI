# [swiftui/view/id(_:)](https://developer.apple.com/documentation/swiftui/view/id(_:))


In SwiftUI, the List view is used to display a collection of views in a scrollable list. The ForEach view is commonly used within a List to iterate over a collection and generate a view for each element.
When using ForEach, you can specify an id parameter to uniquely identify each element in the collection. This helps SwiftUI track changes and update the views efficiently when the collection changes.
Here's an example of using List and ForEach with an id parameter in SwiftUI:


```
struct ContentView: View {
    struct Item: Identifiable {
        let id: UUID
        let name: String
    }
    
    let items = [
        Item(id: UUID(), name: "Item 1"),
        Item(id: UUID(), name: "Item 2"),
        Item(id: UUID(), name: "Item 3")
    ]
    
    var body: some View {
        List {
            ForEach(items, id: \.id) { item in
                Text(item.name)
            }
        }
    }
}

```

In this example, we define a ContentView that contains a list of Item structures. Each Item has an id and a name. We then use ForEach to iterate over the items array, specifying .id as the id parameter to uniquely identify each Item based on the id property.
Within the ForEach closure, we create a Text view for each Item in the array, displaying its name.
By providing the id parameter to ForEach, SwiftUI can efficiently update the views when the collection changes. It helps SwiftUI identify which elements need to be added, removed, or modified in the view hierarchy.
Feel free to customize the Item structure and the view hierarchy within the ForEach to suit your specific needs.

---

In SwiftUI, the List view and the ForEach view work together to efficiently manage the reuse of views. When using ForEach within a List, SwiftUI automatically handles view recycling and reuse to optimize memory usage and scrolling performance.
The ForEach view generates a view for each element in a collection. SwiftUI reuses the generated views as much as possible by updating the view's content with the new data when the collection changes.
Here's an example to demonstrate how SwiftUI handles view reuse with List and ForEach:


```
struct ContentView: View {
    let items = ["Item 1", "Item 2", "Item 3"]
    
    var body: some View {
        List {
            ForEach(items, id: \.self) { item in
                Text(item)
            }
        }
    }
}

```

In this example, we have a simple array of strings called items. We use ForEach to iterate over the items array and generate a Text view for each element. The id: \.self parameter tells SwiftUI to use the item itself as the identifier for view reuse.
When the items array changes (e.g., items are added, removed, or modified), SwiftUI efficiently updates the views by reusing existing views whenever possible. This recycling of views helps improve performance and reduce memory usage.
It's important to note that SwiftUI performs view reuse based on the identifier specified using the id parameter. By default, SwiftUI uses the Equatable protocol to determine whether an element has changed. If an element's identifier remains the same, SwiftUI assumes the content of the view for that element hasn't changed and reuses the existing view.
Therefore, it's recommended to provide a unique identifier for each element in the collection to ensure proper view recycling and avoid unexpected behavior.
Feel free to customize the items array and the view hierarchy within the ForEach to fit your specific requirements. SwiftUI will handle the view reuse automatically, allowing you to focus on building your UI.


## Reference
- [How to identify objects when using SwiftUI's List and ForEach](https://tanaschita.com/20211014-identify-foreach-list-swiftui/)
- [SwiftUI之id(_)如何标识View](https://zhuanlan.zhihu.com/p/150958669)