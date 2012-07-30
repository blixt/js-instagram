# JavaScript Instagram library

This is a simple library to communicate with the Instagram API directly from
JavaScript.

## Example

This example will load the most recent likes of the current user. It will first
send the user to Instagram to authenticate with your application.

The images will be preloaded before the callback is called, so that the user
will see them all at the same time, instantly. If you want to use the data
before the images are available, skip the final "true" argument and use the
`InstagramImage.preload` function to preload the images (or a subset of them)
later.

    // Get an Instagram API client.
    var instagram = new Instagram('your_client_id');
    
    // Make sure the current user has been authenticated to Instagram.
    // If the user is not authenticated, the browser will be redirected to
    // Instagram's authentication page, then redirected back to this page.
    if (!instagram.authenticate()) {
      return;
    }
    
    // Get the most recent images of the current user, preloaded.
    instagram.getLikes('self', function (images) {
      for (var i = 0, len = images.length; i < len; i++) {
        var img = document.createElement('img');
        img.src = images[i].imageUrl;
        document.body.appendChild(img);
      }
    }, true);

## Notes

This API is currently in a very early stage and is lacking a lot of info in the
`InstagramImage` class. Watch this repository for updates and feel free to
submit pull requests!

## MIT license

This project is licensed under an MIT license.  
<http://www.opensource.org/licenses/mit-license.php>

Copyright © 2012 Blixt <me@blixt.org>
