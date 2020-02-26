Envoy

Terms 
	Host - Logical network application
	Downstream host 
	Upstream host
	Listener: A listener is a named network location (e.g., port, unix domain socket, etc.) that can be connected to by downstream clients. Envoy exposes one or more listeners that downstream hosts connect to.

Envoy has a built in network level filter called the HTTP connection manager

Envoy includes an HTTP router filter which can be installed to perform advanced routing tasks

Request retries specified either via HTTP header or via route configuration.



Envoy allows retries to be configured both in the route configuration as well as for specific requests via request headers. The following configurations are possible:

Maximum number of retries: Envoy will continue to retry any number of times. An exponential backoff algorithm is used between each retry. Additionally, all retries are contained within the overall request timeout. This avoids long request times due to a large number of retries.

Retry conditions: Envoy can retry on different types of conditions depending on application requirements. For example, network failure, all 5xx response codes, idempotent 4xx response codes, etc.

Retry budgets: Envoy can limit the proportion of active requests via retry budgets that can be retries to prevent their contribution to large increases in traffic volume.

Host selection retry plugins: Envoy can be configured to apply additional logic to the host selection logic when selecting hosts for retries. Specifying a retry host predicate allows for reattempting host selection when certain hosts are selected (e.g. when an already attempted host is selected), while a retry priority can be configured to adjust the priority load used when selecting a priority for retries.
Note that retries may be disabled depending on the contents of the x-envoy-overloaded.

https://unofficialism.info/posts/envoy-proxy-demos/
https://blog.christianposta.com/microservices/02-microservices-patterns-with-envoy-proxy-part-ii-timeouts-and-retries/