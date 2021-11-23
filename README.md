# Tweet Scraping Monthly
## Requirements
-  Python 3.8.5
-  Anaconda (recommended)

## How to Use
1. Create an environment based on your preference. For example, I would use conda:
```
conda create -n tweet-scrape python=3.8.5
conda activate tweet-scrape
```

2. Open jupyter notebook
- cd to this folder `tweets-scraping-monthly`
```
jupyter-notebook
```

## A Glance of the Notebook
1. Install `snscrape`
    ```
    pip3 install git+https://github.com/JustAnotherArchivist/snscrape.git
    ```
2. Scrapping (based on hashtag)
    <details close>
    <summary>Single Scraping Example</summary>
    For example, the command below scrape tweets with hashtags "yoga" or "exercise" between the date "2021-03-01" and "2021-05-20" capped at maximum 2000 tweets.

    ```
    os.system(f'snscrape --jsonl --progress --max-results 2000 --since 2020-03-01 {arg} "yoga exercise until:2021-05-20" > text-query-tweets.json')
    ```
    Convert JSON file to CSV
    ```
    tweets_df = pd.read_json('text-query-tweets.json', lines=True)
    tweets_df.to_csv('tweet_data_single.csv')
    ```
    You can check your progress in terminal when running the command above.
    ![image](https://user-images.githubusercontent.com/79887667/139456014-cb66b6a2-2a59-4ce3-9dae-0b3b084c8296.png)

    </details>
    <details close>
    <summary>Bulk Scraping Example</summary>
    For example, we provide these hashtags, "valentines", "christmas", "halloween". The command below scrape tweets with the hashtags provided between the date "2021-08-01" and "2021-11-01" capped at maximum 100 tweets each month for each hashtag.

    ```
    hashtag = ["valentines", "christmas", "halloween"] 
    date_interval = ["2021-08-01", "2021-09-01", "2021-10-01", "2021-11-01"]
    ```
    Checkout the notebook we provided to find the code for bulk scraping, in short, the design is a single scraping wrapped in two for loops, one for hashtag, one for date.
    </details>
