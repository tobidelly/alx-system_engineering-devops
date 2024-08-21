# 0x17. Web stack debugging #3

DevOpsSysAdminScriptingDebugging

-   Weight: 1
-   Ongoing second chance project - started Aug 13, 2024 6:00 AM, must end by Aug 19, 2024 6:00 AM
-   An auto review will be launched at the deadline

#### In a nutshell…

-   **Auto QA review:** 0.0/2 mandatory
-   **Altogether:**  **0.0%**
    -   Mandatory: 0.0%
    -   Optional: no optional tasks

### Concepts

_For this project, we expect you to look at these concepts:_

-   [Web Server](https://intranet.alxswe.com/concepts/17)
-   [Web stack debugging](https://intranet.alxswe.com/concepts/68)

## Background Context

![](https://s3.amazonaws.com/intranet-projects-files/holbertonschool-sysadmin_devops/293/d42WuBh.png)

When debugging, sometimes logs are not enough. Either because the software is breaking in a way that was not expected and the error is not being logged, or because logs are not providing enough information. In this case, you will need to go down the stack, the good news is that this is something Holberton students can do :)

Wordpress is a very popular tool, it allows you to run blogs, portfolios, e-commerce and company websites… It [actually powers 26% of the web](https://intranet.alxswe.com/rltoken/qxyFYZIwOXQWw02-HaQ7Bw "actually powers 26% of the web"), so there is a fair chance that you will end up working with it at some point in your career.

Wordpress is usually run on LAMP (Linux, Apache, MySQL, and PHP), which is a very widely used set of tools.

The web stack you are debugging today is a Wordpress website running on a LAMP stack.

## Requirements

### General

-   All your files will be interpreted on Ubuntu 14.04 LTS
-   All your files should end with a new line
-   A `README.md` file at the root of the folder of the project is mandatory
-   Your Puppet manifests must pass `puppet-lint` version 2.1.1 without any errors
-   Your Puppet manifests must run without error
-   Your Puppet manifests first line must be a comment explaining what the Puppet manifest is about
-   Your Puppet manifests files must end with the extension `.pp`
-   Files will be checked with Puppet v3.4

## More Info

### Install `puppet-lint`

```
$ apt-get install -y ruby
$ gem install puppet-lint -v 2.1.1
```

## Tasks

### 0\. Strace is your friend

mandatory

Score: 0.0% (Checks completed: 0.0%)

[![](https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/medias/2019/6/f5af5167e65bd3101f76.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20240817%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20240817T103120Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=d14a26a0b47c8df3bc008db7b248a24805fda7a90d5d88db35854ca9d8e9a8a5)](https://youtu.be/uHEzt1QuASo)

Using `strace`, find out why Apache is returning a 500 error. Once you find the issue, fix it and then automate it using Puppet (instead of using Bash as you were previously doing).

Hint:

-   `strace` can attach to a current running process
-   You can use [tmux](https://intranet.alxswe.com/rltoken/6GpArtwhw7thSyNub9s3qA "tmux") to run [strace](https://intranet.alxswe.com/rltoken/ueMevAif95DjyW2sqVCMoA "strace") in one window and `curl` in another one

Requirements:

-   Your `0-strace_is_your_friend.pp` file must contain Puppet code
-   You can use whatever Puppet resource type you want for you fix

Example:

```
root@e514b399d69d:~# curl -sI 127.0.0.1
HTTP/1.0 500 Internal Server Error
Date: Fri, 24 Mar 2017 07:32:16 GMT
Server: Apache/2.4.7 (Ubuntu)
X-Powered-By: PHP/5.5.9-1ubuntu4.21
Connection: close
Content-Type: text/html

root@e514b399d69d:~# puppet apply 0-strace_is_your_friend.pp
Notice: Compiled catalog for e514b399d69d.ec2.internal in environment production in 0.02 seconds
Notice: /Stage[main]/Main/Exec[fix-wordpress]/returns: executed successfully
Notice: Finished catalog run in 0.08 seconds
root@e514b399d69d:~# curl -sI 127.0.0.1:80
root@e514b399d69d:~#
HTTP/1.1 200 OK
Date: Fri, 24 Mar 2017 07:11:52 GMT
Server: Apache/2.4.7 (Ubuntu)
X-Powered-By: PHP/5.5.9-1ubuntu4.21
Link: &lt;http://127.0.0.1/?rest_route=/&gt;; rel="https://api.w.org/"
Content-Type: text/html; charset=UTF-8

root@e514b399d69d:~# curl -s 127.0.0.1:80 | grep Holberton
&lt;title&gt;Holberton &amp;#8211; Just another WordPress site&lt;/title&gt;
&lt;link rel="alternate" type="application/rss+xml" title="Holberton &amp;raquo; Feed" href="http://127.0.0.1/?feed=rss2" /&gt;
&lt;link rel="alternate" type="application/rss+xml" title="Holberton &amp;raquo; Comments Feed" href="http://127.0.0.1/?feed=comments-rss2" /&gt;
        &lt;div id="wp-custom-header" class="wp-custom-header"&gt;&lt;img src="http://127.0.0.1/wp-content/themes/twentyseventeen/assets/images/header.jpg" width="2000" height="1200" alt="Holberton" /&gt;&lt;/div&gt;  &lt;/div&gt;
                            &lt;h1 class="site-title"&gt;&lt;a href="http://127.0.0.1/" rel="home"&gt;Holberton&lt;/a&gt;&lt;/h1&gt;
        &lt;p&gt;Yet another bug by a Holberton student&lt;/p&gt;
root@e514b399d69d:~#
```

**Repo:**

-   GitHub repository: `alx-system_engineering-devops`
-   Directory: `0x17-web_stack_debugging_3`
-   File: `0-strace_is_your_friend.pp`

Done?! Check your code

×

#### Correction of "0. Strace is your friend"

Start a new test Close

Requirement success

Requirement fail

Code success

Code fail

Efficiency success

Efficiency fail

Text answer success

Text answer fail

Skipped - Previous check failed

Get a sandbox QA Review

×

#### 0\. Strace is your friend

##### Commit used:

-   **User:** \---
-   **URL:** Click here
-   **ID:** `---`
-   **Author:** \---
-   **Subject:** _\---_
-   **Date:** \---

×

#### Recommended Sandbox

Running only

### 1 image<small class="ml-2">(0/2 Sandboxes spawned)</small>

### Ubuntu 14.04 - 293

Web stack debugging #3

Run
