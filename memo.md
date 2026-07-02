
```bash
# chart 를 압축 해서 docs/ 폴더 안에 저장하기
helm package . -d docs/
# index.yaml 파일을 docs. 폴더 안에 자동 생성하기
helm repo index docs --url https://jinsw1.github.io/helm-microservice/

# add, commit, push 진행
git add .
git commit -m "~~~~"
git push

```

```bash
# 현재 등록된 helm 저장소 목록 조회
helm repo ls

[user1@master step24_microservice_helm]$ helm repo ls
NAME                    URL                                               
cnpg                    https://cloudnative-pg.github.io/charts           
argo                    https://argoproj.github.io/argo-helm              
my-repo                 https://jinsw1.github.io/my-helm-chart/           
prometheus-community    https://prometheus-community.github.io/helm-charts

# 방금 만든 helm chart의 위치를 helm 저장소로 등록하기
helm repo add msa https://jinsw1.github.io/helm-microservice/
# 저장소에 있는 내용을 모두 받아올수 있도록 동기화
helm repo update


# 저장소에 어떤 chart가 들어 있는지 검색
helm search repo msa

[user1@master step24_microservice_helm]$ helm search repo msa
NAME                    CHART VERSION   APP VERSION     DESCRIPTION          
msa/msa-platform        0.1.0           1.0.0           index + market + post


# install 해보기
helm install msa-release msa/msa-platform -n msa --create-namespace
```

