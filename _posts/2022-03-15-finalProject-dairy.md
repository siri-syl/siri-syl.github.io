---
published: true
title:  "[Diary] 코드스테이츠 Final Project 후기"
excerpt: ""

categories:
  - Diary
tags:
  - [Project, Review]

toc: true
toc_sticky: true
 
date: 2022-03-15 23:34:00
last_modified_at: 2022-03-15 23:34:00
---

## 4주의 프로젝트 규모  
2주 약간 안 되게 진행했던 퍼스트 프로젝트와 달리 파이널 프로젝트는 약 4주 간 진행하는 프로젝트다.  
기존에 배운 것 말고도 새로운 걸 시도하는 것에 의의를 두는 것이었는데, 과연 내가 속했던 팀이 그만큼 잘 했을까 라는 생각이 든다.  

### 프로젝트 주제+킥(kick)
우리 팀은 tag검색을 기반으로 하자는 한 팀원분의 의견과, 당ㄱ마켓+에브ㄹㅌ임을 섞어서 지역 기반 커뮤니티를 만들고 싶다는 내 의견을 종합하여,  
태그 검색 기반의 지역 커뮤니티를 만들자는 계획을 세우고 프로젝트에 임했었다.  

새로 시도하는 것으로는 `AWS`의 `Router53` 등을 이용한 https 배포, `TypeScript` 사용, `oAuth2.0` 로그인 3개, 비밀번호나 인증번호 이메일 전송(`nodeMailer`), 두 개의 상태창을 한 페이지에서 개별작동하게 하는 것, 채팅방과 신고함을 만드는 것 등이 있었다.  
<br>

## 깃헙 개인 KPT 회고
퍼스트 프로젝트 때와 달리 파이널 프로젝트에서는 **개인 KPT회고 시간은 따로 없었다.**  
그러나 내가 여기서만 개인적으로 적고자 한다. 여기서 적는 것은 팀 활동을 한 나 자신을 돌아보는 시간을 가지며 작성했다.  

그동안의 단체 KPT회고나 Dev.log or error.log를 보고 싶다면 [이 링크](https://github.com/codestates/UDONDAM/issues?q=is%3Aopen+is%3Aissue)를 찾아가면 된다.  

### Keep (유지할 항목)  
* 주기적으로 코드리뷰를 하는 시간을 갖고 서로 나누고 싶은 의견들을 공유한다.  
* 급하게 공유할 것이 있다면 디스코드로 연락하여 당장 되는 사람들이라도 얘기를 한 뒤 참여하지 못한 사람에게 이 소식을 요약하여 전달한다.  
* 깃헙에 error.log, dev.log 등을 꾸준히 작성한다.  
* 깃헙의 이슈를 closed 해도 되는 건 제대로 해두고, 마일스톤과 태스크카드도 제때 체크하여 협업에 차질이 없도록 한다.  
* 시간이 부족하다면 구현하기 어려운 기능은 과감히 제외한다. 어중간한 것보단 낫다.  
* 내 파트가 끝나고 여유가 된다면 다른 파트를 도와준다.  
* 이틀 이상 고민하고 팀원들과 얘기해도 해결하지 못한 문제는 아고라 스테이츠에 문의한다.  
* 팀이 불화를 일으킨 팀원에게 마지막에라도 그 행동을 제지하는 자리를 가졌었다.  

### Problem (문제라고 생각하는 항목)  
* 혼자 나도는 팀원을 제지하지 못하고 팀장에게 도움 요청도 못했다.  
* 위의 팀원이 팀 분위기를 망가뜨리는 행동에 잠깐이지만 화를 냈었다. 좀 더 신경 썼다면 화를 안 내고 해결할 수도 있었을 것 같다.  
* 목표했던 기능을 다 구현하지 못했다.  
* 기획할 때 더 새로운 기능이나 신박한 기능을 넣을 수 있었을 텐데 아이디어가 부족한 것 같다.  

### Try (Action Items)  
* 마음 속 불편함은 추후 커다란 불화를 일으킬 수 있다. 자리를 마련해 의견을 나누는 시간을 가지도록 하자.  
* 소리가 커진다는 건 마음의 거리가 멀어졌다는 뜻이다. 차분한 마음을 가지도록 노력하며 대화를 시도하자.  
* 기획 단계도 중요하지만 기간에 맞게 마일스톤을 잘 짜서 프로젝트에 임해야 한다. 이는 입사하게 될 회사에서도 받쳐줘야 할 능력이다.  
* 팀원들은 '말해줘라, 그러면 구현해보겠다.'는 느낌의 사람들이 많았다. 아이디어 제의에 의욕적인 팀원은 나와 한 사람뿐이었는데, 나는 기획 이후 특별한 제시를 못했고, 다른 팀원은 현 시대의 sns나 커뮤니티 일반적인 기능들을 거의 모르는 분이라 이미 있는 기능들의 하위버전을 제시할 뿐이었다. 더 많은 웹사이트들과 어플리케이션을 접하고 생각을 넓혀가야겠다.  

<br/>

## 개인적으로 느꼈던 점  
퍼스트 프로젝트와 달리 내가 한 일이 많았다는 생각이 들었다. 아쉬운 점도 많았지만, 퍼스트 때와 비교하려고 하면 정말 많은 것을 해내어 개인적으로 뿌듯함은 있었다.  

다만 꼭 좋은 일만 있는 것도 아니었다. 개인적으론 좋았다 해도 팀 전체를 본다면 퍼스트때보다 못한 감도 있었기 때문이다.  
중간중간 팀 이탈 활동을 하는 팀원과 제대로 대화를 나누지도 못해 팀의 분위기가 좋지 않았고, 다른 팀과 비슷하거나 더 좋았던 퍼스트 때와 달리 이번엔 다름 팀에 비해 시각적인 면으로 현저히 수준이 떨어져 보이기도 했다. 디자인 감각뿐만이 아니라 여러 라이브러리나 기능을 구현하는 것 자체에도 떨어진다는 뜻이다.  

변명으로는 기능 제안에 의욕적이지 않은 팀원들 때문이라고 하고 싶지만, 결국 그걸 받침해주지 못한 내 잘못도 있음을 알고 있다.  
나 혼자 잘하면 뭐 하나, 라는 것을 절실히 깨닫게 된 프로젝트라고 할 수 있겠다....  

그래도 이를 바탕으로 새로 돌아보고, 리팩토링이나 코드 리뷰를 다시 해보며 시간을 가지면 미래의 나는 더 좋은 개발자로 있을 것이라 기대하고 있다.  
아자아자!  

<br/>
<br/>