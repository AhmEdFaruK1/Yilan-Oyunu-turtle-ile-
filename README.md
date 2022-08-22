# Yilan-Oyunu-turtle-ile-


    import turtle as tt
    import time 
    import random
    pencere= tt.Screen()
    pencere.title("yılan oyunu")
    pencere.bgcolor("green")
    pencere.setup(width=500,height= 500)
    pencere.tracer(0)
    
    
    
    

    elma= tt.Turtle()
    elma.speed(0)
    elma.shape("circle")
    elma.color("red")
    elma.penup()
    elma.goto(135,175)
    elma.direction = "stop"
    elma.shapesize(0.50,0.50)
    kuyruklar=[]
    kyk=kuyruklar
    class yılan():
        hiz=0.05
        
       
        def __init__(self,renk,kuyruk_renk,x,y,yukarıtuş,aşağıtuş,sağtuş,soltuş,kafa,) :
            
            self.kafa= kafa
            self.yukarıtuş= yukarıtuş
            self.aşağıtuş= aşağıtuş
            self.sağtuş= sağtuş
            self.soltuş= soltuş
            self.kuyruk_renk= kuyruk_renk
            self.renk= renk
            self.x= x
            self.y= y
            global skor
            skor=0
            
            
            
            kafa.speed(0)
            kafa.shape("square")
            kafa.penup()
            kafa.color(renk)        
            kafa.goto(self.x,self.y)
            kafa.direction = "stop"
            kafa.shapesize(1,1)
            
        def move(self,g):
            global ç
            ç=0
            if (self.kafa.xcor()>=250 or self.kafa.ycor()>=250 or self.kafa.xcor()<=-250 or self.kafa.ycor()<=-250):
               self.kafa.hideturtle
               ç=1
               for i in kuyruklar:
                 i.hideturtle
            if ç!=1:
             if self.kafa.direction== "up":
                y=self.kafa.ycor()
                self.kafa.sety(y+g)
             if self.kafa.direction== "down":
                y=self.kafa.ycor()
                self.kafa.sety(y-g)
             if self.kafa.direction== "right":
                x=self.kafa.xcor()
                self.kafa.setx(x+g)
             if self.kafa.direction== "left":
                x=self.kafa.xcor()
                self.kafa.setx(x-g)
        
        def tuştakımı(self):
            def yukarıgit():
              if self.kafa.direction !="down":
                 self.kafa.direction= "up"
                
            def aşağıgit():
                if self.kafa.direction !="up":
                    self.kafa.direction= "down"
                    
            def sağagit():
                if self.kafa.direction !="left":
                   
                    self.kafa.direction= "right"
                    
            def solagit():
                if self.kafa.direction !="right":
                    self.kafa.direction= "left"
            
            pencere.onkey(yukarıgit, self.yukarıtuş)
            pencere.onkey(aşağıgit, self.aşağıtuş)
            pencere.onkey(sağagit, self.sağtuş)
            pencere.onkey(solagit, self.soltuş)
        def yemek_yeme_ve_kuyruk(self):
            global d
            d=self.kafa.xcor()
            global f
            f=self.kafa.ycor()
            
            if (self.kafa.distance(elma)<=15) :
                global skor
                skor+=1
                
              
                o=random.randint(-200,200)
                ö=random.randint(-200,200)
                elma.goto(o,ö)
                ü=0
                while ü<=3:
                  ü+=1
                  kuyruk= tt.Turtle()
                  kuyruk.speed(0)
                  kuyruk.shape("square")
                  kuyruk.color(self.kuyruk_renk)
                  kuyruk.penup()
                  
                  kuyruklar.append(kuyruk)
                  if len(kuyruklar)==1:
                    kuyruk.goto(d,f)
                  else:
                    kuyruk.goto(kuyruklar[0].xcor(),kuyruklar[0].ycor())
        def kuyrukolayları(self):
          for i in range(len(kuyruklar)-1,0,-1):
            l= kuyruklar[i-1].xcor()
            ş= kuyruklar[i-1].ycor()
            kuyruklar[i].goto(l,ş)   
            if len(kuyruklar)>0:
               kuyruklar[0].goto(d,f)         
            
                
    bekleme=0.04
    def hız():
        global bekleme
        
        if bekleme  > 0.015:
          bekleme-=0.005
          
    kafa=tt.Turtle()
    yılan1=yılan("blue","red",0,100,"w","s","d","a",kafa)
    
    yılanlar=[yılan1]
    seçim=int(input("1 kişilik için 1,2kişilik için 2,3 kişilik için 3 e basın:"))
    if seçim >=2 :
       kafa2=tt.Turtle()
       yılan2=yılan("yellow","purple",100,0,"Up","Down","Right","Left",kafa2)
       yılanlar.append(yılan2)
    if seçim==3:
        kafa3=tt.Turtle()
        yılan3=yılan("purple","orange",-100,0,"t","g","h","f",kafa3)
        yılanlar.append(yılan3)
    while True:
        pencere.update()
        pencere.listen()
        for i in yılanlar:
         i.tuştakımı()
         i.yemek_yeme_ve_kuyruk()
         i.kuyrukolayları()
         i.move(6)
        pencere.onkey(hız,"q")
        time.sleep(bekleme)
        
        
    
        if  len(yılanlar) ==1:
           if (yılan1.kafa.xcor()>=250 or yılan1.kafa.ycor()>=250 or yılan1.kafa.xcor()<=-250 or yılan1.kafa.ycor()<=-250):
            print(skor)
            break 
        if  len(yılanlar) ==2:
           if (yılan1.kafa.xcor()>=250 or yılan1.kafa.ycor()>=250 or yılan1.kafa.xcor()<=-250 or yılan1.kafa.ycor()<=-250) and (yılan2.kafa.xcor()>=250 or     yılan2.kafa.ycor()>=250 or yılan2.kafa.xcor()<=-250 or yılan2.kafa.ycor()<=-250):
            print(skor)
            break
        if  len(yılanlar) ==3:
           if (yılan1.kafa.xcor()>=250 or yılan1.kafa.ycor()>=250 or yılan1.kafa.xcor()<=-250 or yılan1.kafa.ycor()<=-250) and (yılan2.kafa.xcor()>=250 or  yılan2.kafa.ycor()>=250 or yılan2.kafa.xcor()<=-250 or yılan2.kafa.ycor()<=-250) and (yılan3.kafa.xcor()>=250 or yılan3.kafa.ycor()>=250 or yılan3.kafa.xcor()<=-250 or  yılan3.kafa.ycor()<=-250):
              print(skor)
          break
