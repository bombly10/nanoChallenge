# nanoChallenge
First Challenge Nankurunaisa

import SwiftUI
import PlaygroundSupport
import CoreGraphics
import Darwin


struct Slide1: View {
    @State var scale = 0.60

    
    var body: some View {
        VStack {
            ZStack {
                Spacer()
                Image(uiImage: UIImage(named: "shool.png")!)
                    .resizable()
                    .scaledToFit()
                    .aspectRatio(contentMode: .fill)
                    .position(x:200,y:230)
                
               VStack {
                   Text("A FAMOUS SCHOOL")
                       .font(.system(size: 45, weight: .heavy, design: .rounded))
                       .padding(.top)
                       .foregroundColor(Color.white)
                       .frame(width: 300)
                       .scaledToFit()
                       .lineLimit(5)
                       .position(x:200,y:90)
                       .scaleEffect(scale)
                       .animation(Animation.easeInOut(duration: 3).repeatForever(autoreverses: true).speed(4))
                       
                   
                    }
               .onAppear(perform: {
                   route()
               })
                
                
               }
            
            Button {
             PlaygroundPage.current.setLiveView(Slide2())
         
             }
             label: {
                 Text("Start")
                     
                     .font(.system(size: 30, weight: .heavy, design: .rounded))
                     .padding(.all)
                     .foregroundColor(.black)
                     .background(Color.white)
                     .cornerRadius(20)
                     .frame(width: 150, height: 50 ,alignment: .center )
                     .scaledToFit()
                     
             }.position(x:200,y:240)
           
         
            
        }
        .frame(width: 400, height: 650)
        .background(Color.black)
    
    }
    func route () {
        
     
        scale = 1
       
        
    }

}

//PlaygroundPage.current.setLiveView(Slide1())



struct Slide2: View {
    @State var scale = 2.0
    @State var rotation = false
    @State var screenText: String = ""
    @State var characterLoopIndex: Int = -1
    @State var positionX = 300
    @State var positionY = 518
    
    let finaltext = "This is a story about a School where the students will surely all be famous , but now they are just students.In an ordinary day Apple was going at school as the other students."
    let loopDuration: Double = 0.08
    var body: some View {
        VStack{
            ZStack {
                Spacer()
                Image(uiImage: UIImage(named: "shool.png")!)
                    .resizable()
                    .scaledToFit()
                    .frame(width: 400, height: 600)
                    //.padding()
                    //.aspectRatio(contentMode: .fill)
                    .position(x: 200, y: 220)
                    
                    VStack {
                            Text(screenText)
                            .foregroundColor(.white)
                            .frame(width:300,alignment: .leading)
                            .font(.system(size: 20, weight: .heavy, design: .rounded))
                            .scaledToFit()
                            .padding(.top)
                            .position(x: 200 , y: 100)
                    }
                            Image(uiImage: UIImage(named: "Apple.png")!)
                                .resizable()
                                .scaledToFit()
                                .aspectRatio(contentMode: .fit)
                                .frame(width: 250, height: 250)
                                .position(x: CGFloat(positionX),y: CGFloat(positionY) )
                                .animation(.linear(duration: 8).delay(2),value:positionX)
                                .animation(.linear(duration: 9).delay(1),value:positionY)
                                .scaleEffect(scale)
                                .animation(
                                    .linear(duration: 7).delay(2),
                                    value: scale)
                                
                
                }
            
            
            Button {
                PlaygroundPage.current.setLiveView(Slide3())

                }
            label:{
                    Image(uiImage: UIImage(named: "freccia")!)
                .resizable()
                .scaledToFit()
                    .foregroundColor(.black)
                    .background(Color.white)
                    .cornerRadius(15)
                    //.frame(width: 50, height: 50)
                    //.position(x: 200, y:50)
                }.frame(width: 50, height: 50)
                .position(x: 200, y:250)
        }
        .frame(width: 400, height: 650)
        .background(Color.black)
        .onAppear(perform: {
            startCharacterAnimation()
            route()
        })
    }
    
    func route () {
        
        positionX -= 50
        positionY -= 1
        scale = 0.5
       
        
    }
    
    func startCharacterAnimation() {
        let timer = Timer.scheduledTimer(withTimeInterval: loopDuration, repeats: true) { (timer) in
            
            characterLoopIndex += 1
            
            if characterLoopIndex >= finaltext.count {
                timer.invalidate()
            }
            screenText = screenText + finaltext[characterLoopIndex]
        }
        timer.fire()
    }
    
}




