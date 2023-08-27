```
[32](https://gitlab.webcase.me/doccine/doccine-frontend/-/jobs/3565#L32)Error: No such image: registry.webcase.me/doccine/doccine-frontend:8d249dca

[33](https://gitlab.webcase.me/doccine/doccine-frontend/-/jobs/3565#L33)Unable to find image 'registry.webcase.me/doccine/doccine-frontend:8d249dca' locally

[34](https://gitlab.webcase.me/doccine/doccine-frontend/-/jobs/3565#L34)docker: Error response from daemon: Head "[https://registry.webcase.me/v2/doccine/doccine-frontend/manifests/8d249dca](https://registry.webcase.me/v2/doccine/doccine-frontend/manifests/8d249dca)": unauthorized: HTTP Basic: Access denied. The provided password or token is incorrect or your account has 2FA enabled and you must use a personal access token instead of a password. See [https://gitlab.webcase.me/help/user/profile/account/two_factor_authentication#troubleshooting](https://gitlab.webcase.me/help/user/profile/account/two_factor_authentication#troubleshooting).

[35](https://gitlab.webcase.me/doccine/doccine-frontend/-/jobs/3565#L35)See 'docker run --help'.

[37](https://gitlab.webcase.me/doccine/doccine-frontend/-/jobs/3565#L37)Cleaning up project directory and file based variables00:00

[39](https://gitlab.webcase.me/doccine/doccine-frontend/-/jobs/3565#L39)ERROR: Job failed: exit status 1
```
- First analyse a problem 
```
frontend/manifests/8d249dca)": unauthorized: HTTP Basic: Access denied. The provided password or token is incorrect or your account has 2FA enabled and you must use a personal access token instead of a password. See 
```
-  clearly mentions error is in 2FA or in Personal acces token

### How we solve 
- Jainel sir has change the password for Personal acces token. So
-  again create a  new acces token for bot name a bot (bot_4) assign that to bot_4
- and retry that failed pipline 
- pipeline passed and problem solved

#### After that new problem Occur 

#### First analyse a problem 
- Can't login to doccine.webcase.me. showing  `Network error `
- `Network error` means doccer container is not communicating with a other container 
- eg front-end container is not comminication with a back-end comtainer. so that is why it is showing network error. 
![[Pasted image 20221123121823.png]]

### How we solve 

- Go to backend of the gitlab.webcase.me 
- we found last pipeline is failed with the same error we got in front-end. so issue is with the pipeline
```
backend/manifests/8d249dca)": unauthorized: HTTP Basic: Access denied. The provided password or token is incorrect or your account has 2FA enabled and you must use a personal access token instead of a password. See 
```
