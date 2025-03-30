# PDF2MD Node.js

<p align="center">
  <img src="https://img.shields.io/badge/node-%3E%3D%2016.0.0-brightgreen" alt="Node.js Version">
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="License">
</p>

A powerful Node.js tool for converting PDF documents to Markdown format using advanced vision models. PDF2MD extracts text, tables, and images from PDFs and generates well-structured Markdown documents.

[中文文档](README.zh-CN.md)

## ✨ Features

- **Full Page Processing**: Convert entire PDF pages to high-quality images for processing
- **Visual Model Integration**: Leverage state-of-the-art vision models for accurate text extraction
- **Multiple Model Support**: Compatible with OpenAI, Claude, Gemini, and Doubao vision models
- **Structured Output**: Generate clean, well-formatted Markdown documents
- **Customizable**: Configure image quality, processing options, and output format

## 🚀 Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/pdf2md.git
cd pdf2md/pdf2md-node

# Install dependencies
npm install
```

## 📋 Requirements

- Node.js 16.0.0 or higher
- API key for at least one of the supported vision models

## 🔧 Usage

### Basic Usage

```javascript
import { parsePdf } from './src/index.js';

const result = await parsePdf('path/to/your.pdf', {
  apiKey: 'your-api-key',
  model: 'gpt-4-vision-preview',
  useFullPage: true // Use full page processing mode
});

console.log(`Markdown file generated: ${result.mdFilePath}`);
```

### Configuration Options

```javascript
const options = {
  // Output directory for generated files
  outputDir: './output',
  
  // API key for the vision model
  apiKey: 'your-api-key',
  
  // API endpoint (if using a custom endpoint)
  baseUrl: 'https://api.example.com/v1',
  
  // Vision model to use
  model: 'gpt-4-vision-preview',
  
  // Custom prompt for the vision model
  prompt: 'Convert this PDF to well-structured Markdown',
  
  // Whether to use full page processing (recommended)
  useFullPage: true,
  
  // Whether to keep intermediate image files
  verbose: false,
  
  // Image scaling factor (higher = better quality but slower)
  scale: 3
};

const result = await parsePdf('path/to/your.pdf', options);
```

## 🔍 Supported Models

| Provider | Models |
|----------|--------|
| OpenAI   | `gpt-4-vision-preview`, `gpt-4o` |
| Claude   | `claude-3-opus-20240229`, `claude-3-sonnet-20240229` |
| Gemini   | `gemini-pro-vision` |
| Doubao   | `doubao-1.5-vision-pro-32k-250115` |

## 🧪 Testing

The project includes several test scripts to verify functionality:

```bash
# Test the full PDF to Markdown conversion process
node test/testFullProcess.js

# Test only the PDF to image conversion
node test/testFullPageImages.js

# Test specific vision models
node test/testModel.js
```

## 📁 Project Structure

```
pdf2md-node/
├── src/
│   ├── index.js          # Main entry point
│   ├── pdfParser.js      # PDF parsing module
│   ├── imageGenerator.js # Image generation module
│   ├── modelClient.js    # Vision model client
│   ├── markdownConverter.js # Markdown conversion module
│   └── utils.js          # Utility functions
├── test/
│   ├── samples/          # Sample PDF files for testing
│   ├── testFullProcess.js # Full process test
│   └── ... (other test files)
└── package.json
```

## 🔄 Module Architecture

PDF2MD consists of the following core modules, each responsible for specific functionality:

### 1. Main Entry Module (index.js)

Coordinates the entire system:
- Receives user input (PDF path and configuration options)
- Sequentially calls other modules to complete the conversion process
- Returns the final Markdown result

### 2. PDF Parser Module (pdfParser.js)

Parses PDF files and extracts structured information:
- Uses PDF.js library to load PDF files
- Extracts text content, images, and graphic elements from each page
- Generates a list of rectangular areas, each representing a content block in the PDF

### 3. Image Generator Module (imageGenerator.js)

Renders PDF areas as images:
- Uses PDF.js rendering engine to render specified areas as high-definition images
- Supports adjustable scaling ratios to ensure image clarity
- Uses Sharp library to process and optimize images

### 4. Model Client Module (modelClient.js)

Interacts with various vision model APIs:
- Supports multiple vision models: OpenAI, Claude, Gemini, Doubao, etc.
- Provides a unified API calling interface, encapsulating features of different models
- Handles API call errors and retry mechanisms

### 5. Markdown Converter Module (markdownConverter.js)

Converts model results to standard Markdown format:
- Processes text content returned by the model
- Formats according to Markdown syntax standards
- Merges Markdown content from multiple areas

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

<a id="pdf2md-nodejs-中文版"></a>

# PDF2MD Node.js (中文版)

<p align="center">
  <img src="https://img.shields.io/badge/node-%3E%3D%2016.0.0-brightgreen" alt="Node.js 版本">
  <img src="https://img.shields.io/badge/license-MIT-blue" alt="许可证">
</p>

一个强大的Node.js工具，使用先进的视觉模型将PDF文档转换为Markdown格式。PDF2MD从PDF中提取文本、表格和图像，并生成结构良好的Markdown文档。

## ✨ 功能特点

- **全页处理**：将整个PDF页面转换为高质量图像进行处理
- **视觉模型集成**：利用最先进的视觉模型进行精确的文本提取
- **多模型支持**：兼容OpenAI、Claude、Gemini和豆包视觉模型
- **结构化输出**：生成干净、格式良好的Markdown文档
- **可定制**：配置图像质量、处理选项和输出格式

## 🚀 安装

```bash
# 克隆仓库
git clone https://github.com/yourusername/pdf2md.git
cd pdf2md/pdf2md-node

