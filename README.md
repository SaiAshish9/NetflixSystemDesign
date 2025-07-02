```
1. More than 125 Million Subscribers,
2. Presence in more than 200+ countries.

Netflix Operates In 2 Clouds:
1. AWS 
2. OpenConnect

Both should work seemlessly to deliver content for youtube.

Netflix has 3 main components:
1. OpenConnect
2. Backend
3. Client => Any device from which we play the video: Android, Desktop, iPhone, WebSite.

OpenConnect is Netflix Own CDN placed at different locations to serve the content much faster.

Avoid data transfer from India to US.

Let's have more servers placed in different countries.
```

<img width="1084" alt="Screenshot 2025-04-17 at 1 39 22 PM" src="https://github.com/user-attachments/assets/41fddd77-88af-4a3a-8c16-f21d63d30eca" />

```
We'll have different cache servers which will hold all the different copies of videos in different countries.

Video will be the served from the nearest edge server, less bandwidth will be consumed b/w India and US

Netflix have placed 1000s of servers in all the countries. Video will be played from very nearest server closest to the user.

Apart from OpenConnect, everytging was placed at AWS.

StartUp speed, run time performance, modularity.

Load is first balanced across the zones first then load is balanced across the instances.
```

<img width="482" alt="Screenshot 2025-04-17 at 1 53 03 PM" src="https://github.com/user-attachments/assets/cd2b332e-fd44-4562-a1da-289c3c59ccb6" />

```
2 tier balancing scheme.

Load is balanced using round robin algorithm.
```

<img width="459" alt="Screenshot 2025-04-17 at 2 04 41 PM" src="https://github.com/user-attachments/assets/aafa6d24-6165-4af0-8964-678ae7b82439" />

```
Video is transformed into different formats using transcoding and encoding.
```

<img width="1122" alt="Screenshot 2025-04-17 at 2 06 19 PM" src="https://github.com/user-attachments/assets/a1cea55e-02de-449a-a961-3742b531fc99" />

```
Transcoding will convert video into different formats optimised for diff. platforms and devices.
```

<img width="1131" alt="Screenshot 2025-04-17 at 2 09 06 PM" src="https://github.com/user-attachments/assets/b7ef0507-feee-4f2b-baf9-25c619b85b9c" />

```
Convert the video to different resolutions to make the vieweing experience much better.

1.5 hr movie 50GB

Space contraint

webApp resolution => much bigger
iPhone => less

Slow N/W => Less Resolution
High N/W => High Resolution 4K/10K

Bandwidth less, this kind of switching is called Adaptive Bit Rate.

File optimized for different N/W speeds.

1000-2000 copies of same movie with diff resolutions, parallel workers.

Video is breaked into chunks, place into the Queue and they all be placed in the workers and then uploaded to S3.

(Break, Process, Upload, Merge)

Source will be converted to different movies, hence we'll have 1000-2000 copies of videos converted to different formats.

Application will figure out best video from openConnect using AI and plays that video.
```

<img width="540" alt="Screenshot 2025-04-17 at 2 19 43 PM" src="https://github.com/user-attachments/assets/b8b4c80e-25b5-4308-b97a-4fc90aad47f0" />

<img width="577" alt="Screenshot 2025-04-17 at 2 20 30 PM" src="https://github.com/user-attachments/assets/9973feea-6b9d-4c5d-9cf6-94fce54ce154" />


```
ZUUL is a gateway service that provides dynamic routing, monitoring, resilience and security => inbound filter, endpoint filter, outbound filter.

1. SHard Traffic
2. LOAD Test
3. Test New Service
4. Filter Bad Service

Beta Testing

Hystrix

Latency and fault tolerant library designed to isolate the points of access to the remote systems and services and third party libraries.

Stop Cascading failures and real time monitoring

<img width="799" alt="Screenshot 2025-04-17 at 2 29 08 PM" src="https://github.com/user-attachments/assets/2d2a485c-916d-493c-96bf-ff20af787886" />

can configure to give a default response if service always fails

MicroServices
=> Critical

User should be able to access those features and make them highly available.

=> Stateless
=> More Reliable
```

<img width="499" alt="Screenshot 2025-04-17 at 2 48 37 PM" src="https://github.com/user-attachments/assets/b22ca58f-5d81-4812-8d3b-6660bea8046a" />

```
Netflix have built their own custom caching layer called EV Cache.
```

<img width="437" alt="Screenshot 2025-04-17 at 2 51 27 PM" src="https://github.com/user-attachments/assets/4eb92149-6bda-4879-9eaf-aa240246feee" />

```
Memcached DB

Read will happen only from the cache server

Advantages of having caching layers in the system:
1. Throughput 
2. Latency
3. Cost

Netflix heavily uses caching layer to save money or SSD in case of RAM.

SSD sits in between the harddisk and RAM and hence its better in comparison to having more RAM.

Netflix uses 2 databases:
1. RDBMS
2. Cassandra

<img width="499" alt="Screenshot 2025-04-17 at 2 58 16 PM" src="https://github.com/user-attachments/assets/3e899e19-ec6b-4458-9997-703b9d088b4c" />

Netflix has read replicas in each and every nodes. (Reads vs Writes, 9:1)

<img width="860" alt="Screenshot 2025-04-17 at 3 01 31 PM" src="https://github.com/user-attachments/assets/cc76a907-8ef6-4081-826d-2fee827b7657" />

Live viewing history, compressed viewing history.

Compress the data, uncompress and use it when required,
```

<img width="442" alt="Screenshot 2025-04-17 at 3 04 06 PM" src="https://github.com/user-attachments/assets/f4302324-8d8c-4282-ab34-8e0fefc7c373" />

```
Netflix produces 500B events and 1.3PB everyday.

All the logs from different parts of a distributed system will be sent to chukwa where we can do monitoring like S3 and kafka. Copy of data is sent to kafka.

From kafka to s3 and ES, Apache samza does the routing.

Elastic Search:
=> 1500 Clusters
=> 3500 Instances

APM all the events happening for that user.

How Netflix is using Spark and ML to do recommendations and all:
1. Sorting
2. Relevance
3. Row Selection

Spark Models.

When user loads front page, Netflix can decide what to show to the user.

Movie Recommendation System =>
1. Collaborative Filtering
2. Content Based

Open Connect =>

Free of charge
High Availability with redundant components

125 millions == 10TB/sec
Small OCA
Big OCA

How does Netflix figure out what content to be cached at which server:
Caching Content
Popular Content
Historical Viewing Pattern
```

```
Netflix uses consistent hashing inside OpenConnect.

Route53 for DNS resolution, Autoscaling for scaling infrastructure.
```
