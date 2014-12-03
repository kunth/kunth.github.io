---
layout: post
title: Linux cron scripts 
description: Linux
category: blog
---

1. 创建cron脚本，如test-cron.cron

2. 内容为 

''' shell
SHELL=/bin/bash
*/1 * * * * cd /home/fibonacci && echo 'xxx' >> crontxt.txt
'''

（前5个*分别表示minute, hour, mday, month, wday）
minute：代表一小时内的第几分，范围 0-59。 
hour：代表一天中的第几小时，范围 0-23。 
mday：代表一个月中的第几天，范围 1-31。 
month：代表一年中第几个月，范围 1-12。 
wday：代表星期几，范围 0-7 (0及7都是星期天)。 

*/1，在第一个位置，表示每过一分钟，依次类推

3. crontab test-cron.cron

4. crontab -l 查询是否成功，之后可以删去test-cron.cron文件了，用命令crontab -e直接修改。

5. 可去指定目录 /home/fibonacci 查看是否存在文件crontxt.txt，并看每过一分钟是否有一行新的‘xxx’



