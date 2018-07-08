# .NET Core on DC/OS 
Microsoft has annouced running .NET in Docker. This has opened the door to being able to run .NET apps on your favorite container orchestrators such as Marathon and Kubernetes.

### Getting a Feel using Docker
See the .NET Core ASP Docker Hub Page for more info.

```sh
docker run -it --rm -p 8000:80 --name aspnetcore_sample microsoft/dotnet-samples:aspnetapp
Unable to find image 'microsoft/dotnet-samples:aspnetapp' locally
aspnetapp: Pulling from microsoft/dotnet-samples
683abbb4ea60: Pull complete
a7e581c00d24: Pull complete
5e5679988195: Pull complete
799abad6ce99: Pull complete
384fcf967d83: Pull complete
dc6d19da5f5f: Pull complete
Digest: sha256:14d97a040222d434a31e6db5706c9117ba2c006fb427e1e561e4d3650bf066d3
Status: Downloaded newer image for microsoft/dotnet-samples:aspnetapp
warn: Microsoft.AspNetCore.DataProtection.KeyManagement.XmlKeyManager[35]
      No XML encryptor configured. Key {adfb2c92-2470-4fdc-964f-a42444bcf844} may be persisted to storage in unencrypted form.
Hosting environment: Production
Content root path: /app
Now listening on: http://[::]:80
Application started. Press Ctrl+C to shut down.
```

Go to browser at 0.0.0.0:8000.

### Marathon JSON
Deploy using the DC/OS CLI.

```sh
dcos marathon app add dotnet.json
```

### Kubernetes Deployment
Using Kubectl.
```sh
kubectl create -f deployment.yaml

# Optional: Expose via Service
kubectl expose deployment dotnet --type=NodePort --name=dotnet-service
``` 
