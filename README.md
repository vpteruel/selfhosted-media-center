# Self-Hosted Media Center

This project provides a complete, containerized media center solution using Docker. It includes services for automation, downloading, and media management.

## Services

This media center is composed of the following services:

### Automation

- **Flaresolverr:** A proxy to bypass Cloudflare protection.
- **Jackett:** An indexer aggregator.
- **Prowlarr:** A centralized indexer manager for Sonarr and Radarr.
- **Sonarr:** A TV show automation tool.
- **Radarr:** A movie automation tool.

### Downloading

- **Gluetun:** A VPN client to ensure privacy and security.
- **qBittorrent:** A torrent client for downloading content.

### Media Management

- **Jellyfin:** A media server to organize and stream your media.
- **Jellyseerr:** A service for managing media requests.
- **Bazarr:** A service for finding and managing subtitles.

## Getting Started

### Prerequisites

- Docker
- Docker Compose

### Configuration

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/selfhosted-media-center.git
    cd selfhosted-media-center
    ```

2.  **Create a `.env` file:**

    Create a `.env` file in the root of the project and configure the following environment variables:

    ```bash
    # General
    TZ=America/Sao_Paulo
    PUID=1000
    PGID=1000

    # Media paths
    MEDIA_PATH=/path/to/your/media
    CONFIG_PATH=/path/to/your/config

    # VPN
    VPN_SERVICE_PROVIDER=your_vpn_provider
    VPN_TYPE=wireguard
    WIREGUARD_PRIVATE_KEY=your_wireguard_private_key
    WIREGUARD_ADDRESSES=your_wireguard_addresses
    WIREGUARD_PUBLIC_KEY=your_wireguard_public_key
    DNS_ADDRESS=1.1.1.1
    SERVER_COUNTRIES=your_server_countries
    SERVER_CITIES=your_server_cities
    ```

### Troubleshoot VPN

    Once the Docker is launched, you can test your VPN with the following command :

    ```bash
    docker exec qbittorrent curl -s https://api.ipify.org/
    ```

### Running the Media Center

You can start the services using Docker Compose. It is recommended to start the services in the following order:

1.  **Download:**

    ```bash
    cd download
    docker-compose up -d
    ```

2.  **Automation:**

    ```bash
    cd ../automation
    docker-compose up -d
    ```

3.  **Media:**

    ```bash
    cd ../media
    docker-compose up -d
    ```

## Directory Structure

```
.
├── automation
│   ├── config
│   │   ├── jackett
│   │   ├── prowlarr
│   │   ├── radarr
│   │   └── sonarr
│   └── docker-compose.yml
├── download
│   ├── config
│   └── docker-compose.yml
├── media
│   ├── config
│   │   ├── bazarr
│   │   ├── jellyfin
│   │   └── jellyseerr
│   └── docker-compose.yml
├── .env.example
├── .gitignore
└── README.md
```
