layout: "post"
title: "mixtape-may2020"
date: "2020-05-03 14:31"
---

#### Test - James

<pre>
  ____________________________
/|............................|
| |:    Mixmastermeatbeaters  :|
| |:         "Move It"        :|
| |:     ,-.   _____   ,-.    :|
| |:    ( `)) [_____] ( `))   :|
|v|:     `-`   ' ' '   `-`    :|
|||:     ,______________.     :|
|||...../::::o::::::o::::\.....|
|^|..../:::O::::::::::O:::\....|
|/`---/--------------------`---|
`.___/ /====/ /=//=/ /====/____/

</pre>

{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}

{% spotify https://open.spotify.com/playlist/37i9dQZF1DX1tz6EDao8it?si=bETMXiHRTnuQ6vxwXKnR7A %}

{% spotify spotify:track:0ZoOOxoA8o0lY590ivyMm4 %}

{% spotify https://open.spotify.com/track/0jan7Og7EncvRl4C6VuWU0?si=qp0E12xYQM2gyu8BvTpi3w %}

{% aplayer "Caffeine" "Jeff Williams" "/audio/2020/05/01.ogg" %}
{% aplayer "Caffeine" "Jeff Williams" "/audio/2020/05/02.mp3" %}

{% youtube mLuPQfIZDSs %}


<img src="/images/2020/04/IMG_20200411_182956.jpg" onclick="playAudio('/audio/2020/05/01.ogg')">

{% aplayer %}
{% aplayerlist %}
{
    "narrow": false,                          // Optional, narrow style
    "autoplay": true,                         // Optional, autoplay song(s), not supported by mobile browsers
    "mode": "random",                         // Optional, play mode, can be `random` `single` `circulation`(loop) `order`(no loop), default: `circulation`
    "showlrc": 3,                             // Optional, show lrc, can be 1, 2, 3
    "mutex": true,                            // Optional, pause other players when this player playing
    "theme": "#e6d0b2",	                      // Optional, theme color, default: #b7daff
    "preload": "metadata",                    // Optional, the way to load music, can be 'none' 'metadata' 'auto', default: 'auto'
    "listmaxheight": "513px",                 // Optional, max height of play list
    "music": [
        {
            "title": "CoCo",
            "author": "Jeff Williams",
            "url": "caffeine.mp3",
            "pic": "caffeine.jpeg",
            "lrc": "caffeine.txt"
        },
        {
            "title": "アイロニ",
            "author": "鹿乃",
            "url": "irony.mp3",
            "pic": "irony.jpg"
        }
    ]
}
{% endaplayerlist %}
{% aplayer %}
---
