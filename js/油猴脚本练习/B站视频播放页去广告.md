```
// ==UserScript==
// @name         B站视频播放页去广告
// @namespace    http://tampermonkey.net/
// @version      2025-04-05
// @description  B站视频播放页去广告
// @author       Anya
// @match        https://www.bilibili.com/*
// @icon         https://www.google.com/s2/favicons?sz=64&domain=ixbk.net
// @grant        none
// ==/UserScript==

(function () {
    'use strict';
    function waitForElement(selector, callback) {
        const observer = new MutationObserver(() => {
            const element = document.querySelector(selector);
            if (element) {
                observer.disconnect();
                callback(element);
            }
        });

        observer.observe(document.body, {
            childList: true,
            subtree: true
        });

        // 防止一开始就存在
        const existing = document.querySelector(selector);
        if (existing) {
            observer.disconnect();
            callback(existing);
        }
    }
    // 使用方式
    waitForElement('.up-avatar .bili-avatar', (el) => {
        // 评论区上方
        document.querySelector('.ad-report.ad-floor-exp.left-banner').remove()
        // 右侧，弹幕列表下方
        document.querySelector('#slide_ad').remove()
        // 页面右下方
        document.querySelector('.ad-report.ad-floor-exp.right-bottom-banner').remove()
    });
})();
```
