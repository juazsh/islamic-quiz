<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
  
<?php  

$mysqli = new mysqli("localhost","root","","courseproject");


    $BookID = $_SESSION['Bookid'];     
    $query = "Select * from book where BookId ='$BookID'"; 
    $books = mysqli_query($mysqli,$query);

    while($book = mysqli_fetch_array($books))
    {
        $form = '<form method="post" action="/">';
        $form += '<label>'. $book["id"] . '</label>';
        $form += '<input type="hidden" name="title" value="'.$book["id"]. '" />';
        $form +=  '<label>Price:' .$book["price"]. '</label>';
        $form +=   '<input type ="hidden" name="price" value ="' .$book["price"]. '" />';
        $form +=  '<label>Enter Quantity: </label><input name="quantity" id="quantity" />' 
         $form += '<input type="submit" name="submit" value="Buy" />';
        $form +=  '</form>';
        echo $form;
    }
    

if(isset($_POST['submit'])){
    
    $quantity = filter_var($_POST['quantity'], FILTER_SANITIZE_STRING);
    $title = filter_var($_POST['title'], FILTER_SANITIZE_STRING);
    $price = filter_var($_POST['price'], FILTER_SANITIZE_STRING);
    $cost = total_cost($price, $quantity);
    echo "Thank you. You ordered book title " + $title +" and cost  " + $cost ; 
        
    
    
		
}


function total_cost($price, $quantity) {
    return ($price*$quantity)*1.15;
}
?>

  
</body>
</html>
