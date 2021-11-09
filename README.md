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
Микросервисное приложение в k8s + настройка ingress: https://serveradmin.ru/nastroyka-kubernetes/#_Ingress </br>
