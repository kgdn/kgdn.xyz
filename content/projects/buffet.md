+++
title = 'Buffet'
summary = 'Web-based virtual machine manager - BSc. Computer Systems dissertation project (Heriot-Watt University)'
description = 'Web-based virtual machine manager - BSc. Computer Systems dissertation project (Heriot-Watt University)'
+++

# Introduction

The purpose of this project was to create a website that would allow users to try out different operating systems and software without having to install them on their own machines. This would be achieved by running the software on a virtual machine on a server and streaming the display to the user's browser. The website was primarily aimed at novice GNU/Linux users who did not want to alter their existing system or risk breaking it by installing new software.

# Technologies Used

- **Front-End**: React.js, TypeScript, noVNC
- **Back-End**: Flask (soon to be replaced with FastAPI), QEMU, KVM, websockify, Ubuntu Server 20.04 LTS
- **Database**: Any database supported by Flask-SQLAlchemy, SQLite3 used for development and testing, PostgreSQL used for production
- **Deployment**: Docker, Docker Compose, Nginx, Gunicorn

# Resources

- Installation: [GitHub Repository](https://github.com/kgdn/buffet)
- License: [GNU Affero General Public License v3.0](https://www.gnu.org/licenses/agpl-3.0.html)