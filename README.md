# Beanstalk 
> NOTE: Doesn't work — has unidentified dependency YAML.

beanstalkd is a fast, distributed, in-memory workqueue service. See http://xph.us/software/beanstalkd/

An example from http://xph.us/software/beanstalkd/:

First, have one process put a job into the queue:
```Io
producer := Beanstalk clone connect("127.0.0.1:11300")
producer put("hello")
```

Then start another process to take jobs out of the queue and run them:
```Io
worker := Beanstalk clone connect("127.0.0.1:11300")
loop(
	job := worker reserve
	job body println # prints "hello"
	job delete
)
```

See Beanstalk.io code and protocol description (http://github.com/kr/beanstalkd/tree/master/doc/protocol.txt) for details.
Both are short and easy to read.

Stat commands depend on <a href="http://github.com/why/syck/tree/a4f241be5d247853aea6127d02dbdedd8a1dd477/ext/io">YAML</a>.

# Installation

```
eerie install https://github.com/IoLanguage/Beanstalk.git
```
