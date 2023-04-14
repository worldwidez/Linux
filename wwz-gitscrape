import requests
import argparse

github_token = "YOUR_GITHUB_TOKEN"

headers = {
    "Accept": "application/vnd.github+json",
    "Authorization": f"token {github_token}",
}

def search_github(query):
    url = f"https://api.github.com/search/repositories?q={query}+in:name+in:description&sort=created&order=desc"
    response = requests.get(url, headers=headers)

    if response.status_code == 200:
        return response.json()
    else:
        print(f"Failed to fetch data from GitHub API. Status code: {response.status_code}")
        return None

def search_code(query):
    url = f"https://api.github.com/search/code?q={query}+in:file+in:path&sort=indexed&order=desc"
    response = requests.get(url, headers=headers)

    if response.status_code == 200:
        return response.json()
    else:
        print(f"Failed to fetch data from GitHub API. Status code: {response.status_code}")
        return None

def get_repository(repo_url):
    response = requests.get(repo_url, headers=headers)

    if response.status_code == 200:
        return response.json()
    else:
        print(f"Failed to fetch repository data from GitHub API. Status code: {response.status_code}")
        return None

def main():
    parser = argparse.ArgumentParser(description='Search for repositories on GitHub')
    parser.add_argument('-c', '--company_name', type=str, help='The name of the company to search for', required=True)
    parser.add_argument('-q', '--query', type=str, help='The value to search for in the repositories', required=False)
    args = parser.parse_args()

    company_name = args.company_name
    query = args.query

    if query:
        repositories = search_github(f"{query}+{company_name}")
    else:
        repositories = search_github(f"{company_name}")

    print(f"\n{'*' * 80}\n")
    print(f"Report for company name: {company_name}, search query: {query}\n")
    print(f"{'*' * 80}\n")

    if repositories:
        print("Repositories mentioning your company (sorted by date created, most recent first):\n")
        for repo in repositories["items"]:
            print(f"Repository: {repo['name']}")
            print(f"URL: {repo['html_url']}")
            print(f"Created at: {repo['created_at']}")
            print(f"Last update: {repo['updated_at']}")
            print(f"Language: {repo['language'] if repo['language'] else 'Not specified'}")
            print("\n")

    print(f"{'*' * 80}\n")

if __name__ == "__main__":
    main()"
