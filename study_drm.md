# 研讀linux source code DRM的部分，學習的linux上面display driver框架的長相

- [DRM（Direct Rendering Manager）学习简介](https://blog.csdn.net/hexiaolong2009/article/details/83720940)
- [屏幕显示(DRM)介绍](https://doc.embedfire.com/linux/rk356x/linux_base/zh/latest/linux_app/drm/drm.html)
- [The DRM/KMS subsystem from a newbie’s point of view](https://events.static.linuxfound.org/sites/events/files/slides/brezillon-drm-kms.pdf)
- [linux DRM source code](https://github.com/torvalds/linux/tree/master/drivers/gpu/drm)
- [RK3399 探索之旅 / Display 子系统 / 基础概念](https://blog.csdn.net/M120674/article/details/123324268) 看起來可以跟kernel source裡面的code互相參考，再花時間回來看
- chatgpt真是幫手，原來soc廠商不太需要在意libdrm module，主要是要專注在kernel的drm driver。
  請他寫一個最簡單使用libdrm的app sample code，再問他soc廠商至少該實做那些ioctl來滿足上面的sample，gpt都給出建議，
  一開始先有個會動的，再慢慢把其他ioctl補上，應該也是一個攻略的方法，希望之後有機會實做看看
