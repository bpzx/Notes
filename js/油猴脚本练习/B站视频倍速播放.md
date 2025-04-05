```
// ==UserScript==
// @name         B站视频倍速播放
// @namespace    http://tampermonkey.net/
// @version      2025-04-05
// @description  B站视频倍速播放
// @author       Anya
// @match        https://www.bilibili.com/*
// @icon         https://www.google.com/s2/favicons?sz=64&domain=ixbk.net
// @grant        none
// ==/UserScript==

(function () {
    'use strict';
    setTimeout(() => {
        let li_2x = document.querySelector('.bpx-player-ctrl-playbackrate-menu > li:nth-child(1)')
        console.log(li_2x);

        let li_custx = li_2x.cloneNode()
        console.log(li_custx);

        li_custx.setAttribute('data-value', '8')
        li_custx.textContent = '8.0x'
        document.querySelector('ul.bpx-player-ctrl-playbackrate-menu').insertBefore(li_custx, li_2x)
        li_custx.addEventListener('click', function (event) {
            document.querySelector('.bpx-player-video-wrap > video').playbackRate = 8
        })
    }, 60000)

})();
```
