# All-About-Dowhy
![](https://www.microsoft.com/en-us/research/uploads/prod/2018/08/SCS-MS-Research_20180816_1400x788_DoWhy_T2-5b7b4771617f2-1024x576.png)

[Microsoft Research Blog]( https://www.microsoft.com/en-us/research/blog/dowhy-a-library-for-causal-inference)|[Video Tutorial](https://note.microsoft.com/MSR-Webinar-DoWhy-Library-Registration-On-Demand.html)|[Arxiv Paper]( https://arxiv.org/abs/2011.04216)|[Arxiv Paper (GCM-extension)](https://arxiv.org/abs/2206.06821)|[Slides]( https://www2.slideshare.net/AmitSharma315/dowhy-an-endtoend-library-for-causal-inference)

Causal Inference를 위해 MS에서 개발한 DoWhy와 Causal Inference의 4가지 단계를 소개합니다.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install Dowhy.

```bash
pip install dowhy
#or conda install dowhy
```

## Usage

```python
import dowhy

# load dataset
data = pd.read_csv('data.csv')
# create a causal model
model = CausalModel(
   data = data,
   treatment = 'treatment'
   outcome = 'y_factual'
   common_cause=["x"+str(i) for i in range(1, 26)]
)
model.view_model()

# identify  model
identified_estimand = model.identify_effect(proceed_when_unidentifiable=True, method_name="maximal-adjustment")

# estimate model
estimate = model.estimate_effect(identified_estimand,
   method_name = "backdoor.propensity_score_matching"
)

# refute model
refute_results = model.refute_estimate(identified_estimand, estimate,
   method_name="random_common_cause"
)
```

## Contributing
[@jhbale11](https://github.com/jhbale11)

## License
[MIT](https://choosealicense.com/licenses/mit/)