struct Slide3: View {
    @State var scale = 0.60
    @State var rotation = false
    @State var screenText: String = ""
    @State var characterLoopIndex: Int = -1
    
    let finaltext = "He had a lot of friends, like his competitor Android who tried to have better marks than him (sometimes cheating),Sony who was always alone and Google, the one who was a friend to all."
    let loopDuration: Double = 0.08
    var body: some View {
        VStack{
            ZStack {
                Spacer()
                Image(uiImage: UIImage(named: "Tutti_in_classe.png")!)
                    .resizable()
                    .scaledToFit()
                   // .frame(width: 400, height: 600)
                    //.padding()
                    .aspectRatio(contentMode: .fill)
                    .position(x: 200, y: 420)
                    
                    VStack {
                            Text(screenText)
                            .foregroundColor(.white)
                            .frame(width:270,alignment: .leading)
                            .font(.system(size: 20, weight: .heavy, design: .rounded))
                            .scaledToFit()
                            .padding(.top)
                            .position(x: 150 , y: 130)
                    }
                            
                }
            
            Button {
                PlaygroundPage.current.setLiveView(Slide4())
                }
            label:{
                    Image(uiImage: UIImage(named: "freccia")!)
                .resizable()
                .scaledToFit()
                    .foregroundColor(.black)
                    .background(Color.white)
                    .cornerRadius(15)
                    //.frame(width: 50, height: 50)
                    //.position(x: 200, y:50)
                }.frame(width: 50, height: 50)
                .position(x: 200, y:250)
        }
        .frame(width: 400, height: 650)
        .background(Color.black)
        .onAppear(perform: {
            startCharacterAnimation()
        })
    }
    
    func startCharacterAnimation() {
        let timer = Timer.scheduledTimer(withTimeInterval: loopDuration, repeats: true) { (timer) in
            
            characterLoopIndex += 1
            
            if characterLoopIndex >= finaltext.count {
                timer.invalidate()
            }
            screenText = screenText + finaltext[characterLoopIndex]
        }
        timer.fire()
    }
    
}

//PlaygroundPage.current.setLiveView(Slide3())

struct Slide4: View {
    @State var scale = 2.0
    @State var rotation = false
    @State var screenText: String = ""
    @State var characterLoopIndex: Int = -1
    @State var positionX = 300
    @State var positionY = 520
    
    let finaltext = "One day arrived a new student, his name was Huawei."
    let loopDuration: Double = 0.08
    var body: some View {
        VStack{
            ZStack {
                Spacer()
                Image(uiImage: UIImage(named: "shool.png")!)
                    .resizable()
                    .scaledToFit()
                    .aspectRatio(contentMode: .fill)
                    .position(x: 200, y: 190)
                    
                    VStack {
                            Text(screenText)
                            .foregroundColor(.white)
                            .frame(width:300,alignment: .leading)
                            .font(.system(size: 20, weight: .heavy, design: .rounded))
                            .scaledToFit()
                            .padding(.top)
                            .position(x: 200 , y: 65)
                    }
                            Image(uiImage: UIImage(named: "Huawei.png")!)
                    .resizable()
                    .scaledToFit()
                    .aspectRatio(contentMode: .fit)
                    .frame(width: 250, height: 250)
                    .position(x: CGFloat(positionX),y: CGFloat(positionY) )
                    .animation(.linear(duration: 8).delay(2),value:positionX)
                    .animation(.linear(duration: 9).delay(1),value:positionY)
                    .scaleEffect(scale)
                    .animation(
                        .linear(duration: 7).delay(2),
                        value: scale)
                
                }
            
            Button {
                PlaygroundPage.current.setLiveView(Slide5())

                }
            label:{
                    Image(uiImage: UIImage(named: "freccia")!)
                .resizable()
                .scaledToFit()
                    .foregroundColor(.black)
                    .background(Color.white)
                    .cornerRadius(15)
                }.frame(width: 50, height: 50)
                .position(x: 200, y:250)
            
        }
        .frame(width: 400, height: 650)
        .background(Color.black)
        .onAppear(perform: {
            startCharacterAnimation()
            route()
        })
    }
    
    func route () {
        
        positionX -= 50
        scale = 0.5
        
       
        
    }
    
    func startCharacterAnimation() {
        let timer = Timer.scheduledTimer(withTimeInterval: loopDuration, repeats: true) { (timer) in
            
            characterLoopIndex += 1
            
            if characterLoopIndex >= finaltext.count {
                timer.invalidate()
            }
            screenText = screenText + finaltext[characterLoopIndex]
        }
        timer.fire()
    }
    
}

