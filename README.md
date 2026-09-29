## OpenKM Demo
Last Updated: September 29, 2026

This is a sample Docker Compose setup for the unofficial [OpenKM Community Edition](https://www.openkm.com/) container, running OpenKM together with MySQL. It is meant for demonstration and local development. By default it runs **OpenKM 7.0.3** using the `mbagnall/openkm:7.0.3-mysql` image.

**Full instructions are in the [OpenKM image repository](https://github.com/ElusiveMind/openkm).** That covers the supported tags, choosing between the 7.0 and 6.3 lines, environment variables, persistent data, KEA, using your own database server and building the image.

For background on the project, see the [Community OpenKM Docker Container](https://www.flyingflip.com/projects/community-openkm) page on FlyingFlip Studios.

---

### Running The Demo

From the root of this repository:

`docker compose up -d`

Then go to:

`http://localhost:8080`

Tomcat redirects to the OpenKM context path. The first start creates the database schema and takes a little while. `docker compose logs -f openkm` shows Tomcat's log, and OpenKM is ready once it prints "Server startup in". The default administrative user and password is as follows:

**Username:** okmAdmin  
**Password:** admin

Documents are kept in `./data` and the MySQL data in `./openkm-datastore`. These two belong together: remove both or neither.

---

### Using OpenKM 6.3

To run the 6.3 line instead, change the image in `docker-compose.yml` to `mbagnall/openkm:6.3.13-mysql` and `OPEN_KM_URL` to `http://localhost:8080/OpenKM`, or leave `OPEN_KM_URL` out so the image picks its own context path. A 6.3 repository and database can't be shared with the 7.0 image, so point it at fresh `./data` and `./openkm-datastore` directories. See [Which Line Should I Use?](https://github.com/ElusiveMind/openkm#which-line-should-i-use) in the OpenKM repository for migration notes.
