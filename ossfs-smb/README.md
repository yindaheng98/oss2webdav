# ossfs-smb

这是一个用ossfs挂载Aliyun OSS到本地目录并转为SMB的镜像。基于`alpine`。

使用的ossfs版本：[https://github.com/aliyun/ossfs/tree/v1.80.6](https://github.com/aliyun/ossfs/tree/v1.80.6)

使用的SMB服务器：[dperson/samba](https://hub.docker.com/r/dperson/samba)

## 使用方法

```sh
docker run --cap-add SYS_ADMIN --device /dev/fuse --security-opt apparmor=unconfined \
 --env BucketName=your-bucket-name \
 --env AccessKeyId=your-access-key-id \
 --env AccessKeySecret=your-access-key-secret \
 --env EndPoint=your.end.point \
 --env MountPoint=/your/mount/dir \
 --env <SMB相关环境变量见dperson/samba>\
 yindaheng98/ossfs:alpine <输入参数见dperson/samba>
```