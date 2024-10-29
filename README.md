<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JONI MOTEL Online Reservation System</title>
    <link href="https://maxcdn.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css" rel="stylesheet">
    <style>
        /* Background for the entire page */
        body {
            background: color fffff 4px;; /* Replace with your apartment image URL */
            background: size 5px;;
            background-repeat: no-repeat;
            background-attachment: fixed;
            color: #333;
        }
        
        .header-title {
            color: #007bff;
            font-size: 2rem;
            font-weight: bold;
        }

        /* Framed and enhanced form container */
        .form-container {
            background-color: #fffff2;
            padding: 30px;
            border-radius: 8px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.3);
            max-width: 700px;
            margin: auto;
            border: 2px solid #007bff;
            margin-top: 20px;
        }

        /* Room images styling */
        .room-image {
            max-width: 100%;
            height: auto;
            margin-bottom: 15px;
            border-radius: 8px;
        }

        /* Price display styling */
        .price-display {
            font-size: 1.2rem;
            color: #28a745;
            margin-top: 10px;
        }

        /* Background color for confirmation message */
        .alert-success {
            background-color: #e6ffed;
            color: #155724;
        }

        /* Button styling */
        .btn-primary {
            background-color: #007bff;
            border: none;
        }

        .btn-primary:hover {
            background-color: #0056b3;
        }

        /* Footer with contact information */
        .footer {
            margin-top: 30px;
            text-align: center;
            color: #555;
            font-size: 1.1rem;
        }
    </style>
</head>
<body>

<div class="container mt-5">
    <!-- Logo and Motel Name -->
    <div class="d-flex align-items-center justify-content-center">
    
        <span class="header-title">JONI MOTEL</span>
    </div>

    <h2 class="text-center mt-4">Hotel Room Reservation</h2>

    <!-- Sign Up and Sign In Buttons -->
    <div class="text-center my-4">
        <button class="btn btn-outline-primary" data-toggle="modal" data-target="#signUpModal">Sign Up</button>
        <button class="btn btn-outline-secondary" data-toggle="modal" data-target="#signInModal">Sign In</button>
    </div>

    <?php
    if ($_SERVER["REQUEST_METHOD"] == "POST") {
        $name = htmlspecialchars($_POST['name']);
        $email = htmlspecialchars($_POST['email']);
        $phone = htmlspecialchars($_POST['phone']);
        $roomType = htmlspecialchars($_POST['roomType']);
        $checkIn = htmlspecialchars($_POST['checkIn']);
        $checkOut = htmlspecialchars($_POST['checkOut']);

        echo "<div class='alert alert-success' role='alert'>";
        echo "<h4 class='alert-heading'>Reservation Confirmed!</h4>";
        echo "<p>Name: $name</p>";
        echo "<p>Email: $email</p>";
        echo "<p>Phone: $phone</p>";
        echo "<p>Room Type: $roomType</p>";
        echo "<p>Check-In Date: $checkIn</p>";
        echo "<p>Check-Out Date: $checkOut</p>";
        echo "</div>";
    } else {
    ?>

    <!-- Reservation Form with Room Images and Price Range -->
    <div class="form-container">
        <form action="" method="POST">
            <div class="form-group">
                <label for="name">Full Name</label>
                <input type="text" class="form-control" id="name" name="name" required>
            </div>
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" class="form-control" id="email" name="email" required>
            </div>
            <div class="form-group">
                <label for="phone">Phone</label>
                <input type="text" class="form-control" id="phone" name="phone" required>
            </div>
            <div class="form-group">
                <label for="roomType">Room Type</label>
                <select class="form-control" id="roomType" name="roomType" onchange="updateRoomInfo()" required>
                    <option value="">Select Room Type</option>
                    <option value="Single">Single Room</option>
                    <option value="Double">Double Room</option>
                    <option value="Suite">Suite</option>
                </select>
            </div>
            
            <!-- Room images displayed based on selection -->
            <div id="room-image-container" class="text-center">
                <img id="singleRoom" src="single-room.jpg" alt="Single Room" class="room-image" style="display:none;">
                <img id="doubleRoom" src="double-room.jpg" alt="Double Room" class="room-image" style="display:none;">
                <img id="suiteRoom" src="suite-room.jpg" alt="Suite Room" class="room-image" style="display:none;">
            </div>
            
            <!-- Price Display based on Room Type -->
            <div id="price-display" class="price-display text-center"></div>

            <div class="form-group">
                <label for="checkIn">Check-In Date</label>
                <input type="date" class="form-control" id="checkIn" name="checkIn" required>
            </div>
            <div class="form-group">
                <label for="checkOut">Check-Out Date</label>
                <input type="date" class="form-control" id="checkOut" name="checkOut" required>
            </div>
            <button type="submit" class="btn btn-primary btn-block">Book Now</button>
        </form>
    </div>

    <?php } ?>

    <!-- Footer with Contact Us Section -->
    <div class="footer">
        <p>Contact Us: <strong>0777456788</strong></p>
    </div>
