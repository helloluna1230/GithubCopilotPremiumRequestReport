# GitHub Copilot Premium Request Report

## 项目简介 / Project Overview

这是一个用于分析 GitHub Copilot Premium 用户模型使用情况的工具。该工具可以分析用户对不同AI模型的使用情况，特别是 GPT-4.1 与其他模型的使用对比，并生成详细的分析报告。

This is a tool for analyzing GitHub Copilot Premium user model usage. It analyzes user usage patterns across different AI models, particularly comparing GPT-4.1 usage versus other models, and generates detailed analysis reports.

## 功能特性 / Features

- 📊 **用户使用情况分析** - 按总使用量排序的用户模型使用分析
- 🏆 **TOP 10 用户详细分布** - 显示前10名用户的详细模型使用分布
- 📈 **整体模型分布统计** - 所有模型的使用情况统计和占比分析
- 📋 **多格式报告输出** - 支持控制台输出、Excel文件和HTML可视化报告
- 🔍 **详细统计汇总** - 包含用户数、模型数、请求数等关键指标

## 系统要求 / Requirements

- Python 3.6+
- pandas
- openpyxl (用于Excel导出)

## 安装 / Installation

1. 克隆仓库 / Clone the repository:
```bash
git clone https://github.com/helloluna1230/GithubCopilotPremiumRequestReport.git
cd GithubCopilotPremiumRequestReport
```

2. 安装依赖 / Install dependencies:

使用 requirements.txt (推荐):
```bash
pip install -r requirements.txt
```

或者手动安装:
```bash
pip install pandas openpyxl
```

## 使用方法 / Usage

### 1. 准备数据文件 / Prepare Data File

确保你有一个包含以下列的 CSV 文件：
- `User` - 用户名
- `Model` - 使用的AI模型名称
- `Requests Used` - 请求使用次数
- `Timestamp` (可选) - 时间戳

Make sure you have a CSV file with the following columns:
- `User` - Username
- `Model` - AI model name used
- `Requests Used` - Number of requests used
- `Timestamp` (optional) - Timestamp

### 2. 修改文件路径 / Modify File Path

**重要：** 在运行脚本之前，需要修改源码中的CSV文件路径。

编辑 `analyze_model_usage_fixed.py` 文件，找到第538行左右的代码：

```python
csv_file = r"c:\github\githubcopilotdemo\模型分析\premium_usage_report_1_3393962b1602425fa286985f6f37b7c5.csv"
```

将其修改为你的CSV文件的实际路径：

```python
csv_file = r"your_csv_file_path_here.csv"
```

**Important:** Before running the script, you need to modify the CSV file path in the source code.

Edit the `analyze_model_usage_fixed.py` file and locate the code around line 538:

```python
csv_file = r"c:\github\githubcopilotdemo\模型分析\premium_usage_report_1_3393962b1602425fa286985f6f37b7c5.csv"
```

Change it to your actual CSV file path:

```python
csv_file = r"your_csv_file_path_here.csv"
```

### 3. 运行分析 / Run Analysis

```bash
python analyze_model_usage_fixed.py
```

## 输出报告 / Output Reports

运行脚本后，将生成以下报告：

### 1. 控制台输出 / Console Output
- 用户模型使用情况分析表格
- TOP 10 用户详细模型分布
- 整体模型使用分布统计
- 统计汇总信息

### 2. Excel 文件 / Excel File
生成 `*_detailed_analysis.xlsx` 文件，包含两个工作表：
- **用户汇总** - 每个用户的汇总统计
- **详细分布** - 每个用户每个模型的详细使用情况

### 3. HTML 报告 / HTML Report  
生成 `*_analysis_report.html` 文件，包含：
- 可视化的统计仪表板
- 交互式用户排名表格
- TOP 10 用户详细分布卡片
- 整体模型使用分布图表

## 输出示例 / Output Examples

### 控制台输出示例 / Console Output Example
```
开始分析用户模型使用情况...
正在读取文件: your_file.csv
总记录数: 1234
时间范围: 2024-01-01 到 2024-01-31

====================================================================================================
用户模型使用情况分析报告
====================================================================================================
用户名               GPT-4.1请求数    GPT-4.1占比   其他模型请求数       其他模型占比      总请求数    
----------------------------------------------------------------------------------------------------
user1                150.00          75.00%        50.00               25.00%          200.00
user2                120.00          80.00%        30.00               20.00%          150.00
...
```

### 关键指标说明 / Key Metrics

- **GPT-4.1 请求数** - 用户使用 GPT-4.1 模型的总请求数
- **GPT-4.1 占比** - GPT-4.1 请求数占用户总请求数的百分比
- **其他模型请求数** - 用户使用除 GPT-4.1 外其他模型的总请求数
- **其他模型占比** - 其他模型请求数占用户总请求数的百分比
- **总请求数** - 用户的所有模型请求总和

## 数据文件格式示例 / Sample Data Format

```csv
User,Model,Requests Used,Timestamp
john.smith,gpt-4.1-preview,25.5,2024-01-15 10:30:00
john.smith,claude-3-opus,10.2,2024-01-15 11:45:00
jane.doe,gpt-4.1-preview,30.8,2024-01-15 14:20:00
jane.doe,gemini-pro,5.1,2024-01-15 15:30:00
```

## 注意事项 / Notes

1. **文件路径** - 确保 CSV 文件路径正确，支持中文路径
2. **数据格式** - 请求使用次数应为数值类型
3. **模型识别** - 脚本通过模型名称是否包含 "gpt-4.1" 来区分 GPT-4.1 和其他模型
4. **内存使用** - 大文件可能需要较多内存，建议分批处理超大数据集

## 故障排除 / Troubleshooting

### 常见错误 / Common Errors

**错误**: `找不到文件`
**解决**: 检查文件路径是否正确，确保文件存在

**错误**: `缺少必要的列`
**解决**: 确保CSV文件包含 User, Model, Requests Used 列

**错误**: `CSV文件为空`
**解决**: 检查CSV文件是否有数据内容

**错误**: `导出Excel文件时出现错误`
**解决**: 确保安装了 openpyxl 库: `pip install openpyxl`

## 贡献 / Contributing

欢迎提交问题报告和功能请求。如果你想要贡献代码：

1. Fork 这个仓库
2. 创建你的功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交你的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启一个 Pull Request

## 许可证 / License

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

---

## 更新日志 / Changelog

### v1.0.0
- 初始版本发布
- 支持用户模型使用情况分析
- 生成 Excel 和 HTML 格式报告
- 提供详细的统计分析功能