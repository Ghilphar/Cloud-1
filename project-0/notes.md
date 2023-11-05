This docker-compose.yml file:

- Defines two services: wordpress and db.
- Uses custom Dockerfiles for each service. If you decide to use official images directly without any customization, you can replace the build directive with image.
- Maps port 80 of the WordPress container to port 80 of the host.
- Uses named volumes for data persistence.

To launch the WordPress site:

1. Navigate to the directory containing your docker-compose.yml and Dockerfiles.
2. Run the following command:
```bash
docker-compose up -d
```
