# Flutter KApp 🚀

[![GitHub License](https://img.shields.io/github/license/kuloud/flutter_kapp)](https://github.com/kuloud/flutter_kapp/blob/main/LICENSE)
[![Flutter Version](https://img.shields.io/badge/flutter-3.24.5-blue)](https://flutter.dev)
[![Dart Version](https://img.shields.io/badge/dart-3.5.4-blue)](https://dart.dev)

一款由Flutter样板工程，集成企业级应用常用功能模块，助力快速启动新项目。

## 🌟 功能特性

- **核心架构**
  - 响应式状态管理：Riverpod
  - 路由导航：go_router（支持深链接）
  - 网络层封装：Dio + 拦截器 + 连接状态检查
  - 本地化方案：intl + ARB文件管理
  - 主题系统：动态切换明暗模式

- **实用工具**
  - 设备信息获取
  - 屏幕适配方案（基于屏幕宽度）
  - 通用扩展方法（字符串/日期/数字处理）
  - 日志系统（分级输出+文件记录）
  - 全局异常捕获

- **业务模块**
  - 用户认证流程（登录/注册/找回密码）
  - RESTful API集成示例
  - 本地数据缓存（Hive/SharedPreferences）
  - 权限管理（地理位置/相机等）
  - 文件上传/下载管理

- **工程化支持**
  - 持续集成流水线（GitHub Actions）
  - 多环境配置（dev/prod）
  - 代码规范检查（lint）
  - 单元测试/Widget测试示例

## 🚀 快速开始

### 环境要求
- Flutter 3.24.5+
- Dart 3.5.4+

### 安装步骤
```bash
git clone https://github.com/kuloud/flutter_kapp.git
cd flutter_kapp
flutter pub get
```

### 运行项目
```bash
# 开发环境
flutter run --flavor dev

# 生产环境
flutter run --flavor prod
```

### 环境配置
复制`.env.example`文件并重命名：
```bash
cp .env.example .env
```
根据实际需求修改环境变量：
```ini
BASE_URL=YOUR_API_ENDPOINT
MAP_API_KEY=YOUR_GOOGLE_MAPS_KEY
SENTRY_DSN=YOUR_SENTRY_DSN
```

## 📁 项目结构
```
lib/
├── common/          # 通用常量/枚举
├── generated/       # 代码生成文件
├── l10n/            # 国际化资源
├── models/          # 数据模型
├── pages/           # 页面组件
├── providers/       # 状态管理
├── services/        # 业务服务
├── utils/           # 工具类
│   ├── extensions   # Dart扩展
│   ├── helpers      # 通用帮助类
│   └── validators   # 表单验证
└── widgets/         # 通用Widget库
```

## 📦 主要依赖
| 包名称              | 用途                  |
|---------------------|---------------------|
| flutter_riverpod    | 状态管理            |
| go_router           | 高级路由方案        |
| dio                 | 网络请求            |
| hive                | 本地数据库          |
| intl                | 国际化支持          |
| flutter_dotenv      | 环境变量管理        |
| logger              | 日志记录            |
| connectivity_plus   | 网络状态检测        |

## 🤝 参与贡献
欢迎通过Issue或PR参与项目改进：
1. Fork项目仓库
2. 创建特性分支 (`git checkout -b feature/your-feature`)
3. 提交修改 (`git commit -m 'Add some feature'`)
4. 推送到分支 (`git push origin feature/your-feature`)
5. 创建Pull Request

## 📄 开源协议
本项目遵循 [MIT License](LICENSE)

---
**Created with ❤️ by kuloud** - 如有问题请提交Issue或联系kuloud@example.com
```

这个README模板包含：
1. 醒目的徽章展示关键信息
2. 功能模块的清晰分类
3. 详细的运行配置说明
4. 直观的目录结构说明
5. 主要依赖表
6. 标准化的贡献流程
7. 移动端开发最佳实践
8. 多环境配置指导

可根据实际项目需求调整各模块内容，建议补充以下内容：
1. 添加应用截图到`## 📸 界面预览`部分
2. 在`services/`目录说明中添加API服务示例
3. 增加测试覆盖率徽章（需要配置CI）
4. 补充具体业务模块的文档链接
5. 添加持续集成配置说明
```
