---
layout: post

title: oracle dbstart ORACLE_HOME_LISTNER problem 
subtitle: "ORACLE_HOME_LISTNER is not SET, unable to auto-start Oracle Net Listener"
cover_image: blog-cover.jpg

excerpt: "Oracle: dbstart – ORACLE_HOME_LISTNER is not SET, unable to auto-start Oracle Net Listener"

author:
  name: 오승목
  gplus: 1234
  bio: Developer
  image: 오승목.jpg
---
오라클을 작동하기 위해 dbstart명령어를 실행하면 아래와 같은 오류가 난다.
{% highlight bash  %}
[oracle@fs ~]$ dbstart
ORACLE_HOME_LISTNER is not SET, unable to auto-start Oracle Net Listener
Usage: /home/oracle/u01/app/oracle/product/11.2.0/dbhome_1/bin/dbstart ORACLE_HOME
{% endhighlight %}

ORACLE_HOME_LISTNER환경변수가 설정되어 있지 않은것 같아 다음과 같이 설정해봤다.
{% highlight bash  %}
[oracle@fs ~]$ export ORACLE_HOME_LISTNER=$ORACLE_HOME
{% endhighlight %}

그리고 다시 실행해 보면
{% highlight bash  %}
[oracle@fs ~]$ dbstart
ORACLE_HOME_LISTNER is not SET, unable to auto-start Oracle Net Listener
Usage: /home/oracle/u01/app/oracle/product/11.2.0/dbhome_1/bin/dbstart ORACLE_HOME
{% endhighlight %}
똑같이 에러가 난다.

해결방법은?
파라미터로 환경변수를 넣어준다.

{% highlight bash  %}
[oracle@fs ~]$ dbstart $ORACLE_HOME
{% endhighlight %}

출처 : http://www.markhneedham.com/blog/2012/01/26/oracle-dbstart-oracle_home_listner-is-not-set-unable-to-auto-start-oracle-net-listener/
