<h1>🚀 Docker Bridge: Balancing Isolation & Connectivity,</h1>
<h2>📌 Objective</h2>
<br>The goal of this exercise is to explore and demonstrate network isolation in Docker containers. We will examine how containers within the same custom bridge network can communicate, while those on different networks remain isolated. Understanding this is crucial for securing microservices and containerized applications.

<h3>🌐 Introduction to Docker Networking</h3>
<br>Docker networking is fundamental for containerized applications, allowing containers to communicate while ensuring security and isolation. Docker provides several networking options:

<h3>🔹 Types of Docker Networks:</h3>
<br>Bridge Network (Default) – Allows communication between containers using internal IPs unless restricted.
<br>Custom Bridge Network – Offers better control and supports name-based resolution.
<br>Host Network – Attaches containers directly to the host’s network stack.
<br>Overlay Network – Enables communication across multiple hosts (Docker Swarm).
<br>Macvlan Network – Assigns a MAC address to each container, making them appear as separate devices.
<br>None Network – Completely disables networking.
<br>For this demonstration, we focus on the custom bridge network, which improves control and network isolation.

<h3>⚡ Why Use a Custom Bridge Network?</h3>
<br>A custom bridge network offers several advantages:<br> ✅ Improved Security – Containers on different networks are isolated by default.<br> ✅ Better Performance – Direct communication without host networking stack overhead.<br> ✅ DNS-Based Resolution – Containers communicate via names instead of IPs. <br>✅ Greater Control – Define specific subnets, IP ranges, and gateways.

<br>To demonstrate, we create a custom bridge network called shreya-bridge and connect multiple containers.

<h3>🔧 1. Creating a Custom Bridge Network</h3>
<br>docker network create --driver bridge --subnet 172.20.0.0/16 --ip-range 172.20.240.0/20 shreya-bridge
<h2>🔍 Explanation:</h2>
<br>--driver bridge → Uses the default bridge network mode.
<br>--subnet 172.20.0.0/16 → Defines the network’s IP range.
<br>--ip-range 172.20.240.0/20 → Allocates IPs dynamically.
<h3>🚀 2. Running Containers in the Custom Network</h3>
<br>Running Redis Container (shreya-database)
<br>docker run -itd --net=shreya-bridge --name=shreya-database redis
<br>Running BusyBox Container (shreya-server-A)
<br>docker run -itd --net=shreya-bridge --name=shreya-server-A busybox
<h2>📌 Check Container IPs</h2>
<br>docker network inspect shreya-bridge
<br>Expected Output:

<br> shreya-database: 172.20.240.1
 <br>shreya-server-A: 172.20.240.2
<h3>📔 3. Testing Communication Between Containers</h3>
<br>Ping from shreya-database to shreya-server-A
<br>docker exec -it shreya-database ping 172.20.240.2
<br>Ping from shreya-server-A to shreya-database
<br>docker exec -it shreya-server-A ping 172.20.240.1
<br>✅ Expected Outcome: Both containers should successfully ping each other.

<h3>🚧 4. Demonstrating Network Isolation with a Third Container</h3>
<br>We add another container (shreya-server-B) on the default bridge network.

<br>docker run -itd --name=shreya-server-B busybox
<h2>📌 Get IP of shreya-server-B</h2>
<br>docker inspect -format='{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' shreya-server-B
<br>(Example IP: 172.17.0.2)

<h3>❌ 5. Testing Communication Between Different Networks</h3>
<br>Ping from shreya-database to shreya-server-B:

<br>docker exec -it shreya-database ping 172.17.0.2
<h3>🚨 Expected Outcome: The ping should fail, as they are on different networks.</h3>

<h3>🔍 6. Confirming Network Isolation</h3>
<br>Inspect Networks
<br>docker network inspect shreya-bridge
<br>docker network inspect bridge
<br>✅ shreya-bridge should contain shreya-database & shreya-server-A. <br>✅ bridge should contain shreya-server-B.

<h2>🏆 Conclusion</h2>
<br>Containers in the same network can communicate.
<br>Containers in different networks are isolated by default.
<br>Docker’s networking model ensures security and separation unless explicitly connected.
<h2>🚀 Now you have mastered Docker Bridge Networking! 🎯</h2>
