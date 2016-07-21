# FetchJSOC

## Usage

Get all keys of dataseries "aia.lev1_euv_12s":
```python
>>> fetch.getKeys('aia.lev1_euv_12s')
['T_REC', 'T_OBS', 'WAVELNTH', 'DATE', ..., 'T_REC_epoch']
```

Get all segments of dataseries "aia.lev1_euv_12s":
```python
>>> fetch.getSegments('aia.lev1_euv_12s')
['image', 'spikes']
```

Fetch `DATE__OBS`, `DATAMEAN` and `image` filepaths for the 304 wavelength of dataseries "aia.lev1_euv_12s" starting from 7/1/16 and lasting 1 minute.
```python
>>> fetch.fetch('aia.lev1_euv_12s', start=datetime.datetime(2016,7,1),
                end_or_span='1m', wavelengths=304, segments='image',
                keys=['DATE__OBS', 'DATAMEAN'], headers=True)
[['DATE__OBS', 'DATAMEAN', 'image'],
['2016-07-01T00:00:06.12Z', '6.01', '/SUM4/D832941546/S00000/image_lev1.fits'],
['2016-07-01T00:00:18.13Z', '6.02', '/SUM15/D832941548/S00000/image_lev1.fits'],
['2016-07-01T00:00:30.12Z', '6.02', '/SUM42/D832941570/S00000/image_lev1.fits'],
['2016-07-01T00:00:42.13Z', '6.03', '/SUM33/D832941550/S00000/image_lev1.fits'],
['2016-07-01T00:00:54.12Z', '6.02', '/SUM8/D832941640/S00000/image_lev1.fits']]
```

Return the above as a pandas.DataFrame object:
```python
>>> fetch.fetch('aia.lev1_euv_12s', start=datetime.datetime(2016,7,1),
                end_or_span='1m', wavelengths=304, segments='image',
                keys=['DATE__OBS', 'DATAMEAN'], headers=True, df=True)
```
```
                 DATE__OBS  DATAMEAN                                     image
0  2016-07-01T00:00:06.12Z      6.01   /SUM4/D832941546/S00000/image_lev1.fits
1  2016-07-01T00:00:18.13Z      6.02  /SUM15/D832941548/S00000/image_lev1.fits
2  2016-07-01T00:00:30.12Z      6.02  /SUM42/D832941570/S00000/image_lev1.fits
3  2016-07-01T00:00:42.13Z      6.03  /SUM33/D832941550/S00000/image_lev1.fits
4  2016-07-01T00:00:54.12Z      6.02   /SUM8/D832941640/S00000/image_lev1.fits
```
