# [swiftui/view/task(priority:_:)](https://developer.apple.com/documentation/swiftui/view/task(priority:_:))

In SwiftUI, you can use the .task modifier to add an asynchronous task that will be performed before a view appears on the screen. This is useful for fetching data or performing any other asynchronous operation that needs to be completed before the view is fully rendered.
Here's an example of using the .task modifier to perform an asynchronous task before a view appears:

```
import SwiftUI

struct ContentView: View {
    @State private var data: String = ""

    var body: some View {
        Text(data)
            .padding()
            .task {
                await fetchData()
            }
    }

    func fetchData() async {
        // Simulating an asynchronous operation
        await Task.sleep(2 * 1_000_000_000)

        // Update the UI on the main queue
        DispatchQueue.main.async {
            data = "Data fetched successfully"
        }
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}
```

In this example, the .task modifier is applied to the Text view. Inside the .task closure, we call the fetchData function asynchronously.
The fetchData function simulates an asynchronous operation using Task.sleep to pause the task for 2 seconds. After the operation completes, we update the UI by assigning the fetched data to the data state variable.
When the view appears on the screen, SwiftUI automatically triggers the asynchronous task specified by the .task modifier.
By using the .task modifier, you can ensure that the asynchronous task is performed before the view appears, allowing you to fetch data or perform any other necessary operations before the view is fully rendered.



## Reference
- [How to run tasks using SwiftUI’s task() modifier](https://www.hackingwithswift.com/quick-start/concurrency/how-to-run-tasks-using-swiftuis-task-modifier)
