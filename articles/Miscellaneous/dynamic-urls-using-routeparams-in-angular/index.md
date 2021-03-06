---
title: Dynamic Urls Using Routeparams In Angular
---
What if you have a lot of users posting _things_ to your website? Maybe your users want to have a profile, or a wall, of the _things_ they've posted, and they want to be able to share it with their friends with a url? You can do that, no biggie!

Let's say you used

    >> yo angular-fullstack:route wall

to generate a <a>http://myapp.wherever.com/wall/</a> route for your users. You want a link to <a>http://myapp.wherever.com/wall/someUsername</a> to show a specific user's _things_.  
Browse to **/client/app/wall/wall.js** and notice that it detects what URL the user is requesting before acting on it:

    $routeProvider.when('/wall', …

You can customize that path to catch when a user is trying to see a profile associated with a specific username like so:

    $routeProvider.when('/wall/:username', …

The colon before "username" indicates that this is a variable, which is then passed to the _$routeParams_ module. In **wall.controller.js**, include _$routeParams_:

    .controller('WallCtrl', function ($scope, $routeParams) { …

Then later on in **wall.controller.js**, you can see what username was requested in the URL by referring to the variable generated by _$routeProvider_ using something like

    var wallOwner = $routeParams.username;