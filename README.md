# laravel-codespaces-poc2
probe of concept of laravel with codespaces

## Steps

curl -s https://laravel.build/example-app | bash



Following:

GitHub Codespaces Laravel. Instalación y primeros pasos

https://www.youtube.com/watch?v=hPDASavmNeo&ab_channel=JavierTer%C3%A1nGonz%C3%A1lez


https://laravel.com/docs/9.x/installation/#getting-started-on-linux

TRUBLESHOOTINGS:

If accidentally you created a mysql volume by running sail without an .env file, which was persistent the whole time thus of course having no user and database configured.

I executed ./vendor/bin/sail down --rmi all -v to remove all images and volumes and then just ran ./vendor/bin/sail up and it created the images and volumes from scratch. 
Now everything worked out and I can migrate my data.
./vendor/bin/sail down --rmi all -v

Or, complete rebuild all the docker containers:
./vendor/bin/sail build --no-cache

Problems with docker:

#(master) $ docker ps

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

my solution:

1.- I killed dockerd process:

`#(master) $ ps -aux | grep dockerd`

`#(master) $ kill -9 DOCKERD_PROCESS_ID`

`#(master) $ sudo dockerd &`

Run dockerd successfully!

## Laravel URL and mempry problems:

I suggest to use this in web.php 


```
ini_set('memory_limit', -1);
$url = config('app.url');
URL::forceRootUrl($url);
if (App::environment('production')) {  
    URL::forceScheme('https');  
}
 ```

##

I disabled debug mode in the .env

NOTE: Migrations has to be run inside of the container
        
