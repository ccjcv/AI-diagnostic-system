# AI-diagnostic-system
项目描述：在Linux环境下，使用C++、QT开发的超声图像AI诊断系统。用户可以捕获四路相机的超声图像以进行存储，采用基于nginx、fastCGI、fastDFS的分布式文件服务器，支持上万的QPS。同时可以使用多个基于pytorch的自研深度学习模型进行分割、追踪和分级。

主要工作：

基于ffmpeg的四路RTSP协议的相机，通过OpenGL实时渲染显示，并对超声视频图像进行采集。
使用FastDFS进行文件的上传与下载操作。
配置Nginx完成静态资源的部署，通过存储节点的反向代理实现服务器的扩容。
实现post请求解析，编写FastCGI程序以实现动态请求，包括用户注册、登录、文件上传、下载、秒传，以及文件列表获取。
Redis保存频繁访问的数据，包括用户token，图像文件token。
基于TCP的子线程连接与发送图像，配置自研的BPAT-UNet(SCI 2区)、弱监督DRTNet(SCI 1区在投)网络模型的超声图像分割。
使用QProcess调用命令行执行python脚本实现超声影像的追踪、分级模型推理。
