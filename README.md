This is a bare bones example of how to implement infinite scrolling using jQuery **without** plugins. If you want to experiment with infinite scrolling and are wondering how to catch the end-of-page condition and load new content in response then this demo is for you. 

This demo starts with a bunch of paragraphs inside a `<div id="content">` tag. This  same chunk of paragraphs also makes up `content.html` which represents the "server response". Here's the entirety of the JavaScript required to implement this simplistic form of infinite scrolling.

    function loadMoreContent()
    {
      $.get('content.html', function(data) {
        if (data != '') {
          $('#content p:last').after(data);
        }
      });
    };

    $(window).scroll(function() {
      // Modify to adjust trigger point. You may want to add content
      // a little before the end of the page is reached. You may also want
      // to make sure you can't retrigger the end of page condition while
      // content is still loading.
      if ($(window).scrollTop() == $(document).height() - $(window).height()) {
        loadMoreContent();
      }
    });

This example is meant to demonstrate the basic JavaScript required for infinite scrolling. It does not assume any details about how you might choose to use infinite scrolling in your particular project. Thus, no effort is made to track record ids or offsets. Nor does it implement a loading indicator or deal with an end of data condition or any other fancy things you may want to do. These pieces of additional functionality are likely to be unique to your project and are fairly easy to implement anyway. Hopefully, you will find this useful in writing your own implementation.

The Lorem Ipsum text was generated using the [Loremify](http://tobiasahlin.com/blog/introducing-loremify/) Dashboard widget for OS X. It's about the only Dashboard widget I actually use. Ever.

MIT license.
