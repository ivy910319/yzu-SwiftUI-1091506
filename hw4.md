<h1>HW1</h1>
      
 ```swift
import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Text("")
            Text("🥤台灣手搖飲料推薦🥤")
                .font(.largeTitle)
                .fontWeight(.heavy)
                .foregroundStyle(.primary)
                
            TabView{
                Group{
                    WelcomeView()
                        .tabItem{
                            Image(systemName: "homekit")
                            Text("Welcome")
                        }
                    CourseListView()
                        .tabItem{
                            Image(systemName: "star.square")
                            Text("Menu")
                        }
                    CardView()
                        .tabItem{
                            Image(systemName: "star.square.on.square")
                            Text("let's drink")
                        }
                }
                .toolbarBackground(Color.black, for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)
            }
            .tint(.yellow)
        }
    }
}

/*這是WelcomeView*/

import SwiftUI

struct WelcomeView: View {
    var body: some View {
        VStack {
            Image("Welcome")
                .resizable()
                .scaledToFit()
            //Text("🐸")
            //    .font(.system(size: 250))
            Text("點擊下方選單到下一頁")
                .font(.system(size: 15, weight: .bold, design: .rounded))
                .lineSpacing(10)
                .foregroundStyle(.white)
                .multilineTextAlignment(.center)
            Text("")
        }.padding(.top, 20)
    }
}

/*這是CourseListView*/

import SwiftUI

struct Course:Identifiable{
    var id = UUID()
    var name:String
    var image:String
    var description:String
}

var courses = [
    Course(name:"八曜和茶", image:"1", description: "推薦🥤：\n1.柚香覺醒307\n2.和風307\n3.炙燒濃乳308\n4.八曜和茶\n5.83蜂見茶"),
    Course(name:"一沐日", image:"2", description: "推薦🥤：\n1.油切蕎麥茶＋粉粿\n2.逮丸奶茶\n3.粉粿桂花檸檬\n4.粉粿黑糖檸檬\n5.荔枝烏龍"),
    Course(name:"上宇林", image:"3", description: "推薦🥤：\n1.青龍茗茶\n2.美人鮮奶茶＋粉角\n3.雪浮奶美人/雪浮奶綠\n4.鐵觀音鮮奶茶\n5.手工粉角鮮奶茶"),
    Course(name:"鶴茶樓", image:"4", description: "推薦🥤：\n1.金萱青茶\n2.鶴頂紅茶\n3.青檸蘭香綠茶+蘆薈\n4.桂花烏龍茶\n5.藝伎那堤"),
    Course(name:"萬波", image:"5", description: "推薦🥤：\n1.黑糖珍珠鮮奶\n2.芋圓茉香奶茶\n3.紅蘋島嶼\n4.紅豆粉粿鮮奶\n5.蘭葉那堤"),
]

struct BasicImageRow: View{
    var thisCourse:Course
    var body: some View {
        HStack{
            Image(thisCourse.image)
                .resizable()
                .frame(width: 40, height: 40)
                .cornerRadius(5)
            Text(thisCourse.name)
        }
    }
}


struct CourseDetailView:View{
    @Environment(\.presentationMode) var presentationMode
    var thisCourse:Course
    var body: some View{
        ScrollView{
            VStack{
                Image(thisCourse.image)
                    .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisCourse.name)
                    .font(.system(.title, design: .rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisCourse.description)
                    .font(.system(.subheadline, design:.rounded))
                    .fontWeight(.light)
                Spacer()
            }
        }
        .overlay{
            HStack{
                Spacer()
                VStack{
                    Button(action:{
                        self.presentationMode.wrappedValue.dismiss()
                    },label: {
                        Image(systemName: "chevron.down.circle.fill")
                            .font(.largeTitle)
                            .foregroundColor(.white)
                    })
                    .padding(.trailing, 20)
                    .padding(.top, 40)
                    Spacer()
                }
            }
        }
    }
}

struct CourseListView: View {
    @State var showDetailView = false
    @State var selectedCourse:Course?
    var body: some View {
        NavigationView{
            List(courses){
                courseItem in
                BasicImageRow(thisCourse: courseItem)
                    .onTapGesture {
                        self.showDetailView = true
                        self.selectedCourse = courseItem
                    }
            }
            .sheet(item: self.$selectedCourse){ thisCourse in
                CourseDetailView(thisCourse: thisCourse)
            }
            .navigationBarTitle("菜單")
        }
    }
}

/*這是CardView*/

import SwiftUI

let imageArray:Array = [
    "11",
    "22",
    "33",
    "44",
    "55"
]

struct TermAndDescription: Identifiable{
    var id = UUID()
    var term:String
    var description:String
}
var myDictionary = [
    TermAndDescription(term: "八曜和茶", description: ""),
    TermAndDescription(term: "一沐日", description: ""),
    TermAndDescription(term: "上雨林", description: ""),
    TermAndDescription(term: "鶴茶樓", description: ""),
    TermAndDescription(term: "萬波", description: ""),
]
struct CardView: View{
    @State var currentCard = Int.random(in: 0...4)
    //@State var currentCard = 0
    var body: some View{
        VStack{
            VStack{
                Text(myDictionary[currentCard].term)
                    .font(.title)
                    .padding(.all, 10)
                /*Text(myDictionary[currentCard].description)
                    .font(.body)
                    .foregroundColor(.blue)
                    .padding(.all, 10)*/
                Image(imageArray[currentCard])
                    .resizable()
                    .scaledToFit()
                Text("")
            }
            .frame(minWidth: 0, idealWidth: 100, maxWidth: 300, minHeight: 0,idealHeight: 100, maxHeight: 300, alignment: .center)
            .background(Color.gray)
            .onTapGesture {
                currentCard = Int.random(in: 0...4)
                /*if currentCard<myDictionary.count-1{
                    currentCard+=1
                }else{
                    currentCard=0
                }*/
            }
            Text("點擊抽取今天喝什麼")
                .padding(.all, 10)
        }
    }
}


 ```

