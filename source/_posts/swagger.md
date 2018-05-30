---
title: spring-boot swagger 配置
date: 2018-05-30 17:03:38
tags: [spring-boot,swagger]
categories: 教程
---
阅读这篇文章，你将获得的知识技能有，spring-boot配置swagger, 以及swagger一些自定义配置，比如说header头，host等

#### 在写最前面
在前后端分离的情景下，后端开发给出api的相应文档就显得尤为重要了，当spring-boot 搭上swagger那就事半功倍了。本文的开发环境是：idea + maven3 + jdk8 + spring-boot 1.5.6

#### swagger集成
在pom.xml中添加如下依赖
```
    <!--swagger2-->
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger2</artifactId>
        <version>2.2.2</version>
    </dependency>
    <dependency>
        <groupId>io.springfox</groupId>
        <artifactId>springfox-swagger-ui</artifactId>
        <version>2.2.2</version>
    </dependency>
```

建立配置文件内容如下
```
@Configuration
@EnableSwagger2
public class Swagger {

    @Bean
    public Docket createRestApi() {
        ParameterBuilder tokenPar = new ParameterBuilder();
        List<Parameter> pars = new ArrayList<>();
        tokenPar.name("自定义http header").description("自定义header描述").modelRef(new ModelRef("string")).parameterType("header").required(true).build();
        pars.add(tokenPar.build());

        return new Docket(DocumentationType.SWAGGER_2)
                .globalOperationParameters(pars)
                .apiInfo(apiInfo())
                .protocols(new HashSet() {{
                    add("https");
                }})
                .select()
                .apis(RequestHandlerSelectors.basePackage("你Controller包名"))
                .paths(PathSelectors.any())
                .build();
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("demo RESTful APIs")
                .description("API描述")
                .termsOfServiceUrl("http://demo.demo.me")
                .contact("demo")
                .version("1.0")
                .build();
    }
}
```

@EnableSwagger2 启动swagger2
new Docket().globalOperationParameters(pars) 可添加自定义http header
new Docket().host("") 可自定义swagger host

#### 注意事项
如果你的版本里没有Docket().host("") 这个函数，那么请在 application.properties 中添加如下配置：springfox.documentation.swagger.v2.host=demo.demo.me/api 效果相同

#### 写在最后
启动spring项目访问 localhost:8080/swagger-ui.html 即可看到swagger生成的api文档。如果在swagger-ui.html 前面加个根路径比如localhost:8080/api/swagger-ui.html，可修改server.context-path=/api。有关前后端分离，nginx转发代理如何访问文档问题也可在此问我。
