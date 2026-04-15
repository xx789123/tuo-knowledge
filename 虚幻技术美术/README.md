# 虚幻技术美术部学习资料

> Unreal Engine、Shader、VFX、渲染优化的完整知识库

## 官方文档

### Unreal Engine
- [UE5官方文档](https://docs.unrealengine.com/) - 英文官方文档
- [UE4官方文档](https://docs.unrealengine.com/4.27/zh-CN/) - UE4中文文档
- [Epic官方YouTube](https://www.youtube.com/@UnrealEngine) - 官方视频教程
- [UE5材质系统](https://docs.unrealengine.com/5.0/en-US/Rendering/Materials/) - 材质系统文档
- [Nanite虚拟几何体](https://docs.unrealengine.com/5.0/en-US/Modeling/GIS/) - Nanite文档
- [Lumen动态光照](https://docs.unrealengine.com/5.0/en-US/Rendering/Lumen/) - Lumen文档
- [Niagara粒子系统](https://docs.unrealengine.com/5.0/en-US/Rendering/Niagara/) - Niagara官方文档

## GitHub 热门开源项目

### Unreal Engine资源
- [mikeroyal/Unreal-Engine-Guide](https://github.com/mikeroyal/Unreal-Engine-Guide) - UE全面指南和资源集合
- [mikeroyal/Game-Console-Dev-Guide](https://github.com/mikeroyal/Game-Console-Dev-Guide) - 游戏主机开发指南
- [AR-VR-Guide](https://github.com/mikeroyal/AR-VR-Guide) - AR/VR开发指南
- [tomlooman/EpicSurvivalGame](https://github.com/tomlooman/EpicSurvivalGame) - UE多人合作游戏示例
- [EGardeur/UE5_Minimal](https://github.com/EGardeur/UE5_Minimal) - UE5最小模板

### VFX与Niagara
- [Shadertech/UE5NiagaraComputeShaderIntegration](https://github.com/Shadertech/UE5NiagaraComputeShaderIntegration) - Niagara计算着色器集成示例
- [NiagaraModules](https://github.com/niagara-modules) - Niagara模块化资源
- [TomAngusDev/Niagara-Tutorials](https://github.com/TomAngusDev/Niagara-Tutorials) - Niagara教程集合
- [UnrealEngineCPP/UE4-Niagara-Examples](https://github.com/UnrealEngineCPP/UE4-Niagara-Examples) - UE4 Niagara示例

### Shader与渲染
- [shadertech/UE5ShaderExamples](https://github.com/shadertech/UE5ShaderExamples) - UE5着色器示例
- [Kh幸创太郎/VirtualGeometryPerformance](https://github.com/Kh幸创太郎/VirtualGeometryPerformance) - 虚拟几何体性能研究
- [ TemporalReprojectionAntiAliasing](https://github.com/TemporalReprojectionAntiAliasing) - 时间重投影抗锯齿

### 地理仿真与Cesium
- [CesiumGS/cesium-unreal](https://github.com/CesiumGS/cesium-unreal) - Cesium for Unreal插件 (2k stars)
- [CesiumGS/cesium-native](https://github.com/CesiumGS/cesium-native) - Cesium原生库
- [CesiumGS/3d-tiles](https://github.com/CesiumGS/3d-tiles) - 3D Tiles规范
- [NVIDIA/Meshroom](https://github.com/alicevision/meshroom) - 3D重建工具

### 开源UE插件
- [GASDocumentation/GASDocumentation](https://github.com/tranek/GASDocumentation) - Gameplay Ability System文档 (2k stars)
- [RyRoLiey/EspreeVehicleTemplate](https://github.com/RyRoLiey/EspreeVehicleTemplate) - UE载具模板
- [Neon's Level Design](https://github.com/neons0/Stumble): 关卡设计示例

### 工具与调试
- [RenderDoc](https://github.com/baldurk/renderdoc) - GPU调试工具 (8k stars)
- [NVIDIA NSight](https://github.com/NVIDIAGameWorks) - NVIDIA开发者工具
- [ue4ss](https://github.com/UE4SS-org/UE4SS) - UE4脚本和modding工具

### Blender与3D资产生态
- [KhronosGroup/glTF](https://github.com/KhronosGroup/glTF) - glTF 3D格式 (6k stars)
- [Assimp/assimp](https://github.com/assimp/assimp) - 3D模型导入库 (8k stars)
- [blender/blender](https://github.com/blender/blender) - Blender开源3D创作 (14k stars)

## 核心技能

### UE5新特性速查
```
Nanite (虚拟几何体):
- 适用: 静态几何体(建筑、地形)
- 不适用: 骨骼网格体、程序化网格
- 启用: 网格体属性 -> Nanite Settings -> Enabled

Lumen (动态全局光照):
- 适用: 动态光照场景
- 性能: 需要DXR显卡支持
```

### Niagara粒子系统模块
```
Spawn模块:
- Spawn Rate: 持续生成
- Burst: 一次性爆发
- Periodic Burst: 定时爆发

Update模块:
- Acceleration: 加速度
- Drag: 空气阻力
- Color: 颜色渐变
- Size: 大小变化

HLSL定制:
- Particle Attribute Reader
- Niagara Advanced Sim Stage
```

### 性能优化清单
```
DrawCall优化:
- [ ] 静态网格体合并
- [ ] LOD层级设置
- [ ] Instanced Static Mesh

内存优化:
- [ ] 纹理流控制
- [ ] 模型LOD
- [ ] 音频压缩

GPU优化:
- [ ] Shader复杂度
- [ ] 光照贴图使用
```

## 资源网站

### 资产商城
- [Quixel Megascans](https://quixel.com/megascans/) - 扫描资产库
- [Unreal Marketplace](https://www.unrealengine.com/marketplace/) - UE资产商城
- [Sketchfab](https://sketchfab.com/) - 3D模型
- [Poly Haven](https://polyhaven.com/) - 免费3D资产

### 学习资源
- [Unreal Engine Learning Library](https://dev.epicgames.com/community/learning) - 官方学习库
- [80 Level](https://80.lv/) - 游戏开发博客
- [GameDev.tv](https://www.gamedev.tv/) - 游戏开发课程

---
*由坨坨维护 · 2026-04-15 · 更新*
