## Requirement
- Mac : Ruby > 2.x
    - 맥에서는 기본 루비설치 되어있는 사람은 거의 될듯 
    - 옛날 맥북이라서 1.9 버젼 깔려있는 사람은... 
    - ruby -version 처서 버젼 확인 
- Window 
    - 루비깔면 될듯...?

## 작성방법
1. _posts 폴더에 년도-월-날짜-제목.md 파일을 만든다. ex) 2014-08-14-내용.md
2. jekyll serve --watch 를 입력해서 서버를 킨다.
3. 내용을 계속 작성
4. 완료후에 rake site:publish 를 해준다.

## 설치
- gem install kekyll --pre
- bundle install

## Run
- 실제로 서버를 실행 시켜 작성한거 확인
- bundle exec jekyll serve

## 올리기
- rake site:generate : html 파일 만들기 
- rake site:publish : gitgub 에 푸시
- git push origin master : 깃에 푸시

## Reference
- [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
- [Jekyll](http://jekyllrb.com/)
