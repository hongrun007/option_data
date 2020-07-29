# 期权数据
介绍：可以获取期权tick数据、greeks数据、分时数据、k线数据、可以查询指定月份和时间的看涨和看跌期权，
可以获取股票tick行情

### 功能
导入模块
```python
from apps.option_data import *

```

* 1、获取合约名称
```python
test_contract_name = contract_name('10001011')
print(test_contract_name)
```
```
输出：
50ETF购11月2600
```

* 2、获取指定标的可交易月份合约
```python
    test_contract_monthly = contract_monthly('300ETF')
    print(test_contract_monthly)
```
```
输出： 
   月份
0  2020-08
1  2020-09
2  2020-12
3  2021-03
```
* 3、获取指定标的、时间、可交易的认购期权合约
```python
    test_contract_up = contract_up("510050", "2009")
    print(test_contract_up)
```
```
输出：
          编码
0   10002423
1   10002405
2   10002406
3   10002299
4   10002300
5   10002301
6   10002302
7   10002303
8   10002269
9   10002231
10  10002232
11  10002233
12  10002234
13  10002235
14  10002236
15  10002237
16  10002238
17  10002239
18  10002641
19  10002657
20  10002681
21  10002682
22  10002683
```
* 4、获取指定标的、时间、可交易的认沽期权合约
```python
    test_contract_down = contract_down("510050", "2009")
    print(test_contract_down)
```
```
输出：
          编码
0   10002424
1   10002407
2   10002408
3   10002304
4   10002305
5   10002306
6   10002307
7   10002308
8   10002270
9   10002240
10  10002241
11  10002242
12  10002243
13  10002244
14  10002245
15  10002246
16  10002247
17  10002248
18  10002642
19  10002658
20  10002684
21  10002685
22  10002686
```
* 5、获取指定编码的股票tick简易行情
```python
    test_tick_simple = tick_simple(['510050.SH', '603000.SH'])
    print(test_tick_simple)
```
```
输出：
    证券简称     最新价    涨跌额   涨跌幅      成交量     成交额
0  50ETF   3.231  0.020  0.62  4208787  136020
1    人民网  19.580  0.120  0.62   117923   23119
```
* 6、获取指定编码的股票tick高质量行情
```python
    test_tick_quality = tick_quality(['510050.SH', '603000.SH'])
    print(test_tick_quality)
```
```
输出：
    证券简称   今日开盘价   昨日收盘价   最近成交价   最高成交价  ...    卖价位五        行情日期      行情时间 停牌状态 1
0  50ETF   3.238   3.211   3.231   3.252  ...   3.234  2020-07-28  15:00:28   00  
1    人民网  19.580  19.460  19.580  19.840  ...  19.630  2020-07-28  15:00:00   00  
```
* 7、获取期权tick行情数据
```python
    test_tick_option = tick_option(['10002591', '10002592'])
    print(test_tick_option)
```
```
输出：
    买量      买价     最新价      卖价  卖量  ...         到期日 剩余天数 虚实值标志   内在价值    时间价值
0   15  0.1747  0.1750  0.1750  59  ...  2020-08-26   29     2  0.131   0.044
1  104  0.1136  0.1136  0.1138   7  ...  2020-08-26   29     2  0.031  0.0826
```
* 8、获取指定多个期权合约的希腊字母
```python
    test_option_greeks = option_greeks(['10002591', '10002592'])
    print(test_option_greeks)
```
```
输出：
         期权合约简称 1 2 3       4  ...                最低价    交易代码     行权价     最新价 理论价值
0  50ETF购8月3100         38241  ...  510050C2008M03100  3.1000  0.1750  0.1831    M
1  50ETF购8月3200        137710  ...  510050C2008M03200  3.2000  0.1136  0.1202    M
```
* 9、获取期权分时行情，默认最近5日分时行情
```python
    test_option_minline = option_minline('10002591')
    print(test_option_minline)
```
```
输出：
                       时间      价格  成交     持仓      均价          日期
0     2020-07-22 09:26:00  0.0000   0      0  0.0000  2020-07-22
1     2020-07-22 09:27:00  0.0000   0      0  0.0000  2020-07-22
2     2020-07-22 09:28:00  0.0000   0      0  0.0000  2020-07-22
3     2020-07-22 09:29:00  0.0000   0      0  0.0000  2020-07-22
4     2020-07-22 09:30:00  0.2600  21  21425  0.2599  2020-07-22
...                   ...     ...  ..    ...     ...         ...
1176  2020-07-28 14:56:00  0.1750  50  29976  0.1799  2020-07-28
1177  2020-07-28 14:57:00  0.1750   0  29976  0.1799  2020-07-28
1178  2020-07-28 14:58:00  0.1750   0  29976  0.1799  2020-07-28
1179  2020-07-28 14:59:00  0.1750   0      0  0.1799  2020-07-28
1180  2020-07-28 15:00:00  0.1750  11  29968  0.1799  2020-07-28
```
* 10、获取期权k线数据
```python
    test_option_k_bar = option_k_bar('10002591')
    print(test_option_k_bar)
```
```
输出：
            时间      开盘      最高      最低      收盘         成交
0   2020-06-29  0.0284  0.0318  0.0183  0.0199   29500790
1   2020-06-30  0.0210  0.0266  0.0193  0.0220   41762455
2   2020-07-01  0.0225  0.0450  0.0224  0.0445  162317745
3   2020-07-02  0.0446  0.1112  0.0446  0.1023  299466718
4   2020-07-03  0.1139  0.1599  0.1094  0.1500  342822418
5   2020-07-06  0.1908  0.4655  0.1899  0.4600  253850606
6   2020-07-07  0.4851  0.6599  0.3503  0.3571   66888367
7   2020-07-08  0.3514  0.4452  0.3423  0.3977   14371854
8   2020-07-09  0.3878  0.4194  0.3720  0.4038    4695577
9   2020-07-10  0.3839  0.3890  0.3114  0.3270    5398112
10  2020-07-13  0.3199  0.4000  0.3021  0.3462   27487399
11  2020-07-14  0.3390  0.3659  0.2887  0.3189    7520761
12  2020-07-15  0.3399  0.3524  0.2880  0.2941   17662574
13  2020-07-16  0.3100  0.3100  0.1850  0.1876   31013475
14  2020-07-17  0.1930  0.2232  0.1791  0.1960  254602790
15  2020-07-20  0.2113  0.2780  0.1891  0.2643  272093045
16  2020-07-21  0.2648  0.2819  0.2400  0.2590  111606422
17  2020-07-22  0.2604  0.3380  0.2456  0.2573  220495315
18  2020-07-23  0.2426  0.2844  0.2131  0.2582  403281206
19  2020-07-24  0.2494  0.2528  0.1531  0.1693  426801531
20  2020-07-27  0.1791  0.1972  0.1543  0.1681  439417272
21  2020-07-28  0.1815  0.1957  0.1655  0.1750  362232282
```
