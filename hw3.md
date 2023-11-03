<h1>HW3</h1>
      
 ```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            TitleView()
            topView()
            
            HStack{
                MiddleView(imageName: "Bear")
                MiddleView(imageName: "Doll")
                MiddleView(imageName: "Car")
                /*TomatoView()
                BananaView()*/
            }
            bottomView()
        }
    }
}

struct TitleView: View {
    var body: some View {
        VStack(alignment:.center, spacing: 2){
            Text("Taco的")
                .font(.system(size:30))
            Text("玩具櫃")
                .font(.title)
                .foregroundColor(Color(red: 200/255, green: 40/255, blue: 200/255))
        }
    }
}

/*struct TomatoView: View {
    var body: some View {
        VStack(){
            Image("tomato")
                .resizable()
                .aspectRatio(contentMode:.fit)
                .frame(width: UIScreen.screenWidth/2-20, alignment: .center)
            Text("Tomato")
                .fontWeight(.bold)
                .font(.system(size: 30))
        }
    }
}

struct BananaView: View {
    var body: some View {
        VStack(){
            Image("banana")
                .resizable()
                .aspectRatio(contentMode:.fit)
                .frame(width: UIScreen.screenWidth/2-20, alignment: .center)
            Text("Banana")
                .fontWeight(.bold)
                .font(.system(size: 30))
        }.padding(.all, 2)
    }
}*/
struct MiddleView: View {
    var imageName: String
    var body: some View {
        VStack(){
            Image(imageName)
                .resizable()
                .aspectRatio(contentMode:.fit)
                .frame(height: 200, alignment:.center)
            Text(imageName.capitalized)
                .fontWeight(.bold)
                .font(.system(size: 25))
        }
        .frame(minWidth: 0, idealWidth: 100,
               maxWidth: .infinity, minHeight: 0,
               idealHeight: 100, maxHeight: .infinity,
               alignment: .center)
    }
}

struct bottomView: View {
    var body: some View {
        VStack(){
            Image("Dog")
                .resizable()
                .aspectRatio(contentMode:.fit)
                .padding(.all, 15)
            Text("Dog")
                .fontWeight(.bold)
                .font(.system(size: 30))
        }
    }
}

struct topView: View {
    var body: some View {
        VStack(){
            Image("Airplane")
                .resizable()
                .aspectRatio(contentMode:.fit)
                .padding(.all, 15)
            Text("Airplane")
                .fontWeight(.bold)
                .font(.system(size: 30))
        }
    }
}

extension UIScreen{
    static let screenWidth = UIScreen.main.bounds.size.width
    static let screenHeight = UIScreen.main.bounds.size.height
    static let screenSize = UIScreen.main.bounds.size
}




 ```

<img width="40%" src="https://raw.githubusercontent.com/chiuune87/yzu-swiftui-1091533/main/hw3.PNG">
