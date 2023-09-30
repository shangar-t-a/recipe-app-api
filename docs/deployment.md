# Deployment in Django

```mermaid
graph TD
    subgraph Users
        A[User]
    end
    subgraph ReverseProxy
        B[Reverse Proxy]
    end
    subgraph Persistent Data
        C[Persistent Data]
    end
    subgraph WSGI Service
        D[WSGI Service]
    end
    
    A --> |Requests| B
    B --> |Data| C
    B --> |App| D
```

## Reverse Proxy

1. WSGI good at serving python but not data
2. nginx - open source, fast, secure, production grade
3. uWSGI - open source, fast, lightweight, simple to use
4. Docker Compose - Pulls it all together

### Docker Compose Setup

```mermaid
graph TD

subgraph Users 
    A["users"]
end

subgraph Service 
    subgraph Proxy 
        B["proxy"]
    end
    subgraph app 
        C["uWSGI"]
    end
    subgraph Database 
        D["DB"]
    end
end

subgraph Volumes 
    E["static-data"]
    F["postgres-data"]
end

A <--> |Request/Response| B <--> |Request 'Not Static/Media'| C
C <--> |Data| D <--> |Data| F
C --> |Static/Media| E --> |Static/Media| B
```

## Handling Configuration

1. Environment variables
   1. .env file on server
   2. Set values in Docker Compose
2. Secret managers

## Using AWS

1. Hosting
2. Keep account secure (Follow Best Practices - MFA, Strong Password, Do Not Share Account)
