---
layout: post
title: 第一次 SDK Code Review 心得
tags: [心得, Git, Code review]
---

在寫這篇時突然想起蠻久以前有看過一篇關於 code review 的文章還不錯，在這邊先分享給大家 [讓 Google 教你 Code Review](https://medium.com/@ryanyang1221/%E8%AE%93-google-%E6%95%99%E4%BD%A0-code-review-be251d4d81b4) ，如果是想看比較有內容有深度應該會收穫比較多的可以點連結過去看一下，下面純屬小菜雞工程師最近遇到的事情以及小小的感想

前陣子在工作上完成了一個相較過去比較大的一個功能改動，既然是一個比較大的功能改動，所以想當然爾在 project 裡面牽動到的部分就非常的多，一開始知道自己要負責的內容時還有點小擔心，畢竟一個小菜雞而已還有蠻多地方不甚了解QQ

還好在開始動工前，自己先用紙筆把整個邏輯流程順了兩三次，大概需要在哪邊新增那些函式、需要在哪邊修改那些參數在心裡有了個底之後便開始動工，果然在邏輯清晰流程確定的情況下基本順利的寫完了~~

不過...你以為一切就這麼結束了嗎？怎麼可能又不是還是學生在做 project ，自己做完自己底完蟲蟲就可以上傳交差了。

一如正常的工作流程將自己的改動 commit，然後再確認一下主幹有沒有人有做了甚麼修改，有的話先做一下 rebase，最後再送出  merage request 把自己的 branch 送出交給其他人進行 code review。

在之前也不是沒有走過這樣的流程，不過之前開發的功能大多主要是與 UI 邏輯還有控制相關的部分，所以影響範圍較小大多自行處理即可。或許可能是前幾次的經驗讓我覺得好像 code review 不是太花時間的事情。

既然前面會這樣說那就代表這次明顯與我想的完全不同XD

因為這次的工作主要處裡的功能算是蠻重要的一部分，所以在許多地方有很多的判斷、DB處理、API處理等等，在我寫的過程中有的部分其實有想到說：「阿！這邊應該會有需要做錯誤回傳、例外處理。」，不過過去自己開發久了很多東西都覺得自己心裡有素，在發生錯誤或是例外的時候輸出一下 log 或是 print 出來看看就好，就沒有做很嚴謹的回傳以及承接的動作。

因為這件事讓我深深的體會到，有些事情該做就是得做，別因為覺得還好、沒關係、或是甚麼這個加上去程式碼看起來很冗之類的，多一兩行判斷或是設定錯誤碼是可以讓 "大家" 在程式發生問題的時候可以快速、明確的知道程式發生了甚麼問題最快速的方式。

寫到最後一直覺得還有一個心得沒寫到，那就是因為自己之前練習跟開發的時候都很習慣會不定期的做一下 Coding style 調整，像是看到多餘的空行或是沒加到空白的地方之類都會忍不住去調成我自己覺得舒服的樣子，甚至偶爾會用 IDE 的自動排版去調整 code 的排版。

恩 沒錯 你知道發生了甚麼，我在我改的幾個檔案有的地方去整理了 Coding style....，一開始我也不知道這會造成怎樣的事情，直到我自己在 git 上確認自己修改的內容時...恩...我到底幹了啥呢...

所以另一個心得就是別手癢去做一些無意義但是會造成程式碼大量改動的動作，因為這很容易造成程式碼在 git 上產生衝突，也會讓你被同事念喔XD