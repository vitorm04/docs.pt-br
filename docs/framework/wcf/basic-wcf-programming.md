---
title: "Programação de WCF básica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa43705fd20a60512ca4c460bb3048220aa1e193
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="74bbe-102">Programação de WCF básica</span><span class="sxs-lookup"><span data-stu-id="74bbe-102">Basic WCF Programming</span></span>
<span data-ttu-id="74bbe-103">Esta seção apresenta os conceitos básicos para criar aplicativos do [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74bbe-103">This section presents the fundamentals for creating [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="74bbe-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="74bbe-104">In This Section</span></span>  
 <span data-ttu-id="74bbe-105">[Basic Programming Lifecycle](../../../docs/framework/wcf/basic-programming-lifecycle.md) (Ciclo de vida de programação básica)</span><span class="sxs-lookup"><span data-stu-id="74bbe-105">[Basic Programming Lifecycle](../../../docs/framework/wcf/basic-programming-lifecycle.md)</span></span>  
 <span data-ttu-id="74bbe-106">Descreve o ciclo de vida de criar, compilar e implantar o serviço do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] e os aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="74bbe-106">Describes the lifecycle of designing, building, and deploying [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service and client applications.</span></span>  
  
 <span data-ttu-id="74bbe-107">[Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md) (Serviços de design e implantação)</span><span class="sxs-lookup"><span data-stu-id="74bbe-107">[Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md)</span></span>  
 <span data-ttu-id="74bbe-108">Descreve como criar e implementar um contrato de serviço, escolher um padrão de troca de mensagem, especificar um contrato de falha e outros aspectos básicos de serviços.</span><span class="sxs-lookup"><span data-stu-id="74bbe-108">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>  
  
 <span data-ttu-id="74bbe-109">[Configuring Services](../../../docs/framework/wcf/configuring-services.md) (Configurando serviços)</span><span class="sxs-lookup"><span data-stu-id="74bbe-109">[Configuring Services](../../../docs/framework/wcf/configuring-services.md)</span></span>  
 <span data-ttu-id="74bbe-110">Descreve como configurar um serviço do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para oferecer suporte aos requisitos do contrato, personalizar o comportamento do tempo de execução local e indicar o endereço para publicar o serviço.</span><span class="sxs-lookup"><span data-stu-id="74bbe-110">Describes how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>  
  
 <span data-ttu-id="74bbe-111">[Hosting Services](../../../docs/framework/wcf/hosting-services.md) (Hospedando serviços)</span><span class="sxs-lookup"><span data-stu-id="74bbe-111">[Hosting Services](../../../docs/framework/wcf/hosting-services.md)</span></span>  
 <span data-ttu-id="74bbe-112">Descreve os conceitos básicos de serviços de hospedagem em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74bbe-112">Describes the basics of hosting services in an application.</span></span>  
  
 <span data-ttu-id="74bbe-113">[Building Clients](../../../docs/framework/wcf/building-clients.md) (Compilando clientes)</span><span class="sxs-lookup"><span data-stu-id="74bbe-113">[Building Clients](../../../docs/framework/wcf/building-clients.md)</span></span>  
 <span data-ttu-id="74bbe-114">Descreve como obter metadados de serviços, convertê-los no código do cliente do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], manipular problemas de segurança e compilar, configurar e hospedar um cliente do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74bbe-114">Describes how to obtain metadata from services, convert that into [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client code, handle security issues, and build, configure, and host an [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span>  
  
 <span data-ttu-id="74bbe-115">[Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md) (Introdução à extensibilidade)</span><span class="sxs-lookup"><span data-stu-id="74bbe-115">[Introduction to Extensibility](../../../docs/framework/wcf/introduction-to-extensibility.md)</span></span>  
 <span data-ttu-id="74bbe-116">Descreve como estender o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] para criar soluções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="74bbe-116">Describes how to extend [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to create custom solutions.</span></span>  
  
 <span data-ttu-id="74bbe-117">[WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) (Início rápido de solução de problemas do WCF)</span><span class="sxs-lookup"><span data-stu-id="74bbe-117">[WCF Troubleshooting Quickstart](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)</span></span>  
 <span data-ttu-id="74bbe-118">Descreve alguns dos problemas mais comuns que ocorrem, o que você pode fazer para resolvê-los e onde localizar mais informações sobre o problema.</span><span class="sxs-lookup"><span data-stu-id="74bbe-118">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>  
  
 <span data-ttu-id="74bbe-119">[WCF and ASP.NET Web API](../../../docs/framework/wcf/wcf-and-aspnet-web-api.md) (WCF e API Web ASP.NET)</span><span class="sxs-lookup"><span data-stu-id="74bbe-119">[WCF and ASP.NET Web API](../../../docs/framework/wcf/wcf-and-aspnet-web-api.md)</span></span>  
 <span data-ttu-id="74bbe-120">Discutir as duas tecnologias, como elas se relacionam e quando usá-las.</span><span class="sxs-lookup"><span data-stu-id="74bbe-120">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="74bbe-121">Referência</span><span class="sxs-lookup"><span data-stu-id="74bbe-121">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="74bbe-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="74bbe-122">Related Sections</span></span>  
 [<span data-ttu-id="74bbe-123">Requisitos do sistema</span><span class="sxs-lookup"><span data-stu-id="74bbe-123">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)  
  
 <span data-ttu-id="74bbe-124">[Conceptual Overview](../../../docs/framework/wcf/conceptual-overview.md) (Visão geral conceitual)</span><span class="sxs-lookup"><span data-stu-id="74bbe-124">[Conceptual Overview](../../../docs/framework/wcf/conceptual-overview.md)</span></span>  
  
 [<span data-ttu-id="74bbe-125">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="74bbe-125">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 <span data-ttu-id="74bbe-126">[Guidelines and Best Practices](../../../docs/framework/wcf/guidelines-and-best-practices.md) (Diretrizes e práticas recomendadas)</span><span class="sxs-lookup"><span data-stu-id="74bbe-126">[Guidelines and Best Practices](../../../docs/framework/wcf/guidelines-and-best-practices.md)</span></span>  
  
 [<span data-ttu-id="74bbe-127">Ferramentas do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="74bbe-127">Windows Communication Foundation Tools</span></span>](../../../docs/framework/wcf/tools.md)  
  
 <span data-ttu-id="74bbe-128">[Windows Communication Foundation Samples](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91) (Amostras do Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="74bbe-128">[Windows Communication Foundation Samples](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)</span></span>  
  
 [<span data-ttu-id="74bbe-129">Introdução</span><span class="sxs-lookup"><span data-stu-id="74bbe-129">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
  
 [<span data-ttu-id="74bbe-130">Hospedagem do IIS utilizando código embutido</span><span class="sxs-lookup"><span data-stu-id="74bbe-130">IIS Hosting Using Inline Code</span></span>](../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)  
  
 [<span data-ttu-id="74bbe-131">Hospedagem interna</span><span class="sxs-lookup"><span data-stu-id="74bbe-131">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
