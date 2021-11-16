### 12.05_kubernetes_cni </br>
После работы с Flannel появилась необходимость обеспечить безопасность для приложения. Для этого лучше всего подойдет Calico.

### Задание 1: установить в кластер CNI плагин Calico
Для проверки других сетевых решений стоит поставить отличный от Flannel плагин — например, Calico. Требования:
установка производится через ansible/kubespray;
после применения следует настроить политику доступа к hello world извне.

-----------------------
1) Установлен кластер: 1 master + 1 worker </br>
Установка K8S по предыдущей работе 12.04:[README](https://github.com/murzinvit/12.04_kubernetes_install_part_2/blob/23a37632e3ec532f3a31b44cdf9c8af8089ea3b1/README.md)</br>
Используемый [inventory.ini](https://github.com/murzinvit/12.05_kubernetes_cni/blob/053af694c6c068b242a3ceabdf58684f9a147aa6/inventory/dev/inventory.ini) </br>
![Calico_install_ok](https://github.com/murzinvit/screen/blob/fa21d71f37702ef759f85ee150577416696b09d9/Kuber_1master_1worker.jpg) </br>
![Calico_system_pods](https://github.com/murzinvit/screen/blob/56268a2f163c70395f098038b7fdb160f81df980/Kuber_get_nodes_from_kube-system.jpg) </br>
Запуск nginx: </br>
![Create_pod](https://github.com/murzinvit/screen/blob/9de2b6bef0a12d5e1e15c2b01e916d7e8bbbc4e9/Kuber_create_pod.jpg) </br>
Результат: </br>
![Get_pod](https://github.com/murzinvit/screen/blob/b40ce00a077380c45c62546009d689bcef5b82c2/Kuber_get_pod_nginx.jpg) </br>
Опупликовать pod: </br>
![Exposed_pod](https://github.com/murzinvit/screen/blob/0f24065b94823259c912f5e31ac5204daf43beca/Kubectl_exposed_pod.jpg) </br>
Разрешить ingress и egress к поду с меткой - lbl-k8s-nginx: </br>
![Ellow_ing_egress](https://github.com/murzinvit/screen/blob/3f5d8c613b718f69d596a92e68ea34559cc39cfe/Kuber_allow_ingress_egress.jpg) </br>
Запретить весь трафик к поду: </br>
![screen](https://github.com/murzinvit/screen/blob/dfdd7216e6e4969fffd146f6cd7c85ff5bd8fdc1/Kuber_deny_ingress_egress.jpg) </br>

### Задание 2: изучить, что запущено по умолчанию: </br>
Самый простой способ — проверить командой calicoctl get . Для проверки стоит получить список нод, ipPool и profile. </br> 
Требования: </br>
Установить утилиту calicoctl; </br>
Получить 3 вышеописанных типа в консоли.</br>

### Рабочие заметки: </br>
Хороша статья про политики: https://habr.com/ru/company/flant/blog/443190/ </br>
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
Demo-policy: https://docs.projectcalico.org/security/tutorials/kubernetes-policy-basic </br>
Подробная и понятная серия статей по k8s: https://russianblogs.com/article/3334128666/ </br>
Полезные команды: </br>
Зайти в pod: </br>
`kubectl exec k8s-mysql -it -- bash`  </br>
`kubectl get pod k8s-mysql -o template --template={{.status.podIP}}` </br>
`kubectl run -t -i --rm --image amouat/network-utils testnet bash`  - контейнер в кластере kubernetes с утилитами для теста сети </br>
`kubectl get pods -o yaml` - Для просмотра label, развёрнутый вывод о подах </br>
