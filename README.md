# MI-Lab-CSV-FHIR-transformation

This repository contains the exercise materials for MI-Lab Exercise 2 on **transforming CSV to FHIR** using [Mirth-Connect](https://www.nextgen.com/solutions/interoperability/mirth-integration-engine)
and [Hapi FHIR](https://hapifhir.io/).

## Table of Contents
1. [Docker Installation](#docker-installation)
2. [Docker-Compose](#docker-compose)
3. [Mirth-Connect Installation](#mirth-connect-installation)
4. [Docker Network with Mirth-Connect](#docker-netzwerk-mit-mirth-connect)
5. [Mirth-Connect Folder Structure](#mirth-connect-ordnerstruktur)

**Prerequisites:** Docker with Docker-Compose, Java

---

## Docker Installation
### Docker Desktop
Docker Desktop [Download](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source=docker&utm_medium=webreferral&utm_campaign=dd-smartbutton&utm_location=module) (Windows) 
For other operating systems, see: [Docker](https://www.docker.com/products/docker-desktop/)
**Important:** The installation will restart your computer once  
1. Configuration
  ![docker1](https://github.com/user-attachments/assets/4df34253-41c2-4a82-86cc-b8016bbac017)
  ![docker2](https://github.com/user-attachments/assets/9b3e3b0b-7084-49f3-9f9c-22a915e6e97b)
2. Continue without signing in  
   Click "Skip" to use Docker Desktop without logging in
   ![docker3](https://github.com/user-attachments/assets/e51ec963-5a34-40dc-88cd-7156395b49e5)
3. Installation completed
   ![docker4](https://github.com/user-attachments/assets/181e767a-9ea1-43a7-855d-a804a72ee707)

### Docker-Compose
**Important:** Docker Desktop must be running in order to work with Docker.  
1. Clone the GitHub repository into a new folder:  `git clone https://github.com/IMISE/MI-Lab-CSV-FHIR-transformation.git`
2. Navigate from the root folder `MI-Lab-CSV-FHIR-transformation` to the `Setup` folder containing the file `docker-compose.yml`  
3. Open a terminal in this folde
4. Run the command: `docker-compose up -d` 
   This will pull all Docker images from a server. The download takes about 5 minutes.
   It will look like this in Docker Desktop: 
   ![docker5](https://github.com/user-attachments/assets/d6a2e65d-983c-4f7c-8e6e-995120973f7b)
  
### Mirth-Connect Installation
1. Open `http://localhost:8080` in your browser
   Or access it via Docker Desktop:
   ![docker7GIF](https://github.com/user-attachments/assets/9a5c6943-7c36-4771-bf29-6eae11f62833)
2. Click **Download Administrator Launcher**
3. nstall the downloaded file "mirth-administrator-launcher-latest-windows"

## Docker Network with Mirth-Connect 
For this exercise, several applications are required, which are connected via a network as Docker containers. 
Using [Docker-Compose](https://docs.docker.com/compose/), all required containers can be started with a single command.

The following containers (applications) are available after [starting](#docker-compose) docker-compose:
| Container | Ports | Volumes | Purpose |
| -------- | ------- | ------- | ------- |
| Mirth-Connect | **8080**, 8443 | Folder: /Setup/mirth-connect/ | Main application |
| Mirth-Connect Database | 5434 || Database for storing Mirth-Connect data |
| Hapi FHIR | **8090** || Hapi FHIR server where the final mapped FHIR resources are sent |
| Hapi FHIR Database| 5433 || Database for storing Hapi FHIR data |
| ClinFHIR | **8000** || Browser application for graphical visualization of FHIR data |

## Mirth-Connect Folder Structure
In this exercise, Mirth-Connect should access the CSV files in a defined folder and read them. Since Mirth-Connect runs isolated within a
Docker container, a folder inside the container is mapped to a local folder on the computer.  
More information can be found in the Docker documentation on [Volumes](https://docs.docker.com/engine/storage/volumes/).

**Docker container folder**: /opt/connect/appdata  

**Local folder**: [/Setup/mirth-connect](https://github.com/IMISE/MI-Lab-E02-CSV-to-FHIR/tree/main/Setup/mirth-connect)

**Important:** Only files and subfolders within the folder **/Setup/mirth-connect** are recognized by Mirth-Connect.

