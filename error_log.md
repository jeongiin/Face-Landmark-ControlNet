# `python gradio_landmark2image.py` 시 발생했던 라이브러리 에러

- 대부분은 pip install, conda install 명령으로 해결했으나 3분 이상 소요된 에러만 기록

1. `ModuleNotFoundError: No module named 'Crypto`
    - pip install 로 설치하면 해결되지 않았음, 환경이나 파이썬에 따라 다른 명령어로 설치해야 함
    - `conda install -c conda-forge pycryptodome` 로 설치 완료
2. `ModuleNotFoundError: No module named 'pytorch_lightning.`
   - `conda install lightning -c conda-forge` 로 설치 완료
3. `from pytorch_lightning.utilities.distributed import rank_zero_only`
   - 특정 등급의 함수를 호출하는데 사용할 수 있는 utils, 라이브러리가 꼬인 문제로 파악되어 우선 주석 처리한 채 진행
4. `models/control_sd15_landmarks.pth` 없음
   - github 코드에 없어 생긴 오류, [직접 다운](https://huggingface.co/georgefen/Face-Landmark-ControlNet/tree/main)받아서 models에 저장
5. `notimplementederror: no operator found for `memory_efficient_attention_forward`
   - xformers 와 버전 충돌 문제로 파악되어 우선 uninstall xformers 후 진행