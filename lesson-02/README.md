<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>Retirement</title>
</head>

<body>

<h1>Thinking about retirement?</h1>
<p>Enter your birthdate and see if you qualify for Social Security retirement benefits.</p>

<?php
// evaluate whether page has been processed
if ($_SERVER['REQUEST_METHOD'] === 'POST' ) {
?>    

<?php

// this function calculates age based on a date
function age($birthdate) {
	return (strtotime('now') - strtotime($birthdate))/(60*60*24*365);	
}

// call function, variable age = result of function
$age = age($_POST['birthdate']);

$retage = 67;

$diff = $retage - $age;

// conditional statement
if ($age >= 67) {
	
?>

    <h2 style="color:green">You are <?php echo intval($age) ?>. Congratuations! You can retire with full Social Security retirement benefits.</h2>
    
<?php
	
} else {
	
?>
    <h2 style="color:red">Sorry, you are only <?php echo intval($age) ?>. You have <?php echo intval($diff) ?> more years before you can retire with full Social Security retirement benefits. Keep working!</h2>

<?php
}

} else {
?>
    <form action="" method="post">
    <input name="birthdate" type="text">
    <input name="" type="submit">
    </form>

<?php
}

?>
</body>
</html>