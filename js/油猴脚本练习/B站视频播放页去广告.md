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
        let ad1 = document.querySelector('.ad-report.ad-floor-exp.left-banner')
        if (ad1) {
            ad1.remove()
            console.log('已移除广告位置：评论区上方');
        }
        // 右侧，弹幕列表下方
        let ad2 = document.querySelector('.video-card-ad-small')
        if (ad2) {
            ad2.remove()
            console.log('已移除广告位置：右侧，弹幕列表下方');
        }
        // 页面右下方
        let ad3 = document.querySelector('.ad-report.ad-floor-exp.right-bottom-banner')
        if (ad3) {
            ad3.remove()
            console.log('已移除广告位置：页面右下方');
        }
    });
})();
```
