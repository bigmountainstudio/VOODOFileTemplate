# VOODO File Template
An Xcode file template that will create your view, observable object, and data object all in one file with sample data.

### You can then edit, delete or separate out parts if you want.

⚠️ Note: This template uses `ObservableObject`.

👉For the `@Observable` template, go [here](https://github.com/bigmountainstudio/VOODOFileTemplate2).

# How to Install
Add the VOODO.xctemplate to this directory: 
`~/Library/Developer/Xcode/Templates/File Templates/Custom/`

*(Click your home directory and then show hidden folders with COMMAND+SHIFT+. )*

*Note: That full directory might not even exist so you will have to create it.*

# In Xcode
1. Start Xcode and add a new file.
1. Scroll down until you see the **Custom** section and select VOODO:
![image](https://user-images.githubusercontent.com/24855856/125980564-a21fc5f1-d0f3-4405-b3a9-85375634b02b.png)

# Example Output
```swift
// View
import SwiftUI

struct PersonView: View {
    @StateObject private var oo = PersonOO()
    
    var body: some View {
        List(oo.data) { datum in
            Text(datum.name)
        }
        .onAppear {
            oo.fetch()
        }
    }
}

struct Person_Previews: PreviewProvider {
    static var previews: some View {
        PersonView()
    }
}

// Observable Object
import SwiftUI

class PersonOO: ObservableObject {
    @Published var data: [PersonDO] = []
    
    func fetch() {
        data = [PersonDO(name: "Datum 1"),
                PersonDO(name: "Datum 2"),
                PersonDO(name: "Datum 3")]
    }
}

// Data Object
import Foundation

struct PersonDO: Identifiable {
    let id = UUID()
    var name: String
}
```

# Preview
![preview](https://user-images.githubusercontent.com/24855856/125980957-fd972bfe-daac-4ac7-8b3e-a68a96f53210.png)

# You Are In Control
From here, you can:
* Delete what you don't need
* Keep all the parts in one file
* Break out the parts into separate files
* Change the template to use any naming convention you want

# Resources
For more information on this architecture and how to work with data in SwiftUI, take a look at this book: **Working with Data in SwiftUI**.

![working with data in swiftui](https://user-images.githubusercontent.com/24855856/125804293-5f4ec808-220d-41a7-b1ce-9caebc06069e.png)

[Learn More](https://www.bigmountainstudio.com/data)

