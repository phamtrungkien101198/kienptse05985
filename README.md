# kienptse05985
# kienptse05985
#TRUNG BINH VA PHUONG SAI DO DAI CUA URL.
import re
import math
def abc(_file,regex,start,end):
    list  = []
    f = open(_file,'r')
    text = f.read()
    finds=re.findall(regex,text)
    for line in finds:
     list.append(line.strip(start).strip(end))
    return list
result = (abc('anomalousTrafficTest.txt','\?(.*) ','\?','HTTP/1.1'))
print len(result)
avg=(sum(map(len,result))/len(result))

listlen = []
for item in result:
    listlen.append(len(item))

phuongsai= math.sqrt(sum([(item-avg)**2 for item in listlen])/len(result))


#TRUNG BINH SO LAN XUAT HIEN CUA KY TU DAC BIET.
a = "\n".join(result)
specialChars = (len(a) - len( re.findall('[\w]', a)))/len(result)
#print specialChars

#PHAN TRAM :
count =0
for item in result:
        new = re.sub('[\w]+' ,'', item)
        if len(new) >specialChars and len(item) >phuongsai:
            count +=1 #dem so phan tu con lai
print count
phantram = (len(result)/count)*10
print phantram,"%"
       
          
    


    
