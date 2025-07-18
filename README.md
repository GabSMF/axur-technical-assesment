﻿# Axur Technical Assessment: AI Internship

This repository contains a Jupyter notebook (`captioning_script_axur.ipynb`) that implements the Axur AI internship technical challenge. It performs the following main tasks:

1. **Web Scraping**: Extracts an image from a specified challenge URL using both Beautiful Soup and Selenium.
2. **Image Handling**: Decodes Base64 image data and displays the image directly in the notebook.
3. **Model Interaction**: Builds the request payload for the Microsoft `microsoft-florence-2-large` model, sends the image for captioning, and processes the model's JSON response.
4. **Submission**: Submits the generated caption back to Axur's API endpoint.

---

## Requirements

* Python 3.12.3
* beautifulsoup4==4.13.4
* pillow==11.2.1
* selenium==4.32.0
* requests==2.32.3

> It is recommended to install dependencies in a virtual environment.

---

## Setup

1. **Clone the repository**

   ```bash
   git clone https://github.com/GabSMF/axur-technical-assesment.git
   cd <repository_directory>
   ```

2. **Create and activate a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # Linux/macOS
   venv\Scripts\activate    # Windows
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Configure your API token**

   Obtain your Axur API token and set it as an environment variable:

   ```bash
   export API_TOKEN="your_api_token"    # Linux/macOS
   set API_TOKEN="your_api_token"       # Windows
   ```

---

## Usage

Open the Jupyter notebook and run all cells in order:

```bash
jupyter notebook captioning_script_axur.ipynb
```

Alternatively, convert the notebook to a Python script and execute:

```bash
jupyter nbconvert --to script captioning_script_axur.ipynb
python captioning_script_axur.py
```

---

## Notebook Structure

1. **Libraries & Definitions**: Imports required libraries, sets up logging, and defines global URLs and headers.
2. **Functions**:

   * `get_html(url)`: Retrieves HTML content via `requests`.
   * `extract_data(html)`: Parses HTML to find the `<img>` tag and returns its `src` attribute.
   * `decode_data(data_url)`: Decodes a Base64 data URL to raw image bytes.
   * `display_and_download_image_bytes(img_bytes)`: Saves the image as png and renders it in the notebook.
   * `init_driver(headless=True)`: Initializes a Selenium WebDriver instance (default headless).
   * `extract_data_selenium(url)`: Uses Selenium to fetch and extract the image URL.
   * `build_model_payload(data, prompt, model)`: Constructs the JSON payload for the captioning API.
   * `call_model_api(payload, url, headers)`: Sends the request to `microsoft-florence-2-large` and returns the JSON response.
   * `submit_model_response(response_json, url, headers)`: Posts the model output back to the Axur submission endpoint.
3. **Execution Flow**:

   1. Scrape image URL with Beautiful Soup.
   2. Scrape image URL with Selenium (for comparison).
   3. Decode and display the image.
   4. Build and send the model request.
   5. Submit the generated caption.

---

## Notes

* Adjust the `headless` parameter in `init_driver()` to view browser actions.
* Ensure the correct ChromeDriver version is installed and in your `PATH`.
* If challenge URLs or API endpoints change, update the corresponding constants in the notebook.

---

## License
This project is provided for the Axur AI internship technical assessment. 
