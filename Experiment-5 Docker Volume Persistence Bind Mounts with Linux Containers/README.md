<h1>🚀 Docker Volume Persistence: Bind Mounts on Linux Container 🐳</h1>
<br><h2>📌 Introduction</h2>
<p></p>This experiment demonstrates how to use Docker bind mounts with a Linux container to persist data beyond a container’s lifecycle. By mounting a local directory into a container, data remains accessible even after the container is removed.</p>

<br>🔧 Steps & Observations
<h3>🏗 Step 1: Running a Container with a Bind Mount</h3>
<br>You executed:

<br>docker run -dit --name alpine_with_bind_mount -v C:\Users\asus\docker_data:/data alpine:latest sh
<br>🔍 What Happened?
<br>Since alpine:latest was not found locally, Docker pulled it from the official repository.
<br>A new container named alpine_with_bind_mount was created.
<br>The -v flag mounted the local directory C:\Users\asus\docker_data to /data inside the container.
<br>The container started a shell (sh) in detached mode.
<h3>📄 Step 2: Creating a File Inside the Bind Mount</h3>
<br>Inside the container, you created a file:

<br>docker exec -it alpine_with_bind_mount sh -c "echo 'Hello, shreya!' > /data/testfile.txt"
<br>🔍 What Happened?
<br>The command executed a shell inside the running container.
<br>It created a file testfile.txt inside /data and wrote "Hello, shreya!" into it.
<br>Since /data is a bind-mounted directory, the file was actually stored in C:\Users\asus\docker_data on the host.
<h3>✅ Step 3: Verifying the File Exists</h3>
<br>To check the contents:

<br>docker exec -it alpine_with_bind_mount sh -c "cat /data/testfile.txt"
<h3>📌 Output:</h3>
<br>Hello, shreya!
<br>This confirms that the file was successfully created and accessible inside the container. 🎉

<h3>🗑 Step 4: Removing the First Container</h3>
<br>You removed the container:

<br>docker rm -f alpine_with_bind_mount
<br>🔍 What Happened?
<br>The container was forcefully stopped and removed.
<br>However, since testfile.txt was inside the bind-mounted directory, it remained on the host system. 🏠
<h3>🔄 Step 5: Creating a New Container with the Same Bind Mount</h3>
<br>You started a new container:

<br>docker run -dit --name new_alpine -v C:\Users\asus\docker_data:/data alpine sh
<br>🔍 What Happened?
<br>A new container named new_alpine was created.
<br>The same bind-mounted directory (C:\Users\asus\docker_data) was mounted to /data.
<h3>🔎 Step 6: Verifying File Persistence</h3>
<br>Inside the new container, you checked if testfile.txt still exists:

<br>docker exec -it new_alpine sh -c "cat /data/testfile.txt"
<h3>📌 Output:</h3>
<br>Hello, shreya!
<br>This confirms that bind mounts persist data even after a container is removed. 🔥

<h3>🎯 Conclusion</h3>
<br>✅ Bind mounts allow data persistence across multiple container instances.<br> ✅ Deleting a container does not remove data stored in the bind-mounted directory.<br> ✅ Any new container with the same mount can access previous container data. <br>✅ Useful for sharing files between containers and persisting data beyond the container’s lifecycle.

<h3>🚀 Next Steps</h3>
<br>🛠 Experiment with named volumes (docker volume create) to manage persistent storage more efficiently.
<br>🐳 Try using bind mounts with different container images.
<br>🔐 Explore how permissions impact bind-mounted files across host and container.
<br>🎯 This experiment showcases the power of bind mounts in Docker. Keep exploring, and happy coding! 🚀
