# Project Title

Web Scraper for AndhraJyothy News

## Description

This project is a Python-based web scraper designed to scrape news articles from the AndhraJyothy website. It navigates through different news categories, fetches articles, and stores them in JSON format. The scraper uses the `requests` library for HTTP requests, `BeautifulSoup` for parsing HTML content, and `json` for storing the scraped data.
Check out the article link here: https://www.andhrajyothy.com/

## Features

- **Randomized User Agents**: To avoid being blocked by the website, the scraper uses a pool of user agents and randomly selects one for each request.
- **Retry Mechanism**: Utilizes a retry strategy to handle transient HTTP errors.
- **Category-Based Scraping**: Scrapes multiple categories such as national news, latest news, politics, etc.
- **Error Handling**: Gracefully handles errors and continues the scraping process.
- **Data Storage**: Saves the links of scraped articles to prevent duplicates and stores articles' content in JSON files categorized by their type.

## Prerequisites

- Python 3.6 or higher
- Required Python libraries: `requests`, `beautifulsoup4`

## Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

2. Install the required libraries:

    ```sh
    pip install requests beautifulsoup4
    ```

## Usage

To run the scraper, simply execute the script. The script will automatically scrape the specified categories and save the data in JSON files.

```sh
python scraper.py
```

### Configuration

- **User Agents**: You can add or remove user agents in the `user_agents` list to suit your needs.
- **Categories**: Modify the `categories` list in the `if __name__ == "__main__":` block to change the categories being scraped.

## Code Overview

### `get_headers()`

Returns a dictionary with a random User-Agent header.

### `make_request(url, max_retries=5)`

Creates a session with a retry strategy and makes a GET request to the provided URL.

### `load_scraped_links(filename="scraped_hrefs.json")`

Loads the list of already scraped links from a JSON file.

### `save_scraped_link(link, filename="scraped_hrefs.json")`

Saves a new link to the list of scraped links if it hasn't been scraped before.

### `append_article(article, category)`

Appends an article to a JSON file named after the category.

### `get_selector(category)`

Returns the CSS selector for extracting the article content based on the category.

### `scrape_page(url, category)`

Scrapes all articles from a given page URL and category, saves the links and content.

### `scrape_all_pages(base_url, category)`

Iterates through paginated URLs for a given category and scrapes articles until no more new articles are found.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request for review.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Requests](https://docs.python-requests.org/en/master/)
- [BeautifulSoup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)
