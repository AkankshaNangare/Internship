# Internship
# Create a simple html page and load user images using a JSON of this structure [ { "image":"url"}]. Add 25 image object in JSON array and your test is evaluated based on how fast the images are loading and the coding practices.


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Images</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f0f0f0;
        }
        .image-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
            padding: 20px;
            
        }
        .image-item {
            
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
        }
        .image-item img {
            
            width: 100%;
            height: auto;
            display: block;
        }
        .button {
            padding: 8px 16px;
            width: 300px;
            background-color: #c1cad3;
            color: #161414;
            font-size:medium;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .button:hover {
            background-color:rgba(46, 162, 166, 0.8);
        }
        .name-profession {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background-color: rgba(46, 162, 166, 0.8);
            /* padding: 5px; */
            display: none;
        }
    </style>
</head>
<body>
    <div class="image-grid" id="image-grid"></div>
<script>
        document.addEventListener("DOMContentLoaded", function() {
            const images = [
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "John Doe", "profession": "Web Developer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Jane Smith", "profession": "Graphic Designer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },
                { "image": "https://img.freepik.com/free-photo/portrait-successful-man-having-stubble-posing-with-broad-smile-keeping-arms-folded_171337-1267.jpg?size=626&ext=jpg&ga=GA1.1.379831603.1708620886&semt=ais", "name": "Alex Johnson", "profession": "Photographer" },

            ];

            const imageGrid = document.getElementById("image-grid");

            images.forEach(imageData => {
                const imageUrl = imageData.image;
                const name = imageData.name;
                const profession = imageData.profession;
                const imageItem = document.createElement("div");
                imageItem.classList.add("image-item");

                const imageElement = document.createElement("img");
                imageElement.src = imageUrl;
                imageElement.alt = "User Image";

                const captionElement = document.createElement("div");
                captionElement.classList.add("name-profession");
                captionElement.textContent = `${name}, ${profession}`;

                const buttonElement = document.createElement("button");
                buttonElement.classList.add("button");
                buttonElement.innerHTML = `${name} <br> ${profession}`;

                buttonElement.addEventListener("click", function() {
                    captionElement.style.display = (captionElement.style.display === "none") ? "block" : "none";
                });

                imageItem.appendChild(imageElement);
                imageItem.appendChild(buttonElement);
                imageItem.appendChild(captionElement);
                imageGrid.appendChild(imageItem);
            });
        });
    </script>
</body>
</html>
