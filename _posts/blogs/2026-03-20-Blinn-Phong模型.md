---
title: Blinn-Phong 模型
tags: [Geometry]
categories: [Geometry]
---

```cpp
Eigen::Vector3f phong_fragment_shader(const fragment_shader_payload& payload)
{
    Eigen::Vector3f ka = Eigen::Vector3f(0.005, 0.005, 0.005);
    Eigen::Vector3f kd = payload.color;
    Eigen::Vector3f ks = Eigen::Vector3f(0.7937, 0.7937, 0.7937);

    auto l1 = light\{{20, 20, 20}, {500, 500, 500}\};
    auto l2 = light\{{-20, 20, 0}, {500, 500, 500}\};

    std::vector<light> lights = {l1, l2};
    Eigen::Vector3f amb_light_intensity{10, 10, 10};
    Eigen::Vector3f eye_pos{0, 0, 10};

    float p = 150;

    Eigen::Vector3f color = payload.color;
    Eigen::Vector3f point = payload.view_pos;
    Eigen::Vector3f normal = payload.normal;

    Eigen::Vector3f result_color = {0, 0, 0};
    for (auto& light : lights)
    {
        // 📖-4 补全布林冯模型: 计算l, v, h向量并返回颜色
        // components are. Then, accumulate that result on the *result_color* object.
        auto VlightIn = (light.position - point).normalized();//计算l，着色点到光线方向
        auto VlightView = (eye_pos - point).normalized();//计算v，着色点到观察者方向
        auto Vhalf = (VlightIn + VlightView).normalized();//计算h，半程向量
        auto r2lightIn = (light.position - point).norm() * (light.position - point).norm();//计算r^2，r是光线在空间中球形传播的半径（距离）
        // float lightIntensity = std::sqrt(light.intensity * light.intensity);
        result_color += Eigen::Vector3f{ka[0]*amb_light_intensity[0],ka[1]*amb_light_intensity[1],ka[2]*amb_light_intensity[2]};
                                        //ka是环境光反射系数
        result_color += Eigen::Vector3f{kd[0]*light.intensity[0],kd[1]*light.intensity[1],kd[2]*light.intensity[2]} / r2lightIn * MYMAX(0,normal.dot(VlightIn));
                                        //kd是漫反射系数
        result_color += Eigen::Vector3f{ks[0]*light.intensity[0],ks[1]*light.intensity[1],ks[2]*light.intensity[2]} / r2lightIn * std::pow(MYMAX(0,normal.dot(Vhalf)), p);
                                        //ks是镜面反射系数，一般是1，p是高光系数，使cosα快速衰减
    }

    return result_color * 255.f;
}
```