<html>
<head>
</head>
<body>

<form method="post" enctype="multipart/form-data">
<lable> Enter Name </label>
<input name="name" type="text"/>
<label>Upload CV</label>
<input type="file" name="ImageFilename"><br>
					<input type="submit" name ="submit">
                    </fomr>
<h1> Receive and echo  registration data
</h1>
<?php

if(isset($_POST['submit'])){
	extract($_POST);

	$mysqli = new mysqli("localhost","root","","courseproject");
	$upFile = "images/".date("Y_m_d_H_i_s").$_FILES["ImageFilename"]["name"];
	$name = filter_var($_POST['name'], FILTER_SANITIZE_STRING);
	print($upFile);
	if(is_uploaded_file($_FILES["ImageFilename"]["tmp_name"])) {
		if(!move_uploaded_file($_FILES["ImageFilename"]["tmp_name"], $upFile)) {
			echo "Problem could not move file to destination. Please check again later. <a href='index.php'>Please go back.</a>";
			exit;
		}
	} else {
		echo "Problem: Possible file upload attack. Filename: ";
		echo $_FILES["ImageFilename"]["name"];
		exit;
	}

	
	$query = "INSERT INTO USER (name,path) VALUES ('$name','$upFile')" ; 
	echo $query ; 
	$addingResult = mysqli_query($mysqli,$query);
	
	if ($addingResult == true){ 
		echo "User Added" ; 
	}	

else {
    echo "there was a problem moving the file";
}
 

?>