# 安装依赖
npm install
```

## 📋 系统要求

- Node.js 16.0.0 或更高版本
- 至少一个支持的视觉模型的API密钥

## 🔧 使用方法

### 基本用法

```javascript
import { parsePdf } from './src/index.js';

const result = await parsePdf('path/to/your.pdf', {
  apiKey: 'your-api-key',
  model: 'gpt-4-vision-preview',
  useFullPage: true // 使用全页处理模式
});

console.log(`Markdown文件已生成：${result.mdFilePath}`);
```

### 配置选项

```javascript
const options = {
  // 生成文件的输出目录
  outputDir: './output',
  
  // 视觉模型的API密钥
  apiKey: 'your-api-key',
  
  // API端点（如果使用自定义端点）
  baseUrl: 'https://api.example.com/v1',
  
  // 要使用的视觉模型
  model: 'gpt-4-vision-preview',
  
  // 视觉模型的自定义提示
  prompt: '将此PDF转换为结构良好的Markdown',
  
  // 是否使用全页处理（推荐）
  useFullPage: true,
  
  // 是否保留中间图像文件
  verbose: false,
  
  // 图像缩放因子（更高 = 更好的质量但更慢）
  scale: 3
};

const result = await parsePdf('path/to/your.pdf', options);
```

## 🔍 支持的模型

| 提供商 | 模型 |
|----------|--------|
| OpenAI   | `gpt-4-vision-preview`, `gpt-4o` |
| Claude   | `claude-3-opus-20240229`, `claude-3-sonnet-20240229` |
| Gemini   | `gemini-pro-vision` |
| 豆包     | `doubao-1.5-vision-pro-32k-250115` |

## 🧪 测试

项目包含多个测试脚本以验证功能：

```bash
# 测试完整的PDF到Markdown转换流程
node test/testFullProcess.js

# 仅测试PDF到图像的转换
node test/testFullPageImages.js

# 测试特定视觉模型
node test/testModel.js
```

## 📁 项目结构

```
pdf2md-node/
├── src/
│   ├── index.js          # 主入口点
│   ├── pdfParser.js      # PDF解析模块
│   ├── imageGenerator.js # 图像生成模块
│   ├── modelClient.js    # 视觉模型客户端
│   ├── markdownConverter.js # Markdown转换模块
│   └── utils.js          # 工具函数
├── test/
│   ├── samples/          # 用于测试的示例PDF文件
│   ├── testFullProcess.js # 完整流程测试
│   └── ... (其他测试文件)
└── package.json
```

## 🔄 模块架构

PDF2MD由以下核心模块组成，每个模块负责特定功能：

### 1. 主入口模块 (index.js)

协调整个系统：
- 接收用户输入（PDF路径和配置选项）
- 按顺序调用其他模块完成转换过程
- 返回最终的Markdown结果

### 2. PDF解析模块 (pdfParser.js)

解析PDF文件并提取结构化信息：
- 使用PDF.js库加载PDF文件
- 提取每页的文本内容、图像和图形元素
- 生成矩形区域列表，每个矩形代表PDF中的内容块

### 3. 图像生成模块 (imageGenerator.js)

将PDF区域渲染为图像：
- 使用PDF.js渲染引擎将指定区域渲染为高清图像
- 支持可调节的缩放比例，确保图像清晰度
- 使用Sharp库处理和优化图像

### 4. 模型客户端模块 (modelClient.js)

与各种视觉模型API交互：
- 支持多种视觉模型：OpenAI、Claude、Gemini、豆包等
- 提供统一的API调用接口，封装不同模型的特性
- 处理API调用错误和重试机制

### 5. Markdown转换模块 (markdownConverter.js)

将模型结果转换为标准Markdown格式：
- 处理模型返回的文本内容
- 按照Markdown语法标准格式化
- 合并多个区域的Markdown内容

## 📄 许可证

本项目采用MIT许可证 - 详情请参阅LICENSE文件。

## 数据流程与模块协作

PDF到Markdown的转换过程按照以下流程进行：

1. **输入处理**：主入口模块接收PDF文件路径和配置选项

2. **PDF解析**：
   - `pdfParser.js` 加载PDF文件
   - 提取每一页的内容元素
   - 生成初始矩形区域列表

3. **矩形处理**：
   - `rectProcessor.js` 接收初始矩形列表
   - 调用 `mergeRects` 函数合并相近的矩形
   - 调用 `adsorbRects` 函数吸附小矩形
   - 调用 `filterSmallRects` 函数过滤小矩形
   - 返回优化后的矩形列表

4. **图像生成**：
   - `imageGenerator.js` 接收优化后的矩形列表
   - 对每个矩形区域调用 `renderRectToImage` 函数
   - 生成高清图像并保存
   - 返回图像路径列表

5. **模型识别**：
   - `modelClient.js` 接收图像路径列表
   - 根据配置选择适当的视觉模型
   - 调用模型 API对图像进行内容识别
   - 返回模型分析结果

6. **Markdown转换**：
   - `markdownConverter.js` 接收模型分析结果
   - 将结果转换为标准Markdown格式
   - 按照区域在PDF中的位置合并内容
   - 生成最终的Markdown文档

7. **输出结果**：主入口模块返回最终的Markdown内容

## 实现原理

1. **PDF解析与区域识别**：使用PDF.js解析PDF文件，识别出文档中的文本区域、图片区域和绘图元素

2. **区域分割与合并**：将相近的区域合并，识别出PDF中的逻辑块

3. **区域转图像**：将每个识别出的区域转换为高清图像

4. **图像OCR与解析**：使用视觉模型API对生成的图像进行内容识别和转换为Markdown

5. **结果合并**：将所有区域的Markdown内容合并成完整的文档
