I utilized the following templates for the Website Project:

# Boostrap Documentation

**Images:**  
[Bootstrap Images](https://getbootstrap.com/docs/5.3/content/images/)

**Text:**  
[Bootstrap Text Utilities](https://getbootstrap.com/docs/5.3/utilities/text/)

**Card:**  
[Bootstrap Card Component](https://getbootstrap.com/docs/5.3/components/card/)

**Navbar:**  
[Bootstrap Navbar Component](https://getbootstrap.com/docs/5.3/components/navs-tabs/)

# Leaflet CSS Mapping Tool (Developed with help of ChatGPT and Leaflet Documentation)

[Leaflet CSS](https://unpkg.com/leaflet@1.7.1/dist/leaflet.css)

# Assistance from ChatGPT

- Code to make card image sizes and text boxes align in size
**
<style>
    .card-img-top {
        height: 400px; /* Adjust the height of the images (This was done with help of ChatGPT)*/  
        object-fit: cover;
    }

    .card-body {
        height: 900px; /* Adjust the height of the card body (This was done with help of ChatGPT)*/
        overflow: auto; /* Enable scrolling if the content exceeds the height (This was done with help of ChatGPT)*/
    }

    .card-title {
        height: 60px; /* Ensure the same height for all card titles(This was done with help of ChatGPT) */
    }
</style>**

- Code to have quotes randomly displayed at the top of the page (with guidance from me regarding the quotes and prompt engineering)
**<!-- Display random historic quote (This was done with help of ChatGPT) -->
<div id="quote-container" class="container">
    <blockquote class="blockquote text-center">
        <p id="quote"></p>
        <footer class="blockquote-footer" id="author"></footer>
    </blockquote>
</div>

<script>
    // Array of historic quotes (This was done with help of ChatGPT)
    const quotes = [
        { quote: "The only true wisdom is in knowing you know nothing.", author: "Socrates" },
        { quote: "The only way to do great work is to love what you do.", author: "Steve Jobs" },
        { quote: "I have a dream.", author: "Martin Luther King Jr." },
        { quote: "In three words I can sum up everything I've learned about life: It goes on.", author: "Robert Frost" },
        { quote: "To be yourself in a world that is constantly trying to make you something else is the greatest accomplishment.", author: "Ralph Waldo Emerson" },
        { quote: "You miss 100% of the Shots you dont take", author: "Wayne Gretsky or maybe Micheal Jordan"},
        { quote: "Milk is good for you", author:"United Milk Alliance"},
        {quote:"It takes something more than intelligence to act intelligently", author:"Fyodor Dostoyevsky"},
        // Add more quotes as needed
    ];

    // Function to display a random quote
    function displayRandomQuote() {
        const randomIndex = Math.floor(Math.random() * quotes.length);
        const randomQuote = quotes[randomIndex];
        document.getElementById('quote').textContent = randomQuote.quote;
        document.getElementById('author').textContent = randomQuote.author;
    }

    // Display a random quote when the page loads
    window.addEventListener('DOMContentLoaded', displayRandomQuote);
</script>**
- Code to have the leaflet map load coordinates from a CSV file in the directory instead of having the values hardcoded.

** 
 // Load CSV data and create heatmap
fetch('heatmap_data.csv')
    .then(response => response.text())
    .then(csvData => {
        // Parse CSV data
        var rows = csvData.split('\n');
        var heatMapData = [];
        for (var i = 1; i < rows.length; i++) { // Start from index 1 to skip headers
            var columns = rows[i].split(',');
            var city = columns[0];
            var latitude = parseFloat(columns[1]); // Latitude is in column 1
            var longitude = parseFloat(columns[2]); // Longitude is in column 2
            // Check if latitude and longitude are valid numbers
            if (!isNaN(latitude) && !isNaN(longitude)) {
                var intensity = Math.random(); // Assign random intensity value
                heatMapData.push([latitude, longitude, intensity]);
            } else {
                console.error('Invalid latitude or longitude for city:', city);
            }
        }
        // Code to have the leaflet map display specific coordinates at random intensity values
        // Create heatmap layer
        var heat = L.heatLayer(heatMapData, {
            radius: 20, // Adjust radius for heatmap intensity
            blur: 15, // Adjust blur for heatmap intensity
            maxZoom: 10 // Limit heatmap visibility to certain zoom levels
        }).addTo(map);
    })
    .catch(error => console.error('Error fetching CSV:', error));
**
- Code to make search bar functional by connecting it to Google (Based on feedback to Website Challenge)
**<script>
                function search() {
                    // Get the search query from the input field
                    var searchQuery = document.getElementById('search-input').value;
            
                    // Construct the Google search URL
                    var googleSearchUrl = "https://www.google.com/search?q=" + encodeURIComponent(searchQuery);
            
                    // Redirect the user to the Google search results page
                    window.location.href = googleSearchUrl;
            
                    // Prevent the form from submitting to a different page
                    event.preventDefault();
                }
            </script>**

- Debugging the embeding of My Resume into an HTML File.

**<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Resume</title>
</head>
<body>
    <h1>David Keptsi's Resume</h1>
    <embed src="Dkeptsi Resume 2024.pdf" type="application/pdf" width="100%" height="800px">
</body>
</html>**

```

** (MIT License)**
