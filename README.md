## Cisco AnyConnect Compatibility WIP
Started to make Pow compatible with the Cisco AnyConnect VPN client.  This isn't an ideal 
situation, but it was supposed to be close enough.  To make it work:

* Remove the DNS server and it's auto-dropping of /etc/resolver files.  These cause AnyConnect to gray-screen within about 30 seconds of starting the VPN.
* Remove IPFW rule that forwards traffic from 80 to the default Pow port of 20559.  This also causes AnyConnect to gray-screen.
* Run Pow on port 80 by default
* Run powd as root via system LaunchAgent, so that it can bind to port 80
* setuid back to unprivileged user after binding for security

I however abandoned this when I learned that AnyConnect was also overwriting /etc/hosts on boot.  There is at least one other bug (because using something like localtest.me doesn't work either), but I stopped digging into it eventually.

## Original Readme


                          W
                         R RW        W.
                       RW::::RW    DR::R
            :RRRRRWWWWRt:::::::RRR::::::E        jR
             R.::::::::::::::::::::::::::Ri  jiR:::R
              R:::::::.RERRRRWWRERR,::::::Efi:::::::R             GjRRR Rj
               R::::::.R             R:::::::::::::;G    RRj    WWR    RjRRRRj
               Rt::::WR      RRWR     R::::::::::::::::fWR::R;  WRW    RW    R
           WWWWRR:::EWR     E::W     WRRW:::EWRRR::::::::: RRED WR    RRW   RR
           'R:::::::RRR            RR     DWW   R::::::::RW   LRRR    WR    R
             RL:::::WRR       GRWRR        RR   R::WRiGRWW    RRR    RRR   R
               Ri:::WWD    RWRRRWW   WWR   LR   R W    RR    RRRR    RR    R
      RRRWWWWRE;,:::WW     R:::RW   RR:W   RR   ERE    RR    RRR    RRR    R
       RR:::::::::::RR    tR:::WR   Wf:R   RW    R     R     RRR    RR    R
         WR::::::::tRR    WR::RW   ER.R   RRR       R       RRRR    RR    R
            WE:::::RR     R:::RR   :RW   E RR      RW;     GRRR    RR    R
            R.::::,WR     R:::GRW       E::RR     WiWW     RRWR   LRRWWRR
          WR::::::RRRRWRG::::::RREWDWRj::::RW  ,WR::WR    iRWWWWWRWW    R
        LR:::::::::::::::::::::::::::::::::EWRR::::::RRRDi:::W    RR   R
       R:::::::::::::::::::::::::::::::::::::::::::::::::::tRW   RRRWWWW
     RRRRRRRRRRR::::::::::::::::::::::::::::::::::::,:::DE RRWRWW,
               R::::::::::::: RW::::::::R::::::::::RRWRRR
               R::::::::::WR.  ;R::::;R  RWi:::::ER
               R::::::.RR       Ri:iR       RR:,R
               E::: RE           RW           Y
               ERRR
               G       Knock Out Rails & Rack Apps Like A Superhero.


## Pow is a zero-config Rack server for Mac OS X.

[Pow Web Site](http://pow.cx/) -
[User's Manual](http://pow.cx/manual) -
[Annotated Source Code](http://pow.cx/docs/) -
[2-Minute Screencast](http://get.pow.cx/media/screencast.mov)

-----

Current Version: **0.4.0**

To install or upgrade Pow, open a terminal and run this command:

    $ curl get.pow.cx | sh

To set up a Rack app, just symlink it into `~/.pow`:

    $ cd ~/.pow
    $ ln -s /path/to/myapp

That's it! Your app will be up and running at `http://myapp.dev/`.
See the [user's manual](http://pow.cx/manual) for more information.

-----

&copy; 2012 Sam Stephenson, 37signals
