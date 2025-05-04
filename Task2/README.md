# Задание 2. Динамическое масштабирование контейнеров

1. Запустим minikube

minikube start --driver=docker

2. Применим конфигурации

kubectl apply -f deployments.yaml
kubectl apply -f service.yaml
kubectl apply -f hpa.yaml

minikube service scaletestapp-service --url

3. Включим сбор метрик 

minikube addons enable metrics-server

4. Запустим нагрузочный тест с предусловиями - 1_config_load_test.png - скриншот настроек теста.
Запуск теста - 2_start_load_test.png

5. Результаты - при повышении нагрузки сработало горизонтальное масштабирование и был создан дополнительный под - 3_up_to_2_pods.png
6. После завершения теста конфигурация автоматически изменилась - дополнительный под был удалён - 4_down_to_1_pod.png
