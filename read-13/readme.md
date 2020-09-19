# Local Storage:

# THE PAST, PRESENT & FUTURE OF LOCAL STORAGE FOR WEB APPLICATIONS

## DIVING IN
 > * Historically, web applications have had none of these luxuries. Cookies were invented early in the web’s history, and indeed they can be used for persistent local storage of small amounts of data. But they have three potentially dealbreaking downsides:
  > * Cookies are included with every HTTP request, thereby slowing down your web application by needlessly transmitting the same data over and over.
  > * Cookies are included with every HTTP request, thereby sending data unencrypted over the internet (unless your entire web application is served over SSL).
  > * Cookies are limited to about 4 KB of data — enough to slow down your application (see above), but not enough to be terribly useful.

## A BRIEF HISTORY OF LOCAL STORAGE HACKS BEFORE HTML5:
 > * In the beginning, there was only Internet Explorer. Or at least, that’s what Microsoft wanted the world to think. To that end, as part of the First Great Browser Wars, Microsoft invented a great many things and included them in their browser-to-end-all-browser-wars, Internet Explorer. One of these things was called DHTML Behaviors, and one of these behaviors was called userData.
 > * userData allows web pages to store up to 64 KB of data per domain, in a hierarchical XML-based structure. (Trusted domains, such as intranet sites, can store 10 times that amount. And hey, 640 KB ought to be enough for anybody.) IE does not present any form of permissions dialog, and there is no allowance for increasing the amount of storage available.
 > * In 2002, Adobe introduced a feature in Flash 6 that gained the unfortunate and misleading name of “Flash cookies.” Within the Flash environment, the feature is properly known as Local Shared Objects. Briefly, it allows Flash objects to store up to 100 KB of data per domain. Brad Neuberg developed an early prototype of a Flash-to-JavaScript bridge called AMASS (AJAX Massive Storage System), but it was limited by some of Flash’s design quirks. By 2006, with the advent of ExternalInterface in Flash 8, accessing LSOs from JavaScript became an order of magnitude easier and faster. Brad rewrote AMASS and integrated it into the popular Dojo Toolkit under the moniker dojox.storage. Flash gives each domain 100 KB of storage “for free.” Beyond that, it prompts the user for each order of magnitude increase in data storage (1 Mb, 10 Mb, and so on).
 > * In 2007, Google launched Gears, an open source browser plugin aimed at providing additional capabilities in browsers. (We’ve previously discussed Gears in the context of providing a geolocation API in Internet Explorer.) Gears provides an API to an embedded SQL database based on SQLite. After obtaining permission from the user once, Gears can store unlimited amounts of data per domain in SQL database tables.
 > * In the meantime, Brad Neuberg and others continued to hack away on dojox.storage to provide a unified interface to all these different plugins and APIs. By 2009, dojox.storage could auto-detect (and provide a unified interface on top of) Adobe Flash, Gears, Adobe AIR, and an early prototype of HTML5 storage that was only implemented in older versions of Firefox.
 > * As you survey these solutions, a pattern emerges: all of them are either specific to a single browser, or reliant on a third-party plugin. Despite heroic efforts to paper over the differences (in dojox.storage), they all expose radically different interfaces, have different storage limitations, and present different user experiences. So this is the problem that HTML5 set out to solve: to provide a standardized API, implemented natively and consistently in multiple browsers, without having to rely on third-party plugins.

## INTRODUCING HTML5 STORAGE
 > * what is HTML5 Storage? Simply put, it’s a way for web pages to store named key/value pairs locally, within the client web browser. Like cookies, this data persists even after you navigate away from the web site, close your browser tab, exit your browser, or what have you. Unlike cookies, this data is never transmitted to the remote web server (unless you go out of your way to send it manually). Unlike all previous attempts at providing persistent local storage, it is implemented natively in web browsers, so it is available even when third-party browser plugins are not.

## USING HTML5 STORAGE
 > * HTML5 Storage is based on named key/value pairs. You store data based on a named key, then you can retrieve that data with the same key. The named key is a string. The data can be any type supported by JavaScript, including strings, Booleans, integers, or floats. However, the data is actually stored as a string. If you are storing and retrieving anything other than strings, you will need to use functions like parseInt() or parseFloat() to coerce your retrieved data into the expected JavaScript datatype.

## TRACKING CHANGES TO THE HTML5 STORAGE AREA
 > * If you want to keep track programmatically of when the storage area changes, you can trap the storage event. The storage event is fired on the window object whenever setItem(), removeItem(), or clear() is called and actually changes something. For example, if you set an item to its existing value or call clear() when there are no named keys, the storage event will not fire, because nothing actually changed in the storage area.
 > * The storage event is supported everywhere the localStorage object is supported, which includes Internet Explorer 8. IE 8 does not support the W3C standard addEventListener (although that will finally be added in IE 9). Therefore, to hook the storage event, you’ll need to check which event mechanism the browser supports. (If you’ve done this before with other events, you can skip to the end of this section. Trapping the storage event works the same as every other event you’ve ever trapped. If you prefer to use jQuery or some other JavaScript library to register your event handlers, you can do that with the storage event, too.)


