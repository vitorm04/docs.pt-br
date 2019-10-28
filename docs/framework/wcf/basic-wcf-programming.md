---
title: Programação de WCF básica
ms.date: 03/30/2017
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
ms.openlocfilehash: eff565fa18e3360170584395adcf2a3e7029ac07
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960927"
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="d0a77-102">Programação básica do WCF</span><span class="sxs-lookup"><span data-stu-id="d0a77-102">Basic WCF programming</span></span>

<span data-ttu-id="d0a77-103">Esta seção apresenta os conceitos básicos para a criação de aplicativos Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d0a77-103">This section presents the fundamentals for creating Windows Communication Foundation (WCF) applications.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d0a77-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d0a77-104">In this section</span></span>

 <span data-ttu-id="d0a77-105">\ de [ciclo de vida de programação básica](basic-programming-lifecycle.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-105">[Basic Programming Lifecycle](basic-programming-lifecycle.md)\</span></span>
 <span data-ttu-id="d0a77-106">Descreve o ciclo de vida de criação, criação e implantação de aplicativos cliente e serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="d0a77-106">Describes the lifecycle of designing, building, and deploying WCF service and client applications.</span></span>

 <span data-ttu-id="d0a77-107">[Serviços de design e implantação](designing-and-implementing-services.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-107">[Designing and Implementing Services](designing-and-implementing-services.md)</span></span>\
 <span data-ttu-id="d0a77-108">Descreve como criar e implementar um contrato de serviço, escolher um padrão de troca de mensagem, especificar um contrato de falha e outros aspectos básicos de serviços.</span><span class="sxs-lookup"><span data-stu-id="d0a77-108">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>

 <span data-ttu-id="d0a77-109">[Configurando serviços](configuring-services.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-109">[Configuring Services](configuring-services.md)</span></span>\
 <span data-ttu-id="d0a77-110">Descreve como configurar um serviço WCF para dar suporte aos requisitos de contrato, personalizar o comportamento de tempo de execução local e indicar o endereço para publicar o serviço.</span><span class="sxs-lookup"><span data-stu-id="d0a77-110">Describes how to configure a WCF service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>

 <span data-ttu-id="d0a77-111">[Serviços de hospedagem](hosting-services.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-111">[Hosting Services](hosting-services.md)</span></span>\
 <span data-ttu-id="d0a77-112">Descreve os conceitos básicos de serviços de hospedagem em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d0a77-112">Describes the basics of hosting services in an application.</span></span>

 <span data-ttu-id="d0a77-113">[Compilando clientes](building-clients.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-113">[Building Clients](building-clients.md)</span></span>\
 <span data-ttu-id="d0a77-114">Descreve como obter metadados de serviços, convertê-los em código de cliente WCF, lidar com problemas de segurança e criar, configurar e hospedar um cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="d0a77-114">Describes how to obtain metadata from services, convert that into WCF client code, handle security issues, and build, configure, and host a WCF client.</span></span>

 <span data-ttu-id="d0a77-115">[Introdução à extensibilidade](introduction-to-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-115">[Introduction to Extensibility](introduction-to-extensibility.md)</span></span>\
 <span data-ttu-id="d0a77-116">Descreve como estender o WCF para criar soluções personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d0a77-116">Describes how to extend WCF to create custom solutions.</span></span>

 <span data-ttu-id="d0a77-117">[Início rápido de solução de problemas do WCF](wcf-troubleshooting-quickstart.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-117">[WCF Troubleshooting Quickstart](wcf-troubleshooting-quickstart.md)</span></span>\
 <span data-ttu-id="d0a77-118">Descreve alguns dos problemas mais comuns que ocorrem, o que você pode fazer para resolvê-los e onde localizar mais informações sobre o problema.</span><span class="sxs-lookup"><span data-stu-id="d0a77-118">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>

 <span data-ttu-id="d0a77-119">[WCF e ASP.NET Web API](wcf-and-aspnet-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="d0a77-119">[WCF and ASP.NET Web API](wcf-and-aspnet-web-api.md)</span></span>\
 <span data-ttu-id="d0a77-120">Discutir as duas tecnologias, como elas se relacionam e quando usá-las.</span><span class="sxs-lookup"><span data-stu-id="d0a77-120">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>

## <a name="reference"></a><span data-ttu-id="d0a77-121">Referência</span><span class="sxs-lookup"><span data-stu-id="d0a77-121">Reference</span></span>

- <xref:System.ServiceModel>
- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Description>

## <a name="related-sections"></a><span data-ttu-id="d0a77-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d0a77-122">Related sections</span></span>

- [<span data-ttu-id="d0a77-123">Visão geral conceitual</span><span class="sxs-lookup"><span data-stu-id="d0a77-123">Conceptual Overview</span></span>](conceptual-overview.md)
- [<span data-ttu-id="d0a77-124">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="d0a77-124">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="d0a77-125">Diretrizes e práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="d0a77-125">Guidelines and Best Practices</span></span>](guidelines-and-best-practices.md)
- [<span data-ttu-id="d0a77-126">Ferramentas do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d0a77-126">Windows Communication Foundation Tools</span></span>](tools.md)
- [<span data-ttu-id="d0a77-127">Exemplos de Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="d0a77-127">Windows Communication Foundation (WCF) samples</span></span>](./samples/index.md)
- [<span data-ttu-id="d0a77-128">Introdução</span><span class="sxs-lookup"><span data-stu-id="d0a77-128">Getting Started</span></span>](./samples/getting-started-sample.md)
- [<span data-ttu-id="d0a77-129">Hospedagem do IIS utilizando código embutido</span><span class="sxs-lookup"><span data-stu-id="d0a77-129">IIS Hosting Using Inline Code</span></span>](./samples/iis-hosting-using-inline-code.md)
- [<span data-ttu-id="d0a77-130">Auto-hospedagem</span><span class="sxs-lookup"><span data-stu-id="d0a77-130">Self-Host</span></span>](./samples/self-host.md)
