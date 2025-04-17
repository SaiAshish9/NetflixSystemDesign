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

<img width="1084" alt="Screenshot 2025-04-17 at 1 39 22 PM" src="https://github.com/user-attachments/assets/41fddd77-88af-4a3a-8c16-f21d63d30eca" />

We'll have different cache servers which will hold all the different copies of videos in different countries.

Video will be the served from the nearest edge server, less bandwidth will be consumed b/w India and US

Netflix have placed 1000s of servers in all the countries. Video will be played from very nearest server closest to the user.

Apart from OpenConnect, everytging was placed at AWS.

StartUp speed, run time performance, modularity.

Load is first balanced across the zones first then load is balanced across the instances.

<img width="482" alt="Screenshot 2025-04-17 at 1 53 03 PM" src="https://github.com/user-attachments/assets/cd2b332e-fd44-4562-a1da-289c3c59ccb6" />

2 tier balancing scheme.

Load is balanced using round robin algorithm.

<img width="459" alt="Screenshot 2025-04-17 at 2 04 41 PM" src="https://github.com/user-attachments/assets/aafa6d24-6165-4af0-8964-678ae7b82439" />

Video is transformed into different formats using transcoding and encoding.

<img width="1122" alt="Screenshot 2025-04-17 at 2 06 19 PM" src="https://github.com/user-attachments/assets/a1cea55e-02de-449a-a961-3742b531fc99" />

Transcoding will convert video into different formats optimised for diff. platforms and devices.

<img width="1131" alt="Screenshot 2025-04-17 at 2 09 06 PM" src="https://github.com/user-attachments/assets/b7ef0507-feee-4f2b-baf9-25c619b85b9c" />

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



```
