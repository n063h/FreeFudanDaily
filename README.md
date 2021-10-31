# 平安复旦自动打卡

使用GitHub Actions实现全自动打卡。
Fork并修改自某已被和谐的FudanDaily,请不要设置为public.

## 如何使用
1. Fork 本代码库
2. 配置 Secret  
   在 Settings - Secret 页面添加如下内容：
   - USERNAME: 学号
   - PASSWORD: UIS密码
   - PUSH_KEY[可选]: Server酱SCKEY，用于推送通知，详见[http://sc.ftqq.com/](http://sc.ftqq.com/)，建议开启，可以通过微信接收打卡状态。
   - API_KEY:百度文字识别API应用API Key
   - SECRET_KEY:百度文字识别API应用Secret Key
3. 修改[work.yml](./.github/workflow/work.yml)中的`cron`为你喜欢的打卡时间(UTC)。GitHub Actions运行会有15分钟以内的延迟，请配合Server酱通知使用。
4. 开启 Workflow  
   在 Actions 页面：
   - 开启 Workflows
   - 选择 `Fudan Daily` workflow, enable workflow

## 说明
- 打卡时使用前一日地理位置信息。
- 打卡前会检测当日是否已打卡，避免重复提交。
- 如需变更打卡位置请提前停止自动打卡，到新位置手动打卡一次再开启（或赶在自动打卡时间前手动打卡）。
- 未经充分测试，不保证最终效果，请酌情使用。
- 添加CaptchaDaily功能,使用百度OCR API -- https://ai.baidu.com/tech/ocr/general
- 百度OCR API使用方法:
  - 注册,登录
  - 领取免费额度 -- https://console.bce.baidu.com/ai/#/ai/ocr/overview/resource/getFree
  - 控制台创建OCR应用 -- https://console.bce.baidu.com/ai/?fromai=1#/ai/ocr/overview/index
  - 进入控制台应用管理界面,获取API_KEY和SECRET_KEY
