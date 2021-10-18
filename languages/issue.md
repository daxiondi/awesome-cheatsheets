- 分析CPU
火焰图适合分析cpu抖动
perf 适合c/c++内核分析
```
perf record -g --pid -a -F 99 -- sleep 60
git clone https://github.com/brendangregg/FlameGraph.git
perf script > redis.perf.stacks
stackcollapse-perf.pl redis.perf.stacks > redis.folded.stacks
flamegraph.pl redis.folded.stacks > redis.svg
```

实时查看cpu和内存
```
perf top
```

java火焰图使用arthas
- 观察内存情况
```
watch -n 5 'jmap -histo pid'
vmtool --action getInstances --className java.lang.String --limit 10
```

- 生成火焰图
```
profiler start --event alloc
profiler stop 
```

