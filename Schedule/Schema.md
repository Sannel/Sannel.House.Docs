[Home](../index.md) -> [Schedule](index.md)

## Schedule Table Schema
![Table Relationships](Schema.svg)
<br />
<br />

__Schedules__

|Column|Type|Key|Nullable|
|--|--|--|--|
|ScheduleId|long|Primary Key|false|
|ScheduleKey|Guid|Index|false|
|Name|string(255)||false|
|DefaultMinValue|double||false|
|DefaultMaxValue|double||true|
|MinimumDifference|double||true|

Note: DefaultMinValue is always required but DefaultMaxValue does not have to be set but is used for schedules like temperature. So you can say if its less then 70 degrees turn the heater on if the more then 80 degrees turn on the ac. But if this schedule was for sprinklers we would not need the DefaultMaxValue instead we would use DefaultMinValue as a flag value to say which zone should be turned on though it would probably be 0 here. MinimumDifference is so you can say DefaultMinValue and DefaultMaxValue must be separated by at least MinimumDifference in everything pertaining to this schedule.

<br />

__ScheduleProperties__

|Column|Type|Key|Nullable|
|--|--|--|--|
|SchedulePropertyId|Guid|Primary key|false|
|ScheduleId|long|Foreign Key(Schedules)|false|
|Name|string(512)|Index|false|
|Value|string(1024)||false|

<br />

__ScheduleStarts__

|Column|Type|Key|Nullable|
|--|--|--|--|
|ScheduleStartId|Guid|Primary Key|false|
|ScheduleId|long|Foreign Key(Schedules)|false|
|Name|string(255)||false|
|Start|DateTimeOffset||false|
|Type|Enum(Interval,DayOfWeek,Date)||false|
|DurationMinutes|int||true|
|ValueMin|double||false|
|ValueMax|double||true|

Note: ValueMin and ValueMax are the same concepts as DefaultValueMin and DefaultValueMax in Schedules.