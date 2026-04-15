# 虚幻技术美术部学习资料

> Unreal Engine、Shader、VFX、渲染优化的完整知识库

## 官方文档

### Unreal Engine
- [UE5官方文档](https://docs.unrealengine.com/) - 英文官方文档
- [UE4官方文档](https://docs.unrealengine.com/4.27/zh-CN/) - UE4中文文档
- [Epic官方YouTube](https://www.youtube.com/@UnrealEngine) - 官方视频教程
- [Unreal Engine 5.3 新特性](https://docs.unrealengine.com/5.3/zh-CN/whats-new/unreal-engine-5-3/) - 最新版本特性
- [UE5材质系统](https://docs.unrealengine.com/5.0/en-US/Rendering/Materials/) - 材质系统文档
- [Nanite虚拟几何体](https://docs.unrealengine.com/5.0/en-US/Modeling/GIS/) - Nanite文档
- [Lumen动态光照](https://docs.unrealengine.com/5.0/en-US/Rendering/Lumen/) - Lumen文档
- [World Partition](https://docs.unrealengine.com/5.0/en-US/BuildingWorlds/DynamicWorldUpdates/) - 世界分区系统

### Shader编程
- [HLSL参考](https://learn.microsoft.com/zh-cn/windows/win32/direct3dhlsl/dx-graphics-hlsl-reference) - DirectX HLSL官方
- [ShaderToy](https://www.shadertoy.com/) - Shader学习社区
- [Ronja Shader教程](https://www.ronja-tutorials.com/) - Unity Shader教程(可借鉴)
- [The Art of Code](https://www.youtube.com/@BigWings) - Shader入门视频
- [Inigo Quilez](https://iquilezles.org/) - Shader大神博客

### VFX特效
- [Niagara官方文档](https://docs.unrealengine.com/5.0/en-US/Rendering/Niagara/) - Niagara粒子系统
- [Niagara入门教程](https://dev.epicgames.com/community/learning/courses/unreal-engine/introduction-to-niagara) - 官方教程
- [HLSL in Niagara FX](https://dev.epicgames.com/community/learning/tutorials/m6X7/unreal-engine-introduction-to-hlsl-scratch-pad-in-niagara-fx) - Niagara HLSL
- [Niagara YouTube教程](https://www.youtube.com/playlist?list=PLSsBDmERZUmVwSxhKMmNYok9SAM0x6GLP) - 官方播放列表
- [VFX Hotfix](https://www.vfxhotfix.com/) - UE VFX技巧博客

### 地理仿真
- [Cesium for Unreal](https://cesium.com/learn/unreal/) - Cesium官方教程
- [Cesium插件下载](https://github.com/CesiumGS/cesium-unreal) - GitHub仓库
- [WorldMachine](https://www.worldmachine.com/) - 地形生成工具
- [GeoTIFF](https://geotiff.io/) - 地理TIFF格式
- [OSSIM](https://trac.osgeo.org/ossim/) - 地理图像处理

### 工具
- [RenderDoc](https://renderdoc.org/) - GPU调试工具
- [NVIDIA Nsight](https://developer.nvidia.com/nvidia-nsight-gpus) - NVIDIA GPU调试
- [Blender](https://www.blender.org/) - 3D建模软件
- [Substance Painter](https://www.substance3d.com/) - 3D纹理绘制
- [Maya](https://www.autodesk.com/maya/) - 3D动画制作
- [ZBrush](https://www.zbrush.com/) - 数字雕刻

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
- 启用: Project Settings -> Ray Tracing -> Lumen

Nanite + Lumen组合:
- 电影级光照效果
- 实时全局光照
- 虚拟几何体无LOD损失

World Partition:
- 大世界流式加载
- LOD层级管理
- 多人协作编辑

MetaHuman:
- 数字人类制作
- 高保真实时渲染
- 支持身体动画

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

Events:
- Collision: 碰撞检测
- Death: 粒子消亡

HLSL定制:
- Particle Attribute Reader
- Niagara Advanced Sim Stage
```

### Shader基础 (HLSL示例)
```hlsl
// 简单漫反射
float4 SimpleLitMaterial(
    float2 UV,
    float3 WorldNormal,
    float3 LightDirection
)
{
    float NdotL = dot(WorldNormal, LightDirection);
    float Diffuse = saturate(NdotL);
    
    float3 BaseColor = tex2D(BaseColorSampler, UV).rgb;
    
    return float4(BaseColor * Diffuse, 1.0);
}
```

### 性能优化清单
```
DrawCall优化:
- [ ] 静态网格体合并
- [ ] LOD层级设置
- [ ] HLOD系统使用
- [ ] Instanced Static Mesh

内存优化:
- [ ] 纹理流控制
- [ ] 模型LOD
- [ ] 音频压缩

GPU优化:
- [ ] Shader复杂度
- [ ] 光照贴图使用
- [ ] 后处理效果精简

渲染优化:
- [ ] 视锥剔除
- [ ] 遮挡剔除
- [ ] 距离剔除
- [ ] 帧率目标设置
```

### 渲染设置推荐 (性能优先)
```
全局:
- Shadow Map Resolution: 1024x1024
- Dynamic Range: Limited
- Anti-Aliasing: TSR Medium

光照:
- Static: 质量优先
- Stationary: 性能优先
- Movable: 仅必要

后处理:
- Bloom: Off 或 Medium
- Tone Curve: Simple
- Lens Flare: Off
- Ambient Occlusion: SSAO Medium
```

## 资源网站

### 资产商城
- [Quixel Megascans](https://quixel.com/megascans/) - 扫描资产库
- [Unreal Marketplace](https://www.unrealengine.com/marketplace/) - UE资产商城
- [Sketchfab](https://sketchfab.com/) - 3D模型
- [Poly Haven](https://polyhaven.com/) - 免费3D资产

### 学习资源
- [Unreal Engine Learning Library](https://dev.epicgames.com/community/learning) - 官方学习库
- [GameDev.tv](https://www.gamedev.tv/) - 游戏开发课程
- [Zenva](https://gameacademy.zenvia.com/) - UE5课程
- [80 Level](https://80.lv/) - 游戏开发博客

---
*由坨坨维护 · 2026-04-15 · 更新*
