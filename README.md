# Json-
Json into data frame
key_to_use=['id','all_artists','title','medium']

def get_record_from_file(file_path,key_to_use):
    with open(file_path) as artwork_file:
        print(artwork_file)
        content = json.load(artwork_file)
       # print(content)
        #print('hello')
    record = []
    
    for field in key_to_use:
        record.append(content[field])
        
        
    return tuple(record)

import os
import json
SAMPLE_JSON=r'C:\Users\uverma\Desktop\collection-master\artworks\a\000\a00001-1035.json'

SAMPLE_JSON

SAMPLE_JSON= os.path.join('..','collection-master','artworks','a','000','a00001-1035.json')

import pandas as pd



def read_artworks_from_json(keys_to_use):
    JSON_ROOT = r'C:\Users\uverma\Desktop\collection-master\artworks'
    #print('Hello1')
   # print(JSON_ROOT)
    artworks=[]
    i=1
    for root, _ , files in os.walk(JSON_ROOT):
        print(i)
        i+=1
        print(root,_,files)
        for f in files:
           # print(f)
            if f.endswith('json'):
                
                record=get_record_from_file(os.path.join(root,f),keys_to_use)
                
                artworks.append(record)
                break
                
        
#    df=pd.DataFrame.from_records(artworks,columns=keys_to_use,index='id') 
#    return df

read_artworks_from_json(key_to_use)
