# General

Current directory uses the default "Hello <X>" example where you send a message to the server with your name, and the server sends back "Hello <name you send>.

It has a server build on the currently new .NET Core 3.0, which has gRPC integrated [.NET Core ❤ gRPC](https://grpc.io/blog/grpc-on-dotnetcore/).  

However there is a problem upon trying to connect to the server from a Java Client.

```java
Failed... : 
io.grpc.StatusRuntimeException: INTERNAL: Protocol error
Rst Stream
	at io.grpc.stub.ClientCalls.toStatusRuntimeException(ClientCalls.java:235)
	at io.grpc.stub.ClientCalls.getUnchecked(ClientCalls.java:216)
	at io.grpc.stub.ClientCalls.blockingUnaryCall(ClientCalls.java:141)
	at io.grpc.examples.helloworld.GreeterGrpc$GreeterBlockingStub.sayHello(GreeterGrpc.java:228)
	at io.grpc.helloworldexample.HelloworldActivity$GrpcTask.doInBackground(HelloworldActivity.java:90)
	at io.grpc.helloworldexample.HelloworldActivity$GrpcTask.doInBackground(HelloworldActivity.java:72)
	at android.os.AsyncTask$2.call(AsyncTask.java:333)
	at java.util.concurrent.FutureTask.run(FutureTask.java:266)
	at android.os.AsyncTask$SerialExecutor$1.run(AsyncTask.java:245)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1167)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:641)
	at java.lang.Thread.run(Thread.java:764)

```

