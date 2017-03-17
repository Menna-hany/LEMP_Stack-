Name = Menna tallah Hany Hosny 
Email = menna.hany@hotmail.com 



LEMP stack 
RunScript file is a scipt to build all images 
steps inside script 
docker build -t menna/mysql . 
docker build -t menna/nginx . 
docker build -t menna/phpfpm . 
docker build -t menna/wp . 
docker run -d --name mysql menna/mysql
docker run -it --name wp menna/wp
docker run -d --name app --volumes-from wp --link mysql:db menna/phpfpm
docker run -d -p 80:80 --name nginx --volumes-from wp --link app:app menna/nginx 
