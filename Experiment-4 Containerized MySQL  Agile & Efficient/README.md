<h1>🐬 Setting Up MySQL in a Docker Container with an Initialization Script 🚀</h1>
<h2>📌 Prerequisites</h2>
<br>✅ Install Docker on your system.
<br>✅ Ensure Docker is running.
<br>✅ Create an SQL initialization script (database_students.sql) with database and table definitions.

<h2>📂 Project Directory Structure</h2>
<br>Ensure your project directory is organized as follows:

<br>project-directory/<br>
│── Dockerfile<br>
│── database_students.sql<br>
This structure keeps all necessary files in one place for an efficient setup.<br>

<h3>🛠 Step 1: Create a Dockerfile</h3>
<br>Create a Dockerfile in your project directory:

# 🏗 Use the official MySQL image<br>
FROM mysql:latest<br><br>

# 📂 Copy initialization script to the container<br>
COPY database_students.sql /docker-entrypoint-initdb.d/<br><br>

# 🔥 Expose MySQL port<br>
EXPOSE 3306<br><br>
<h3>📜 Step 2: Create an SQL Initialization Script</h3>
<br>Create a file named database_students.sql in the same directory:

<br>CREATE DATABASE student_db;
<br>USE student_db;

<br>CREATE TABLE students (
    <br>id INT AUTO_INCREMENT PRIMARY KEY,
    <br>name VARCHAR(100),
   <br> age INT
<br>);

<br>INSERT INTO students (name, age) VALUES ('Alice', 22), ('Bob', 24);<br>
<h3>🏗 Step 3: Build the Docker Image</h3>
<br>Run the following command to build the Docker image:

<br>docker build -t mysql-custom .
<br>💡 This command creates a custom MySQL image named mysql-custom.

<h3>🚀 Step 4: Run MySQL Container</h3>
<br>To start a MySQL container using the custom image and set the root password, execute:

<br>docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=root -d mysql-custom
<br>🧐 Explanation:
<br>🏷 Creates a container named mysql-container.
<br>🔐 Sets the root password to root.
<br>🏃 Runs the container in detached mode (-d).
<br>🛠 Uses the custom MySQL image mysql-custom.

<h3>🔍 Step 5: Access the Running Container</h3>
<br>To enter the running container’s shell:

<br>docker exec -it mysql-container bash
<br>💡 This command opens an interactive terminal session inside mysql-container.

<br><h3>💻 Step 6: Connect to MySQL</h3>
<br>Once inside the container, access MySQL using:

<br>mysql -u root -p
<br>🔑 Enter the root password (root) when prompted.

<h3>🏗 Step 7: Verify Database and Tables</h3>
<br>After logging into MySQL, check the available databases:

<b3>SHOW DATABASES;
<b3>🔄 Switch to the student_db database:

<b3>USE student_db;
<b3>📊 Query the students table:

<b3>SELECT * FROM students;
<h2>🎉 Conclusion</h2>
<br>🎯 You have successfully set up MySQL in a Docker container with an initialization script. This method ensures that the database is automatically initialized with predefined schemas and data when the container starts.

<h2>🚀 Happy coding! 🎨</h2>
