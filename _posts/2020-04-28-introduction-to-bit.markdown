---
layout: post
title:  "Introduction to bit"
date:   2020-04-28 12:43:16 +0800
categories: react bit
comments: true
---

I have been looking into various ways to add components to my new react application. Then I found this new way to manage components called - [bit](https://bit.dev/). May not be new for some of you though. But as you all know, I am still a newbie 😅

It looks interesting to me thus wants to write a short post on it. Even though it's well documented, I am just giving a gist here 😎

![bit.dev](/assets/bit_post_1.png)

**What is bit?**

 If you are JS dev you are familiar with npm and if you are Java dev you must be familiar with maven and gradle. So can you imagine a world without these component libraries? ????  😱😱😱

My answer is a definite NOOOOOOO 😂 and I know most of you will agree with me on this too 😅

Yes these are components or dependencies that are an integral part of our daily development life. These components makes our life easier. 🤓

Then what is bit here? 🤔

Bit is a platform for collaboration on atomic components.

I have seen a simple definition of bit here from a [blog](https://blog.bitsrc.io/15-reasons-to-build-your-component-library-in-bit-dev-93a514878863) 

**"If a component library is like a music CD-Album, then bit.dev is like iTunes or Spotify for UI components."** 😎

It's an **open-source tool** ❤️ for collaborating on components across projects and repositories. Means, if you have a team and they are building and sharing a lot of components within themselves then you could make use of bit. 😃😃😃

If you want to share your component to the public as we always do through the traditional npm package you can do that as well. Lovely! 💜

**How to get started?**

[bit](https://bit.dev/) provides a very comprehensive documentation on how to get started, but if you ask me I will go the easiest way possible like below:

By the way I am on Mac, so I will be showing how to do this on Mac. Don't worry if you are on Winodws or Linux, [bit](https://bit.dev/) have all documented well for you too 😍

* Sign up/in to bit [bit](https://bit.dev/) using your credentials. If you don't have one create it 🤓

*  Install bit via [npm](https://www.npmjs.com/) or [homebrew](https://brew.sh/) ❤️

{% highlight zsh %}

npm install bit-bin --global

{% endhighlight %}
    
    
or
    

{% highlight zsh %}

brew install bit

{% endhighlight %}

Sweet!! 😎

* Configure the bit registry

{% highlight zsh %}

npm config set @bit:registry https://node.bit.dev

{% endhighlight %}

* Login to bit using your bit credentials

{% highlight zsh %}

npm login --registry=https://node.bit.dev --scope=@bit

{% endhighlight %}

or

{% highlight zsh %}

bit login

{% endhighlight %}

* That's it; you have set bit in your system! ❤️


**How to browse and install a library in your app?**

* Open [bit](https://bit.dev/) and sign in
*    Search for the component you are looking for - I want to add a chart library for react. Thus I enter search text as "chart" and Dependency option as "react". Because my app is based on react so I am only interested in react components. 

![search](/assets/bit_post_2.png)


By the way bit supports a wide variety of frameworks such as react, angular, vue.js and many more 💪

* Select the component you like to use and for now I have selected [**"chart v4.2.0"**](https://bit.dev/primefaces/primereact/chart/~code) released by [**"primefaces"**](https://bit.dev/primefaces) 


![search](/assets/bit_post_3.png)

* On the top right you can see how to install this component in your app. I have used npm thus, I just copy and paste the following on to my command line, enter 😃

{% highlight zsh %}

npm i @bit/primefaces.primereact.chart

{% endhighlight %}

* That's it you can start integrating the component as per the sample code 

**Summarize**

So that's about it 😃😎

Check it out more from [here](https://docs.bit.dev/docs/quick-start)

 Enjoy! 🤘🤘🤘
 
{% if page.comments %}

<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = 'https://syam00.github.io/graph/database/2020/04/28/introduction-to-bit.html';  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = '2020/04/28/introduction-to-bit'; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://https-syam00-github-io.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            
{% endif %}


