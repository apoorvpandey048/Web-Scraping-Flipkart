

# Flipkart Product Scraper

This Python script scrapes product data from multiple Flipkart product pages and extracts key information such as product name, price, specifications, and ratings. The data is saved to a CSV file for further analysis.

## Features
- Scrapes product details such as:
  - Product Name
  - Price
  - Maximum Power
  - Displacement
  - Brake Front
  - Tire Type
  - Rating
  - Number of Ratings
  - Number of Reviews
- Can scrape multiple pages by iterating through files in the specified folder.
- Outputs the scraped data in CSV format.

## Prerequisites
To run this script, you need to install the following Python libraries:
- **BeautifulSoup4**: For parsing HTML.
- **Pandas**: For data manipulation and saving data to CSV.

Install the required libraries by running the following command:

```bash
pip install beautifulsoup4 pandas
```

## Usage

1. **Prepare HTML Files**: 
   - Ensure the HTML files (e.g., `flipkart_page_1.html`, `flipkart_page_2.html`, etc.) are stored in the same directory as the script or in the `Flipkart_Scraper` folder.
   - These files should contain the Flipkart product pages that you wish to scrape.

2. **Run the Script**:
   - The script will loop through each HTML file in the directory (e.g., `flipkart_page_1.html`, `flipkart_page_2.html`), extract the product details, and store the results in a CSV file.
   - You can adjust the page range in the script (currently set for pages 1 and 2) to match the number of files you have.

   ```bash
   python flipkart_scraper.py
   ```

3. **Output**: 
   - After running the script, the product data will be saved in a CSV file called `flipkart_product_data_all_pages.csv`.
   - This file will contain the following columns:
     - `Product Name`
     - `Price`
     - `Maximum Power`
     - `Displacement`
     - `Brake Front`
     - `Tire Type`
     - `Rating`
     - `Number of Ratings`
     - `Number of Reviews`

## Script Details

### Main Components
- **parse_html_page()**: 
  - This function parses each HTML file, extracts product details (name, price, specifications, ratings, etc.), and returns the data in a structured format.
  
- **Scraping Logic**: 
  - The script looks for specific HTML elements using `BeautifulSoup`. It identifies the product cards by their class names and extracts relevant details like product name, price, specifications, and ratings.

- **Iterating through Files**: 
  - The script dynamically handles multiple HTML files by iterating through filenames (`flipkart_page_1.html`, `flipkart_page_2.html`, etc.) and extracting the data from each page.

- **Data Aggregation**: 
  - After extracting data from all pages, the script combines the results into a Pandas DataFrame and saves the final output to a CSV file.

### Example Output:
The output CSV will look something like this:

| Product Name          | Price  | Maximum Power     | Displacement | Brake Front | Tire Type | Rating | Number of Ratings | Number of Reviews |
|-----------------------|--------|-------------------|--------------|-------------|-----------|--------|--------------------|-------------------|
| Bajaj Pulsar 220 F    | ₹1,40,954 | 15 kW (20.4 PS)   | 220 cc       | Disc        | Tubeless  | 4.3    | 21                 | 2                 |
| Bajaj Pulsar NS 160   | ₹1,20,000 | 13.5 kW (18 PS)   | 160 cc       | Disc        | Tubeless  | 4.5    | 30                 | 5                 |

## Troubleshooting

- **Class Name Errors**: If you encounter `N/A` values in the output, it might be due to incorrect class names or changes in the website’s HTML structure. You can inspect the HTML of the product page and update the class names in the script accordingly.
  
- **Missing Data**: If any data is missing (e.g., missing price or rating), the script will store "N/A" for that field. This usually happens when the corresponding HTML element is not found on the page.

## Customization
- **File Range**: Modify the loop that iterates over HTML files (`for i in range(1, 3)`) to scrape additional pages or use specific file names.
  
- **Additional Data**: You can easily extend the script to extract more information, such as product descriptions or manufacturer details, by inspecting the HTML structure and adding new `find` statements.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

