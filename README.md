### 12.05_kubernetes_cni </br>
После работы с Flannel появилась необходимость обеспечить безопасность для приложения. Для этого лучше всего подойдет Calico.

#### Задание 1: установить в кластер CNI плагин Calico
Для проверки других сетевых решений стоит поставить отличный от Flannel плагин — например, Calico. Требования:
установка производится через ansible/kubespray;
после применения следует настроить политику доступа к hello world извне.

-----------------------
1) Установил кластер 1-мастер,1-worker,1-ингресс </br>
Установка K8S с calico: [README.md](https://github.com/murzinvit/12.04_kubernetes_install_part_2/blob/23a37632e3ec532f3a31b44cdf9c8af8089ea3b1/README.md) </br>
Используемый inventory.ini - https://github.com/murzinvit/12.05_kubernetes_cni/tree/main/inventory/dev  </br>
![Kuber_calico](https://github.com/murzinvit/screen/blob/2569383921ebc363ba4c6c4e394157f3b7cf6c0d/Kuber_calico_kube_system.jpg) </br>


#### Рабочие заметки: </br>
Понятно по k8s: http://linuxsql.ru/content/kubernetes-glazami-novichka </br>
Самая адекватная статья: https://mcs.mail.ru/help/ru_RU/k8s-net/k8s-ingress </br>
Calico статья: https://www.kryukov.biz/kubernetes/set-kubernetes-teoriya/calico/ </br>
Расшарить hello-world: https://kubernetes.io/docs/tutorials/stateless-application/expose-external-ip-address/ </br>
Микросервисное приложение в k8s + настройка ingress: https://serveradmin.ru/nastroyka-kubernetes/#_Ingress </br>
Статья по calico: https://habr.com/ru/company/flant/blog/485716/ </br>
Статья по хранилищам данных: https://serveradmin.ru/hranilishha-dannyh-persistent-volumes-v-kubernetes/ </br>
Работа с HELM: https://serveradmin.ru/rabota-s-helm-3-v-kubernetes/ </br>
Развёртывание MYSQL в k8s: https://itisgood.ru/2020/12/09/kak-razvernut-mysql-na-kubernetes/ </br>
Открытие доступа к приложению в k8s: https://kubernetes.io/ru/docs/tutorials/kubernetes-basics/expose/expose-intro/ </br>
Управление трафиком в Kubernetes-кластере с Calico: https://habr.com/ru/company/nixys/blog/494194/ </br>
Введение в kubectl(толковое объяснение от mail.ru): https://mcs.mail.ru/blog/kak-effektivnee-ispolzovat-kubectl-podrobnoe-rukovodstvo </br>
Полезные команды: 
Зайти в pod: </br>
kubectl exec k8s-mysql -it -- bash  </br>
kubectl get pod k8s-mysql -o template --template={{.status.podIP}} </br>
kubectl run -t -i --rm --image amouat/network-utils testnet bash  - контейнер в кластере kubernetes с утилитами для теста сети</br>