## LIMITATIONS IN CURRENT BROWSERS
 > * “5 megabytes” is how much storage space each origin gets by default. This is surprisingly consistent across browsers, although it is phrased as no more than a suggestion in the HTML5 Storage specification. One thing to keep in mind is that you’re storing strings, not data in its original format. If you’re storing a lot of integers or floats, the difference in representation can really add up. Each digit in that float is being stored as a character, not in the usual representation of a floating point number.

## HTML5 STORAGE IN ACTION
 > * How does it work? Every time a change occurs within the game, we call this function:
  > * function saveGameState() {
    if (!supportsLocalStorage()) { return false; }
    localStorage["halma.game.in.progress"] = gGameInProgress;
    for (var i = 0; i < kNumPieces; i++) {
	localStorage["halma.piece." + i + ".row"] = gPieces[i].row;
	localStorage["halma.piece." + i + ".column"] = gPieces[i].column;
    }
    localStorage["halma.selectedpiece"] = gSelectedPieceIndex;
    localStorage["halma.selectedpiecehasmoved"] = gSelectedPieceHasMoved;
    localStorage["halma.movecount"] = gMoveCount;
    return true;
 } 
 > * On page load, instead of automatically calling a newGame() function that would reset these variables to hard-coded values, we call a resumeGame() function instead. Using HTML5 Storage, the resumeGame() function checks whether a state about a game-in-progress is stored locally. If so, it restores those values using the localStorage object.
  > * function resumeGame() {
    if (!supportsLocalStorage()) { return false; }
    gGameInProgress = (localStorage["halma.game.in.progress"] == "true");
    if (!gGameInProgress) { return false; }
    gPieces = new Array(kNumPieces);
    for (var i = 0; i < kNumPieces; i++) {
	var row = parseInt(localStorage["halma.piece." + i + ".row"]);
	var column = parseInt(localStorage["halma.piece." + i + ".column"]);
	gPieces[i] = new Cell(row, column);
    }
    gNumPieces = kNumPieces;
    gSelectedPieceIndex = parseInt(localStorage["halma.selectedpiece"]);
    gSelectedPieceHasMoved = localStorage["halma.selectedpiecehasmoved"] == "true";
    gMoveCount = parseInt(localStorage["halma.movecount"]);
    drawBoard();
    return true;
 }

 > * The most important part of this function is the caveat that I mentioned earlier in this chapter, which I’ll repeat here: Data is stored as strings. If you are storing something other than a string, you’ll need to coerce it yourself when you retrieve it. For example, the flag for whether there is a game in progress (gGameInProgress) is a Boolean. In the saveGameState() function, we just stored it and didn’t worry about the datatype:
  > * localStorage["halma.game.in.progress"] = gGameInProgress;
  > * But in the resumeGame() function, we need to treat the value we got from the local storage area as a string and manually construct the proper Boolean value ourselves:
  > * gGameInProgress = (localStorage["halma.game.in.progress"] == "true");
  > * Similarly, the number of moves is stored in gMoveCount as an integer. In the saveGameState() function, we just stored it:
  > * localStorage["halma.movecount"] = gMoveCount;
  > * But in the resumeGame() function, we need to coerce the value to an integer, using the parseInt() function built into JavaScript:
  > * gMoveCount = parseInt(localStorage["halma.movecount"]);


## BEYOND NAMED KEY-VALUE PAIRS: COMPETING VISIONS
 > * While the past is littered with hacks and workarounds, the present condition of HTML5 Storage is surprisingly rosy. A new API has been standardized and implemented across all major browsers, platforms, and devices. As a web developer, that’s just not something you see every day, is it? But there is more to life than “5 megabytes of named key/value pairs,” and the future of persistent local storage is… how shall I put it… well, there are competing visions.
 > * One vision is an acronym that you probably know already: SQL. In 2007, Google launched Gears, an open source cross-browser plugin which included an embedded database based on SQLite. This early prototype later influenced the creation of the Web SQL Database specification. Web SQL Database (formerly known as “WebDB”) provides a thin wrapper around a SQL database, allowing you to do things like this from JavaScript:
  > * openDatabase('documents', '1.0', 'Local document storage', 5*1024*1024, function (db) {
  db.changeVersion('', '1.0', function (t) {
    t.executeSql('CREATE TABLE docids (id, name)');
  }, error);
});

*Alaa Aldous*

 





