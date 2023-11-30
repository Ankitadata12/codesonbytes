import os
import pandas as pd

path = "E:\\project"
files =os.listdir(path)
for eachfile in files:
    if eachfile.endswith(".xlsx"):
        cleanfilename = eachfile.replace(".xlsx","")
        xlfile=pd.ExcelFile(eachfile)
        sheets= xlfile.sheet_names
        for eachsheet in sheets:
            sheetdata=xlfile.parse(eachsheet)
            csvname=cleanfilename + "-" + eachsheet +".csv"
            print(csvname)
            sheetdata.to_csv(csvname,index = False)
