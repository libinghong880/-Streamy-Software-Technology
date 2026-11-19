# Streamy System Architecture (C4 Container Diagram)

This document illustrates the high-level container architecture for the Streamy Video Streaming Platform, generated automatically via GitHub Actions.

## Container View

```mermaid
C4Container
    title Container Diagram for Streamy Video Streaming Platform

    Person(viewer, "Viewer / User", "Watches videos, browses catalog, and submits reviews.")

    System_Boundary(streamy_boundary, "Streamy Platform") {
        Container(web_app, "Web & Mobile Client", "React / iOS", "Provides video playback UI, search, and user profile management.")
        Container(api_gateway, "API Gateway", "Nginx / Node.js", "Routes incoming requests, enforces rate limiting, and terminates SSL.")
        Container(auth_service, "Auth Service", "Python / JWT", "Validates access tokens and manages user sessions.")
        Container(catalog_engine, "Media Catalog & Core Engine", "Python (streamy_core)", "Manages Titles, TVShows, Seasons, Episodes, Actors, and HLS stream handshakes.")
        ContainerDb(database, "Metadata Database", "PostgreSQL", "Stores media metadata, user reviews, and taxonomy indexes.")
        Container(cdn_storage, "Video Storage & CDN", "AWS S3 / CloudFront", "Stores encrypted video chunks and delivers HLS streams.")
    }

    Rel(viewer, web_app, "Browses and streams media using", "HTTPS")
    Rel(web_app, api_gateway, "Sends API & playback requests to", "JSON/HTTPS")
    Rel(api_gateway, auth_service, "Verifies access tokens with", "gRPC/HTTPS")
    Rel(api_gateway, catalog_engine, "Forwards authorized media requests to", "REST/HTTPS")
    Rel(catalog_engine, database, "Reads and writes metadata & reviews", "SQL/TCP")
    Rel(catalog_engine, cdn_storage, "Fetches HLS stream manifests from", "HTTPS")
    Rel(web_app, cdn_storage, "Streams encrypted video segments directly from", "HLS/HTTPS")
```