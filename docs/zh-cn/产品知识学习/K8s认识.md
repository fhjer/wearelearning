# K8s

## 存储卷（Volume）

存储卷是Pod中能够被多个容器访问的共享目录，定义在Pod上，属于计算资源。（挂载到Pod中的容器里的某个目录上）

## 存储类型

### emptyDir

在Pod分配到Node时创建，初始内容为空，且无须制定宿主机上对应的目录文件（K8s自动分配的）。当Pod从Node上移除时，emptyDir中的数据也会被永久删除。用户不可控。

### hostPath

在Pod上挂载宿主机上的文件或目录。

### NFS

使用NFS网络文件系统提供的共享目录存储数据时，需要在系统中部署一个NFS服务器。

### ceph



## PV&PVC

### PV

只能是网络存储，不属于任何Node，但可在每个Node上访问；独立于Pod之外。

PV访问模式

ReadWriteOnce：读写权限，只能被单个Node挂载

ReadOnlyMany：只读权限，可被多个Node挂载

ReadWriteMany：读写权限，允许被多个Node挂载

## 命名空间（Namespace）

用于实现多租户的资源隔离



# Pod

### 重启策略

Pod的重启策略应用于Pod内的所有容器。

- Always：容器失效时，由kubelet自动重启该容器。
- OnFailure：容器终止运行且退出码不为0时，由kubelet自动重启该容器。
- Never：不论容器运行状态如何，kubelet都不会重启该容器。

## 健康检查策略

### 存活探针

用于判断容器是否存活。若检测到容器不健康，则kubelet将杀掉该容器，并根据容器的重启策略做相应处理。

### 就绪探针

用于判断容器服务是否可用，是否准备好接收处理用户请求。

### 实现方式

#### 探测方式

- ExecAction（命令）：在容器内部执行一个命令，返回码为0，则表明容器健康。
- TCPSocketAction（TCP）：通过容器IP地址和端口号执行TCP检查，若能建立TCP连接，则表明容器健康。
- HTTPGetAction（HTTP）：通过容器IP地址、端口号和路径调用HTTP Get方法，若响应的状态码在[200,400)中，则认为容器健康。

#### 探测参数

- initalDelaySeconds（首次健康检查延时）：启动容器后进行首次健康检查的等待时间，单位：秒
- timeoutSeconds（超时时间）：健康检查发送请求后等待响应的超时时间。发生超时时，则认为该容器已无法提供服务，重启该容器。









