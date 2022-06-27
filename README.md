# Wprowadzenie do Kubernetes

Prezentacja z PHPers Summit 2022.

# Zasoby dodatkowe

- Dokumentacja Kubernetes WEB:https://kubernetes.io/docs/home/
- Dokumentacja Kubernetes CLI:	`kubectl explain namespace`
- Kubernetes in Action edycja I: https://www.manning.com/books/kubernetes-in-action

## Wymagane narzędzia

### kubectl

Narzędzie służy do obsługi wszystkich klastrów k8s. Wymagane do pracy sysops/devops.

- Install kubectl on Linux https://kubernetes.io/docs/tasks/tools/install-kubectl-linux
- Install kubectl on macOS https://kubernetes.io/docs/tasks/tools/install-kubectl-macos
- Install kubectl on Windows https://kubernetes.io/docs/tasks/tools/install-kubectl-windows

Przykładowy sposób użycia:

```
kubectl get namespaces # pobranie listy namespace'ów
kubectl get pods # pobranie listy podów w aktualnym ns
```

## Narzędzia opcjonalne

### Lens

GUI/IDE do przeglądania i zarządzania zasobami Kubernetes.

Oferuje szeroki zakres funkcjonalności, od przeglądania zasobów, analizę metryk Prometheus, aż po logowanie się na konkretne kontenery i nody.

Do pobrania z <https://k8slens.dev/>. Aplikacja jest darmowa, płatne są tylko dodatkowe funkcjonalności zespołowe.

### Helm

Do pobrania z https://github.com/helm/helm/releases - polecenie konsolowe służące do kontrolowania narzędzi helm

Opcjonalne do pracy sysops, wymagane do pracy devops.

## Zalecana konfiguracja

### auto completion

Autokompletowanie pozwala uniknąć żmudnego wpisywania poleceń. Przykładowo:

```
# zamiast pisać
kubectl -n summit describe pod phpers-0
# z autokompletowaniem można wpisać
kubectl -n s<TAB> des<TAB> pod p<TAB>
```

Instalacja w bash poprzez dopisanie do ~/.bashrc:
```
source <(kubectl completion bash)
```

Obslugiwany jest też zsh, inne narzędzia np. helm, flux posiadają autokompletowanie ustawianie w taki sam sposób.

### przełączanie pomiędzy namespace'ami

```
# kcd - ustawienie domyślnego namespace
# przyklad uzycia: kcd ingress; kubectl get pods
alias kcd='kubectl config set-context $(kubectl config current-context) --namespace '
```

Lub alternatywnie - narzędzie kubens+kubectx: https://github.com/ahmetb/kubectx
