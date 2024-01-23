# Today-s-Top-5-Most-Popular-YouTube-Videos
## YouTube Data Analysis Project

![Project Image]([https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.serpwizard.com%2Fyoutube-video-url-scraper%2F&psig=AOvVaw0OA86yPyOX_JyeCWfOQxL4&ust=1706092894076000&source=images&cd=vfe&opi=89978449&ved=0CBMQjRxqFwoTCID13rmp84MDFQAAAAAdAAAAABAD](https://piunikaweb.com/wp-content/uploads/2020/11/YouTube-Logo-2.jpg)) 

🚀 **Exciting Project Update!**

I recently completed a captivating project, delving into the world of data using the YouTube API. This Python-based endeavor involved extracting key information such as view counts, published dates, and channel names for the most popular videos.

## Key Features

- **Data Visualization:** Utilized Power BI to transform raw data into a visually engaging report.
- **Dynamic Visuals:** Thumbnails of top videos alongside data bars reflecting view counts provide insightful visualizations.
- **Automation:** Implemented scheduled tasks in Windows for code refresh and Power BI report updates at regular intervals, creating a live dashboard.

## Learning Experience

Exploring the nuances of data analysis, harnessing the YouTube API, and integrating automation have been incredible learning experiences.

# Code

{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": 1,
   "id": "bd11acbe",
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "CSV file saved successfully.\n"
     ]
    }
   ],
   "source": [
    "import pandas\n",
    "import seaborn as sns\n",
    "from googleapiclient.discovery import build\n",
    "api_key = 'AIzaSyA-8MIvXrK9uldbX9imnjpgukoB9X4uI34'\n",
    "channel_id= 'UCpnJnY5pz3QkoySVHkrPW5w'\n",
    "\n",
    "\n",
    "youtube = build('youtube','v3', developerKey = api_key)\n",
    "from googleapiclient.discovery import build\n",
    "import pandas as pd\n",
    "from IPython.display import Image, display\n",
    "\n",
    "\n",
    "# Create a YouTube service object\n",
    "youtube = build('youtube', 'v3', developerKey=api_key)\n",
    "\n",
    "try:\n",
    "    # Request the most popular videos from the YouTube API for India\n",
    "    request = youtube.videos().list(\n",
    "        part='snippet,statistics',\n",
    "        chart='mostPopular',\n",
    "        regionCode='IN',  # India region code\n",
    "        maxResults=5  # Get top 5 videos\n",
    "    )\n",
    "\n",
    "    response = request.execute()\n",
    "\n",
    "    # Create empty lists to store data\n",
    "    video_titles = []\n",
    "    thumbnail_urls = []\n",
    "    view_counts = []\n",
    "    channel_names = []\n",
    "    published_dates = []\n",
    "\n",
    "    # Extract information for each video\n",
    "    for video in response['items']:\n",
    "        video_titles.append(video['snippet']['title'])\n",
    "        thumbnail_urls.append(video['snippet']['thumbnails']['medium']['url'])\n",
    "        view_counts.append(video['statistics']['viewCount'])\n",
    "        channel_names.append(video['snippet']['channelTitle'])\n",
    "        published_dates.append(video['snippet']['publishedAt'])\n",
    "\n",
    "    # Create a DataFrame\n",
    "    data = {\n",
    "        'Video Title': video_titles,\n",
    "        'Thumbnail URL': thumbnail_urls,\n",
    "        'View Count': view_counts,\n",
    "        'Channel Name': channel_names,\n",
    "        'Published Date': published_dates\n",
    "    }\n",
    "    df = pd.DataFrame(data)\n",
    "\n",
    "    # Save DataFrame to a CSV file\n",
    "    df.to_csv('top_videos_in_india.csv', index=False)\n",
    "    print(\"CSV file saved successfully.\")\n",
    "\n",
    "except Exception as e:\n",
    "    print(f\"An error occurred: {e}\")\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "id": "e28d4e48",
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>Video Title</th>\n",
       "      <th>Thumbnail URL</th>\n",
       "      <th>View Count</th>\n",
       "      <th>Channel Name</th>\n",
       "      <th>Published Date</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>Shri Ram Lalla Pran Pratishtha LIVE | PM Modi ...</td>\n",
       "      <td>https://i.ytimg.com/vi/xBwfbsv3WjU/mqdefault.jpg</td>\n",
       "      <td>10552522</td>\n",
       "      <td>Narendra Modi</td>\n",
       "      <td>2024-01-22T10:13:36Z</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>PM Modi LIVE | Ayodhya Ram Mandir LIVE | Shri ...</td>\n",
       "      <td>https://i.ytimg.com/vi/EU4fJn0YdXw/mqdefault.jpg</td>\n",
       "      <td>10745464</td>\n",
       "      <td>Narendra Modi</td>\n",
       "      <td>2024-01-22T10:34:31Z</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>Ayodhya Ram Mandir: राम मंदिर पहुंचे PM Modi, ...</td>\n",
       "      <td>https://i.ytimg.com/vi/IC0M3UsybPw/mqdefault.jpg</td>\n",
       "      <td>3737421</td>\n",
       "      <td>Aaj Tak</td>\n",
       "      <td>2024-01-22T07:00:10Z</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>Ayodhya Ram Mandir: Ramlala के दर्शन कर Jackie...</td>\n",
       "      <td>https://i.ytimg.com/vi/P8zfsBnWK6U/mqdefault.jpg</td>\n",
       "      <td>2338620</td>\n",
       "      <td>NDTV India</td>\n",
       "      <td>2024-01-22T12:12:13Z</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>My BROTHER babysits our BABY for 24 HOURS 😱</td>\n",
       "      <td>https://i.ytimg.com/vi/3lS6leJG35Q/mqdefault.jpg</td>\n",
       "      <td>1613289</td>\n",
       "      <td>Wanderers Hub</td>\n",
       "      <td>2024-01-22T09:00:09Z</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "                                         Video Title  \\\n",
       "0  Shri Ram Lalla Pran Pratishtha LIVE | PM Modi ...   \n",
       "1  PM Modi LIVE | Ayodhya Ram Mandir LIVE | Shri ...   \n",
       "2  Ayodhya Ram Mandir: राम मंदिर पहुंचे PM Modi, ...   \n",
       "3  Ayodhya Ram Mandir: Ramlala के दर्शन कर Jackie...   \n",
       "4        My BROTHER babysits our BABY for 24 HOURS 😱   \n",
       "\n",
       "                                      Thumbnail URL View Count   Channel Name  \\\n",
       "0  https://i.ytimg.com/vi/xBwfbsv3WjU/mqdefault.jpg   10552522  Narendra Modi   \n",
       "1  https://i.ytimg.com/vi/EU4fJn0YdXw/mqdefault.jpg   10745464  Narendra Modi   \n",
       "2  https://i.ytimg.com/vi/IC0M3UsybPw/mqdefault.jpg    3737421        Aaj Tak   \n",
       "3  https://i.ytimg.com/vi/P8zfsBnWK6U/mqdefault.jpg    2338620     NDTV India   \n",
       "4  https://i.ytimg.com/vi/3lS6leJG35Q/mqdefault.jpg    1613289  Wanderers Hub   \n",
       "\n",
       "         Published Date  \n",
       "0  2024-01-22T10:13:36Z  \n",
       "1  2024-01-22T10:34:31Z  \n",
       "2  2024-01-22T07:00:10Z  \n",
       "3  2024-01-22T12:12:13Z  \n",
       "4  2024-01-22T09:00:09Z  "
      ]
     },
     "execution_count": 2,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "df"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "id": "41c48da9",
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.13"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}

