# Kepler.gl 系统架构与功能分析

## 项目概述
Kepler.gl 是一个基于 MapLibre GL 和 deck.gl 的地理数据可视化工具，支持百万级数据点渲染和空间聚合。它提供了丰富的交互功能，使用户能够轻松地探索、分析和可视化地理空间数据。

## 技术栈
- **前端框架**: React
- **状态管理**: Redux
- **地图渲染**: MapLibre GL, deck.gl
- **编程语言**: TypeScript, JavaScript
- **构建工具**: Webpack, Babel
- **测试框架**: Jest

## 系统架构
Kepler.gl 采用模块化架构，主要包含以下核心模块：

### 1. 核心模块
- **components**: 包含所有 UI 组件，如地图容器、控制面板、图层管理器等
- **reducers**: Redux reducer 实现，管理应用状态
- **actions**: Redux action 创建器
- **schemas**: 数据结构定义和验证
- **processors**: 数据处理逻辑
- **layers**: 地图图层实现
- **styles**: 样式定义
- **utils**: 工具函数

### 2. 扩展模块
- **ai-assistant**: AI 辅助功能
- **cloud-providers**: 云服务提供商集成
- **duckdb**: 数据处理引擎集成
- **effects**: 视觉效果实现
- **localization**: 国际化支持
- **table**: 数据表格组件
- **tasks**: 任务管理
- **types**: TypeScript 类型定义

### 3. 文件结构
```
kepler.gl/
├── src/
│   ├── actions/
│   ├── ai-assistant/
│   ├── cloud-providers/
│   ├── components/
│   ├── constants/
│   ├── deckgl-arrow-layers/
│   ├── deckgl-layers/
│   ├── duckdb/
│   ├── effects/
│   ├── layers/
│   ├── localization/
│   ├── processors/
│   ├── reducers/
│   ├── schemas/
│   ├── styles/
│   ├── table/
│   ├── tasks/
│   ├── types/
│   └── utils/
├── examples/
├── docs/
└── website/
```

## 核心功能
1. **数据可视化**
   - 支持多种图层类型（点、线、面、热力图等）
   - 百万级数据点高效渲染
   - 空间聚合和分析功能

2. **地图交互**
   - 缩放、平移、旋转等基本地图操作
   - 图层切换和配置
   - 地图样式自定义

3. **数据处理**
   - 数据导入和导出
   - 数据过滤和转换
   - 数据统计分析

4. **UI 组件**
   - 可折叠侧边栏
   - 模态对话框
   - 时间轴控制器
   - 图例和颜色选择器

## 使用方法
1. 安装依赖
```bash
npm install @kepler.gl/components @kepler.gl/reducers @kepler.gl/actions @kepler.gl/schemas
```

2. 基本配置
```javascript
import { KeplerGl } from '@kepler.gl/components';
import { createStore, combineReducers } from 'redux';
import { keplerGlReducer } from '@kepler.gl/reducers';

// 创建 Redux store
const store = createStore(
  combineReducers({
    keplerGl: keplerGlReducer
  })
);

// 在应用中使用 KeplerGl 组件
function App() {
  return (
    <KeplerGl
      id="map"
      mapboxApiAccessToken="YOUR_MAPBOX_TOKEN"
      width={window.innerWidth}
      height={window.innerHeight}
    />
  );
}
```

## 总结
Kepler.gl 是一个功能强大的地理数据可视化工具，采用模块化架构设计，基于 React 和 Redux 构建。它提供了丰富的地图交互和数据处理功能，适用于各种地理空间数据可视化场景。其模块化设计使得开发者可以根据需求灵活使用和扩展。