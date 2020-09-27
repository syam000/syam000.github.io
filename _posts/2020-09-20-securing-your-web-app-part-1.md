---
layout: post
title:  "How to secure your web application - Part I"
date:   2020-09-20 12:43:16 +0800
categories: security
comments: true
---

![](/assets/secure_web_app_1.jpg)

It's is a dangerous world out there! 🤯 😱 🙀 Yes, it's true!

Take a look at this article:
[Amazon says it mitigated the largest DDoS attack ever recorded](https://www.theverge.com/2020/6/18/21295337/amazon-aws-biggest-ddos-attack-ever-2-3-tbps-shield-github-netscout-arbor)

And I have personally experienced a systematic bot attack while working on my new web application. So thought to share with you all and it may help someone out there.

**What I am working on?** 😃 😃 😃

* A [NodeJS](https://nodejs.org/en/) Backend Application
    - An app to handle user requests and perform certain actions based on the user requests
    - Connected to a [arangodb](https://www.arangodb.com/) instance 
    - Exposed REST APIs via [express.js](https://expressjs.com/)
* A [ReactJS](https://reactjs.org/) Frontend Application
    - An admin dashboard to perform administrator tasks
* Few other micro-services built on NodeJS
    - Backup database on regular basis - cronjob
    - Send email notifications on regaulr basis - cronjob
    - Etc.


I won't say it's a highly sophisticated application. But it has its complexities. 

**Where it hosted?** 😃 😃 😃

I have hosted the application on [Amazon Web Services - AWS](https://aws.amazon.com/)
    - Provisioned an EC2 instance with all the dependencies
    - Using [PM2](https://pm2.keymetrics.io/) carry out application process management

This was my setup. 

**What happened?** 😱 😱 😱

After setting up everything I have carried some sanity tests, it all went well. But after a week noticed that everyday morning the server is throwing [503 - Service Unavailable.](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/503) error. And there is the only person who is actively accessing the resources and it was me. I started thinking 🤔 🤔 🤔 How come this is happening.

Then started analyzing the logs via pm2 

{% highlight zsh %}

pm2 logs --format

{% endhighlight %}

Then I realized some bad bots are attacking my web application regularly. Thus making my web application to crash at some point. 

Badddddd!!! 🥺

Then I started thinking of making changes to my setup to handle the attacks.

**How I tackled it?** 😎 😎 😎

I have tackled the attack at different levels.

- Application Level -  Added rate liming using the [rate limiter library](https://www.npmjs.com/package/express-rate-limit)
    - Rate limiting is a very powerful feature for securing backend APIs from malicious attacks and for handling unwanted streams of requests from users.
    In general terms, it allows us to control the rate at which user requests are processed by our server. [More info](https://blog.logrocket.com/rate-limiting-node-js/#:~:text=Rate%20limiting%20is%20a%20very,are%20processed%20by%20our%20server.)

- [AWS Web Application Firewall](https://aws.amazon.com/waf/)
    - AWS WAF is a web application firewall that helps protect your web applications or APIs against common web exploits that may affect availability, compromise security, or consume excessive resources. 
    - AWS WAF gives you control over how traffic reaches your applications by enabling you to create security rules that block common attack patterns, such as SQL injection or cross-site scripting, and rules that filter out specific traffic patterns you define. 
    - You can get started quickly using Managed Rules for AWS WAF, a pre-configured set of rules managed by AWS or AWS Marketplace Sellers. 
    - The Managed Rules for WAF address issues like the [OWASP Top 10 security risks](https://owasp.org/). These rules are regularly updated as new issues emerge. AWS WAF includes a full-featured API that you can use to automate the creation, deployment, and maintenance of security rules.

Once I have provisioned this service, I have started monitoring the network logs and found the issues in a detailed way.

I have employed AWS Managed Rules - these are predefined rules that can capture common threats. Also added my own specific
rules and I have seen the results. 🤓 🤓 🤓

![](/assets/secure_web_apps_2.png)

AWS WAF pricing was also reasonable and they only charge me under 10$. 🤗

Even though this was not enough and I know the security aspects of the application is something that you have to monitor regularly.

Also, I have added some more AWS Services during this period:
- [AWS Certificate Manager](https://aws.amazon.com/certificate-manager/) to install the HTTPS certificate
- [AWS Route 53](https://aws.amazon.com/route53/) - DNS web Service
- [AWS Autoscaling](https://aws.amazon.com/autoscaling/) - AWS Auto Scaling monitors your applications and automatically adjusts capacity to maintain steady, predictable performance at the lowest possible cost. 


**Best practices?** 👨‍💻 👨‍💻 👨‍💻

- Add rate-limiting your API resources
- Adhere to secure programming practices - For [NodeJS](https://blog.risingstack.com/node-js-security-checklist/)
- Install HTTPS certificate
- Restrict the access to the server via IP filtering for development purpose
- Provision web application firewall according to the cloud system you are using
- Enable system level logging and employ process managers
- Carry out an internal security audit using the https://owasp.org/www-project-top-ten/


To be continued...

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