</div>

<!-- Sign Up Modal -->
<div class="modal fade" id="signUpModal" tabindex="-1" role="dialog" aria-labelledby="signUpModalLabel" aria-hidden="true">
    <div class="modal-dialog" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="signUpModalLabel">Sign Up</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <button class="btn btn-outline-danger btn-block mb-2">Continue with Google</button>
                <hr>
                <form>
                    <div class="form-group">
                        <label for="signUpEmail">Email</label>
                        <input type="email" class="form-control" id="signUpEmail" required>
                    </div>
                    <div class="form-group">
                        <label for="signUpPassword">Password</label>
                        <input type="password" class="form-control" id="signUpPassword" required>
                    </div>
                    <button type="submit" class="btn btn-primary btn-block">Sign Up</button>
                </form>
            </div>
        </div>
    </div>
</div>

<!-- Sign In Modal -->
<div class="modal fade" id="signInModal" tabindex="-1" role="dialog" aria-labelledby="signInModalLabel" aria-hidden="true">
    <div class="modal-dialog" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title" id="signInModalLabel">Sign In</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
            </div>
            <div class="modal-body">
                <button class="btn btn-outline-danger btn-block mb-2">Continue with Google</button>
                <hr>
                <form>
                    <div class="form-group">
                        <label for="signInEmail">Email</label>
                        <input type="email" class="form-control" id="signInEmail" required>
                    </div>
                    <div class="form-group">
                        <label for="signInPassword">Password</label>
                        <input type="password" class="form-control" id="signInPassword" required>
                    </div>
                    <button type="submit" class="btn btn-primary btn-block">Sign In</button>
                </form>
            </div>
        </div>
    </div>
</div>

<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.2/dist/js/bootstrap.bundle.min.js"></script>
<script>
    // Function to update room image and price based on selected room type
    function updateRoomInfo() {
        // Hide all room images initially
        document.getElementById('singleRoom').style.display = 'none';
        document.getElementById('doubleRoom').style.display = 'none';
        document.getElementById('suiteRoom').style.display = 'none';

        // Variables for displaying price range
        let priceText = "";
        let roomType = document.getElementById('roomType').value;

        // Show selected room type image and set price
        if (roomType === 'Single') {
            document.getElementById('singleRoom').style.display = 'block';
            priceText = "Price Range: $50 - $80 per night";
        } else if (roomType === 'Double') {
            document.getElementById('doubleRoom').style.display = 'block';
            priceText = "Price Range: $90 - $120 per night";
        } else if (roomType === 'Suite') {
            document.getElementById('suiteRoom').style.display = 'block';
            priceText = "Price Range: $150 - $200 per night";
        }

        // Display the price range
        document.getElementById('price-display').innerText = priceText;
    }
</script>
</body>
</html>
