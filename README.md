# Books:
- [프랑스어권 학습자를 위한 한국어 – 초급 (다락원) / Cours de coréen - niveau débutant (Darakwon)](http://www.darakwon.co.kr/koreanbooks/book_view.asp?lg=en&bookid=53), Yonghae KWON, Hye-gyeong KIM, Hye-young TCHO, Jungyoon CHOI
- [50 règles essentielles - coréen (Studyrama)](https://librairie.studyrama.com/produit/1890/9782759027293/50-regles-essentielles-coreen), Stéphane COURALET

# Korean Conjugation:
- [Wiktionary](https://en.wiktionary.org/wiki/어둡다#Conjugation)
- [Dongsa Korean Verb Conjugator](https://koreanverb.app/?search=어둡다)
- [Irregular Verbs](https://www.morninglands.com/korean-language-bank-category/irregular-verbs)

# Dictionaries:
- [Naver](https://korean.dict.naver.com/koendict/#/search?query=어둡다)
- [Glosbe](https://glosbe.com/ko/fr/어둡다)

# Fonts:
- [Free Korean Fonts](http://www.freekoreanfont.com)
- [WAZU JAPAN's Gallery of Korean Unicode Fonts](http://www.wazu.jp/gallery/Fonts_Korean.html)


# Note Types: 한국어

## Fields
- 발음  *(prononciation)*
- 한국어  *(coréen), sort by this field in the browser*
- 프랑스어  *(français)*

## Cards
### Front Template
```
<span class="fr">{{프랑스어}}</span>
```

### Back Template
```
{{FrontSide}}
<hr id=answer>
{{한국어}}
<br>
{{발음}}
```

### Styling
```
.card {
  font-family: "UnDotum";
  font-size: 40px;
  text-align: center;
  color: black;
  background-color: white;
  line-height: 1.1;
}
.fr {
  font-family: "Garamond";
  font-size: 24px;
}
.em {
  font-weight: bold;
  color: blue;
}
.light {
  color: #85929e;
}
.small {
  font-size: 50%;
}
.fr .small {
  font-size: 70%;
}
ul {
  font-size: 70%;
  text-align: left;
  list-style-type: square;
  padding-left: 10px;
}
table {
  width: 100%;
  border-collapse: collapse;
  text-align: left;
  font-size: 75%;
}
table td {
  vertical-align: top;
}
#underlined-header th {
  border-bottom: solid;
  border-width: thin;
  border-color: black;
  vertical-align: top;
}
.발음 /* prononciation */ {
  font-size: 50%; /* small */
  color: #85929e; /* light */
}
.활용 .부정사 .발음 /* prononciation */ {
  margin: inherit;
  padding: inherit;
  color: #DCDCDC;
  font-weight: normal;
}
.활용 /* conjugaison */ {
  margin: 1px;
  padding: 2px;
  border: none;
  color: white;
  text-align: center;
  font-weight: normal;
  font-size: 50%;
}
.활용 .bloc {
  margin: inherit;
  padding: inherit;
  border-left: 3px solid black;
  border-radius: 5px;
}
.활용 .부정사 /* infinitif */ {
  margin: inherit;
  padding: inherit;
  background-color: #626567;
  font-weight: bold;
}
.불규칙 /* irrégulier */ {
  padding: inherit;
  color: #78281f;
}
.활용 .불규칙 /* irrégulier */ {
  margin: inherit;
  padding: inherit;
  color: white;
  background-color: #7d8082;
}
.활용 .현재 /* (indicatif) présent */ {
  margin: inherit;
  padding: inherit;
  background-color: #336699;
}
.활용 .과거 /* (indicatif) passé */ {
  margin: inherit;
  padding: inherit;
  background-color: #2673a6;
}
.활용 .미래 /* (indicatif) futur */ {
  margin: inherit;
  padding: inherit;
  background-color: #1a80b2;
}
.활용 .명령법 /* impératif */ {
  margin: inherit;
  padding: inherit;
  background-color: #ff6600;
}
.활용 .연결 /* mots de liaison (connective forms) */ {
  margin: inherit;
  padding: inherit;
  background-color: #0e6251;
}
.활용 .고 {
  margin: inherit;
  padding: inherit;
  background-color: hsl(168, 75%, 20%);
}
.활용 .지만 {
  margin: inherit;
  padding: inherit;
  background-color: hsl(168, 75%, 22%);
}
.활용 .는데 {
  margin: inherit;
  padding: inherit;
  background-color: hsl(168, 75%, 24%);
}
.활용 .면 {
  margin: inherit;
  padding: inherit;
  background-color: hsl(168, 75%, 26%);
}
.활용 .서 {
  margin: inherit;
  padding: inherit;
  background-color: hsl(168, 75%, 28%);
}
.하십시오체 /* registre formel poli */ {
  text-align: right;
}
.해요체 /* registre informel poli */ {
  text-align: center;
}
.해체 /* registre informel non poli */ {
  text-align: left;
}
.높임 /* honorifique */ {
  font-size: 70%;
}
@font-face {
  font-family: "UnDotum";
  src: url('_UnDotum.ttf');
}
@font-face {
  font-family: "Garamond";
  src: url('_Garamond-Regular.ttf');
}
```


# Media
```
koreanverb() {
  # usage: koreanverb 가깝다 가까워요
  local verb=/tmp/koreanverb.$1.html
  local file=${2/ /_}.mp3

  [ ! -s $verb ] && http -o $verb GET https://koreanverb.app/?search=$1
  local encoded=$(jq -R -r @uri <<<"$2")
  local check=$(grep "$encoded" $verb | sed "s#.*${encoded}.mp3?check=##" | sed "s/&#39;.*//")
  [ -n "$check" ] && http -o $file GET https://pronunciations.koreanverb.app/$encoded.mp3 Referer:https://koreanverb.app/ check==$check
  echo $file
}

naver() {
  # usage: naver 가까워요
  local file=${1/ /_}.mp3
  http -o $file GET https://korean.dict.naver.com/api/nvoice Referer:https://korean.dict.naver.com/koendict/ speaker==mijin service==dictionary speech_fmt==mp3 vcode==700535 text=="$1"
  echo $file
}

pronunciation() {
  # usage: pronunciation 가깝다 가까우시다 가깝습니다 가까우십니다
  #        pronunciation 가깝다 가까우시다 가까워요 가까우세요
  #        pronunciation 가깝다 가까우시다 가까웠어요 가까우셨어요
  #        pronunciation 가깝다 가까우시다 "가까울 거예요" "가까우실 거예요"
  echo "# $1 $2 $3 $4"
  local f1=$(koreanverb $1 "$3")
  local f2=$(koreanverb $2 "$4")
  [ ! -s $f2 ] && f2=$(koreanverb $1 "$4")

  [ ! -s $f1 ] && f1=$(naver "$3")
  [ ! -s $f2 ] && f2=$(naver "$4")

  local silenceDurationInSeconds=2

  [ -s $f1 ] && [ -s $f2 ] && ffmpeg -y -v quiet \
    -i $f1 \
    -f lavfi -t $silenceDurationInSeconds -i anullsrc \
    -i $f2 \
    -filter_complex "[0:a][1:a][2:a]concat=n=3:v=0:a=1" ${f1%%.mp3}.$f2

  [ -s ${f1%%.mp3}.$f2 ] && mv -f ${f1%%.mp3}.$f2 $f1 \
                         && rm -f $f2 \
                         || echo "unexpected error occurred" >&2
}


grep 부정사 13-과.csv | grep 현재 | grep 과거 | grep 미래 | sed 's#.*<div class="부정사">##' | sed 's#<div class="불규칙">[^<]*</div>##' | sed 's#<div class="명령법">[^<]*</div>##' | sed 's#</div><div class="bloc">##' | sed 's#</div></div></div><div class="bloc"><div class="고">.*##' | sed 's#</div><div class="[^"]*"><div class="하십시오체"><div class="높임"># #g' | sed 's#</div><div class="해요체"><div class="높임"># #g' | sed "s#</div># #g" | awk 'NF==17 && $1!=infinitive{infinitive=$1; print "naver",infinitive,$3,$2; print "naver",infinitive,$5,$4; print "naver",infinitive,$9,$8; printf "naver %s \"%s\" \"%s\"\n",infinitive,$16" "$17,$14" "$15}' > media.sh


sha1=$(git log -1 --pretty="format:%h"); for w in $(git show $sha1 | awk '/sound:/{print $1}' | sed 's/^.*:\(.*.mp3\)./\1/'); do echo $w $(git log --name-only $sha1 | grep "/$w"); done | grep -v media
cp collection.media/* ~/.local/share/Anki2/User\ 1/collection.media/
```
