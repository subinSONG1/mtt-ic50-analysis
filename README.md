# H₂O₂ 세포독성 MTT Assay — IC50 분석

HEK293T 세포에 H₂O₂를 농도별(0–1000 µM)로 처리하고 MTT assay로 생존율을 측정,
4-모수 로지스틱(4PL) 회귀로 **IC50**를 산출하는 분석 노트북.

## 결과
- **IC50 ≈ 173.8 µM** (Hill ≈ 1.16 / Top = 100% 고정 / Bottom 0–30% 제한)
- 결과 그래프: `MTT assay.png`

![IC50 dose-response](MTT%20assay.png)

## 파일 구성
```
.
├── mtt.ipynb                  # 분석 노트북
├── 0611데이터분석용.xlsx       # 원자료 (시트 '570' / '630')
├── MTT assay.png              # 결과 그래프 (노트북 Run All 시 갱신)
├── README.md
├── requirements.txt
└── .gitignore
```

## 실행 방법
```bash
git clone <이 저장소 주소>
cd <저장소 폴더>
pip install -r requirements.txt   # jupyter 미설치 시: pip install jupyter
jupyter notebook mtt.ipynb        # 또는 VS Code에서 열기
```
> 노트북은 **저장소 최상위 폴더에서 실행**해야 상대경로(`0611데이터분석용.xlsx`)가 맞습니다.
> `Run All` 하면 동일한 IC50와 그래프가 그대로 재현됩니다.

## 데이터 설명
- `570` 시트: MTT formazan 흡광도(신호) / `630` 시트: 참조 파장(배경 보정) → 분석은 **(570 − 630)** 사용
- 행 B~G: 농도당 **6개 반복 well**
- 0 µM 무처리 대조군은 2열로 측정했고, 그중 1열만 baseline(100% 기준)으로 사용
