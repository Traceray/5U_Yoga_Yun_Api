# 课程信息

### 瑜伽课程信息Api设计思路

CourseInfo API 是一类简单的HTTP接口，用于返回查询瑜伽课程数据，且提供单个课程的详情查询服务，用户可以使各种语言发送HTTP请求且接收json、xml的数据

服务地址：http://api.yoga.o3onet.com/course/v1/info

通用接口参数 以下参数，适用于三种区域检索方法的Place API.

| 参数        | 是否必须   |  默认值  |  格式举例  |  含义  |
| --------   | -----  | ----  | ----  | ----  |
|appid| 是|无|100123|查询课程信息时，app的ID信息|
|  ak |是|无|f3916e1b-0c14-42d8-ade2-a142f8fe9727|用户的访问密钥，必填项。|
|scope|是|1|1,2,3,4，5|检索结果详细程度。取值为1 或空，则返回基本信息；取值为2，返回课程详细信息；取值为3,返回包含前面信息及课程类别信息(courseTypeInfo)取值为4,返回包含前面信息及页面显示控制信息(pageConfigInfo);取值为5,显示课程所有的信息|
|  query | 否  |  无 |  空中瑜伽,高温瑜伽 | 检索课程名称。支持多个关键字并集检索。不同关键字间以$符号分隔，最多支持10个关键字检索。如:”空中瑜伽$高温瑜伽” |
|filter|否|无|  filter=course_type_ids:ids!sort_name:courseName!sort_rule:1 |检索过滤条件，当scope取值为2时才会调用这些过滤信息。默认为1时不做过滤排序处理:采用竖线分隔。<br/> 【course_type_ids】 课程类别id，注意：设置该字段可提高检索速度和过滤精度，各个Id之间以,分隔开来 。 【sort_name】 排序字段 取值有： default（默认）；courseName（课程名称）；courseHourLength（课程时长）；maxOrderNum（最大可预约数量）；maxOrderLineUpNum（最大可排队数量）；createAt;updateAt; 【sort_rule】 排序规则：0（从高到低），1（从低到高）| 



> 

