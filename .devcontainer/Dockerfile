# See here for image contents: https://github.com/devcontainers/images/tree/main/src/javascript-node

# [Choice] Node.js version: 20, 18, 16
ARG VARIANT="20-bullseye"
FROM mcr.microsoft.com/devcontainers/javascript-node:1-${VARIANT}

# Prepare for apt-based install of Cloud Foundry CLI by adding Cloud Foundry Foundation public key & package repository (see https://docs.cloudfoundry.org/cf-cli/install-go-cli.html)
RUN wget -q -O - https://packages.cloudfoundry.org/debian/cli.cloudfoundry.org.key | sudo gpg --dearmor -o /usr/share/keyrings/cloudfoundry-cli.gpg
RUN echo "deb [signed-by=/usr/share/keyrings/cloudfoundry-cli.gpg] https://packages.cloudfoundry.org/debian stable main" | sudo tee /etc/apt/sources.list.d/cloudfoundry-cli.list

# Update local package index and run installs
RUN apt-get update
RUN apt-get install cf7-cli sqlite3

# Install global node modules for SAP CAP and frontend development
RUN su node -c "npm install -g @ui5/cli @sap/cds-dk yo mbt"
