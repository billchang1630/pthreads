# Threading for PHP - Share Nothing, Do Everything :)&nbsp;&nbsp;&nbsp;<a href="https://travis-ci.org/#!/krakjoe/pthreads"><img alt="pthreads build status" src="https://secure.travis-ci.org/krakjoe/pthreads.png" border="0px"/></a>

This project provides multi-threading that is compatible with PHP based on Posix Threads.

## Highlights

* An easy to use, quick to learn Threading API for PHP5.3+
* Execute any and all predefined and user declared methods and functions asynchronously
* Ready made synchronization included, geared towards the PHP environment
* Seemless operation in multi-threaded SAPI environments
* A world of possibilities ...

## Technical Features

* Posix Threads
* Mutex
* Conditions
* Synchronization
* Worker Threads

pthreads was written with simplicity, compatibiilty and efficiency in mind, it's performance beggars belief !!

## Requirements

* PHP5.3+ on x64 or x86
* ZTS Enabled ( Thread Safety )
* Posix Threads implementation that PHP will compile with

Testing has been carried out both on x86 and x64 architechtures with varying hardware, this code may work in untested environments, keep me updated ...

### Supported PHP Versions

pthreads should compile and work in any version of PHP from 5.3.0 to 5.4.7, many versions of PHP are used in testing from both 5.3 and 5.4 series

### Windows Support

Yes !! Windows support is offered thanks to the pthread-w32 library. Pre-built binary downloads are available on the github downloads page for Windows users.

### Mac OSX Support

Yes !! It's reported to me that pthreads compiles fine on your machines, I don't have access to a Mac so any reports are very welcome :)

### Hello World

As is customary in our line of work:

```php
<?php
class AsyncOperation extends Thread {
  public function __construct($arg){
    $this->arg = $arg;
  }

  public function run(){
    if($this->arg){
      printf("Hello %s\n", $this->arg);
    }
  }
}
$thread = new AsyncOperation("World");
if($thread->start())
  $thread->join();
?>
```

### Are you serious ?

Absolutely, this is not a hack, we _don't_ use forking or any other such nonsense, what you create are honest to goodness posix threads that are completely compatible with PHP and safe ... this is true multi-threading :)

PHP is awesomely powerful, but the simple fact of the matter is, the number of extensions or features a language has doesn't matter one bit. What matters is how many features or extensions you can utilize in your latest and greatest project.
We only have about one or two seconds to send a page to a user, in practice we end up picking and choosing which of PHP's features we will use because time is always a factor. Enterprising applications usually have to look to Java or the .NET
framework if they are designed to do heavy lifting, aggregation, mathematics or the like. 

No man is an island: today's websites have to interact with several sources of data - from reference databases, to social networking API's and content feeds ... and everything inbetween ... they have to use and reuse caches, update those caches and then, log all about it, they have to do this several hundred million times a week, if your startup is successful. 
PHP excells at all of those tasks; but having to execute them synchronously will often mean that when you do start getting the traffic you want to your new project, things are a bit shaky, and from that moment on you're looking to replace the perfectly good code that you "made it" with, or even worse you're looking for features to remove ! 
Bringing threads to PHP stretches your two seconds as far as it will go; and I believe allow you to design your applications to do more than you would if Threads were not available; and allow you to develop much faster than
you can in Java or .NET, or any other language ( perhaps ), and as a result, you will be a happier human being, as will your boss, and your projects have virtually no limits ...

### SAPI Support

No restrictions here, you should have no problem running pthreads in your chosen SAPI.

You should bear in mind that in a SAPI environment your threads cannot write the standard output or read the standard input of the serving process, this may be obvious to some of you, but being a new subject probably worth mentioning.

### Documentation

Documentation can be found on http://pthreads.org, and some examples can be found in the "examples" folder in the master repository.

### Feedback

Please submit issues, and send your feedback and suggestions as often as you have them.

### Developers

There is no defined API for you to create your own threads in your extensions, this project aims to provide Userland threading, it does not aim to provide a threading API for extension developers. I suggest you allow users to decide what they thread and keep your own extension focused on your functionality.
