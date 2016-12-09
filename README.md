[![Go Report Card](https://goreportcard.com/badge/github.com/insp3ctre/race-the-web)](https://goreportcard.com/report/github.com/insp3ctre/race-the-web)

# Race The Web

Tests for race conditions in web applications by sending out a user-specified number of requests to a target URL (or URLs) *simultaneously*, and then compares the responses from the server for uniqueness. Includes a number of configuration options.

## Watch The Talk

[![Racing the Web - Hackfest 2016](https://img.youtube.com/vi/4T99v957I0o/0.jpg)](https://www.youtube.com/watch?v=4T99v957I0o)

_Racing the Web - Hackfest 2016_

## Usage

`race-the-web config.toml`

### Configuration File

**Example configuration file included (_config.toml_):**

```toml
# Sample Configurations

# Send 100 requests to each target
count = 100
# Enable verbose logging
verbose = true
# Use an http proxy for all connections
proxy = "http://127.0.0.1:8080"

# Specify the first target
[[target]]
    # Use the GET request method
    method = "GET"
    # Set the URL target. Any valid URL is accepted, including ports, https, and parameters.
    url = "https://example.com/pay?val=1000"
    # Set the request body.
    # body = "body=text"
    # Set the cookie values to send with the request to this target. Must be an array.
    cookies = ["PHPSESSIONID=12345","JSESSIONID=67890"]
    # Set custom headers to send with the request to this target. Must be an array.
    headers = ["X-Originating-IP: 127.0.0.1", "X-Remote-IP: 127.0.0.1"]
    # Follow redirects
    redirects = true

# Specify the second target
[[target]]
    # Use the POST request method
    method = "POST"
    # Set the URL target. Any valid URL is accepted, including ports, https, and parameters.
    url = "https://example.com/pay"
    # Set the request body.
    body = "val=1000"
    # Set the cookie values to send with the request to this target. Must be an array.
    cookies = ["PHPSESSIONID=ABCDE","JSESSIONID=FGHIJ"]
    # Set custom headers to send with the request to this target. Must be an array.
    headers = ["X-Originating-IP: 127.0.0.1", "X-Remote-IP: 127.0.0.1"]
    # Do not follow redirects
    redirects = false
```
