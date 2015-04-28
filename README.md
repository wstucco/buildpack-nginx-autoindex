# NGINX Buildpack for Dokku - Hosting static pages with autoindex enabled
This buildpack has been successfully run on Digital Ocean instances of Ubuntu 14.02 (Status: Apr 2015). It might also work with different configurations.

## Purpose
`buildpack-nginx-static` is a fork of [`buildpack-nginx`](https://github.com/florianheinemann/buildpack-nginx) (a simple, low overhead way of hosting static pages and websites on Dokku) that adds site wide directory indexes and the ability to set the index format (`html`, `xml`, `json`, `jsonp`).  
Thedefault index format is `jsonp`.   
Please refer to [nginx docs](http://nginx.org/en/docs/http/ngx_http_autoindex_module.html#autoindex_format) for a description of the various formats.  
Just add the `.env` and `.static` file to the root directory of your website as described below.

## Usage
1. Add a file with the name `.env` in the root of your directory with the following content: `export BUILDPACK_URL=https://github.com/wstucco/buildpack-nginx-autoindex.git`
2. Add another, *empty* file called `.static` to your root directory of your web project. It signals that this buildpack shall be used
3. Optionally set `NGINX_AUTOINDEX_FORMAT` to `html` `xml` or `json` to customize autoindex output.  
To disable autoindex set `NGINX_AUTOINDEX` to `off`.
4. Push your project to Dokku

All static files that you want to serve should be in the root directory of your repository. No need to use a seperate `www` folder. `buildpack-nginx-autoindex` will automatically download the buildpack, download NGINX, compile it, and install it. The next time you push your project, the buildpack will reuse the precompiled binaries. 

## Credits and License
`buildpack-nginx-autoindex` is licensed under the CC0 1.0 Universal license   

[Massimo Ronca](http://twitter.com/wstucco/)

[`buildpack-nginx`](https://github.com/florianheinemann/buildpack-nginx) was created by [Florian Heinemann](http://twitter.com/TheSumOfAll/)
