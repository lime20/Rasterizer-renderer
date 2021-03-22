# 光栅渲染器


## 项目来源及依赖


&#8194;&#8194;本项目源于课程作业，以实现如下功能：texture shader，Blinn-Phong，Bump Mapping，Displacement Mapping。

&#8194;&#8194;为保障顺利运行需安装Eigen，OpenCV。若是使用Visual Studio 中NuGet 包管理器安装Eigen ，需修改部分代码。


## 工作流程

1. 读取模型数据
2. MVP变换
3. 确认渲染模式
4. 渲染
5. 输出

## 注意事项

### Z坐标插值修正
在本项目中，对像素投影回原坐标系的实现方法是采用一种近似处理，而非标准插值矫正。[透视矫正插值看这里](https://zhuanlan.zhihu.com/p/144331875)
```
float zp = alpha * v[0].z() / v[0].w() + beta * v[1].z() / v[1].w() + gamma * v[2].z() / v[2].w();
本系统采用右手系，相机方法朝向-Z方向，故未取倒数。
```



##  运行
```  c++
 使用代码中的 texture shader
./Rasterizer output.png texture

 使用代码中的 normal shader.
./Rasterizer output.png normal

 使用代码中的 blinn-phong shader.
./Rasterizer output.png phong

 使用代码中的 bump shader.
./Rasterizer output.png bump

 使用代码中的 displacement shader.
./Rasterizer output.png displacement

```

```
若是使用VS 中NuGet工具添加 Eigen 库，需进行如下操作：
原：#include <eigen3/Eigen/Eigen>
改：#include <Eigen/Eigen>
```

## 效果

* normal shader
	
![normal shader](https://dm2305files.storage.live.com/y4mbBH40dXwWdj5DOi45RBcej38htX1G4iWNwg4Bcv1lnBIOKkT4KXWGe4s1fxI7-lCNCtknh6V9npxzswG2Q1akDxehAS_9tnSlqda_We43U_jNRDF78wPFVKlJjNqrgUNQ2kcA1R4hUtx5rQhgEm_x_nJ-6lWu3x18ZutghjW7KFytNc9_KNm2aVBbqAX8GVc?width=660&height=660&cropmode=none)
    
* Blinn-Phong

![Blinn-Phong](https://dm2305files.storage.live.com/y4mAjFriUXm0GRGPKqNY38E1mMw7ovybGN0mE_2K4BYDFUvG4B_qKzEcXKnzAtKrLmHNCb7-cePYfW-p0Yv4n-82DUINGRiYjbuRDXBnSHvWkYS2Z45YA-RZSOlU_oV6Tw1p1YaoyyQSxXlGwnZN1C3wfvqAZQBLOzZfDOzF84EjMsF81grwFlSs_A99Wdt5mel?width=660&height=660&cropmode=none)

* texture shader

![texture shader](https://dm2305files.storage.live.com/y4mJbqtGkKw41cNlVCv07PdlSWnQOaTbfexJ-0vZa_J8yHqYUl0MaQnKMbyPsycsCKZgBXhslXXxgpUSeYj-Qh5sFb1NsUvs2-fZgbXK9dm1mxKT7HokZWZiCIT03FEbpH0KgcEuiAqiJRs6ndwvOqzHXRWIRrLboTVWjHNbIfX33lYmcQXsSskOLf1XjQbX995?width=660&height=660&cropmode=none)

* bump shader

![bump shader](https://dm2305files.storage.live.com/y4mOqRt2LYAyTaCKCsBPckBl-m4MPjz6Ej9ZxzukNCj01D6V5h9l1qxMEoyhfyKZ4byte488HAoIZZ3qFFAC3xAcxFEW0K-r5KoCX_MGliGEvfyiTbW21C5uIHyPqlY3ImvS3CPj1pCCCvBTIfL44LVzaw9Ae6I16ppYTJIS4wl2wNdqqiJe4KBuHxKDTRJfn0y?width=660&height=660&cropmode=none)

* displacement shader

![displacement shader](https://dm2305files.storage.live.com/y4mGrpzmqPOcWxQgRJiKKdC_kctt1ZD7tk7iOd2GLiealc0NEm7aKaugEPIZRv1K1Ii0s6JaZso_tUMpfdGFbgEWw6VoL-7FYfbewF_irL-dkTvb43jdxy303uzpPpXsgERSZ4I3MT77aTlFn1-_JekBaYpbY1E8ZHL-Q68aZ1P0uncbpYpjQel2PlutrEvpiSX?width=660&height=660&cropmode=none)


