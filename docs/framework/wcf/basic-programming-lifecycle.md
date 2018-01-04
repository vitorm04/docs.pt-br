---
title: "Ciclo de vida de programação básica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f5c45cad0b1e4ae1aa6b1963e9acdab47cd9203
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-programming-lifecycle"></a><span data-ttu-id="60d5e-102">Ciclo de vida de programação básica</span><span class="sxs-lookup"><span data-stu-id="60d5e-102">Basic Programming Lifecycle</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="60d5e-103">permite que aplicativos se comuniquem se estiverem no mesmo computador, através da Internet, ou em diferentes plataformas de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60d5e-103"> enables applications to communicate whether they are on the same computer, across the Internet, or on different application platforms.</span></span> <span data-ttu-id="60d5e-104">Este tópico descreve as tarefas que são necessárias para criar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="60d5e-104">This topic outlines the tasks that are required to build a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="60d5e-105">Para um aplicativo de exemplo de funcionamento, consulte [Tutorial de Introdução](../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="60d5e-105">For a working sample application, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
## <a name="the-basic-tasks"></a><span data-ttu-id="60d5e-106">As tarefas básicas</span><span class="sxs-lookup"><span data-stu-id="60d5e-106">The Basic Tasks</span></span>  
 <span data-ttu-id="60d5e-107">As tarefas básicas para executar são, em ordem:</span><span class="sxs-lookup"><span data-stu-id="60d5e-107">The basic tasks to perform are, in order:</span></span>  
  
1.  <span data-ttu-id="60d5e-108">Defina o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="60d5e-108">Define the service contract.</span></span> <span data-ttu-id="60d5e-109">Um contrato de serviço Especifica a assinatura de um serviço, os dados trocados por ele e outros dados necessários ao contrato.</span><span class="sxs-lookup"><span data-stu-id="60d5e-109">A service contract specifies the signature of a service, the data it exchanges, and other contractually required data.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="60d5e-110">[Criar contratos de serviço](../../../docs/framework/wcf/designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="60d5e-110"> [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md).</span></span>  
  
2.  <span data-ttu-id="60d5e-111">Implemente o contrato.</span><span class="sxs-lookup"><span data-stu-id="60d5e-111">Implement the contract.</span></span> <span data-ttu-id="60d5e-112">Para implementar um contrato de serviço, crie uma classe que implementa o contrato e especificar comportamentos personalizados deve ter o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="60d5e-112">To implement a service contract, create a class that implements the contract and specify custom behaviors that the runtime should have.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="60d5e-113">[Implementando contratos de serviço](../../../docs/framework/wcf/implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="60d5e-113"> [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
3.  <span data-ttu-id="60d5e-114">Configure o serviço especificando pontos de extremidade e outras informações de comportamento.</span><span class="sxs-lookup"><span data-stu-id="60d5e-114">Configure the service by specifying endpoints and other behavior information.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="60d5e-115">[Configurando serviços](../../../docs/framework/wcf/configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="60d5e-115"> [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>  
  
4.  <span data-ttu-id="60d5e-116">Hospede o serviço.</span><span class="sxs-lookup"><span data-stu-id="60d5e-116">Host the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="60d5e-117">[Serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="60d5e-117"> [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
5.  <span data-ttu-id="60d5e-118">Crie um aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="60d5e-118">Build a client application.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="60d5e-119">[Criação de clientes](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="60d5e-119"> [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
 <span data-ttu-id="60d5e-120">Embora os tópicos nesta seção siga esta ordem, alguns cenários não começar do início.</span><span class="sxs-lookup"><span data-stu-id="60d5e-120">Although the topics in this section follow this order, some scenarios do not start at the beginning.</span></span> <span data-ttu-id="60d5e-121">Por exemplo, se você quiser criar um cliente para um serviço preexistente, você começa com a etapa 5.</span><span class="sxs-lookup"><span data-stu-id="60d5e-121">For example, if you want to build a client for a pre-existing service, you start at step 5.</span></span> <span data-ttu-id="60d5e-122">Ou, se você estiver criando um serviço que outras pessoas usarão, você pode ignorar a etapa 5.</span><span class="sxs-lookup"><span data-stu-id="60d5e-122">Or if you are building a service that others will use, you may skip step 5.</span></span>  
  
 <span data-ttu-id="60d5e-123">Quando você estiver familiarizado com o desenvolvimento de contratos de serviço, você também pode ler [Introdução à extensibilidade](../../../docs/framework/wcf/introduction-to-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="60d5e-123">Once you are familiar with developing service contracts, you can also read [Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md).</span></span> <span data-ttu-id="60d5e-124">Se você tiver problemas com seu serviço, verifique [início rápido de solução de problemas do WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) para ver se outras pessoas tenham problemas iguais ou semelhantes.</span><span class="sxs-lookup"><span data-stu-id="60d5e-124">If you have problems with your service, check [WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) to see whether others have the same or similar problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60d5e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60d5e-125">See Also</span></span>  
 [<span data-ttu-id="60d5e-126">Implementando contratos de serviço</span><span class="sxs-lookup"><span data-stu-id="60d5e-126">Implementing Service Contracts</span></span>](../../../docs/framework/wcf/implementing-service-contracts.md)
