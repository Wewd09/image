# image
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Upload Example</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        #imageContainer {
            width: 300px;
            height: 300px;
            border: 2px solid #007BFF;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            margin-top: 10px;
        }

        #uploadButton {
            padding: 10px 20px;
            border: none;
            background-color: #007BFF;
            color: white;
            font-size: 16px;
            cursor: pointer;
        }

        #imageDisplay {
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            position: absolute;
            top: 0;
            left: 0;
            z-index: 0; /* Ensure background is below */
        }
    </style>
</head>
<body>
    <button id="uploadButton" onclick="document.getElementById('fileInput').click();">Upload Image</button>
    <input type="file" id="fileInput" accept="image/*" style="display:none;">

    <div id="imageContainer">
        <div id="imageDisplay"></div>
    </div>

    <script>
        document.getElementById('fileInput').addEventListener('change', function(event) {
            const file = event.target.files[0];
            if (file) {
                const reader = new FileReader();
                
                reader.onload = function(e) {
                    const imageDisplay = document.getElementById('imageDisplay');
                    imageDisplay.style.backgroundImage = `url(${e.target.result})`;
                };

                reader.readAsDataURL(file);
            }
        });
    </script>
</body>
</html>
