# web-challenge
for the web challenge you proposed. it's developped by laravel framework .
# Installation
*composer needed
*wamp/server needed
downald the file web-challenge.rar and unzipp it in some directory like (c:/path ) 
go to commandline(cmd) and reach this unzipedd directory ;command> cd path/web-challenge
and run the installation  using command: composer install
after installation create a database with name (web-challenge) in mysql or depending on your dabatabase server (if it's not wamp mysql please do the configuration in the file .env) and just create it (if you change db name or db username or password or it s hosted in another server please check .env file and do what it has to be modified).
return to cmd and apply command: php artisan migrate 
after the success of migration run the command :php artisan db:seed 
(i made a database seeder to have some shops )
and finally run the service using command : php artisan serve
and the command line will show you the url (http//ip:port) in localhost it will be :http://localhost:8000.

# the web-challenge site
it contains all what you suggest (principal/optional) items , you have to registre ,to make your authentification ,after that you will be found on a store of shops as it's descriped containings shops ,you can like and unlike shops ,if you like a shop it will be found on the prefered shops and if youd dislike it it will disapear for 2 hours from your store of shops .
you can also remove the shop from the prefered shops .
and finally you can logout .

# Code organisation 
as you know laravel is working with mvc design pattern ,so i made my models in the app folder ,there is two models shop and user with a n:n relation between them .
the database migration are done in database/migration you will find the 4 tables to migrate (runned firstly with php artisan migrate ).
the views are in the resources/views . i try to have a good structure including home page in the layout and ,the 2 pages nearbyshops and preferedshops are included in the home page optimizing codes .
finally The controllers in app\Http\Controllers ,I did a repositories folder which it contain a shoprepository for making code more clear;
finally i programmed a cron by the default scheduler of laravel in app/console/kernel.php to return the unliked shops to the store every 2 hours by calling a the cronReshop in app/console/command , it s functional if you do a homestead or it s hosted ,you can try by runing on parallel cmd the command : php artisan command:cronReshop

# the functionning of the functions 
you can see in the HomeController and the shopController  the methods like unlike and remove .
actualy i did a pivot recording in database shop_user that attach every user with liked and unliked the same time (to avoid duplicating tables )but i added an boolean attribut unliked to distingue the liked and unliked one .for the liked one it display normally but the unliked are stored and not displayed .after the 2 hour cron ,the unliked will be deleted from the shop_user and reposted again in the nearbyShop.

# finaly
I wish i was clear enough,thank you for reading .regards
