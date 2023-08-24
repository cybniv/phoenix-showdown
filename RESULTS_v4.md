# Comparative Benchmark Numbers, Round 4
`system_profiler SPHardwareDataType`:

```
      Model Name: MacBook Pro
      Model Identifier: MacBookPro16,2
      Processor Name: Quad-Core Intel Core i7
      Processor Speed: 2,3 GHz
      Number of Processors: 1
      Total Number of Cores: 4
      L2 Cache (per Core): 512 KB
      L3 Cache: 8 MB
      Hyper-Threading Technology: Enabled
      Memory: 32 GB
      System Firmware Version: 1968.140.7.0.0 (iBridge: 20.16.6072.0.0,0)
      OS Loader Version: 577.140.2~15
```


| Framework | Throughput (req/s) | Latency (ms) | Consistency (σ ms) |
|:----------|-------------------:|-------------:|-------------------:|
| Rails     |             448.41 |       602.69 |               7.73 |


## Detailed Results

### Benchmarking Rails
MRI 2.3.1

```bash
$ PUMA_WORKERS=4 MIN_THREADS=1 MAX_THREADS=16 RACK_ENV=production bundle exec puma
$ wrk -t4 -c100 -d30S --timeout 2000 "http://localhost:3000/showdown"
Running 30s test @ http://localhost:3000/showdown
  4 threads and 100 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency   602.69ms  726.48ms   2.27s    78.51%
    Req/Sec   121.63     65.84   420.00     77.13%
  13469 requests in 30.04s, 33.91MB read
Requests/sec:    448.41
Transfer/sec:      1.13MB
```
