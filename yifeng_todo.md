# Yifeng's GeoLLM Project Progress & TODO

## 📅 日期: 2024年12月19日

## 🎯 项目目标
重现和扩展GeoLLM项目，从大语言模型中提取地理空间知识

## ✅ 已完成的工作

### 1. 环境设置
- [x] 克隆GeoLLM仓库: `git clone git@github.com:lauyihong/GeoLLM.git`
- [x] 解决SSH连接问题 (GitHub密钥认证)
- [x] 安装Miniconda3
  - 下载: `wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`
  - 安装: `./miniconda.sh`
  - 初始化: `conda init bash`
- [x] 创建conda环境
  - 原始环境文件有兼容性问题 (macOS vs Linux)
  - 创建了 `environment_simple.yml` 简化版本
  - 成功创建 `geospatial` 环境
- [x] 验证环境: `python -c "import geopandas; print('GeoLLM environment is ready')"`

### 2. 代码管理
- [x] 提交更改到本地仓库
- [x] 推送到fork仓库: `git push origin main`
- [x] 添加了 `environment_simple.yml` 文件

## 📁 项目结构

### 数据文件
- `data/povmap_global_subnational_infant_mortality_rates_v2_01.tif` - 婴儿死亡率数据
- `data/ppp_2020_1km_Aggregated.tif` - 人口密度数据

### 提示文件
- `prompts/100000_prompts.jsonl` - 10万个全球位置提示
- `prompts/world_prompts.jsonl` - 2000个世界可视化提示
- `prompts/bay_area_prompts.jsonl` - 湾区位置提示

### 主要脚本
- `make_predictions_and_visualize.py` - 主要预测和可视化脚本
- `select_visualization_prompts.py` - 选择可视化提示
- `calculate_spearman_correlation.py` - 计算相关性
- `calculate_bias_score.py` - 计算偏差分数

## 🚀 下一步计划

### 短期目标 (下次会话)
1. **获取API密钥**
   - [ ] OpenAI API密钥
   - [ ] Google API密钥 (可选)
   - [ ] Together API密钥 (可选)

2. **运行第一个测试**
   - [ ] 使用世界提示进行人口密度预测
   - [ ] 生成可视化地图
   - [ ] 验证结果质量

3. **探索项目功能**
   - [ ] 测试不同的地理任务
   - [ ] 尝试不同的LLM模型
   - [ ] 理解预测结果

### 中期目标
1. **数据探索**
   - [ ] 分析婴儿死亡率数据
   - [ ] 分析人口密度数据
   - [ ] 生成自定义提示

2. **偏差分析**
   - [ ] 运行偏差评估脚本
   - [ ] 分析LLM的地理偏差
   - [ ] 比较不同模型的偏差

3. **自定义实验**
   - [ ] 为特定地区生成提示
   - [ ] 测试新的地理任务
   - [ ] 创建自定义可视化

### 长期目标
1. **模型微调** (如果有ground truth数据)
   - [ ] 准备微调数据
   - [ ] 训练微调模型
   - [ ] 评估微调效果

2. **扩展研究**
   - [ ] 探索新的地理空间任务
   - [ ] 分析不同LLM的性能差异
   - [ ] 开发新的评估指标

## 🔧 技术细节

### 环境信息
- **操作系统**: Linux 6.8.0-60-generic
- **Python版本**: 3.9 (conda环境)
- **主要依赖**: geopandas, rasterio, folium, openai, google-generativeai, together

### 命令备忘
```bash
# 激活环境
conda activate geospatial

# 运行预测
python make_predictions_and_visualize.py openai YOUR_API_KEY gpt-3.5-turbo-0613 prompts/world_prompts.jsonl "Population Density"

# 选择提示
python select_visualization_prompts.py prompts/100000_prompts.jsonl prompts/selected_prompts.jsonl 2000 ""

# 计算相关性
python calculate_spearman_correlation.py results/predictions.csv data/ground_truth.tif
```

## 📝 笔记和想法
- 原始环境文件是为macOS设计的，在Linux上需要简化
- 项目支持多种API (OpenAI, Google, Together)
- 可以生成交互式HTML地图
- 支持偏差分析和相关性评估

## 🎯 下次会话重点
1. 设置API密钥
2. 运行第一个完整的预测流程
3. 理解输出结果和可视化
4. 规划具体的实验方向

---
*最后更新: 2024年12月19日* 