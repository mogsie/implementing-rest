State can mean many things in a RESTful environment.  There are three main types of State:

- *Resource State* — think of a static web server, it has some files on its file system.  The collection of files at any point in time are that server's collective resource state.
- *Application State* — think of a web browser viewing a specific web page, and the text, imagery and so on that the user is viewing and interacting with.  The browser window *is* the application state.

The first two states are states that we want to have, yet none of these have directly to do with the *stateless* nature of HTTP, the "stateless" constraint in REST.  Statelessness focuses on a third type of state:

- *Conversational State* — think of two people conversing, they exchange words, which when put together are understood; each utterance depends on the current conversational state.

The Web can't be used as an analogy for this _conversational_ state, because the web by default doesn't have any conversational state.

For example, when a web browser makes a request to a web server, the request contains all information necessary for the server to understand the context of the request, including any authentication information, if the browser already has a cached copy of this, or if that cached copy is out-dated.  It's all there in the headers.  The server doesn't care where the browser came from immediately prior to this request, and processes the request independently of any previous interaction the browser may have had.

Likewise, the browser, when it *receives* a response from a server, makes few, if any assumptions on what it should be doing with the data; all the information is there in the response: `Content-Type: text/html` tells the browser to render it as HTML; `image/jpeg` would tell it to show the byte-stream as an image.  The lack of conversational state also means that the browser should / must render the page regardless of whatever the browser has been up to previously, so like the server, the browser processes the response independently of any previous interaction it may have had.

A stateless conversation between two humans would be extremely long-winded, because every sentence would include everything that's relevant to the conversation up to that point.  Imagine going to get a cup of coffee at starbucks, but every time I started a new sentence, the Starbucks employee would be swapped out with a completely new person who didn't know who I was:

- Hi!
  - Hi!
- Hi, I'd like a cup of coffee!
  - Hi! Great! Latte or Frappuccino? Or perhaps an Ice coffee?  Or maybe something else?
- Hi, I'd like a cup of coffe, a latte!
  - Hi! Soy or regular?
- Hi, I'd like a cup of coffee, a latte, regular.
  - Hi, Great, that'll be $1.23.
- Hi, I'd like a cup of coffe, a latte, regular, and here's the $1.23.
  - Hi, Thanks, what's your name?.
- Hi, I'd like a cup of coffe, a latte, regular, and here's the $1.23, and I'm Sean.
  - Good to know you Sean, go over there and wait.
- Hi, I'd like a cup of coffe, a latte, regular, and here's the $1.23, and I'm Sean, and I was told to wait here.
  - Hi, please hold on a few more seconds.
- Hi, I'd like a cup of coffe, a latte, regular, and here's the $1.23, and I'm Sean, and I was told to wait here, and to please hold on a few more seconds.
  - Hi, Here's your coffee!

Of course you have to be civil and say "Thank you!":

- Hi, I'd like a cup of coffe, a latte, regular, and here's the $1.23, and I'm Sean, and I was told to wait here, and wait some more, and Thank you!
  - Have a nice day!


Thankfully, we humans enjoy stateful conversations.


State Transitions
-----------------

Since we have three types of states, talking about state transitions can be tricky.

- Web browser on page A, user clicks on a link, browser GETs page B, and the *application state* transitions to page B

- Web browser on page A, user pushes button, browser POSTs something somewhere, the server runs some code and therefore (perhaps) the *resource state* transitions to something else. Usually this also happens with a change in *application state* by way of the browser showing the response of the POST to the user.

Since conversational state is something to avoid, we won't talk about conversational state transitions.  The idea is that since there is no conversational state (beyond that of the current "page" so to speak), 


See also:
- [*Identifying Application State* — TAG Finding 01 December 2011](http://www.w3.org/2001/tag/doc/IdentifyingApplicationState-20111201) by w3c
- [*REST, where's my state?* — HTTP interactions should be stateless, but two kinds of state are involved](http://ruben.verborgh.org/blog/2012/08/24/rest-wheres-my-state/) by Ruben Verborgh
