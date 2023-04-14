GitHub Search Script
This script allows you to search for repositories and code on GitHub based on a company name and a search query.

Prerequisites
Python 3.x
A GitHub personal access token with the repo and read:user scopes
Installation
Clone this repository or copy the contents of 3gitscrape.py to your local machine
Install the required packages by running pip install -r requirements.txt
Open the 3gitscrape.py file in a text editor and replace the YOUR_GITHUB_TOKEN placeholder with your GitHub personal access token
Usage
To search for repositories and code, use the following command:

perl
Copy code
python3 3gitscrape.py -c <company_name> -q <search_query>
The -c flag specifies the name of the company you want to search for, and the -q flag specifies the value you want to search for in the repositories.

If the search query is found in the code of a repository, the script will display the file or folder and the line number where the query is found.
