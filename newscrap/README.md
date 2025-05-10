# Universal Web Scraper

A powerful and flexible web scraping tool that can be configured to scrape product data from various e-commerce websites. Currently supports Amazon and n11.com, with the ability to easily add more websites.

## Features

- Universal scraping architecture that can be adapted for different websites
- Selenium-based scraping for JavaScript-heavy websites
- Configurable selectors for different website structures
- Support for multiple data fields (title, price, rating, reviews, etc.)
- Data export to both CSV and JSON formats
- Built-in retry mechanism and error handling
- Anti-bot detection measures

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/universal-web-scraper.git
cd universal-web-scraper
```

2. Install the required packages:
```bash
pip install -r requirements.txt
```

3. Install Chrome browser if not already installed (required for Selenium)

## Usage

### Basic Usage

1. For Amazon products:
```bash
python amazon_scraper.py
```

2. For n11.com products:
```bash
python selenium_n11_scraper.py
```

### Adding New Websites

To add support for a new website:

1. Create a new configuration file (e.g., `new_site_scraper.py`)
2. Define the selectors for the website using the `SelectorConfig` class
3. Create a scraper instance with the appropriate base URL and selectors

Example:
```python
from universal_scraper import UniversalScraper, SelectorConfig

# Define selectors for the new website
new_site_selectors = SelectorConfig(
    title=['.product-title', 'h1.name'],
    price=['.price', '.product-price'],
    # ... other selectors
)

# Create scraper instance
scraper = UniversalScraper(
    base_url='https://example.com',
    selectors=new_site_selectors
)
```

## Project Structure

```
universal-web-scraper/
├── README.md
├── requirements.txt
├── universal_scraper.py      # Base scraper class
├── amazon_scraper.py         # Amazon-specific implementation
├── selenium_n11_scraper.py   # n11.com implementation with Selenium
└── output/                   # Directory for scraped data
    ├── amazon_products.csv
    ├── amazon_products.json
    ├── n11_products.csv
    └── n11_products.json
```

## Requirements

- Python 3.7+
- Chrome browser
- Required Python packages (see requirements.txt)

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Disclaimer

This tool is for educational purposes only. Please respect websites' terms of service and robots.txt files. Always check if a website allows scraping before using this tool.

## Acknowledgments

- BeautifulSoup4 for HTML parsing
- Selenium for browser automation
- Fake UserAgent for rotating user agents 