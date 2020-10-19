## Table Schema
![Table Relationships](Schema.svg)
<br />
<br />

__Schedules__

|Column|Type|Key|Nullable|
|--|--|--|--|
|ScheduleId|long|Primary Key|false|
|LocalDeviceId|Guid|Foreign Key(Devices)|false|
|ScheduleKey|Guid|Index|false|
|DefaultValue|double||false|

<br />

__Devices__

|Column|Type|Key|Nullable|
|--|--|--|--|
|LocalDeviceId|Guid|Primary Key|false|
|DeviceId|int|Virtual Foreign Key(Devices Service)|false|
|Uuid|Guid|Index(Uuid)|true|
|MacAddress|long|Index(MacAddress)|true|
|Manufacture|string|Index(Manufacture, ManufactureId)|true|
|ManufactureId|string|Index(Manufacture, ManufactureId)|true|

<br />

__ScheduleProperties__

|Column|Type|Key|Nullable|
|--|--|--|--|
|SchedulePropertyId|Guid|Primary key|false|
|ScheduleId|long|Foreign Key(Schedules)|false|
|Name|string(512)|Index|false|
|Value|string(1024)||true|

<br />

__ScheduleStarts__

|Column|Type|Key|Nullable|
|--|--|--|--|
|ScheduleStartId|Guid|Primary Key|false|
|ScheduleId|long|Foreign Key(Schedules)|false|
|Name|string(255)||false|
|Start|DateTimeOffset||false|
|Type|Enum(DayOfWeek,Interval,Date,Length)||false|
|Duration|int||true|
|Value|double||false|