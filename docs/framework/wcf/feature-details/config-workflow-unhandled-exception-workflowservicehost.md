---
title: Практическое руководство. Как настроить поведение необработанного исключения рабочего процесса при помощи WorkflowServiceHost
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 3881d1af21dcc0c211c6738162360e522648d949
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593598"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Практическое руководство. Как настроить поведение необработанного исключения рабочего процесса при помощи WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> - это поведение, которое позволяет указать действие, предпринимаемое при возникновении необработанного исключения в рабочем процессе, размещенном в <xref:System.ServiceModel.Activities.WorkflowServiceHost>. В этом разделе описано, как настроить поведение в файле конфигурации.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Настройка WorkflowUnhandledExceptionBehavior  
  
1. Добавьте элемент <`workflowUnhandledException`> в `behavior` элемент <> в `serviceBehaviors` элементе <> с помощью `action` атрибута, чтобы указать действие, выполняемое при возникновении необработанного исключения, как показано в следующем примере.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > В предыдущем образце конфигурации используется упрощенная конфигурация. Дополнительные сведения см. в разделе [упрощенная конфигурация](../simplified-configuration.md).  
  
     Это поведение может быть настроено в коде, как показано в следующем примере.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action`Атрибуту `workflowUnhandledException` элемента <> можно присвоить одно из следующих значений:  
  
     **прерывания**  
     Прерывает работу экземпляра в памяти без обращения к сохраненному состоянию экземпляра (т.е. выполняет откат к последней сохраненной точке).  
  
     **abandonAndSuspend**  
     Прерывает работу экземпляра в памяти и обновляет приостанавливаемый сохраненный экземпляр.  
  
     **cancel**  
     Вызывает отмену обработчиков экземпляра, а затем завершает работу экземпляра в памяти, что может удалить его из хранилища экземпляров.  
  
     **заканчива**  
     Завершает работу экземпляра в памяти и удаляет его из хранилища экземпляров.  
  
     Дополнительные сведения о см <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> . в разделе [Расширяемость узла службы рабочих процессов](workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Дополнительно

- [Расширяемость узла службы рабочих процессов](workflow-service-host-extensibility.md)
- [Службы рабочего процесса](workflow-services.md)
