# Google-Map-Downloader
`downloader`: A small tool, you only need to input the spatial extent and map zoom level to download Google Maps, and output to TIFF format, including the spatial coordinate system.  

### Use
```python
if __name__ == '__main__':
    start_time=time.time()
    
    # main(100.361,38.866,100.386,38.839,13,r'C:\Users\test.tif')
    main(left,top,right,bottom,zoom,filePath,style='s',server="Google")

    end_time=time.time()
    print('lasted a total of {:.2f} seconds'.format(end_time-start_time))
```
```python
'''
Parameters
----------
left, top : left-top coordinate, for example (100.361,38.866)
    
right, bottom : right-bottom coordinate
    
z : zoom

filePath : File path for storing results, TIFF format
    
style : 
    m for map; 
    s for satellite; 
    y for satellite with label; 
    t for terrain; 
    p for terrain with label; 
    h for label;

source : Google
'''
```
## Issues
If you encounter the problem of Bad network link, you can change the HEADERS in the download function, and try again.
```python
def download(self,url):
        HEADERS = {'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/29.0.1547.76 Safari/537.36'}
        header = ur.Request(url,headers=HEADERS)
        err=0
        while(err<3):
            try:
                data = ur.urlopen(header).read()
            except:
                err+=1
            else:
                return data
        raise Exception("Bad network link.")
```

## Setup
* `python3 -m venv venv`
* `source venv/bin/activate`
* `pip install -r requirements.txt`