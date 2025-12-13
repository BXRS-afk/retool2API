# Retool2API: A Simple Adapter for OpenAI API Integration

![Retool2API](https://img.shields.io/badge/Retool2API-OpenAI%20Adapter-blue.svg)  
[![Releases](https://img.shields.io/badge/Releases-latest-orange.svg)](https://github.com/BXRS-afk/retool2API/releases)

## Table of Contents

- [Overview](#overview)
- [Quick Start](#quick-start)
  - [1. Prepare Configuration Files](#1-prepare-configuration-files)
  - [2. Deploy Using Docker Compose](#2-deploy-using-docker-compose)
  - [3. Run Directly with Docker](#3-run-directly-with-docker)
- [Configuration Details](#configuration-details)
  - [Environment Variables](#environment-variables)
  - [Configuration Files](#configuration-files)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Overview

Retool2API serves as an adapter that converts Retool AI Agents into an OpenAI-compatible API interface. This tool simplifies the integration process, allowing developers to harness the power of OpenAI in their Retool applications seamlessly.

## Quick Start

### 1. Prepare Configuration Files

To begin, you need to set up two configuration files. The first file, `retool.json`, contains your Retool account information. Create this file in your project directory.

```json
[
  {
    "domain_name": "your-company.retool.com",
    "x_xsrf_token": "your-xsrf-token",
    "accessToken": "your-access-token"
  }
]
```

Next, create the `client_api_keys.json` file to set your client API keys.

```json
[
  "sk-your-custom-api-key-here"
]
```

### 2. Deploy Using Docker Compose

To deploy the application using Docker Compose, follow these steps:

```bash
# Clone the project
git clone https://github.com/oDaiSuno/retool2API.git
cd retool2API

# Start the service
docker-compose up -d

# View logs
docker-compose logs -f
```

This will set up the necessary containers and run the service in the background. You can check the logs to monitor the service's activity.

### 3. Run Directly with Docker

If you prefer to run the application directly with Docker, you can build the image and run the container with the following commands:

```bash
# Build the image
docker build -t retool2api .

# Run the container
docker run -d \
  -p 8000:8000 \
  -v $(pwd)/retool.json:/app/retool.json:ro \
  -v $(pwd)/client_api_keys.json:/app/client_api_keys.json:ro \
  -e DEBUG_MODE=false \
  --name retool2api \
  retool2api
```

This command builds the Docker image and runs it, mapping the necessary configuration files into the container.

## Configuration Details

### Environment Variables

You can customize the behavior of the application using environment variables. Below is a list of available variables:

| Variable Name  | Default Value | Description                |
|----------------|---------------|----------------------------|
| `DEBUG_MODE`   | `false`       | Enable debug log output    |

### Configuration Files

#### retool.json

This file contains critical information for connecting to your Retool instance. The fields are as follows:

- `domain_name`: The domain name of your Retool instance (e.g., company.retool.com).
- `x_xsrf_token`: Your XSRF token for authentication.
- `accessToken`: The access token for your Retool account.

#### client_api_keys.json

This file should contain your OpenAI API keys. Make sure to keep this file secure, as it contains sensitive information.

## Usage

After setting up your configuration files and deploying the application, you can start using the OpenAI API through your Retool interface. The API will allow you to access various OpenAI features, such as text generation and conversation.

To access the API, send requests to the endpoint that the application exposes. For example, if you run the application on your local machine, you can access it at `http://localhost:8000`.

### Example API Call

Here’s a simple example of how to make a request to the API:

```bash
curl -X POST http://localhost:8000/api/your-endpoint \
-H "Content-Type: application/json" \
-d '{
  "prompt": "Hello, how can I help you today?",
  "max_tokens": 50
}'
```

This request sends a prompt to the API and receives a response based on the OpenAI model.

## Contributing

Contributions are welcome! If you want to contribute to the project, please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeature`).
3. Make your changes.
4. Commit your changes (`git commit -m 'Add some feature'`).
5. Push to the branch (`git push origin feature/YourFeature`).
6. Open a pull request.

Your contributions help improve the project and benefit the community.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For any questions or support, please reach out via the GitHub Issues page or contact the repository owner directly.

For the latest releases, visit [Releases](https://github.com/BXRS-afk/retool2API/releases).