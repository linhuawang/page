---
layout: post
title:  "How to use Jupyter Notebook on a cluster"
date:   2019-02-13 15:57:39 -0500
categories: tech
---
<!-- You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/ -->

I sometimes want to test my code on a cluster and don't want to download codes/data to my desktop. Under such circumstances, I usually use jupyter notebook on the cluster and use the terminal on my desktop to send instructions and visualize intermediate results. In this post, I will show you how I do it.

Let's say, your cluster address is `hpc.cluster.com`, your user name is `linhuaw`, and you want to work in the directory `/path/to/work`.

# STEP 1: log into the cluster and go to the working folder.
{% highlight ruby %}
> ssh linhuaw@hpc.cluster.com
> password:
> cd /path/to/work
{% endhighlight %}

# STEP 2: invoke notebook in the working directory on the cluster.
{% highlight ruby %}
> jupyter notebook --no-browser --port=8888
{% endhighlight %}

# STEP 3: open a local terminal, and type: 
{% highlight ruby %}
> ssh -N -f -L localhost:8888:localhost:8888 linhuaw@hpc.cluster.com
> password: 
{% endhighlight %}

# STEP 4: open a browser, and type: `localhost: 8888`

Now, you are good to go.

