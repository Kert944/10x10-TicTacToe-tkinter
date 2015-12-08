# 10x10-TicTacToe-tkinter
from tkinter import *
from tkinter import ttk
from tkinter import messagebox


väljak = [0,1,2,3,4,5,6,7,8,9,
          10,11,12,13,14,15,16,17,18,19,
          20,21,22,23,24,25,26,27,28,29,
          30,31,32,33,34,35,36,37,38,39,
          40,41,42,43,44,45,46,47,48,49,
          50,51,52,53,54,55,56,57,58,59,
          60,61,62,63,64,65,66,67,68,69,
          70,71,72,73,74,75,76,77,78,79,
          80,81,82,83,84,85,86,87,88,89,
          90,91,92,93,94,95,96,97,98,99]

def näita_väljakut():
    print(väljak[0], " |",väljak[1], " |",väljak[2]," |",väljak[3]," |",väljak[4], " |",väljak[5]," |",väljak[6]," |",väljak[7]," |",väljak[8]," |",väljak[9])
    print("-----------------------------------------------")
    for i in range(10,100,10):
        print(väljak[i], "|",väljak[i+1], "|",väljak[i+2],"|",väljak[i+3],"|",väljak[i+4], "|",väljak[i+5],"|",väljak[i+6],"|",väljak[i+7],"|",väljak[i+8],"|",väljak[i+9])
        print("-----------------------------------------------")


def reavõit(tähis):

    
    for i in range(0,100,10):
        for j in range(0,6):
            try:
                if väljak[i+j]==tähis and väljak[i+j+1]==tähis and väljak[i+j+2]==tähis and väljak[i+j+3]==tähis and väljak[i+j+4]==tähis:
                    return True
            except:
                False

def tulbavõit(tähis):
    #ei ole palju variante läbi proovind aga tundub, et toimib
    for i in range(0,6):
        for j in range(0,100,10):
            try:
                if väljak[i+j]==tähis and väljak[i+j+10]==tähis and väljak[i+j+20]==tähis and väljak[i+j+30]==tähis and väljak[i+j+40]==tähis:
                    return True
            except:
                False



def diagonaalivõit_ülevalt_alla(tähis):
    for i in range(0,6):
        for j in range(0,100,10):
            try:
                ### diagonaal ülevalt vasakult alla paremale
                if väljak[i+j]==tähis and väljak[i+j+11]==tähis and väljak[i+j+22]==tähis and väljak[i+j+33]==tähis and väljak[i+j+44]==tähis:
                    return True
            except:
                False

def diagonaalivõit_alt_ülesse(tähis):
     for i in range(0,6):
        for j in range(0,100,10):
            try:
                ### diagonaal alt vasakult üles paremale
                if väljak[i+j]==tähis and väljak[i+j-9]==tähis and väljak[i+j-18]==tähis and väljak[i+j-27]==tähis and väljak[i+j-36]==tähis:
                    return True
            except:
                False

def võit(sümbol):
    if reavõit(sümbol) == True or tulbavõit(sümbol)==True or diagonaalivõit_ülevalt_alla(sümbol)==True or diagonaalivõit_alt_ülesse(sümbol)== True:
        return True
    else:
        return False


def väljakusse(aa, tähis):
    väljak[aa]=tähis

def reeglid():
    messagebox.showinfo("Info", message="Võidab 5 järjestikust ühesugust elementi:\n - vasakult-paremale \n - ülevalt-alla \n - diagonaal vasakult-paremale \n - diagonaal paremalt-vasakule \n Võitmiseks kliki mõne tähistatud kasti peale")

    
click=True

def kontroll(nupud, koht):
    global click
    if nupud["text"]==" " and click == True:
        nupud["text"]="X"
        väljakusse(koht, "X")
        click=False
    elif nupud["text"]==" " and click == False:
        nupud["text"] = "O"
        väljakusse(koht, "O")
        click = True

    



    elif võit("X")==True:
        messagebox.showinfo("Võitja X!", message="X on võitnud mängu!")
    elif võit("O")==True:
        messagebox.showinfo("Võitja O!", message="O on võitnud mängu!")
            

        
               


tk=Tk()
tk.title("10x10 Trips-Traps-Trull")

klahv_reeglid=Button(tk, text="Info", font=("Times 12"), command=lambda:reeglid())
klahv_reeglid.grid(row=10, column=0, sticky=(N,W))



###for i in range(10,100):
    ###print("nupp"+str(i)+"""=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp"""+str(i)+", "+str(i)+"))")
    ###print("nupp"+str(i)+".grid(row="+str(i//10)+", column="+str(i%10)+", sticky = (N,W))")