//PlaygroundPage.current.setLiveView(Slide4())



struct Slide5: View {
    @State var scale = 0.75
    @State var rotation = false
    @State var screenText: String = ""
    let finaltext = "In a short time he attracted too much attention making the other students jealous. The teachers thought that he was a smart and promising student."
    @State var characterLoopIndex: Int = -1
    let loopDuration: Double = 0.08

    var body: some View {
        VStack{
            ZStack {
                Spacer()
                Image(uiImage: UIImage(named: "In_classe_Huawei.png")!)
                    .resizable()
                    .scaledToFit()
                    .aspectRatio(contentMode: .fill)
                    .position(x: 200, y: 420)
                    
                    VStack {
                       
                        Text(screenText)
                            .foregroundColor(.white)
                            .frame(width:320,alignment: .leading)
                            .font(.system(size: 20, weight: .heavy, design: .rounded))
                            .scaledToFit()
                            .position(x: 200, y:80)
                            .padding(.top)
                        
                          
                }
            }
                .onAppear(perform: {
                    startCharacterAnimation()
                })
            
            Button {
                PlaygroundPage.current.setLiveView(Slide6())

                }
            label:{
                    Image(uiImage: UIImage(named: "freccia")!)
                .resizable()
                .scaledToFit()
                    .foregroundColor(.black)
                    .background(Color.white)
                    .cornerRadius(15)
                    //.frame(width: 50, height: 50)
                    //.position(x: 200, y:50)
                }.frame(width: 50, height: 50)
                .position(x: 200, y:250)
        }.frame(width: 400, height: 650)
            .background(Color.black)
      
        
        
    }
    func startCharacterAnimation() {
        let timer = Timer.scheduledTimer(withTimeInterval: loopDuration, repeats: true) { (timer) in
            
            characterLoopIndex += 1
            
            if characterLoopIndex >= finaltext.count {
                timer.invalidate()
            }
            screenText = screenText + finaltext[characterLoopIndex]
        }
        timer.fire()
    }
}

PlaygroundPage.current.setLiveView(Slide5())



struct Slide6: View {
    @State var progressValue: Float = 0.2
    @State var screenText: String = ""
    let finaltext = "But the truth was that Huawei had bad behaviours, like stealing Google’s Stuff."
    @State var characterLoopIndex: Int = -1
    let loopDuration: Double = 0.08

    var body: some View {
        
        VStack{
            ZStack {
                Spacer()
                Image(uiImage: UIImage(named: "Ladro.png")!)
                    .resizable()
                    .scaledToFit()
                    .aspectRatio(contentMode: .fill)
                    .position(x: 200, y: 350)
                
                ProgressBar(value: $progressValue).frame(width: 95,height: 5)
                    .position(x:90,y:244)
                    .rotationEffect(.init(degrees:-21))
                    .onTapGesture(perform: {
                        self.startProgressBar()})
                   
                    VStack {
                  
                        Text(screenText)
                            .foregroundColor(.white)
                            .frame(width:300,alignment: .leading)
                            .font(.system(size: 20, weight: .heavy, design: .rounded))
                            .scaledToFit()
                            .padding(.top)
                            .position(x: 200, y:65)
                        
                           
                }
               
                
                
            }
                .onAppear(perform: {
                    startCharacterAnimation()
                })
              
            Button {
                PlaygroundPage.current.setLiveView(Slide7())

                }
            label:{
                    Image(uiImage: UIImage(named: "freccia")!)
                .resizable()
                .scaledToFit()
                    .foregroundColor(.black)
                    .background(Color.white)
                    .cornerRadius(15)
                }.frame(width: 50, height: 50)
                .position(x: 200, y:250)
            
        }.frame(width: 400, height: 650)
            .background(Color.black)
       
      
        
    }
        
  
    
    func startCharacterAnimation() {
        let timer = Timer.scheduledTimer(withTimeInterval: loopDuration, repeats: true) { (timer) in
            
            characterLoopIndex += 1
            
            if characterLoopIndex >= finaltext.count {
                timer.invalidate()
            }
            screenText = screenText + finaltext[characterLoopIndex]
        }
        timer.fire()
    }
    
    func startProgressBar() {
        
            for _ in 0...100 {
                       self.progressValue += 0.015
                   }
    }
    
    func resetProgressBar() {
       
        self.progressValue = 0
    }
}

