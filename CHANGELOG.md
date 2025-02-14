Changes by Version
==================

2.17.1 (unreleased)
-------------------

- Nothing yet.


2.17.0 (2019-08-30)
-------------------
- Add a flag for firehose mode (#419) <Prithvi Raj>
- Default sampling server URL to agent (#414) <Bryan Boreham>
- Update default sampling rate when sampling strategy is refreshed (#413) <Bryan Boreham>
- Support "Self" Span Reference (#411) <dm03514>
- Don't complain about blank service name if tracing is Disabled (#410) Yuri <Shkuro>
- Use IP address from tag if exist (#402) <NikoKVCS>
- Expose span data to custom reporters [fixes #394] (#399) <Curtis Allen>
- Fix the span allocation in the pool (#381) <Dmitry Ponomarev>


2.16.0 (2019-03-24)
-------------------

- Add baggage to B3 codec (#319) <Pavol Loffay>
- Add support for 128bit trace ids to zipkin thrift spans. (#378) <Douglas Reid>
- Update zipkin propagation logic to support 128bit traceIDs (#373) <Douglas Reid>
- Accept "true" for the x-b3-sampled header (#356) <Adrian Bogatu>

- Allow setting of PoolSpans from Config object (#322) <Matthew Pound>
- Make propagators public to allow wrapping (#379) <Ivan Babrou>
- Change default metric namespace to use relevant separator for the metric backend (#364) <Gary Brown>
- Change metrics prefix to jaeger_tracer and add descriptions (#346) <Gary Brown>
- Bump OpenTracing to ^1.1.x (#383) <Yuri Shkuro>
- Upgrade jaeger-lib to v2.0.0 (#359) <Gary Brown>
- Avoid defer when generating random number (#358) <Gary Brown>
- Use a pool of rand.Source to reduce lock contention when creating span ids (#357) <Gary Brown>
- Make JAEGER_ENDPOINT take priority over JAEGER_AGENT_XXX (#342) <Eundoo Song>


2.15.0 (2018-10-10)
-------------------

- Fix FollowsFrom spans ignoring baggage/debug header from dummy parent context (#313) <Zvi Cahana>
- Make maximum annotation length configurable in tracer options (#318) <Eric Chang>
- Support more environment variables in configuration (#323) <Daneyon Hansen>
- Print error on Sampler Query failure (#328) <Goutham Veeramachaneni>
- Add an HTTPOption to support custom http.RoundTripper (#333) <Michael Puncel>
- Return an error when an HTTP error code is seen in zipkin HTTP transport (#331) <Michael Puncel>


2.14.0 (2018-04-30)
-------------------

- Support throttling for debug traces (#274) <Isaac Hier>
- Remove dependency on Apache Thrift (#303) <Yuri Shkuro>
- Remove dependency on tchannel  (#295) (#294) <Yuri Shkuro>
- Test with Go 1.9 (#298) <Yuri Shkuro>


2.13.0 (2018-04-15)
-------------------

- Use value receiver for config.NewTracer() (#283) <Yuri Shkuro>
- Lock span during jaeger thrift conversion (#273) <Won Jun Jang>
- Fix the RemotelyControlledSampler so that it terminates go-routine on Close() (#260) <Scott Kidder> <Yuri Shkuro>
- Added support for client configuration via env vars (#275) <Juraci Paixão Kröhling>
- Allow overriding sampler in the Config (#270) <Mike Kabischev>


2.12.0 (2018-03-14)
-------------------

- Use lock when retrieving span.Context() (#268)
- Add Configuration support for custom Injector and Extractor (#263) <Martin Liu>


2.11.2 (2018-01-12)
-------------------

- Add Gopkg.toml to allow using the lib with `dep`


2.11.1 (2018-01-03)
-------------------

- Do not enqueue spans after Reporter is closed (#235, #245)
- Change default flush interval to 1sec (#243)


2.11.0 (2017-11-27)
-------------------

- Normalize metric names and tags to be compatible with Prometheus (#222)


2.10.0 (2017-11-14)
-------------------

- Support custom tracing headers (#176)
- Add BaggageRestrictionManager (#178) and RemoteBaggageRestrictionManager (#182)
- Do not coerce baggage keys to lower case (#196)
- Log span name when span cannot be reported (#198)
- Add option to enable gen128Bit for tracer (#193) and allow custom generator for high bits of trace ID (#219)


2.9.0 (2017-07-29)
------------------

- Pin thrift <= 0.10 (#179)
- Introduce a parallel interface ContribObserver (#159)


2.8.0 (2017-07-05)
------------------

- Drop `jaeger.` prefix from `jaeger.hostname` process-level tag
- Add options to set tracer tags


2.7.0 (2017-06-21)
------------------

- Fix rate limiter balance [#135](https://github.com/uber/jaeger-client-go/pull/135) [#140](https://github.com/uber/jaeger-client-go/pull/140)
- Default client to send Jaeger.thrift [#147](https://github.com/uber/jaeger-client-go/pull/147)
- Save baggage in span [#153](https://github.com/uber/jaeger-client-go/pull/153)
- Move reporter.queueLength to the top of the struct to guarantee 64bit alignment [#158](https://github.com/uber/jaeger-client-go/pull/158)
- Support HTTP transport with jaeger.thrift [#161](https://github.com/uber/jaeger-client-go/pull/161)


2.6.0 (2017-03-28)
------------------

- Add config option to initialize RPC Metrics feature


2.5.0 (2017-03-23)
------------------

- Split request latency metric by success/failure [#123](https://github.com/uber/jaeger-client-go/pull/123)
- Add mutex to adaptive sampler and fix race condition [#124](https://github.com/uber/jaeger-client-go/pull/124)
- Fix rate limiter panic [#125](https://github.com/uber/jaeger-client-go/pull/125)


2.4.0 (2017-03-21)
------------------

- Remove `_ms` suffix from request latency metric name [#121](https://github.com/uber/jaeger-client-go/pull/121)
- Rename all metrics to "request" and "http_request" and use tags for other dimensions [#121](https://github.com/uber/jaeger-client-go/pull/121)


2.3.0 (2017-03-20)
------------------

- Make Span type public to allow access to non-std methods for testing [#117](https://github.com/uber/jaeger-client-go/pull/117)
- Add a structured way to extract traces for logging with zap [#118](https://github.com/uber/jaeger-client-go/pull/118)


2.2.1 (2017-03-14)
------------------

- Fix panic caused by updating the remote sampler from adaptive sampler to any other sampler type (https://github.com/uber/jaeger-client-go/pull/111)


2.2.0 (2017-03-10)
------------------

- Introduce Observer and SpanObserver (https://github.com/uber/jaeger-client-go/pull/94)
- Add RPC metrics emitter as Observer/SpanObserver (https://github.com/uber/jaeger-client-go/pull/103)


2.1.2 (2017-02-27)
-------------------

- Fix leaky bucket bug (https://github.com/uber/jaeger-client-go/pull/99)
- Fix zap logger Infof (https://github.com/uber/jaeger-client-go/pull/100)
- Add tracer initialization godoc examples


2.1.1 (2017-02-21)
-------------------

- Fix inefficient usage of zap.Logger


2.1.0 (2017-02-17)
-------------------

- Add adapter for zap.Logger (https://github.com/uber-go/zap)
- Move logging API to ./log/ package


2.0.0 (2017-02-08)
-------------------

- Support Adaptive Sampling
- Support 128bit Trace IDs
- Change trace/span IDs from uint64 to strong types TraceID and SpanID
- Add Zipkin HTTP B3 Propagation format support #72
- Rip out existing metrics and use github.com/uber/jaeger-lib/metrics
- Change API for tracer, reporter, sampler initialization


1.6.0 (2016-10-14)
-------------------

- Add Zipkin HTTP transport
- Support external baggage via jaeger-baggage header
- Unpin Thrift version, keep to master


1.5.1 (2016-09-27)
-------------------

- Relax dependency on opentracing to ^1


1.5.0 (2016-09-27)
-------------------

- Upgrade to opentracing-go 1.0
- Support KV logging for Spans


1.4.0 (2016-09-14)
-------------------

- Support debug traces via HTTP header "jaeger-debug-id"
