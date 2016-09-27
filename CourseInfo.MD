# 课程信息

### 瑜伽课程信息Api设计思路

CourseInfo API 是一类简单的HTTP接口，用于返回查询瑜伽课程数据，且提供单个课程的详情查询服务，用户可以使各种语言发送HTTP请求且接收json、xml的数据

服务地址：http://api.yoga.o3onet.com/course/v1/info

通用接口参数 以下参数，适用于三种区域检索方法的Place API.

| 参数        | 是否必须   |  默认值  |  格式举例  |  含义  |
| --------   | -----  | ----  | ----  | ----  |
|appid| 是|无|100123|查询课程信息时，app的ID信息|
|  ak |是|无|f3916e1b-0c14-42d8-ade2-a142f8fe9727|用户的访问密钥，必填项。|
|scope|是|1|1,2,3,4，5|检索结果详细程度。取值为1 或空，则返回基本信息；取值为2，返回课程详细信息；取值为3,返回包含前面信息及课程类别信息(courseTypeInfo)取值为4,返回包含前面信息及页面显示控制信息(pageConfigInfo);取值为5,显示课程所有的信息;取值为6时根据fields的字段来控制|
|  query | 否  |  无 |  空中瑜伽,高温瑜伽 | 检索课程名称。支持多个关键字并集检索。不同关键字间以$符号分隔，最多支持10个关键字检索。如:”空中瑜伽$高温瑜伽” |
|filter|否|无|  filter=course_type_ids:ids |检索过滤条件，当scope取值为2时才会调用这些过滤信息。默认为1时不做过滤排序处理:各个字段间采用竖线分隔。<br/> 【course_type_ids】 课程类别id，注意：设置该字段可提高检索速度和过滤精度，各个Id之间以,分隔开来 。| 
|fields|否|无|默认根据请求字段根据请求格式来|给API消费者一个可以选择字段的能力,各个字段间以,分隔。仅当scope为6时生效。取值为（objectId,appid,courseName,courseDescribe,courseDetailDescribe,courseHourLength,maxOrderNum,maxOrderLineUpNum,imgUrl_courseImg,addressInfoId,courseTypeId,isShowOnPage,pageShowConfig,otherInfoConfig,note）|
|embed|否|无|CourseTypeInfo|自动加载相关资源，仅当SCOPE为6自定义时生效,以逗号为分隔串。值为(AddressInfo,CourseTypeInfo)|
|sort|否|无|courseName|【sort】 排序字段,可以选择多种排序组合方式,排序规则以逗号为分隔,排序方式以+-为区分 取值有： default（默认）；courseName（课程名称）；courseHourLength（课程时长）；maxOrderNum（最大可预约数量）；maxOrderLineUpNum（最大可排队数量）；createAt(创建时间);updateAt(更新时间); |
|page_size|否|20|20|范围记录数量，默认为10条记录，最大返回20条。多关键字检索时，返回的记录数为关键字个数*page_size。|
|page_num|否|0|0、1、2、3|分页页码，默认为0,0代表第一页，1代表第二页，以此类推。|
|output | 否|json|json、xml|输出格式为json或者xml|
|sn	|否|	无	||用户的权限签名。|
|timestamp|	否|	无|1474924259	|设置sn后该值必填。|




> 

