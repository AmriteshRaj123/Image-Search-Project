# Image Search App

This is a simple image search application that allows users to search for images using the Unsplash API. Users can enter a keyword, submit the search form, and view the results on the page. Additionally, users can load more results by clicking a "Show More" button.

## Features

- Search for images using keywords
- Display search results with clickable links to the image on Unsplash
- Load more results with the "Show More" button

## Getting Started

### Prerequisites

- A web browser
- An internet connection

### Installation

1. Clone the repository:

    ```bash
    git clone https://github.com/yourusername/image-search-app.git
    cd image-search-app
    ```

2. Open the `index.html` file in your web browser to run the application.

### Usage

1. Enter a keyword in the search box.
2. Press the "Search" button to fetch and display images related to the keyword.
3. Click the "Show More" button to load more images.

### Code Overview

The main functionality of the application is implemented in the `script.js` file. Below is a brief explanation of the code:

- `searchForm`, `searchBox`, `searchResult`, and `showMoreBtn` are DOM elements retrieved using `document.getElementById`.
- `accessKey` is the Unsplash API access key.
- `keyword` and `page` are variables to store the current search keyword and page number.
- `searchImages` is an asynchronous function that fetches images from the Unsplash API and displays them on the page.
- Event listeners are added to the search form and the "Show More" button to handle user interactions.

### Example Code

```javascript
const searchForm = document.getElementById("search-form");
const searchBox = document.getElementById("search-box");
const searchResult = document.getElementById("search-result");
const showMoreBtn = document.getElementById("show-more-btn");

const accessKey = "bIGzXRka_gCeJIAd2jKZ3eewmMb1sTBHaObXSm_YX_0";

let keyword = "";
let page = 1;

async function searchImages() {
  keyword = searchBox.value;
  const url = `https://api.unsplash.com/search/photos?page=${page}&query=${keyword}&client_id=${accessKey}&per_page=12`;

  const response = await fetch(url);
  const data = await response.json();

  if (page == 1) {
    searchResult.innerHTML = "";
  }

  const results = data.results;

  results.map((result) => {
    const image = document.createElement("img");
    image.src = result.urls.small;
    const imageLink = document.createElement("a");
    imageLink.href = result.links.html;
    imageLink.target = "_blank";

    imageLink.appendChild(image);
    searchResult.appendChild(imageLink);
  });

  showMoreBtn.style.display = "block";
}

searchForm.addEventListener("submit", (e) => {
  e.preventDefault();
  page = 1;
  searchImages();
});

showMoreBtn.addEventListener("click", () => {
  page++;
  searchImages();
});
