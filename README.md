# 🕹 Project
Signup and Login Project

## 👨🏼‍💻Scenario

Users can add new tasks by entering the task title. When the "Add Task" button is clicked, the task is inserted into the "tasks" table in the database, and when user click delete button the task that choosen will disappear.


## ⚡️Requirements:

1. Add Tasks:
- Registered users should be able to log in using their credentials.
- Verify the user's entered password against the stored hashed password.
- Implement session management to maintain user authentication across different pages.

2. Delete Tasks:
- Users can delete tasks by selecting them from the list and clicking the "Delete Task" button. The application removes the selected tasks from the database.

3. Database:
- Stored into text.txt in text editor (VS Code)

## 🤖Programming Language
This program was made by `PHP`, `SQL`, `HTML`, also `CSS`

## 🦾Implementation
1. Preparation: <br>
Before going to the code, we make files that include:
- `index.php`
- `login.php`
- `signup.php`
- `connection.php`
- `functions.php`

2. Index.php:
In this file we make page that will show after login to the web, the code show below:
```
<!DOCTYPE HTML>
<html>
	<head>
		<title>Halaman utama</title>
		<meta charset="utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no" />
		<link rel="stylesheet" href="assets/css/main.css" />
		<noscript><link rel="stylesheet" href="assets/css/noscript.css" /></noscript>
	</head>
	<body class="is-preload">
		<div id="wrapper">
			<div id="bg"></div>
			<div id="overlay"></div>
			<div id="main">
				<!-- Header -->
					<header id="header">
						<h1>Raja Syam</h1>
						<p>Web Dev &nbsp;&bull;&nbsp; Back-End &nbsp;&bull;&nbsp; Never asked for this</p>
						<nav>
							<ul>
								<li><a href="https://instagram.com/rajasyamabbas" class="icon brands fa-instagram"><span class="label">Instagram</span></a></li>
								<li><a href="https://www.linkedin.com/in/raja-syam-abbas-shagir/" class="icon brands fa-linkedin"><span class="label">LinkedIn</span></a></li>
								<li><a href="https://youtube.com/@syam-data" class="icon brands fa-youtube"><span class="label">YouTube</span></a></li>
								<li><a href="https://github.com/rajasyamabbas" class="icon brands fa-github"><span class="label">Github</span></a></li>
								<li><a href="mailto:rajasyamabbas@gmail.com" class="icon solid fa-envelope"><span class="label">Email</span></a></li>
							</ul>
						</nav>
					</header>

				<!-- Footer -->
					<footer id="footer">
						<span class="copyright">&copy; Made with: ❤️.</span>
					</footer>

			</div>
		</div>
		<script>
			window.onload = function() { document.body.classList.remove('is-preload'); }
			window.ontouchmove = function() { return false; }
			window.onorientationchange = function() { document.body.scrollTop = 0; }
		</script>
	</body>
</html>
```

3. Make a login code

```
<?php 

session_start();

	include("connection.php");
	include("functions.php");

	if ($_SERVER['REQUEST_METHOD'] == "POST") 
	{
		// something was posted
		$user_name = $_POST['user_name'];
		$password = $_POST['password'];

		if (!empty($user_name) && !empty($password) && !is_numeric($user_name)) 
		{
			// read from database
			$query = "SELECT * FROM users WHERE user_name = '$user_name'";
			$result = mysqli_query($con, $query);

			if ($result) {
				if ($result && mysqli_num_rows($result) > 0) 
				{
					$user_data = mysqli_fetch_assoc($result);
					if ($user_data['password'] === $password) {
						$_SESSION['user_id'] = $user_data['user_id'];
						header("Location: index.php");
						die;
					}
				}
			}
			echo "wrong username or password";
		}else
		{
			echo "wrong username or password";
		}
	}

?>
```

4. Singup code
```
<?php 
session_start();

	include("connection.php");
	include("functions.php");

	if ($_SERVER['REQUEST_METHOD'] == "POST") 
	{
		// something was posted
		$user_name = $_POST['user_name'];
		$password = $_POST['password'];

		if (!empty($user_name) && !empty($password) && !is_numeric($user_name)) 
		{
			// save to database
			$user_id = random_num(20);
			$query = "INSERT INTO users (user_id,user_name,password) VALUES ('$user_id','$user_name','$password')";

			mysqli_query($con, $query);

			header("Location: login.php");
			die;
		}else
		{
			echo "Please enter some valid information!";
		}
	}
?>
```

## 👌🏻Result

See the complete demo on video below:

[![Video Name](https://img.youtube.com/vi/sHiYCDOwDZs/0.jpg)](https://www.youtube.com/watch?v=sHiYCDOwDZs)

*Click this button to see complete code* 
[CLICK ME](https://github.com/rajasyamabbas/signup-login-system/archive/refs/heads/main.zip)
