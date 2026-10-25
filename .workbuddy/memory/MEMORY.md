# sky-take-out 项目长期备忘

## 技术栈
- Spring Boot 2.7.3（父 pom）+ MyBatis + Druid + PageHelper + knife4j 3.0.2（springfox）+ Lombok 1.18.30，字节码版本 Java 8。
- 模块：`sky-take-out/{sky-common, sky-pojo, sky-server}`；启动类 `com.sky.SkyApplication`。
- MySQL 8 本地 3306，库 `sky_take_out`，root/123456（`application-dev.yml`）。

## 必须遵守的构建约定
- **只能用 JDK 17 编译**。`JAVA_HOME` 指向的是 JDK 25，Lombok 1.18.30 在 25 上注解处理失效，会报一堆「找不到符号 getXxx()」。
  命令行构建：`JAVA_HOME="D:/Program Files/Java/jdk-17" mvn -DskipTests clean package`。
  IDEA 项目 SDK 已是 17，Maven Runner 的 JRE 也要设成 17。
- 出现 `ClassFormatError: Invalid method Code length 0` 一律是 target 里的旧/损坏 class，`clean` 重编译即可，与源码无关。
