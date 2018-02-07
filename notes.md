## Redis 主从+哨兵（sentinel）

使用主从结构+哨兵（sentinel）来进行容灾


## 【Redis集群主机】
{{range $index, $group:=.Group}}
    {{if eq $group.Name "redis"}}
        {{range $index, $host:=$group.Hosts}}
            {{$host.IP}}
        {{end}}
    {{end}}
{{end}}

## 【Sentinel主机】
{{range $index, $group:=.Group}}
    {{if eq $group.Name "sentinel"}}
        {{range $index, $host:=$group.Hosts}}
            {{$host.IP}}
        {{end}}
    {{end}}
{{end}}

## 【使用】

1、使用redis客户端连接到集群任意一台Sentinel主机，`redis-cli -a {{.Vars.redis.redis.password}}  -p  {{.Vars.redis.redis.port}}`

2、查看哨兵信息：`info Sentinel`

3、查看集群主从：` SENTINEL masters`
