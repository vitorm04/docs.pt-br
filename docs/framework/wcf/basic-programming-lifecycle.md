---
title: Ciclo de vida de programação básica
description: Saiba mais sobre as tarefas para criar um aplicativo WCF. O WCF permite que os aplicativos se comuniquem no mesmo computador, em redes ou em diferentes plataformas de aplicativos.
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: c672827fff780fd263f5355520bb6ccf02bb902e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245525"
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="3c183-104">Ciclo de vida de programação básica</span><span class="sxs-lookup"><span data-stu-id="3c183-104">Basic Programming Lifecycle</span></span>
<span data-ttu-id="3c183-105">O Windows Communication Foundation (WCF) permite que os aplicativos se comuniquem se estão no mesmo computador, na Internet ou em diferentes plataformas de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3c183-105">Windows Communication Foundation (WCF) enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="3c183-106">Este tópico descreve as tarefas que são necessárias para criar um aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="3c183-106">This topic outlines the tasks that are required to build a WCF application.</span></span> <span data-ttu-id="3c183-107">Para um aplicativo de exemplo funcional, consulte [introdução tutorial](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="3c183-107">For a working sample application, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="3c183-108">As tarefas básicas</span><span class="sxs-lookup"><span data-stu-id="3c183-108">The Basic Tasks</span></span>  
 <span data-ttu-id="3c183-109">As tarefas básicas a serem executadas são, em ordem:</span><span class="sxs-lookup"><span data-stu-id="3c183-109">The basic tasks to perform are, in order:</span></span>  
  
1. <span data-ttu-id="3c183-110">Defina o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c183-110">Define the service contract.</span></span> <span data-ttu-id="3c183-111">Um contrato de serviço especifica a assinatura de um serviço, os dados que ele troca e outros dados necessários contratuais.</span><span class="sxs-lookup"><span data-stu-id="3c183-111">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> <span data-ttu-id="3c183-112">Para obter mais informações, consulte [Designing Service Contracts](designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3c183-112">For more information, see [Designing Service Contracts](designing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="3c183-113">Implemente o contrato.</span><span class="sxs-lookup"><span data-stu-id="3c183-113">Implement the contract.</span></span> <span data-ttu-id="3c183-114">Para implementar um contrato de serviço, crie uma classe que implemente o contrato e especifique comportamentos personalizados que o tempo de execução deve ter.</span><span class="sxs-lookup"><span data-stu-id="3c183-114">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> <span data-ttu-id="3c183-115">Para obter mais informações, consulte [implementando contratos de serviço](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3c183-115">For more information, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
3. <span data-ttu-id="3c183-116">Configure o serviço especificando pontos de extremidade e outras informações de comportamento.</span><span class="sxs-lookup"><span data-stu-id="3c183-116">Configure the service by specifying endpoints and other behavior information.</span></span> <span data-ttu-id="3c183-117">Para obter mais informações, consulte [Configurando serviços](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c183-117">For more information, see [Configuring Services](configuring-services.md).</span></span>  
  
4. <span data-ttu-id="3c183-118">Hospede o serviço.</span><span class="sxs-lookup"><span data-stu-id="3c183-118">Host the service.</span></span> <span data-ttu-id="3c183-119">Para obter mais informações, consulte [serviços de hospedagem](hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c183-119">For more information, see [Hosting Services](hosting-services.md).</span></span>  
  
5. <span data-ttu-id="3c183-120">Compilar um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="3c183-120">Build a client application.</span></span> <span data-ttu-id="3c183-121">Para obter mais informações, consulte [Building clients](building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3c183-121">For more information, see [Building Clients](building-clients.md).</span></span>  
  
 <span data-ttu-id="3c183-122">Embora os tópicos nesta seção sigam essa ordem, alguns cenários não começam no início.</span><span class="sxs-lookup"><span data-stu-id="3c183-122">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="3c183-123">Por exemplo, se você quiser criar um cliente para um serviço pré-existente, comece na etapa 5.</span><span class="sxs-lookup"><span data-stu-id="3c183-123">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="3c183-124">Ou, se você estiver criando um serviço que outras pessoas usarão, você pode ignorar a etapa 5.</span><span class="sxs-lookup"><span data-stu-id="3c183-124">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="3c183-125">Quando estiver familiarizado com o desenvolvimento de contratos de serviço, você também poderá ler [introdução à extensibilidade](introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="3c183-125">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](introduction-to-extensibility.md).</span></span> <span data-ttu-id="3c183-126">Se você tiver problemas com seu serviço, marque [início rápido de solução de problemas do WCF](wcf-troubleshooting-quickstart.md) para ver se outros têm problemas semelhantes ou similares.</span><span class="sxs-lookup"><span data-stu-id="3c183-126">If you have problems with your service, check [WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c183-127">Veja também</span><span class="sxs-lookup"><span data-stu-id="3c183-127">See also</span></span>

- [<span data-ttu-id="3c183-128">Implementando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="3c183-128">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
