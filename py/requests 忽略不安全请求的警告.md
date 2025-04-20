> 使用 `requests` 时，如果禁用了 SSL 验证（verify=False），控制台输出时会有警告信息，强迫症看着很难受

忽略警告信息：
```
import warnings

# 忽略不安全请求的警告（仅用于测试目的）
warnings.filterwarnings('ignore', message='Unverified HTTPS request')
```
