---
title: Hello World
description: 查看更多
copyright: true
---
Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).

# ok 你好

## Quick Start 你好

### Create a new post

``` bash
$ hexo new "My New Post"
```

#### hello 可

``` java

    public Flux<RouteDefinition> getRouteDefinitions() {
        DiscoveryLocatorProperties properties = getProperties();

        SpelExpressionParser parser = new SpelExpressionParser();
        Expression includeExpr = parser.parseExpression(properties.getIncludeExpression());
        Expression urlExpr = parser.parseExpression(properties.getUrlExpression());

        Predicate<ServiceInstance> includePredicate;
        if (isIncludeAllExpression(properties.getIncludeExpression())) {
            // 包含全部
            includePredicate = instance -> true;
        } else {
            includePredicate = instance -> {
                Boolean include = includeExpr.getValue(evaluationContext, instance, Boolean.class);
                if (include == null) {
                    return false;
                }
                return include.booleanValue();


```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)
