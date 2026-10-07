# Hogeon Kim

OpenAI Student Collective

Chemical and Biomolecular Engineering undergraduate at Sogang University, focused on physics-informed machine learning and experimental optimization.

I build research software that connects physical models, material characterization, and data-driven experimental design.

## Selected Research

### [cvd-reconstruction](https://github.com/mthogeon0731/cvd-reconstruction)

Research software reimplemented from research descriptions and specifications to study coating thickness and bottom-to-top step coverage in rectangular trenches. It connects a steady one-dimensional reaction–diffusion model with quantitative optical-image metrology, REF/DARK correction, and registered observation windows.

RF, KRR, and SVR are evaluated on held-out conditions, with model selection and scaling inside training folds. Dependency checks reject shared specimens, batches, or image content across conditions; image tiles are features, not independent observations. Paired thickness estimates yield step coverage, while Monte Carlo propagation reports uncertainty conditional on supplied parameter and measurement assumptions.

Public examples and validation use synthetic images, labels, and calibration inputs. Real OM/FE-SEM validation remains pending; the synthetic results establish software consistency only.

[Synthetic results](https://github.com/mthogeon0731/cvd-reconstruction/blob/main/docs/EXAMPLE.md) · [Model and limits](https://github.com/mthogeon0731/cvd-reconstruction/blob/main/docs/MODEL.md) · [Provenance](https://github.com/mthogeon0731/cvd-reconstruction/blob/main/docs/PROVENANCE.md)

### [formulation-bo](https://github.com/mthogeon0731/formulation-bo)

A Bayesian optimization library for balancing apparent thermal conductivity and viscosity in Al₂O₃/PDMS formulations. Its `ask`/`tell` interface combines physical priors (McLachlan GEM and Krieger–Dougherty), residual Gaussian Processes, an optional dispersion mediator, and ParEGO scalarization with Expected Improvement. Recommendations search one filler-fraction variable, propagating predicted mediator uncertainty before the next batch is made.

The public record includes one real 35-batch campaign: 15 shared initial batches and ten further batches per arm, comparing optimization with and without dispersion feedback. CSV data and replay/analysis scripts accompany the results; `demo.py` is a separate synthetic example.

Analysis distinguishes predictions using measured D_CV from predictions available before mixing. Repeated cross-validation reshuffles one dataset, and k_app includes contact resistance. This campaign does not establish causal effects, statistically significant superiority, or experiment-count savings.

[Campaign results and limits](https://github.com/mthogeon0731/formulation-bo#results-from-a-real-campaign) · [Data and reproduction scripts](https://github.com/mthogeon0731/formulation-bo/tree/master/docs/results)

### [dcv-vision](https://github.com/mthogeon0731/dcv-vision)

A deterministic OpenCV measurement pipeline for describing spatial variation in microscope images. Explicit dark/bright particle selection, global Otsu segmentation, and an 8 × 8 grid produce D_CV, a mask preview, and versioned measurement metadata. Definition v2 uses void fractions above 50% particle coverage.

An exploratory check of 19 real micrographs informed the pipeline; uneven illumination still caused segmentation failures in three comparison frames. Two downscaled photos are public, while the other 17 are unavailable in the repository, preventing full replay of this check. It is not an accuracy benchmark.

This is the measurement side of the same materials workflow as formulation-bo: inspect dispersion, record properties, then inform subsequent formulations.

[Exploratory results and limitations](https://github.com/mthogeon0731/dcv-vision#real-micrograph-check)

## Research Experience

**Undergraduate Researcher**  
CEPL, Sogang University  
Sep 2026 – Present

Contributing to research on flash distillation processes and reliability.

**Undergraduate Researcher**  
Electronic & Ionic Materials Engineering Lab, Sogang University  
Jun 2026 – Oct 2026

Worked on [formulation-bo](https://github.com/mthogeon0731/formulation-bo) and [dcv-vision](https://github.com/mthogeon0731/dcv-vision) for Bayesian optimization of thermal interface material formulations and image-based characterization of particle dispersion.

## Shipped Apps

- **[BO Lab](https://apps.apple.com/hk/app/bo-lab/id6800664866)** — An iOS app translating the optimization workflow into experiment recommendations, shared records, and Pareto visualization. The public [research core](https://github.com/mthogeon0731/formulation-bo) covers the optimizer; the complete app source is not published there.
- **[PODO](https://apps.apple.com/kr/app/podo/id6768158603)** — An iOS group scheduling app with availability-overlap and candidate-date voting. Its [repository](https://github.com/mthogeon0731/PODO) is a selected code showcase.
- **[CLOCK OUT.exe / 퇴근](https://apps.apple.com/kr/app/id6768991274)** — An iOS shared-counter app. Its [code showcase](https://github.com/mthogeon0731/CLOCK-OUT) documents click batching, broadcast moderation, and server-side authorization.

Separate prototype: [SYNC](https://github.com/mthogeon0731/SYNC), a calendar exploring LLM-assisted memory and scheduling.

## Community

Inaugural cohort participant in OpenAI Student Collective, one of 15 students selected in South Korea.

## Methods / Tools

**Research methods:** reaction–diffusion modeling, image metrology, grouped model evaluation, residual GPs, Bayesian optimization, and conditional uncertainty propagation.

**Implementation:** Python, NumPy, SciPy, pandas, scikit-learn, OpenCV, Matplotlib; TypeScript, React Native/Expo, Next.js, and FastAPI. Development includes AI-assisted coding, with implementation choices and validation limits documented in the repositories.

## Contact

[mt.hogeon0731@gmail.com](mailto:mt.hogeon0731@gmail.com)

한국어 요약: 서강대학교 화공생명공학과 학부생입니다. CEPL(2026년 9월–현재)에서 flash distillation 공정과 신뢰성 중심 연구에 참여하고 있으며, Electronic & Ionic Materials Engineering Lab(2026년 6월–10월)에서 학부연구생으로 formulation-bo와 dcv-vision을 수행했습니다. OpenAI Student Collective 첫 기수의 대한민국 선발 학생 15명 중 한 명입니다. 출시 앱은 BO Lab, PODO, 퇴근이며 SYNC는 별도 프로토타입입니다.