//PlaygroundPage.current.setLiveView(Slide6())
struct Slide7: View {
    @State var screenText: String = ""
    let finaltext = "Apple  told the teachers the truth. The headmaster Donald  kicked him out"
    @State var characterLoopIndex: Int = -1
    let loopDuration: Double = 0.08

    var body: some View {
        VStack{
            ZStack {
                Spacer()
                Image(uiImage: UIImage(named: "Trump.png")!)
                    .resizable()
                    .scaledToFit()
                    .aspectRatio(contentMode: .fill)
                    .position(x: 200, y: 420)
                    
                    VStack {
                       
                        Text(screenText)
                            .foregroundColor(.white)
                            .frame(width:300,alignment: .leading)
                            .font(.system(size: 20, weight: .heavy, design: .rounded))
                            .scaledToFit()
                            .position(x: 200, y:55)
                            .padding(.top)
                        
                        
                }
            }
                .onAppear(perform: {
                    startCharacterAnimation()
                })
            
            Button {
                PlaygroundPage.current.setLiveView(Slide8())

                
            }
    label:{
                Image(uiImage: UIImage(named: "freccia")!)
            .resizable()
            .scaledToFit()
                .foregroundColor(.black)
                .background(Color.white)
                
                .cornerRadius(15)
                .frame(width: 50, height: 50)
                .position(x: 200, y:250)
            }
        }.frame(width: 400, height: 650)
            .background(Color.black)
      
        
        
    }
    func startCharacterAnimation() {
        let timer = Timer.scheduledTimer(withTimeInterval: loopDuration, repeats: true) { (timer) in
            
            characterLoopIndex += 1
            
            if characterLoopIndex >= finaltext.count {
                timer.invalidate()
            }
            screenText = screenText + finaltext[characterLoopIndex]
        }
        timer.fire()
    }
}


struct Slide8: View {
    @State var scale = 0.60
    @State var scale2 = 0.60
    @State var rotation = false
    @State var posY = -400
    @State private var isEnabled = false

    var body: some View {
        
        ZStack {
            
            VStack {
                
                
                Image(uiImage: UIImage(named: "fine.png")!)
                    .resizable()
                    .scaledToFit()
                    .aspectRatio(contentMode: .fit)
                    .position(x: 200,y: CGFloat(posY) )
                    .scaleEffect(scale)
                    .animation(.linear(duration: 10).delay(3).speed(3))
                 
                    .scaleEffect(scale2)
                    .animation(Animation.easeInOut(duration: 3).repeatForever(autoreverses: true).speed(4),value: isEnabled)
                
                    .onAppear(perform: {
                       
                        root()
                       
                    })
        
                Button {
                    PlaygroundPage.current.setLiveView(Slide1())

                
            } label: {
                Text("THE END")
                    
                    .font(.system(size: 25, weight: .heavy, design: .rounded))
                    .padding(.all)
                    .foregroundColor(.black)
                    .background(Color.white)
                    .cornerRadius(20)
                    .position(x:200,y:240)
                    
            }
            }
           
                
        }
        .frame(width: 400, height: 650)
        .background(Color.black)
    }
    
    
    func root()
    {
        posY += 650
        scale = 1.3
        scale2 = 1
        isEnabled = true
    }
}





extension String {

    var length: Int {
        return count
    }

    subscript (i: Int) -> String {
        return self[i ..< i + 1]
    }

    func substring(fromIndex: Int) -> String {
        return self[min(fromIndex, length) ..< length]
    }

    func substring(toIndex: Int) -> String {
        return self[0 ..< max(0, toIndex)]
    }

    subscript (r: Range<Int>) -> String {
        let range = Range(uncheckedBounds: (lower: max(0, min(length, r.lowerBound)),
                                            upper: min(length, max(0, r.upperBound))))
        let start = index(startIndex, offsetBy: range.lowerBound)
        let end = index(start, offsetBy: range.upperBound - range.lowerBound)
        return String(self[start ..< end])
    }
}


struct ProgressBar: View {
    @Binding var value: Float
    
    var body: some View {
        GeometryReader { geometry in
            ZStack(alignment: .leading) {
                Rectangle().frame(width: geometry.size.width , height: geometry.size.height)
                    .opacity(0.3)
                    .foregroundColor(Color(UIColor.systemTeal))
                
                Rectangle().frame(width: min(CGFloat(self.value)*geometry.size.width, geometry.size.width), height: geometry.size.height)
                    .foregroundColor(Color(UIColor.systemBlue))
                    .animation(.linear)
            }.cornerRadius(45.0)
        }
    }
}
PlaygroundPage.current.setLiveView(Slide1())

 
