#FROM openjdk:8-jdk-alpine
FROM java:8-jre
VOLUME /tmp
ADD k8s-demo.jar /app.jar
#RUN bash -c 'touch app.jar'

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN echo 'Asia/Shanghai' >/etc/timezone

COPY /so /so
#添加可执行权限
RUN chmod a+x -R  so
#创建so软链到/usr/lib下（此处有另一种更优的方法：在yaml文件中添加env,其路径指向当前/so即可【- name: LD_LIBRARY_PATH value: /so】）
#RUN ln -s /so/libuuid.so.1 /usr/lib && ln -s /so/ld-linux-x86-64.so.2 /usr/lib && ln -s /so/libsapjco3.so /usr/lib
RUN echo 'Asia/Shanghai' >/etc/timezone
# "-Djava.library.path=/so",
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
