# P2P BTC Trading system
Building a pure P2P bitcoins trading system that let users trade digital works online, kind of like freelancing.

## Deployment Instructions 

   **Install dependencies**
    
     CouchDB
     Libssl-dev 
     Vim-nox 
     Nginx 
     Unzip 
     G++ 
     Screen 
     Git-core 
     Nodejs>= 0.6.1
     npm

```
2. vim /etc/nginx/sites-available/b2w
=====================================================
upstream app_cluster_1 {
        server 127.0.0.1:3001;
}

server {
        listen 0.0.0.0:80;
        server_name b2w.com www.b2w.com;
        access_log /var/log/nginx/b2w.log;

        location / {
          proxy_set_header X-Real-IP $remote_addr;
          proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
          proxy_set_header Host $http_host;
          proxy_set_header X-NginX-Proxy true;

          proxy_pass http://app_cluster_1/;
          proxy_redirect off;
        }
}
=====================================================
```

3. Enable Nginx server
      
        ln -s /etc/nginx/sites-available/b2w /etc/nginx/sites-enabled/b2w

4. Under the b2w folder, run: 
        
        npm install forever LazyBoy ejs express

5. `<path-to-forever-npm_module>/bin/forever start app.js`
