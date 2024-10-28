# Use the Jenkins inbound agent as the base image
FROM jenkins/inbound-agent:alpine
USER root
# Set environment variables
ENV ARGOCD_VERSION=v2.8.0

# Install necessary packages and ArgoCD CLI
RUN apk add --no-cache curl && \
    curl -sSL -o /usr/local/bin/argocd "https://github.com/argoproj/argo-cd/releases/download/${ARGOCD_VERSION}/argocd-linux-amd64" && \
    chmod +x /usr/local/bin/argocd && \
    apk del curl

# Verify installation
RUN argocd version --client
USER jenkins