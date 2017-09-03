# ljj
林俊杰歌词分析
# -*- coding: utf-8 -*-
import xlrd
import jieba
import numpy
import codecs
import pandas

f=codecs.open(r"E:\\dhf.txt",'r','utf-8')
content=f.read()
f.close()
segments=[]
segs=jieba.cut(content)
for seg in segs:
    if len(seg)>1:
        segments.append(seg)
segmentDF=pandas.DataFrame({'segment':segments})
df=segmentDF.groupby("segment")["segment"].agg({"计数":numpy.size}).reset_index()
print(df.head(100))
df.to_excel(r"E:\\dhf.xls",sheet_name='sheet1')

//统计出现的次数
python2
# -*- coding: utf-8 -*-
 
from src.QcloudApi.qcloudapi import QcloudApi
 
module='wenzhi'
 
config = {
    'Region': 'gz',
    'secretId': 'AKIDtgWEk94PErMfmg4uDKPyMYYLwLXbq7Zq',
    'secretKey': 'CD5mjV5SdbNxSlsnW2MTP0QegW9apvoU',
    'method': 'post'
}

'''
action='LexicalAnalysis'
       'TextSentiment'
       'TextClassify'
       'TextKeywords'
       'TextDependency'
       'LexicalSynonym'
       'LexicalCheck'
       'ContentTranscode'
'''
action='LexicalAnalysis'

#different action has differnet params
params={
   'text':'你只是个好人',
   'code':'0x00200000'
   
   }
try:
    service = QcloudApi(module, config)
    print service.call(action, params).decode('unicode_escape')
except Exception, e:
    print 'exception:', e
//这是腾讯文智的接口文档。可以进行情绪分析
