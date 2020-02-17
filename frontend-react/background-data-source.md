---
description: Getting API Data
---

# Background - Data Source

As you know, most of web development deals with sending and receiving request. For example, in a web browser you may perform a google search for a certain page \(i.e. a get request\) and receive a response.

In this project, we are going to mimic that set up. For the back-end, we will rely on `github.com` to provide us with the required data, but any other back-end API will work just the same.

We are going to use a UNIX developing environment, in my case it is `Ubuntu app 18.04` installed in `windows 10`. If you are unfamiliar with this set up, please refer to the previous tutorials. The first process will be to ensure you have `curl` installed in your system. `curl` is a command line program that enables us perform common HTTP tasks as GET, PUT, DELETE and UPDATE on a server. Most latest UNIX environment as Mac and Linux come with curl installed, if not just check how to install it. It should be a straight forward process.

From your terminal, type the following commands:

```text
curl https://api.github.com/
```

You should be able to see a list of links listed in the GitHub API homepage.

{% embed url="https://api.github.com/" %}

If you happen to test some of those links, you will realize that they raise some kind of error. For example, try accessing [`https://api.github.com/user/emails`](https://api.github.com/user/emails) you will notice an error is raised

```javascript
{
  "message": "Requires authentication",
  "documentation_url": "https://developer.github.com/v3/users/emails/#list-email-addresses-for-a-user"
}
```

For now will ignore the `"message" : "Requires authentication"` will deal with it later, first let's try and access the accessible link below:

```text
curl https://api.github.com/gists/public
```

We can play around with the URL to get formalized with it. From the Ubuntu terminal type:

```python
$ python3
```

This should open the python shell. Type the following commands:

```python
>>> import requests
```

If an error appears with the above command, try `pip install requests` the run the above command.

```python
>>> url = https://api.github.com/gists/public
>>> response = requests.get(url).json()
>>> len(response)
```

In the above code, the `requests` object gets the URL from the API and converts it to a JSON object that is stored as a `response`. The last line displays the total number of JSON objects  that are stored in the response object. In my case, there are `30` items. At this point we are ready to create our react application.

