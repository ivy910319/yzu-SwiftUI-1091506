<h1>HW2</h1>
      
 ```swift
import SwiftUI
var pss = ["剪刀","石頭","布"]
struct ContentView: View {
    @State var randomInt = Int.random(in: 0...2)
    var body: some View{
        VStack{
            Text(pss[randomInt]) 
                //.padding(.all,10)
                .frame(width:300,height:200,alignment:.center)
                .font(.system(size:80))
            Button(action: {
                randomInt = Int.random(in: 0...2)
            }, label: {
                Text("Go")
                    .padding(.all,10)
                    .frame(width: 300, height: 100, alignment:.center)
                    .font(.system(size:50))
                    .background(Color.purple)
                    .foregroundColor(.white)
                    .border(Color.purple, width: 5)
                    .cornerRadius(20)
            })
        }
    }
}



 ```

[![hw2](https://res.cloudinary.com/marcomontalbano/image/upload/v1698568341/video_to_markdown/images/youtube--7u11M1IPeVY-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/7u11M1IPeVY?si=wZjCVwvCSo7oD9qg "hw2")
