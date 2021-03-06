import plotly.express as px
import numpy as np 
from numpy import sin,pi
import pandas as pd  

x = np.linspace(0,2000,num=100000)
y = np.linspace(0,2000,num=100000)

n=100
step = np.linspace(0,2*pi,num=n) 
data = []
b = 0 
for k in step:
    b = b + 1
    Ds1 = []
    Ds2 = [] 
    for i in range(int(len(x)/n)):
        data.append([x[i],0,sin(x[i]),
                     'Wave 1',str(round(k/pi,2))+'π'])
        Ds1.append([x[i],0,sin(x[i])])
    
    for i in range(int(len(x)/n)):
            data.append([x[i],sin(x[i]+k),0,
                         'Wave 2'
                         ,str(round(k/pi,2))+'π'])
            Ds1.append([x[i],sin(x[i]+k),0])
    
    for i in range(int(len(x)/n)):
            data.append([x[i],Ds1[i][1]+Ds1[int(len(x)/n)+i][1],
                         Ds1[i][2]+Ds1[int(len(x)/n)+i][2],'Superposed Wave'
                         ,str(round(k/pi,2))+'π'])
        
df = pd.DataFrame(data, columns = ['x', 'y','z','Name','Shift'])
fig = px.line_3d(df, x="x", y="y", z="z",animation_frame="Shift", 
                 animation_group="Name",template = "plotly_dark",color = "Name")

fig["layout"].pop("updatemenus")

fig.write_html("3D_Wave_Superposition.html")
