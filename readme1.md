

# Web Scraping with Flipkart

This project demonstrates how to scrape product information from Flipkart using Python and BeautifulSoup. We extract various product details such as the product name, price, specifications, and ratings.

## Technologies Used

- Python
- BeautifulSoup (for parsing HTML)
- Selenium (for interacting with dynamic web pages)
- Pandas (for storing data in DataFrame)
- Git (for version control)

## Installation

To run this project locally, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/apoorvpandey048/Web-Scraping-Flipkart.git
   cd Web-Scraping-Flipkart
   ```

2. **Install required packages**:
   The following Python libraries are required:
   - `beautifulsoup4`
   - `pandas`
   - `selenium`
   - `webdriver-manager` (for managing the Selenium driver)

   Install these packages via pip:
   ```bash
   pip install beautifulsoup4 pandas selenium webdriver-manager
   ```

3. **Setup WebDriver**:
   This project uses **Selenium WebDriver** to interact with Flipkart's pages. Ensure that you have the appropriate browser driver installed for your browser. For Chrome, you can use the `webdriver-manager` package to automatically handle it.

## Usage

1. **Run the Jupyter notebook**:
   After installing the necessary packages, open the Jupyter notebook and run each cell sequentially to scrape product data from Flipkart.

2. **Scraping Flow**:
   - The script uses **Selenium** to load pages dynamically (if necessary).
   - **BeautifulSoup** is used to parse the HTML and extract data.
   - The data is then processed and stored into a Pandas DataFrame.
   - All the extracted product information is saved into a CSV file (`flipkart_product_data_all_pages.csv`).

3. **Selenium Example**:
   In case you need to run a dynamic scraping task using Selenium, here’s how it’s done for Flipkart:

   ```python
   from selenium import webdriver
   from webdriver_manager.chrome import ChromeDriverManager

   # Set up the Selenium WebDriver (Chrome)
   driver = webdriver.Chrome(ChromeDriverManager().install())

   # Open Flipkart page
   driver.get("https://www.flipkart.com/")
   
   # Add logic here to interact with the page (e.g., clicking buttons, scrolling, etc.)

   # Extract the page's source after loading it fully
   html_content = driver.page_source

   # Parse the HTML with BeautifulSoup
   soup = BeautifulSoup(html_content, 'html.parser')

   # Find the product cards and extract information
   product_cards = soup.find_all("div", class_="KzDlHZ")
   ```

4. **Scrape Multiple Pages**:
   The scraping logic is designed to loop through multiple pages (e.g., page 1, page 2, etc.), save the extracted data in a DataFrame, and export it to a CSV file.

   ```python
   all_data = []
   for i in range(1, 3):  # Scraping pages 1 to 2
       html_file = f"flipkart_page_{i}.html"
       if os.path.exists(html_file):
           page_data = parse_html_page(html_file)
           all_data.append(page_data)

   # Combine all data into a DataFrame
   df = pd.DataFrame()
   for page_data in all_data:
       temp_df = pd.DataFrame(page_data)
       df = pd.concat([df, temp_df], ignore_index=True)

   # Save the combined DataFrame to CSV
   df.to_csv("flipkart_product_data_all_pages.csv", index=False)
   ```

5. **Exporting Data**:
   After running the scraping script, you’ll get a CSV file (`flipkart_product_data_all_pages.csv`) containing the following columns:
   - Product Name
   - Price
   - Maximum Power
   - Displacement
   - Brake Front
   - Tire Type
   - Rating
   - Number of Ratings
   - Number of Reviews

## Notes

- This project relies on **static scraping** for most data. If dynamic content loading is required (e.g., for infinite scroll or AJAX-loaded data), **Selenium** is used to handle such cases.
- For scraping multiple pages, the HTML files for each page are loaded from the saved `flipkart_page_x.html` files.
- The structure of the HTML may change over time, so the selectors (like `class_="KzDlHZ"`) may need to be updated accordingly.

## Contributing

If you'd like to contribute, feel free to fork the repository, make changes, and submit a pull request.

## License

This project is licensed under the MIT License.

