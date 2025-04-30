# Chineseholiday Card
下面图片是我个人自己修改后的版本. master那个branch. 有需要自己下载. 

![20250430214858](https://github.com/user-attachments/assets/d5748856-537e-456f-8305-348e9f0ae310)



更改内容:
1. 背景去掉, 用透明
2. 调整时钟的位置和格式.
3. 调整部分间距,让卡片内容看起来更紧凑些.
4. 新增问候语部分以及可自定义部分问候语
5. 增加字体颜色自适应不同颜色的主题。
6. 新增每日一句激励语（仅支持中文句子，其他可以提供中英互译句子和图片+英文句子语音播放，每日一句参考https://github.com/WalterDSU/ha_daily_english）
7. 增加显示日期的星期几
8. 增加周数显示
9. 优化节假日放假详情显示

配合插件一起使用. 这只是一个卡片.
https://github.com/Crazysiri/chineseholiday

注意：新增的每日一句需要在configuration.yaml添加下面senor，来提供每日一句的内容获取, 需要重新HA，并确定sensor.daily_english正常显示，每日一句参考https://github.com/WalterDSU/ha_daily_english。
```
sensor：
  - platform: rest
    name: daily_english
    resource: http://open.iciba.com/dsapi
    value_template: >-
          {% if value_json.dateline == states("sensor.date")  -%}
            有效
          {% else %}
            无效
          {% endif %}
    scan_interval: 10800
    json_attributes:
      - content
      - note
      - picture
      - tts
