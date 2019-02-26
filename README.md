#SoundScribe Info

##The Problem

For some, taking notes using a computer can be hard, as compared to pen and paper. There are several solutions out there that try to allow the user to do complex actions in a short amount of time, to be able to keep up with the lecture or meeting. This is because the action taking notes is divided into two main actions - transcribing and note taking. It is important to have record of what was being said, so that the notes have context. It is equally important to take notes, to further expand comprehension of the material. Instead of trying to make the user an expert at using a given paradigm, we simply take care of 50% of the task for them, by having an automatic transcription.

##Basics

SoundScribe is a note taking software, aimed for students in lectures. It is unique in that it transcribes audio in realtime from a microphone, and supplies features that take advantage of this capability so that users can more efficiently take effective notes. The UI consists of two main parts; Transcription and Notes, each a separate panel. The transcription is constantly being appended to by the speech recognition. The notes consist of only the user’s specific inputs. Notes can be linked to a specific point in both the audio and the transcription, so that reviewing them can be extremely easy.

##Additional Points:

- Targeting Desktop/Laptop release.
- Built with ~~NodeJS~~ iojs and ~~NodeWebkit~~ Atom-Shell
- Using really neat new web techs, like WebComponents, because we have a standardized release environment
- ~~Speech Recognition with OSS CMUSphinx (As a likely choice)~~
- Since we're using a packaged browser environment based on very current Chromium releases - we have reliable access to the Web Speech API, which is insanely accurate, and pretty painless to implement.

---

#How to set up


##What Git and GitHub is.

If you're not familiar with Git, it's a form of version control much like svn or cvn. If you're not familiar with version control, definitely look it up. It's a way of collaborating, making incremental improvements and keeping backups of a code base. If you're going to be a programer, essentially any organization you'll work for will almost certainly use some form of version control - so it's good to know how to use. The way it works is that one centralized server (in this case GitHub) keeps track of your code in a place called a **repository**. You can download the latest version of the code from this repository, and when you make changes, **commit**  it back to the server, with a comment about what is changed. It makes it really easy to collaborate on complex projects - but it's useful even in one-man operations.

You can download a git GUI [here](http://git-scm.com/downloads/guis), or if you're feeling especially savvy, just download the git command line version [here](http://git-scm.com/downloads).

Version control means that we want our code to be kept track of by the Git server - but we need other stuff to get our code running. For example, if you wanted to make a webserver and website, you need Apache (or nginx or httpd or what-have-you) to run your website right? And if you wanted to put your website under version control - you'd be tempted to throw in the instance of Apache you have as well. But you don't want Apache to be in your version control. We didn't make Apache, and unless we made some heavy modifications to it - it's better to keep it off of our git repository. We aren't making changes to Apache, so there's no versions to keep track of, and it's smarter to let anyone who wants to work with our code to just download the latest version. In the same way that you don't sell a book about engine repair that comes with an engine for $700. You let the user determine what engine they need to work with. It's a bad metaphor, I know. I'm also clearly not familiar with engine prices.

##Our dependencies

In our case, we're using [NodeJS](http://nodejs.org/) and [Atom-Shell](https://github.com/atom/atom-shell) (Well, technically using io.js - they just changed their names a few weeks ago). These are both really really cool technologies that are becoming very increasingly used in the industry. If you don't know what NodeJS is, [here](http://blog.modulus.io/absolute-beginners-guide-to-nodejs) is a pretty decent primer. It's a way of using JavaScript for desktop development. NodeJS is great - but you can't really make a UI with it on it's own - like most scripting, it's very powerful, but limitted without writing native modules. Fortunately for us, there is Atom-Shell. This essentially running a minimal chromium browser as your application - and the JavaScript instance shares the same hooks as NodeJS. Meaning, you can make a UI using super easy web technologies - and have the ability to work with the computer in a Native-like way.


###Quick note:

So very recently (matter of months and weeks), a lot of have been unhappy with the way Node.js has been progressing. I'm not sure exactly the nature of these complaints to be perfectly honest. Something to do with threading, and using an older version of V8. So people forked it and made iojs. Now everyone loves it because it's marginally faster, and is being regularly updated. Atom-Shell will state in some of it's documentation that it's built from Node, and some that it's built from io.js. For now, they're interchangable in almost every aspect, so this has no impact.

Atom-Shell is GitHub's framework for building Atom. Their really cool text editor. It works off the same exact principles as Node-Webkit - but handles things a little bit differently that may make our lives easier down the line.

###Other things to know:

I've been typing for too long now, and I'm getting tired. Here's some things you need to know about as well:

1. npm. This is NodeJSs way of managing modules. For example. You want to be able to make to connect to a MongoDB database from Node? Easy peasy. Just look it up, and you'll find [this](https://www.npmjs.com/package/mongoose). It tells you to go to the root directory of your project and run this one line:

    npm install mongoose
    
Which (spoiler alert) will look the same for almost any module. Then you're done. It's really nice and easy.

2. ~~node-gyp.~~ **Ignore this - this is why we've switched to Atom-Shell**. Since NodeWebkit is weird in some way, you sometimes have to compile modules yourself using their tool. It's usually not a problem. But sometimes it is. I haven't been able to compile the NodeJS versions of Speech Recognition tools to work with NodeWebkit.

3. bower. Bower is like npm for the browser. If you have a webserver, and you want to install [angular](https://angularjs.org/) - just like with npm, you go to your root directory and type in

    bower install angular
    
Super easy. "But wait!", you say - "We don't run a web server. Why is this relevant?" Well. We're running ~~NodeWebkit~~ Atom-Shell, which pretty much is a minimal browser that points to your file system, and pretends it's all a Web Server. We're using HTML, JS and CSS to make the bulk of the UI and code. So we'll need to get stuff like angular.

###Set up:

1. Download an Atom-Shell release from [here](https://github.com/atom/atom-shell).
2. Install git. Clone my repo. Drag and Drop the 'src' directory onto Atom.exe from atom-shell to run it.
3. Make changes. Commit. Push Request.

