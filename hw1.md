<h1>HW1</h1>
      
 ```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        Image("Taco")
            .resizable()
            .scaledToFill()
            //.aspectRatio(contentMode: .fill)
            .overlay(
                Text("1091506張筠婷")
                    .fontWeight(.bold)
                    .foregroundColor(.purple)
                    .font(.system(size: 20))
                    .position(x:250,y:500)
            )
            .overlay(
                Text("To attempt the impossible.")
                    .fontWeight(.heavy)
                    .lineSpacing(20)
                    .font(.system(size: 32.0))
                    .foregroundColor(.white)
                    .frame(width: 350, height: 150 , 
                           alignment: .center)
                    .background(Color.gray)
                    .cornerRadius(30.0)
                    .opacity(0.8)
                 ,
                 alignment: .bottom
            )
            .overlay(
                Image(systemName: "face.smiling.fill")
                    .font(.system(size:50))//260
                    .foregroundColor(.white)
                    .shadow(color: .gray, radius: 5, x: 5, y:5)
                    .position(x:350,y:275)//210
            )
    
    }
}




 ```

<img width="40%" src="https://raw.githubusercontent.com/ivy910319/yzu-SwiftUI-1091506/main/IMG_0832.png">
