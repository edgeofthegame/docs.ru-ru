---
title: Модернизация приложений с помощью мониторинга и данных телеметрии
description: Модернизировать существующих приложений .NET с помощью Azure Cloud and Windows Containers | Модернизировать приложения с помощью мониторинга и телеметрии
ms.date: 04/30/2018
ms.openlocfilehash: 5bffb336234f63dca150acc9ef31f9efa2e3937b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578177"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a>Модернизация приложений с помощью мониторинга и данных телеметрии

При запуске приложения в рабочей среде очень важно иметь представление о том, как выполняется приложение. Выполняется ли он на высоком уровне? Являются ли пользователи ошибками, или приложение является стабильным и надежным? Вам требуется полнофункциональный мониторинг производительности, мощные средства оповещения и панели мониторинга, чтобы обеспечить доступность и выполнение приложения в соответствии с ожидаемым. Кроме того, необходимо иметь возможность быстро увидеть, есть ли проблемы, определить, сколько клиентов затрагивается, и выполнить анализ основных причин, чтобы найти и устранить проблему.

## <a name="monitor-your-application-with-application-insights"></a>Мониторинг приложения с помощью Application Insights

Application Insights — это расширяемая служба управления производительностью приложений (APM) для веб-разработчиков, работающих на нескольких платформах. Используйте его для мониторинга интерактивного веб-приложения. Application Insights автоматически обнаруживает аномалии производительности. Она включает мощные средства анализа, помогающие диагностировать проблемы и позволяющие понять, какие пользователи фактически делают с вашим приложением. Application Insights призвана помочь в постоянном повышении производительности и удобства использования. Она работает для приложений на различных платформах, включая .NET, Node. js и J2EE, независимо от того, размещена ли она локально или в облаке. Application Insights интегрируется с процессами DevOps и имеет точки подключения к различным средствам разработки.

На рис. 4-10 показан пример того, как Application Insights наблюдает за приложением и как он отражает эти сведения на панели мониторинга.

![Панель мониторинга Application Insights мониторинга](./media/image10.png)

> **Рис. 4-10.** Панель мониторинга Application Insights мониторинга

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a>Мониторинг инфраструктуры DOCKER с помощью Log Analytics и решения для мониторинга контейнеров

[Log Analytics Azure](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) является частью [Microsoft Azure общего решения мониторинга](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview). Это также служба в Operations [Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview). Log Analytics наблюдает за облачными и локальными средами (OMS для локальной среды), чтобы обеспечить доступность и производительность. Он собирает данные, созданные ресурсами в облачной и локальной средах, а также из других средств мониторинга для обеспечения анализа в нескольких источниках.

В отношении журналов инфраструктуры Azure Log Analytics, как служба Azure, принимает данные журналов и метрик из других служб Azure (через [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), виртуальные машины Azure, контейнеры DOCKER и локальные или другие облачные инфраструктуры. Log Analytics предлагает гибкий поиск по журналам и готовый анализ на основе этих данных. Он предоставляет широкие средства, которые можно использовать для анализа данных в разных источниках, позволяя выполнять сложные запросы во всех журналах и получать Упреждающее оповещение на основе указанных условий. Вы даже можете получать пользовательские данные в централизованном репозитории Log Analytics, где их можно запрашивать и визуализировать. Вы также можете воспользоваться преимуществами встроенных решений Log Analytics, чтобы немедленно получить ценные сведения о безопасности и функциональности инфраструктуры.

Доступ к Log Analytics можно получить с помощью портала OMS или портал Azure, который работает в любом браузере, и предоставить доступ к параметрам конфигурации и нескольким средствам для анализа собранных данных и выполнения действий с ними.

[Решение для мониторинга контейнеров](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) в log Analytics помогает просматривать узлы контейнеров DOCKER и Windows и управлять ими в одном расположении. Решение показывает, какие контейнеры выполняются, какой образ контейнера выполняется и где работают контейнеры. Можно просмотреть подробные сведения аудита, в том числе команды, используемые с контейнерами. Вы также можете устранять неполадки в контейнерах, просматривая и выполняя поиск в централизованных журналах, не требуя удаленного просмотра узлов DOCKER или Windows. Можно найти контейнеры, которые могут быть шумами и потреблять избыточные ресурсы на узле. Кроме того, для контейнеров можно просматривать централизованное использование ЦП, памяти, хранилища и сети, а также сведения о производительности. На компьютерах под управлением Windows можно централизовать и сравнить журналы из контейнеров Windows Server, Hyper-V и DOCKER. Решение поддерживает следующие orchestration контейнеры:

- Docker Swarm

- DC/OS

- Kubernetes

- Red Hat OpenShift

На рис. 4-11 показаны связи между разными узлами контейнеров и агентами и OMS.

![Log Analytics решение для мониторинга контейнеров](./media/image11.png)

> **Рис. 4-11.** Log Analytics решение для мониторинга контейнеров

Решение для мониторинга контейнеров Log Analytics можно использовать для следующих задач:

- Ознакомьтесь со сведениями обо всех узлах контейнеров в одном расположении.

- Определите, какие контейнеры работают, какие образы они выполняются и где они работают.

- Ознакомьтесь с журналом аудита действий в контейнерах.

- Устранение неполадок путем просмотра и поиска централизованных журналов без удаленного входа на узлы DOCKER.

- Найдите контейнеры, которые могут быть "шумными соседями", и изменяйте ресурсы узла.

- Сведения о централизованном использовании ЦП, памяти, хранилища, сети и производительности для контейнеров.

### <a name="additional-resources"></a>Дополнительные ресурсы

- **Общие сведения о мониторинге в Microsoft Azure**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Что такое Azure Application Insights?**

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- **Что такое Log Analytics?**

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- **Решение для мониторинга контейнеров в Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- **Общие сведения о Azure Monitor**

<https://docs.microsoft.com/azure/azure-monitor/overview>

- **Что такое Operations Management Suite (OMS)?**

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

>[!div class="step-by-step"]
>[Назад](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[Вперед](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)