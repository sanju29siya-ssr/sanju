<?php
include "dbconnect.php";
header("Content-Type: application/json");

if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    $user_id = $_POST['user_id'];
    $product_id = $_POST['product_id'];
    $quantity = isset($_POST['quantity']) ? $_POST['quantity'] : 1;

    $query = "INSERT INTO cart (user_id, product_id, quantity) VALUES ('$user_id', '$product_id', '$quantity')";
    if (mysqli_query($conn, $query)) {
        echo json_encode(["status" => "success", "message" => "Item added to cart"]);
    } else {
        echo json_encode(["status" => "error", "message" => "Error adding to cart: " . mysqli_error($conn)]);
    }
}
?>
