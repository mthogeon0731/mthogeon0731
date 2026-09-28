# Hogeon Kim

Chemical Biomolecular Engineering, Sogang University.

I study chemical and biomolecular engineering and build software around problems I run into, from coordinating schedules to deciding which materials experiment to run next.

Currently active in the **inaugural cohort of OpenAI Student Collective in South Korea**, as one of **16 students selected nationwide**.

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

**dcv-vision** turns a microscope image into a repeatable measure of spatial dispersion. I built it because judging filler distribution by eye gave us no consistent number to feed back into the experiment loop. It splits an image into an 8 × 8 grid and calculates **D_CV**, the coefficient of variation in coverage across the cells. Lower values mean more even coverage.

In **v2**, you explicitly choose dark or bright particles, and global Otsu thresholding separates them from the background. The pipeline normalizes image scale when a supported scale bar is present. When particles cover more than half the image, it measures variation in the **voids** instead, so dense samples do not hide uneven empty regions. Results include the definition version and the phase measured; v1 and v2 values are not directly interchangeable.

The core runs as a standalone Python function, with an optional local HTTP API and a synthetic demo. Measurements still depend on consistent imaging conditions and a sensible segmentation mask.

The two libraries support the same experiment loop: measure dispersion from a sample image, combine it with thermal conductivity and viscosity measurements, and use those observations to guide the next formulation.

Python, scikit-learn, NumPy, OpenCV, FastAPI.

## Stack

Python, TypeScript, React Native / Expo, Next.js, FastAPI, Supabase, OpenAI API, scikit-learn, OpenCV.

Contact: mt.hogeon0731@gmail.com

---

# 한국어

서강대학교 화공생명공학과.

화공생명공학을 공부하며 직접 마주친 문제를 해결하는 소프트웨어를 만듭니다. 함께 만날 시간을 정하는 일부터 다음 소재 실험을 설계하는 일까지, 대부분 스스로 필요해서 개발을 시작했습니다.

대한민국에서 선발된 **16명 중 한 명으로 OpenAI Student Collective 1기에 참여해 활동하고 있습니다.**

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

**dcv-vision**은 현미경 사진에서 분산 상태를 반복 가능한 수치로 얻기 위해 만들었습니다. 충전재가 얼마나 고르게 퍼졌는지 눈으로만 판단하면 실험에 다시 넣을 일관된 값이 없었습니다. 사진을 8 × 8 격자로 나누고, 각 칸의 면적 비율이 얼마나 달라지는지 변동계수 **D_CV**로 계산합니다. 값이 낮을수록 공간적으로 더 고르게 분포한 상태입니다.

**v2**에서는 입자가 배경보다 어두운지 밝은지 직접 지정하고, 전역 Otsu 임계값으로 입자와 배경을 분리합니다. 지원하는 스케일바가 있으면 이미지 축척을 정규화합니다. 입자가 화면의 절반을 넘는 고밀도 시료에서는 입자 대신 **빈 공간의 분포**로 편차를 계산해, 입자가 가득 찼다는 이유로 불균일한 빈 영역이 가려지지 않도록 했습니다. 결과에 지표 정의 버전과 계산에 사용한 상도 함께 반환하며, v1과 v2 수치는 그대로 섞어 비교하지 않습니다.

독립적인 Python 함수로 사용할 수 있고, 선택적으로 로컬 HTTP API와 합성 이미지 데모를 제공합니다. 측정값을 해석할 때는 촬영 조건을 일정하게 유지하고, 입자가 제대로 분리됐는지 마스크를 확인해야 합니다.

두 라이브러리는 같은 실험 흐름을 위한 도구입니다. 시료 사진에서 얻은 분산도와 열전도도·점도 측정값을 모아, 다음에 만들 배합을 정하는 데 활용합니다.

Python, scikit-learn, NumPy, OpenCV, FastAPI.

## 사용 기술

Python, TypeScript, React Native / Expo, Next.js, FastAPI, Supabase, OpenAI API, scikit-learn, OpenCV.

연락: mt.hogeon0731@gmail.com

