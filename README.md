# Instagram Profile Media Scraper

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-Ready-orange?logo=googlecolab&logoColor=white)](https://colab.research.google.com/)
[![Apify](https://img.shields.io/badge/Apify-Scraper-green?logo=apify&logoColor=white)](https://apify.com)
[![Google Gemini](https://img.shields.io/badge/Google%20Gemini-AI-4285F4?logo=google&logoColor=white)](https://ai.google.dev)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A ready-to-use **Google Colab** script that scrapes public Instagram posts & reels within a specific date range, downloads all images and videos, generates AI descriptions with Google Gemini, and creates a clean Excel guide that maps every media file to its original post.


---

## Features

- Scrape posts and reels from any **public** Instagram profile
- Filter by custom date range
- Download high-quality images (`.jpg`) and videos (`.mp4`)
- Automatically handle carousel posts
- Generate short AI descriptions using **Google Gemini**
- Create a detailed Excel + CSV mapping file
- Clean and organized folder structure
- Fully works on **free Apify** and **free Gemini** accounts

---

## Requirements

| Service          | Purpose                     | Free Tier Available |
|------------------|-----------------------------|---------------------|
| [Google Colab](https://colab.research.google.com) | Run the script              | Yes                 |
| [Apify](https://console.apify.com)               | Instagram scraping          | Yes ($5 free credit/month) |
| [Google AI Studio](https://aistudio.google.com)  | Gemini API key              | Yes                 |

---

## Quick Start

1. Open [Google Colab](https://colab.research.google.com) and create a new notebook.
2. Copy the full script into a cell.
3. Replace the two placeholders at the top of the script:

```python
APIFY_TOKEN    = "apify_api_xxxxxxxxxxxxxxxxxxxxxxxx"
GEMINI_API_KEY = "AIzaSyxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

4. Run the cell.
5. After the script finishes, download the results:

```python
!zip -r instagram_scrape.zip /content/instagram_scrape

from google.colab import files
files.download("instagram_scrape.zip")
```

---

## Configuration

You can easily change these variables at the top of the script:

| Variable                  | Description                              | Default              |
|---------------------------|------------------------------------------|----------------------|
| `USERNAME`                | Instagram username                       | `justcutitgh`        |
| `START_DATE`              | Start of date range (`YYYY-MM-DD`)       | `2026-01-20`         |
| `END_DATE`                | End of date range (`YYYY-MM-DD`)         | `2026-05-18`         |
| `RESULTS_LIMIT`           | Maximum posts requested from Apify       | `100`                |
| `INCLUDE_REELS`           | Also scrape reels                        | `True`               |
| `DOWNLOAD_MEDIA`          | Download images and videos               | `True`               |
| `GENERATE_DESCRIPTIONS`   | Generate AI descriptions with Gemini     | `True`               |

---

## Output Structure

```text
instagram_scrape/
├── media/
│   ├── posts/                     # One folder per post (named by shortcode)
│   │   ├── DYePwOBMeuu/
│   │   │   ├── DYePwOBMeuu_img_00.jpg
│   │   │   └── DYePwOBMeuu_video_01.mp4
│   │   └── ...
│   ├── images/                    # All images collected in one place
│   └── videos/                    # All videos collected in one place
├── justcutitgh_2026-01-20_to_2026-05-18_media_guide.xlsx
├── justcutitgh_2026-01-20_to_2026-05-18_media_guide.csv
└── raw_filtered_data.json
```

---

## Excel Guide Columns

The Excel file contains one row per media file with the following columns:

| Column                 | Description                                      |
|------------------------|--------------------------------------------------|
| `post_shortcode`       | Unique Instagram shortcode of the post           |
| `post_url`             | Full URL of the original post                    |
| `post_type`            | Image / Video / Carousel / Reel                  |
| `timestamp`            | When the post was published                      |
| `likes` / `comments`   | Engagement metrics                               |
| `caption`              | Original post caption                            |
| `gemini_description`   | Short AI-generated description of the post       |
| `media_filename`       | Name of the downloaded file                      |
| `media_type`           | `image` or `video`                               |
| `local_folder`         | Relative path to the post folder                 |
| `original_media_url`   | Original Instagram CDN URL (expires quickly)     |

---

## Notes & Limitations

- Works only with **public** Instagram profiles
- Instagram media links expire quickly — the script downloads them immediately
- Free Apify accounts have monthly credit limits → start with a lower `RESULTS_LIMIT`
- Gemini free tier has rate limits (a small delay is already included in the script)
- Uses the official Apify Actor: [`apify/instagram-scraper`](https://apify.com/apify/instagram-scraper)

---

## Project Structure (Recommended for GitHub)

```text
instagram-profile-media-scraper/
├── README.md
├── LICENSE
├── script.ipynb                 # or script.py
├── assets/
│   ├── excel-preview.png
│   ├── folder-structure.png
│   └── media-preview.png
└── examples/
    └── sample_output/
```

---

## Credits

- [Apify](https://apify.com) – Instagram data extraction
- [Google Gemini](https://ai.google.dev) – AI post descriptions
- Built for easy use in Google Colab

---

## License

This project is licensed under the **MIT License**.  
Feel free to use, modify, and share.

---

**Made with care for content creators, researchers, and archivists.**

---
