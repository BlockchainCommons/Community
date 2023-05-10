# Codeowners Report

Also see: [current run for Blockchain Commons](script-codeowners-results.md).

This `python` script is intended to list out codeowners and the total open issues + PR (and potentially other metadata) for each repo in an organization or owner by a person.

To use it:

1. Be sure `python` is installed on your local machine.
2. Download the script as something like `co-report.py`.
3. Create a Fine-grained personal-access token for your account.
   * Go to `Settings`.
   * Go to `developer setting
   * Go to `Fine-grained tokens`
   * Click `Generate new token`
   * Enter info
   * Copy the token.
4. Enter the token into the `GITHUB_PAT` variable in your local file.
5. Run the script, e.g., `python3 co-report.py`.
6. Enter your organization name or personal account as preferred.

For this script to work for an organization, `Your Organizations`->`Settings` for the appropriate Organization->`Personal Access Tokens`->`Settings` must be set to allow your fine-grained access token

```
import requests
import re

GITHUB_API_BASE_URL = 'https://api.github.com'
GITHUB_PAT = 'Put Your GitHub Personal Access Token Here'

def get_user_repos(username):
    all_repos = []
    page = 1
    per_page = 100
    headers = {'Authorization': f'token {GITHUB_PAT}'}

    while True:
        url = f'{GITHUB_API_BASE_URL}/users/{username}/repos?page={page}&per_page={per_page}'
        response = requests.get(url, headers=headers)

        if response.status_code == 200:
            repos = response.json()
            if not repos:  # Empty response, no more repos to fetch
                break
            all_repos.extend(repos)
            page += 1
        else:
            print(f'Error {response.status_code}: Could not fetch repos')
            break

    return all_repos

def get_codeowners_file_contents(owner, repo_name):
    url = f'{GITHUB_API_BASE_URL}/repos/{owner}/{repo_name}/contents/CODEOWNERS'
    headers = {'Authorization': f'token {GITHUB_PAT}'}
    response = requests.get(url, headers=headers)

    if response.status_code == 200:
        return response.json()
    else:
        return None

def get_codeowners_open_issues(owner, repo_name):
    url = f'{GITHUB_API_BASE_URL}/repos/{owner}/{repo_name}'
    headers = {'Authorization': f'token {GITHUB_PAT}'}
    response = requests.get(url, headers=headers)
    return response.json()

def extract_usernames(codeowners_content):
    pattern = r'@(\w+)'
    usernames = re.findall(pattern, codeowners_content)
    return usernames

def main():
    account = input('Enter the GitHub account username: ')

    print("\n| Repo | Code Owners | Issues & PRs|")
    print("|------|-------------|------------|")

    for repo in get_user_repos(account):
        if repo["name"] == '.github':
            continue

        codeowners = get_codeowners_file_contents(account, repo['name'])
        issues = get_codeowners_open_issues(account, repo['name'])

        if codeowners:
            content = requests.get(codeowners['download_url']).text
            usernames = extract_usernames(content)
            print(f'| {repo["name"]} | {", ".join(usernames)} | {issues["open_issues_count"]} |')
        else:
            print(f'| {repo["name"]} | | {issues["open_issues_count"]} |')


if __name__ == '__main__':
    main()

```
