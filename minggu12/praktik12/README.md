
import pandas as pd
import numpy as np

college = pd.read_csv('data/college.csv', index_col='INSTNM')
city = college['CITY']
city.head()

OUT : INSTNM
Alabama A & M University                   Normal
University of Alabama at Birmingham    Birmingham
Amridge University                     Montgomery
University of Alabama in Huntsville    Huntsville
Alabama State University               Montgomery
Name: CITY, dtype: object

city.iloc[3]

OUT : 'Huntsville'

city.iloc[[10,20,30]]

OUT : INSTNM
Birmingham Southern College                            Birmingham
George C Wallace State Community College-Hanceville    Hanceville
Judson College                                             Marion
Name: CITY, dtype: object

city.iloc[4:50:10]

OUT : INSTNM
Alabama State University              Montgomery
Enterprise State Community College    Enterprise
Heritage Christian University           Florence
Marion Military Institute                 Marion
Reid State Technical College           Evergreen
Name: CITY, dtype: object

college = pd.read_csv('data/college.csv', index_col='INSTNM')
college.head()

OUT : CITY	STABBR	HBCU	MENONLY	WOMENONLY	RELAFFIL	SATVRMID	SATMTMID	DISTANCEONLY	UGDS	...	UGDS_2MOR	UGDS_NRA	UGDS_UNKN	PPTUG_EF	CURROPER	PCTPELL	PCTFLOAN	UG25ABV	MD_EARN_WNE_P10	GRAD_DEBT_MDN_SUPP
INSTNM																					
Alabama A & M University	Normal	AL	1.0	0.0	0.0	0	424.0	420.0	0.0	4206.0	...	0.0000	0.0059	0.0138	0.0656	1	0.7356	0.8284	0.1049	30300	33888
University of Alabama at Birmingham	Birmingham	AL	0.0	0.0	0.0	0	570.0	565.0	0.0	11383.0	...	0.0368	0.0179	0.0100	0.2607	1	0.3460	0.5214	0.2422	39700	21941.5
Amridge University	Montgomery	AL	0.0	0.0	0.0	1	NaN	NaN	1.0	291.0	...	0.0000	0.0000	0.2715	0.4536	1	0.6801	0.7795	0.8540	40100	23370
University of Alabama in Huntsville	Huntsville	AL	0.0	0.0	0.0	0	595.0	590.0	0.0	5451.0	...	0.0172	0.0332	0.0350	0.2146	1	0.3072	0.4596	0.2640	45500	24097
Alabama State University	Montgomery	AL	1.0	0.0	0.0	0	425.0	430.0	0.0	4811.0	...	0.0098	0.0243	0.0137	0.0892	1	0.7347	0.7554	0.1270	26600	33118.

5 rows × 26 columns

college.loc[:'Amridge University', :'MENONLY']

OUT : CITY	STABBR	HBCU	MENONLY
INSTNM				
Alabama A & M University	Normal	AL	1.0	0.0
University of Alabama at Birmingham	Birmingham	AL	0.0	0.0
Amridge University	Montgomery	AL	0.0	0.0

college.index[4001]

OUT : 'Spokane Community College'

college = pd.read_csv('data/college.csv', index_col='INSTNM')
cn = 'Texas A & M University-College Station'
college.loc[cn, 'UGDS_WHITE']

OUT : 0.66099999999999992

college.at[cn, 'UGDS_WHITE']

OUT : 0.66099999999999992

%timeit college.loc[cn, 'UGDS_WHITE']

OUT : 9.93 µs ± 274 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit college.at[cn, 'UGDS_WHITE']

OUT : 6.69 µs ± 223 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

row_num = college.index.get_loc(cn)
col_num = college.columns.get_loc('UGDS_WHITE')

row_num, col_num

OUT : (3765, 10)

%timeit college.iloc[row_num, col_num]

OUT : 11.1 µs ± 426 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit college.iat[row_num, col_num]

OUT : 7.47 µs ± 109 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

%timeit college.iloc[5, col_num]

OUT : 10.8 µs ± 467 ns per loop (mean ± std. dev. of 7 runs, 100000 loops

%timeit college.iat[5, col_num]

OUT : 7.12 µs ± 297 ns per loop (mean ± std. dev. of 7 runs, 100000 loops each)

state = college['STABBR']

state.iat[1000]

OUT : 'IL'

state.at['Stanford University']

OUT : 'CA'

college = pd.read_csv('data/college.csv', index_col='INSTNM')
college[10:20:2]

city[10:20:2]

college.index[4001]

OUT : 'Spokane Community College'

start = 'Mesa Community College'
stop = 'Spokane Community College'
college[start:stop:1500]

city[start:stop:1500]

OUT : INSTNM
Mesa Community College                            Mesa
Hair Academy Inc-New Carrollton         New Carrollton
National College of Natural Medicine          Portland
Name: CITY, dtype: object

college = college.sort_index(ascending=False)
college.index.is_monotonic_decreasing

OUT : True

college[:10, ['CITY', 'STABBR']]

OUT : ---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-55-92538c61bdfa> in <module>()
----> 1 college[:10, ['CITY', 'STABBR']]

/Users/Ted/anaconda/lib/python3.6/site-packages/pandas/core/frame.py in __getitem__(self, key)
   1962             return self._getitem_multilevel(key)
   1963         else:
-> 1964             return self._getitem_column(key)
   1965 
   1966     def _getitem_column(self, key):

/Users/Ted/anaconda/lib/python3.6/site-packages/pandas/core/frame.py in _getitem_column(self, key)
   1969         # get column
   1970         if self.columns.is_unique:
-> 1971             return self._get_item_cache(key)
   1972 
   1973         # duplicate columns & possible reduce dimensionality

/Users/Ted/anaconda/lib/python3.6/site-packages/pandas/core/generic.py in _get_item_cache(self, item)
   1641         """Return the cached item, item represents a label indexer."""
   1642         cache = self._item_cache
-> 1643         res = cache.get(item)
   1644         if res is None:
   1645             values = self._data.get(item)

TypeError: unhashable type: 'slice'


