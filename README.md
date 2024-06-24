You can use these docker files for dockerizing your laravel application.
First you need to build a base image for you php base image you can use the docker file inside the php_base_image and then push it to your docker registery.

Now in second step you should put the docker file inside laravel folder in your laravel project and replace the first line with you image address you pushed to your registery in prevoise step.
FROM {{Your build image base which you build in your prevoise step}}

Finally you can build your image from your laravel project and push it in your registery and use it.
