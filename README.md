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

# How to Replicate

 - Open Greeter.sln using Visual Studio and start Server using "Docker" 

Alternatively you can just use Docker commands. 

 - Open command promt or powershell and find your local ip adress.
 ```sh
$ ipconfig
Windows IP Configuration
...
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . : localdomain
   ...
   IPv4 Address. . . . . . . . . . . : 192.168.1.35
   ...
   
Ethernet adapter Bluetooth Network Connection:
....
```

 - Open command promt or powershell and your docker image port.
 ```sh
$ docker ps
CONTAINER ID        IMAGE                               COMMAND               CREATED             STATUS              PORTS                   NAMES
a944cb151e1f        server:dev                          "tail -f /dev/null"   About an hour ago   Up About an hour    0.0.0.0:59055->80/tcp   optimistic_brahmagupta
```

in my case it ended being 192.168.1.35:59055

- Open Android studio and Install Client-Android.
- Open the installed app and call your build IP with some random message for example "test", it should return Hello test, it does not.

