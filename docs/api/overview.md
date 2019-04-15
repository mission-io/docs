# REST Api with `express.js`

## Overview

## Quick Start
### Create new API Project

    mio new api <api-name>

Example

    mio new api DemoApi

## Decorators

### Routable

    @Routable('route-path', 'verbe')

example

``` typescript
import { Routable } from 'mission.api';

@Routable('/health', 'GET')
export class UserController {
    public static async getUsers(req: Request, res: Response, next: NextFunction): Promise<boolean> {
        return { ... };
    }
}

```

## Controller
    
!!! danger "Warning"
    All methods should be `static async`.
    
    Both access specifiers (`public`/`private`) would be exposed as service.
    
Example:

```typescript

    @Routable('/user')
    export class UserRegistrationController {
        public static async getUsers(req: Request, res: Response, next: NextFunction): Promise<any> {
            ...
        }
    }
```

### Built-in Controllers

#### Health Check Controller

```typescript 

@Routable('/health', 'GET')
export class HealthService {
    public static async liveness(req: Request, res: Response, next: NextFunction): Promise<boolean> {
        return true;
    }
    public static async readyness(req: Request, res: Response, next: NextFunction): Promise<boolean> {
        return true;
    }
}
```
To Check the liveness of the appliation
    
    http://localhost:3000/health/liveness

To Check the readyness of the application

    http://localhost:3000/health/readyness

!!! note "Note"
    Readyness api need to be override to check the readyness of the other resources like Sql / NoSql database, redis cache, etc.

#### Facade Controller


## Configuration

### Web Server Configuration

``` typescript
interface WebServerConfig {
    apiPort: number;
    isHttpsEnabled: boolean;
    httpsCertificatepath: string;
    httpsKeypath: string;
    corsOptions: CorsOptions;
}

interface CorsOptions {
    origin?: boolean | string | RegExp | (string | RegExp)[] | CustomOrigin;
    methods?: string | string[];
    allowedHeaders?: string | string[];
    exposedHeaders?: string | string[];
    credentials?: boolean;
    maxAge?: number;
    preflightContinue?: boolean;
    optionsSuccessStatus?: number;
}
```
Example: 

``` typescript

import { config, DotenvResult } from 'dotenv';
import { StaticFileConfig, WebServerConfig } from 'mission.api';

const env: DotenvResult = config();
if (env.error) {
    throw env.error;
}

export const WebConfig: WebServerConfig = {
    apiPort: Number(process.env.WEB_PORT),
    corsOptions: {
        allowedHeaders: (process.env.CORS_ALLOWED_HEADERS || '').split(','),
        credentials: Boolean(process.env.CORS_CREDENTIALS),
        exposedHeaders: (process.env.CORS_EXPOSED_HEADERS || '').split(','),
        maxAge: Number(process.env.CORS_MAX_AGE),
        methods: (process.env.CORS_METHODS || '').split(','),
        origin: process.env.CORS_ORIGIN,
    },
    httpsCertificatepath: process.env.WEB_SSL_CERTIFICATE_PATH || '',
    httpsKeypath: process.env.WEB_SSL_KEY_PATH || '',
    isHttpsEnabled: !!process.env.WEB_SSL_CERTIFICATE_PATH,
};

export const FileConfig: StaticFileConfig = {
    dotfiles: 'ignore',
    etag: false,
    extensions: ['htm', 'html'],
    index: ['index.html', 'index.htm'],
    maxAge: process.env.STATIC_FILE_MAX_AGE || '1d',
    redirect: false,
    setHeaders: (res: any, path: string, stat: string) => {
        res.set('x-timestamp', Date.now().toString());
    },
};

```

Finally can create a WebServer instance with this config as follows.

``` typescript

import { ApplicationRoutes, GetRouter, Router, WebServer } from 'mission.api';
import { WebConfig } from './config';

const server = new WebServer(WebConfig, console);

import './controller';
const route: Router = GetRouter();
route.use(ApplicationRoutes);

server.init();
server.addApiRouting('/', route);
server.start();


```

### Logger Configuration Interface


``` typescript 

interface LoggerInstance {
    log: Function;
    info: Function;
    warn: Function;
    error: Function;
}
```
Morgan Logger configuration: 

Set the following evironment variable. 

    process.env.MORGAN = 'dev'
Accepted Values are: 
1. combined
2. common
3. dev (default)
4. short
5. tiny

[More Reference](https://www.npmjs.com/package/morgan)

## Util

### Wrap

``` typescript
Wrap((req:Request, res:Response, next:NextFunction)=>{});

```

### ErrorWrap
