---
title: Логическая и физическая архитектура
description: Общие сведения о различиях между логическими и физическими архитектурами.
ms.date: 09/20/2018
ms.openlocfilehash: c269369e9b5391e8d25ece46e6b08e34a82fbbba
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673061"
---
# <a name="logical-architecture-versus-physical-architecture"></a><span data-ttu-id="6bc1f-103">Логическая и физическая архитектура</span><span class="sxs-lookup"><span data-stu-id="6bc1f-103">Logical architecture versus physical architecture</span></span>

<span data-ttu-id="6bc1f-104">Теперь будет полезно отвлечься и обсудить разницу между логической и физической архитектурами, а также поговорить о том, какое значение она имеет для проектирования приложений на основе микрослужб.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-104">It's useful at this point to stop and discuss the distinction between logical architecture and physical architecture, and how this applies to the design of microservice-based applications.</span></span>

<span data-ttu-id="6bc1f-105">Начнем с того, что для разработки микрослужб не требуется использовать какую-либо определенную технологию.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-105">To begin, building microservices doesn't require the use of any specific technology.</span></span> <span data-ttu-id="6bc1f-106">Например, для создания архитектуры на основе микрослужб контейнеры Docker не являются обязательными.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-106">For instance, Docker containers aren't mandatory to create a microservice-based architecture.</span></span> <span data-ttu-id="6bc1f-107">Микрослужбы могут также выполняться как обычные процессы.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-107">Those microservices could also be run as plain processes.</span></span> <span data-ttu-id="6bc1f-108">Микрослужбы образуют логическую архитектуру.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-108">Microservices is a logical architecture.</span></span>

<span data-ttu-id="6bc1f-109">Кроме того, даже несмотря на то, что микрослужба может быть физически реализована как отдельная служба, процесс или контейнер (для простоты именно такой подход был выбран в первоначальной версии приложения [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), подобное соответствие бизнес-микрослужбы и физической службы или контейнера не всегда является обязательным, особенно при разработке больших и сложных приложений, состоящих из десятков и даже сотен служб.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-109">Moreover, even when a microservice could be physically implemented as a single service, process, or container (for simplicity's sake, that's the approach taken in the initial version of [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), this parity between business microservice and physical service or container isn't necessarily required in all cases when you build a large and complex application composed of many dozens or even hundreds of services.</span></span>

<span data-ttu-id="6bc1f-110">Именно в этом проявляется различие между логической и физической архитектурами приложения.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-110">This is where there's a difference between an application's logical architecture and physical architecture.</span></span> <span data-ttu-id="6bc1f-111">Логическая архитектура и логические границы системы необязательно должны в точности совпадать с физической архитектурой или архитектурой развертывания.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-111">The logical architecture and logical boundaries of a system do not necessarily map one-to-one to the physical or deployment architecture.</span></span> <span data-ttu-id="6bc1f-112">Они могут совпадать, но часто это не так.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-112">It can happen, but it often doesn't.</span></span>

<span data-ttu-id="6bc1f-113">Возможно, вы уже выделили определенные микрослужбы или ограниченные контексты, но это не значит, что оптимальный способ их реализации всегда состоит в создании отдельной службы (например, веб-API ASP.NET) или отдельного контейнера Docker для каждой микрослужбы.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-113">Although you might have identified certain business microservices or Bounded Contexts, it doesn't mean that the best way to implement them is always by creating a single service (such as an ASP.NET Web API) or single Docker container for each business microservice.</span></span> <span data-ttu-id="6bc1f-114">Правило, гласящее, что каждая микрослужба должна реализовываться как отдельная служба или контейнер, является слишком строгим.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-114">Having a rule saying each business microservice has to be implemented using a single service or container is too rigid.</span></span>

<span data-ttu-id="6bc1f-115">Таким образом, бизнес-микрослужба или ограниченный контекст — это компонент логической архитектуры, которая может совпадать с физической архитектурой, а может, и нет.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-115">Therefore, a business microservice or Bounded Context is a logical architecture that might coincide (or not) with physical architecture.</span></span> <span data-ttu-id="6bc1f-116">Важным требованием является автономность микрослужбы или ограниченного контекста, которая обеспечивает независимое управление версиями, развертывание и масштабирование кода и состояния.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-116">The important point is that a business microservice or Bounded Context must be autonomous by allowing code and state to be independently versioned, deployed, and scaled.</span></span>

<span data-ttu-id="6bc1f-117">Как показано на рис. 4-8, микрослужба каталога может состоять из нескольких служб или процессов.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-117">As Figure 4-8 shows, the catalog business microservice could be composed of several services or processes.</span></span> <span data-ttu-id="6bc1f-118">Это может быть несколько служб на основе веб-интерфейсов API ASP.NET или любых других служб, использующих протокол HTTP либо иной протокол.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-118">These could be multiple ASP.NET Web API services or any other kind of services using HTTP or any other protocol.</span></span> <span data-ttu-id="6bc1f-119">Более того, эти службы могут использовать одни и те же данные при условии, что они связаны с одной предметной областью.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-119">More importantly, the services could share the same data, as long as these services are cohesive with respect to the same business domain.</span></span>

![Схема микрослужбы каталога, содержащей службу API, службу поиска и базу данных SQL Server.](./media/image8.png)

<span data-ttu-id="6bc1f-121">**Рис. 4-8**.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-121">**Figure 4-8**.</span></span> <span data-ttu-id="6bc1f-122">Бизнес-микрослужба с несколькими физическими службами</span><span class="sxs-lookup"><span data-stu-id="6bc1f-122">Business microservice with several physical services</span></span>

<span data-ttu-id="6bc1f-123">Службы в примере имеют общую модель данных, так как служба на основе веб-интерфейса API обращается к тем же данным, что и служба поиска.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-123">The services in the example share the same data model because the Web API service targets the same data as the Search service.</span></span> <span data-ttu-id="6bc1f-124">Поэтому в физической реализации микрослужбы вы разделяете эту функциональность, чтобы каждую из внутренних служб можно было масштабировать по мере необходимости.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-124">So, in the physical implementation of the business microservice, you're splitting that functionality so you can scale each of those internal services up or down as needed.</span></span> <span data-ttu-id="6bc1f-125">Например, для службы на основе веб-интерфейса API обычно может требоваться больше экземпляров, чем для службы поиска, или наоборот.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-125">Maybe the Web API service usually needs more instances than the Search service, or vice versa.</span></span>

<span data-ttu-id="6bc1f-126">Короче говоря, логическая архитектура микрослужб не всегда должна совпадать с архитектурой физического развертывания.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-126">In short, the logical architecture of microservices doesn't always have to coincide with the physical deployment architecture.</span></span> <span data-ttu-id="6bc1f-127">Каждый раз, когда в этом руководстве упоминается микрослужба, имеется в виду бизнес-микрослужба или логическая микрослужба, которой могут соответствовать одна или несколько (физических) служб.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-127">In this guide, whenever we mention a microservice, we mean a business or logical microservice that could map to one or more (physical) services.</span></span> <span data-ttu-id="6bc1f-128">В большинстве случаев это будет одна служба, но их может быть и больше.</span><span class="sxs-lookup"><span data-stu-id="6bc1f-128">In most cases, this will be a single service, but it might be more.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6bc1f-129">[Назад](data-sovereignty-per-microservice.md)
>[Вперед](distributed-data-management.md)</span><span class="sxs-lookup"><span data-stu-id="6bc1f-129">[Previous](data-sovereignty-per-microservice.md)
[Next](distributed-data-management.md)</span></span>