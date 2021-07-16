# VOODO File Template
An Xcode file template that will create your view, observable object and data object all in one file with sample data. 

### You can then edit, delete or separate out parts if you want.

# How to Install
Add the VOODO.xctemplate to this directory: ~/Library/Developer/Xcode/Templates/File Templates/Custom/
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
        VStack {
            List(oo.data) { datum in
                Text(datum.name)
            }
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
import Combine
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
