## Examples of Nginx location directives

```nginx
location  = / {
    # Only matches the / query.
}
```
```nginx
location /data/ {
    # Any query beginning with /data/ but the process continues searching.
    # Will only be matched if regular expressions don't find a match.
}
```
```nginx
location ^~ /img/ {
    # Queries beginning with /img/ and then stops searching.
}
```
```nginx
location ~* .(png|gif|ico|jpg|jpeg)$ {
    # Matches requests ending in png, gif, ico, jpg or jpeg.
    # Any request to the /img/ directory are handled by the location block above.
}
```
Example how to prevent hotlinking of images:
```nginx
location ~ .(png|gif|jpe?g)$ {
    valid_referers none blocked yourwebsite.com *.yourwebsite.com;
    if ($invalid_referer) {
        return   403;
    }
}
```
Reject scripts inside writable directories:
