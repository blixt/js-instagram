# JavaScript Instagram library

This is a simple library to communicate with the Instagram API directly from
JavaScript.

## Example

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


## MIT license

This project is licensed under an MIT license.  
<http://www.opensource.org/licenses/mit-license.php>

Copyright © 2012 Blixt <me@blixt.org>