nupp00=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp00, 0))
nupp00.grid(row=0, column=0, sticky = (N,W))
nupp01=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp01, 1))
nupp01.grid(row=0, column=1, sticky = (N,W))
nupp02=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp02, 2))
nupp02.grid(row=0, column=2, sticky = (N,W))
nupp03=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp03, 3))
nupp03.grid(row=0, column=3, sticky = (N,W))
nupp04=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp04, 4))
nupp04.grid(row=0, column=4, sticky = (N,W))
nupp05=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp05, 5))
nupp05.grid(row=0, column=5, sticky = (N,W))
nupp06=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp06, 6))
nupp06.grid(row=0, column=6, sticky = (N,W))
nupp07=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp07, 7))
nupp07.grid(row=0, column=7, sticky = (N,W))
nupp08=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp08, 8))
nupp08.grid(row=0, column=8, sticky = (N,W))
nupp09=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp09, 9))
nupp09.grid(row=0, column=9, sticky = (N,W))
nupp10=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp10, 10))
nupp10.grid(row=1, column=0, sticky = (N,W))
nupp11=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp11, 11))
nupp11.grid(row=1, column=1, sticky = (N,W))
nupp12=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp12, 12))
nupp12.grid(row=1, column=2, sticky = (N,W))
nupp13=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp13, 13))
nupp13.grid(row=1, column=3, sticky = (N,W))
nupp14=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp14, 14))
nupp14.grid(row=1, column=4, sticky = (N,W))
nupp15=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp15, 15))
nupp15.grid(row=1, column=5, sticky = (N,W))
nupp16=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp16, 16))
nupp16.grid(row=1, column=6, sticky = (N,W))
nupp17=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp17, 17))
nupp17.grid(row=1, column=7, sticky = (N,W))
nupp18=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp18, 18))
nupp18.grid(row=1, column=8, sticky = (N,W))
nupp19=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp19, 19))
nupp19.grid(row=1, column=9, sticky = (N,W))
nupp20=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp20, 20))
nupp20.grid(row=2, column=0, sticky = (N,W))
nupp21=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp21, 21))
nupp21.grid(row=2, column=1, sticky = (N,W))
nupp22=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp22, 22))
nupp22.grid(row=2, column=2, sticky = (N,W))
nupp23=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp23, 23))
nupp23.grid(row=2, column=3, sticky = (N,W))
nupp24=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp24, 24))
nupp24.grid(row=2, column=4, sticky = (N,W))
nupp25=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp25, 25))
nupp25.grid(row=2, column=5, sticky = (N,W))
nupp26=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp26, 26))
nupp26.grid(row=2, column=6, sticky = (N,W))
nupp27=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp27, 27))
nupp27.grid(row=2, column=7, sticky = (N,W))
nupp28=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp28, 28))
nupp28.grid(row=2, column=8, sticky = (N,W))
nupp29=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp29, 29))
nupp29.grid(row=2, column=9, sticky = (N,W))
nupp30=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp30, 30))
nupp30.grid(row=3, column=0, sticky = (N,W))
nupp31=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp31, 31))
nupp31.grid(row=3, column=1, sticky = (N,W))
nupp32=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp32, 32))
nupp32.grid(row=3, column=2, sticky = (N,W))
nupp33=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp33, 33))
nupp33.grid(row=3, column=3, sticky = (N,W))
nupp34=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp34, 34))
nupp34.grid(row=3, column=4, sticky = (N,W))
nupp35=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp35, 35))
nupp35.grid(row=3, column=5, sticky = (N,W))
nupp36=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp36, 36))
nupp36.grid(row=3, column=6, sticky = (N,W))
nupp37=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp37, 37))
nupp37.grid(row=3, column=7, sticky = (N,W))
nupp38=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp38, 38))
nupp38.grid(row=3, column=8, sticky = (N,W))
nupp39=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp39, 39))
nupp39.grid(row=3, column=9, sticky = (N,W))
nupp40=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp40, 40))
nupp40.grid(row=4, column=0, sticky = (N,W))
nupp41=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp41, 41))
nupp41.grid(row=4, column=1, sticky = (N,W))
nupp42=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp42, 42))
nupp42.grid(row=4, column=2, sticky = (N,W))
nupp43=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp43, 43))
nupp43.grid(row=4, column=3, sticky = (N,W))
nupp44=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp44, 44))
nupp44.grid(row=4, column=4, sticky = (N,W))
nupp45=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp45, 45))
nupp45.grid(row=4, column=5, sticky = (N,W))
nupp46=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp46, 46))
nupp46.grid(row=4, column=6, sticky = (N,W))
nupp47=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp47, 47))
nupp47.grid(row=4, column=7, sticky = (N,W))
nupp48=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp48, 48))
nupp48.grid(row=4, column=8, sticky = (N,W))
nupp49=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp49, 49))
nupp49.grid(row=4, column=9, sticky = (N,W))
nupp50=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp50, 50))
nupp50.grid(row=5, column=0, sticky = (N,W))
nupp51=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp51, 51))
nupp51.grid(row=5, column=1, sticky = (N,W))
nupp52=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp52, 52))
nupp52.grid(row=5, column=2, sticky = (N,W))
nupp53=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp53, 53))
nupp53.grid(row=5, column=3, sticky = (N,W))
nupp54=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp54, 54))
nupp54.grid(row=5, column=4, sticky = (N,W))
nupp55=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp55, 55))
nupp55.grid(row=5, column=5, sticky = (N,W))
nupp56=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp56, 56))
nupp56.grid(row=5, column=6, sticky = (N,W))
nupp57=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp57, 57))
nupp57.grid(row=5, column=7, sticky = (N,W))
nupp58=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp58, 58))
nupp58.grid(row=5, column=8, sticky = (N,W))
nupp59=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp59, 59))
nupp59.grid(row=5, column=9, sticky = (N,W))
nupp60=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp60, 60))
nupp60.grid(row=6, column=0, sticky = (N,W))
nupp61=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp61, 61))
nupp61.grid(row=6, column=1, sticky = (N,W))
nupp62=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp62, 62))
nupp62.grid(row=6, column=2, sticky = (N,W))
nupp63=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp63, 63))
nupp63.grid(row=6, column=3, sticky = (N,W))
nupp64=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp64, 64))
nupp64.grid(row=6, column=4, sticky = (N,W))
nupp65=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp65, 65))
nupp65.grid(row=6, column=5, sticky = (N,W))
nupp66=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp66, 66))
nupp66.grid(row=6, column=6, sticky = (N,W))
nupp67=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp67, 67))
nupp67.grid(row=6, column=7, sticky = (N,W))
nupp68=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp68, 68))
nupp68.grid(row=6, column=8, sticky = (N,W))
nupp69=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp69, 69))
nupp69.grid(row=6, column=9, sticky = (N,W))
nupp70=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp70, 70))
nupp70.grid(row=7, column=0, sticky = (N,W))
nupp71=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp71, 71))
nupp71.grid(row=7, column=1, sticky = (N,W))
nupp72=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp72, 72))
nupp72.grid(row=7, column=2, sticky = (N,W))
nupp73=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp73, 73))
nupp73.grid(row=7, column=3, sticky = (N,W))
nupp74=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp74, 74))
nupp74.grid(row=7, column=4, sticky = (N,W))
nupp75=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp75, 75))
nupp75.grid(row=7, column=5, sticky = (N,W))
nupp76=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp76, 76))
nupp76.grid(row=7, column=6, sticky = (N,W))
nupp77=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp77, 77))
nupp77.grid(row=7, column=7, sticky = (N,W))
nupp78=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp78, 78))
nupp78.grid(row=7, column=8, sticky = (N,W))
nupp79=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp79, 79))
nupp79.grid(row=7, column=9, sticky = (N,W))
nupp80=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp80, 80))
nupp80.grid(row=8, column=0, sticky = (N,W))
nupp81=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp81, 81))
nupp81.grid(row=8, column=1, sticky = (N,W))
nupp82=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp82, 82))
nupp82.grid(row=8, column=2, sticky = (N,W))
nupp83=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp83, 83))
nupp83.grid(row=8, column=3, sticky = (N,W))
nupp84=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp84, 84))
nupp84.grid(row=8, column=4, sticky = (N,W))
nupp85=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp85, 85))
nupp85.grid(row=8, column=5, sticky = (N,W))
nupp86=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp86, 86))
nupp86.grid(row=8, column=6, sticky = (N,W))
nupp87=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp87, 87))
nupp87.grid(row=8, column=7, sticky = (N,W))
nupp88=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp88, 88))
nupp88.grid(row=8, column=8, sticky = (N,W))
nupp89=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp89, 89))
nupp89.grid(row=8, column=9, sticky = (N,W))
nupp90=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp90, 90))
nupp90.grid(row=9, column=0, sticky = (N,W))
nupp91=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp91, 91))
nupp91.grid(row=9, column=1, sticky = (N,W))
nupp92=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp92, 92))
nupp92.grid(row=9, column=2, sticky = (N,W))
nupp93=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp93, 93))
nupp93.grid(row=9, column=3, sticky = (N,W))
nupp94=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp94, 94))
nupp94.grid(row=9, column=4, sticky = (N,W))
nupp95=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp95, 95))
nupp95.grid(row=9, column=5, sticky = (N,W))
nupp96=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp96, 96))
nupp96.grid(row=9, column=6, sticky = (N,W))
nupp97=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp97, 97))
nupp97.grid(row=9, column=7, sticky = (N,W))
nupp98=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp98, 98))
nupp98.grid(row=9, column=8, sticky = (N,W))
nupp99=Button(tk, text=" ", font=("Times 12 bold"), height=3, width=8, command=lambda:kontroll(nupp99, 99))
nupp99.grid(row=9, column=9, sticky = (N,W))
