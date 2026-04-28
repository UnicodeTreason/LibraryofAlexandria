# Excel Magic

## Extract epochtime From ISO8601 DateTime

Useful for quick calculation of "time difference" of many events, as with epochtime it becomes a simple subtraction.

2025-10-30T04:03:36Z     | =(((DATEVALUE(LEFT(A2,10))+TIMEVALUE(MID(A2,12,8)))-DATE(1970,1,1))*86400000)
2025-10-30T04:03:36.000Z | =(((DATEVALUE(LEFT(A369,10))+TIMEVALUE(MID(A369,12,8)))-DATE(1970,1,1))*86400000)+VALUE(MID(A369,FIND(".",A369)+1,3))
