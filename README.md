Whois server
------------

Whois server build on top of ruby EventMachine.


Demo Installation
-----------------

Before demo install, please ensure you have rbenv and postgres installed. 

    git clone https://github.com/internetee/whois.git
    cd whois
    bundle
    cp config/database.yml-example config/database.yml # and edit it
    rake db:setup
    ruby whois.rb start # or other commands: status start stop run
    whois hello.ee -h localhost -p 1043 # by default whois run on port 1043

You should receive 

    Hello from whois server!

If you have any issues you can try run whois server on front:

    ruby whois.rb stop   # stops running whois
    ruby whois.rb run    # runs whois server in terminal for debug
    ruby whois.rb --help # for other commands


Production installation
-----------------------

Before production installation, please ensure you have rbenv and postgres installed.

At your local machine:

    git clone https://github.com/internetee/whois.git
    cd whois
    bundle
    mina pr setup


```
    iptables -t nat -A PREROUTING -p tcp --dport 43 -j REDIRECT --to-port 1043
```