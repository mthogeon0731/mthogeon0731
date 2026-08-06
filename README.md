# Hogeon Kim

Chemical Biomolecular Engineering, Sogang University.

I don't have a CS background. Most of what's here started because I needed the thing to exist.

[한국어](#한국어)

---

## CLOCK OUT.exe

iOS, [App Store](https://apps.apple.com/kr/app/%ED%87%B4%EA%B7%BC/id6768991274) · [Repository](https://github.com/mthogeon0731/CLOCK-OUT)

Everyone using the app shares a single counter. Press the button, the number goes up. Time zones keep it moving around the clock — Asia sleeps, Europe picks it up, the Americas take over in the morning. Whoever pushes it to 100% triggers a forced blue screen on every connected device and the count resets.

There's a megaphone that broadcasts a message to every user at once. Handing a worldwide microphone to people venting about work is an obvious moderation problem, so messages run through GPT-4o-mini before they render. It catches hate speech across languages and strips personal information.

The UI is Windows 95 on purpose.

The repository is a showcase rather than the full app. It documents three things: the moderation pipeline, what a single globally shared counter does to a database row, and an authorization design I got wrong the first time and had to rebuild.

React Native (Expo), Supabase Realtime, RevenueCat, OpenAI API.

## PODO

iOS, [App Store](https://apps.apple.com/kr/app/podo/id6768158603) · [Repository](https://github.com/mthogeon0731/PODO)

Group scheduling. Everyone marks the times they're free and the app shows where the overlap is. There's also candidate-date voting for when you already have a few dates in mind.

Beyond scheduling it has a group feed and a pegboard, which is a canvas where a group arranges photos, stickers and notes.

Shipped in May, currently on 1.0.3. Blocking and reporting went in at 1.0.1.

React Native (Expo), Supabase.

## SYNC

Not released. Running on a live server with one user, me. [Repository](https://github.com/mthogeon0731/SYNC)

A calendar that accumulates a picture of how you work. Every action — adding an event, marking it done, rating it, dragging it somewhere else — gets distilled in a background task into a long-term memory record. That record goes into the system prompt on the next AI call.

What it stores looks roughly like this:

    category: study      -> 10:00 high, 15:00 low
    routine:  wednesday  -> 19:00 workout, 82% completion
    fatigue:  3+ back-to-back meetings -> deep work output drops

Which shows up as:

- Unfinished work from yesterday reappears today, placed at the hour that category usually goes well
- At the end of the day you drag your actual schedule into the one you'd rather have had. The difference gets distilled overnight.
- A weekly report on where the week drained you, from completion rates and ratings

I use it every day.

Next.js 15, FastAPI, Supabase, OpenAI API.

## formulation-bo / dcv-vision

Two libraries from one project. [formulation-bo](https://github.com/mthogeon0731/formulation-bo) · [dcv-vision](https://github.com/mthogeon0731/dcv-vision)

We were optimizing a thermal interface material, alumina in PDMS. More filler means better thermal conductivity and worse viscosity, until the paste stops dispensing. Finding the balance properly takes dozens of samples. There were three of us and no budget for that.

**formulation-bo** is the part that decides what to run next. It fits a Gaussian Process to what we've measured, anchored to physical models (McLachlan GEM, Krieger-Dougherty), and suggests one experiment at a time instead of a sweep. There's a demo that runs against a simulated system so you can try it without a lab.

**dcv-vision** exists because that loop needed a number it didn't have. How evenly the filler is dispersed matters as much as how much of it there is, and dispersion was something we were grading by eye off a micrograph — which doesn't reproduce between two people, or between the same person on two days. So: split the frame into a grid, measure particle coverage per cell, take the coefficient of variation. One photo in, one number out, the same number every time.

Together they close the loop. Photograph the sample, get a dispersion figure, feed it back with the thermal and viscosity measurements, get the next formulation to try.

Python, scikit-learn, NumPy, OpenCV, FastAPI.

## Stack

Python, TypeScript, React Native / Expo, Next.js, FastAPI, Supabase, OpenAI API, scikit-learn, OpenCV.

Contact: mt.hogeon0731@gmail.com

---

# 한국어

서강대학교 화공생명공학과.

전공은 공과대학 화공생명공학과입니다. 여기 있는 것들은 대부분 스스로 필요해서 개발을 시작했습니다.

## 퇴근 (CLOCK OUT.exe)

iOS, [App Store](https://apps.apple.com/kr/app/%ED%87%B4%EA%B7%BC/id6768991274) · [저장소](https://github.com/mthogeon0731/CLOCK-OUT)

전 세계 사용자가 카운터 하나를 공유합니다. 버튼을 누르면 숫자가 올라갑니다. 시차 덕분에 24시간 멈추지 않습니다. 아시아가 잠들면 유럽이, 유럽이 지치면 미주가 이어받습니다. 100%를 채운 사람이 나오면 접속 중인 모든 화면에 블루스크린이 뜨고 숫자는 0으로 돌아갑니다.

확성기로 전 세계에 메시지를 쏘는 기능이 있습니다. 회사에 대한 분노를 쏟아내는 앱에서 전 세계 마이크를 쥐여주는 셈이라, 메시지는 노출 전에 GPT-4o-mini를 거칩니다. 다국어 혐오 표현과 개인정보를 걸러냅니다.

UI가 윈도우 95인 건 의도한 겁니다.

저장소는 앱 전체가 아니라 쇼케이스입니다. 세 가지를 기록했습니다. 검열 파이프라인, 전 세계가 공유하는 카운터 하나가 DB 행에 무슨 일을 하는지, 그리고 처음에 잘못 만들어서 다시 세운 인가 구조.

React Native (Expo), Supabase Realtime, RevenueCat, OpenAI API.

## PODO

iOS, [App Store](https://apps.apple.com/kr/app/podo/id6768158603) · [저장소](https://github.com/mthogeon0731/PODO)

그룹 일정 조율 앱입니다. 각자 가능한 시간을 표시하면 겹치는 구간을 보여줍니다. 후보 날짜가 이미 있을 때는 O/X 투표로도 정할 수 있습니다.

일정 외에 그룹 피드와 페그보드가 있습니다. 페그보드는 사진, 스티커, 메모를 자유롭게 배치하는 캔버스입니다.

5월 출시, 현재 1.0.3. 차단과 신고 기능은 1.0.1에서 넣었습니다.

React Native (Expo), Supabase.

## SYNC

미출시. 실서버에서 돌아가고 있고 사용자는 저 한 명입니다. [저장소](https://github.com/mthogeon0731/SYNC)

일하는 방식을 누적해서 파악하는 캘린더입니다. 일정을 넣거나, 완료를 체크하거나, 별점을 주거나, 다른 시간으로 옮길 때마다 백그라운드에서 그 데이터를 압축해 장기 기억으로 저장합니다. 저장된 기억은 다음 AI 호출의 시스템 프롬프트로 들어갑니다.

저장되는 형태는 대략 이렇습니다.

    카테고리: 학업     -> 오전 10시 성취도 상, 오후 3시 하
    루틴:    수요일    -> 저녁 7시 운동, 완료율 82%
    피로도:  연속 미팅 3개 이상 -> 집중 업무 성과 저하

이게 이렇게 나타납니다.

- 어제 못 끝낸 일이 오늘 다시 뜨는데, 그 카테고리가 보통 잘 되는 시간대에 놓입니다
- 하루가 끝나면 실제 일정을 원했던 하루로 끌어다 놓습니다. 그 차이가 밤에 다시 기억으로 압축됩니다.
- 완료율과 별점으로 이번 주에 어디서 지쳤는지 보여주는 주간 리포트

매일 쓰고 있습니다. 추후에 상업화를 하려고 준비 중인 제일 중요한 프로젝트입니다.

Next.js 15, FastAPI, Supabase, OpenAI API.

## formulation-bo / dcv-vision

한 프로젝트에서 나온 두 개의 라이브러리입니다. [formulation-bo](https://github.com/mthogeon0731/formulation-bo) · [dcv-vision](https://github.com/mthogeon0731/dcv-vision)

열전도 소재를 최적화하고 있었습니다. PDMS에 알루미나를 넣는 건데, 충전재를 늘리면 열전도도는 올라가고 점도도 같이 올라가서 어느 지점부터는 아예 도포가 안 됩니다. 제대로 균형점을 찾으려면 수십 번을 돌려야 합니다. 저희는 셋이었고 그럴 예산이 없었습니다.

**formulation-bo**는 다음에 뭘 할지 정하는 쪽입니다. 측정한 데이터에 가우시안 프로세스를 피팅하고, 물리 모델(McLachlan GEM, Krieger-Dougherty)을 사전 정보로 깔아서 전수 조사 대신 다음에 할 실험 하나를 추천합니다. 가상 시스템으로 돌려볼 수 있는 데모가 들어 있어서 장비 없이도 확인할 수 있습니다.

**dcv-vision**은 그 루프에 없던 숫자가 필요해서 만들었습니다. 충전재가 얼마나 들어갔는지만큼 얼마나 고르게 퍼졌는지도 중요한데, 분산도는 현미경 사진을 눈으로 보고 판단하고 있었습니다. 두 사람이 보면 다르게 나오고, 같은 사람이 이틀에 걸쳐 봐도 다르게 나옵니다. 그래서 사진을 격자로 나누고, 칸마다 입자가 덮은 면적을 재고, 그 값들의 변동계수를 냅니다. 사진 하나 넣으면 숫자 하나가 나오고, 몇 번을 돌려도 같은 값이 나옵니다.

둘을 붙이면 루프가 닫힙니다. 시료를 찍어서 분산도 수치를 얻고, 열전도도·점도 측정값과 함께 다시 넣으면 다음에 만들 배합이 나옵니다.

Python, scikit-learn, NumPy, OpenCV, FastAPI.

## 사용 기술

Python, TypeScript, React Native / Expo, Next.js, FastAPI, Supabase, OpenAI API, scikit-learn, OpenCV.

연락: mt.hogeon0731@gmail.com
