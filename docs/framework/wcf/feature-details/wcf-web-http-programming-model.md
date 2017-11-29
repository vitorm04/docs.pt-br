---
title: "Modelo de programação WCF Web HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f51ad4a228de0a4a2fae0fb325d045bb09263b3d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="17d76-102">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="17d76-102">WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="17d76-103">O modelo de programação do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP que permite aos desenvolvedores expor operações de serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a pontos de extremidade não SOAP.</span><span class="sxs-lookup"><span data-stu-id="17d76-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="17d76-104">Os tópicos nesta seção examinam o recurso em detalhes.</span><span class="sxs-lookup"><span data-stu-id="17d76-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17d76-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="17d76-105">In This Section</span></span>  
 [<span data-ttu-id="17d76-106">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="17d76-106">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="17d76-107">Fornece uma visão geral do Modelo de programação do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="17d76-107">Provides an overview of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="17d76-108">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="17d76-108">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="17d76-109">Discute o Modelo de Programação do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP e como ele funciona.</span><span class="sxs-lookup"><span data-stu-id="17d76-109">Discusses the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="17d76-110">Como: criar um serviço de Web HTTP WCF básico</span><span class="sxs-lookup"><span data-stu-id="17d76-110">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="17d76-111">Descreve como gravar um serviço básico que expõe um ponto de extremidade de não SOAP.</span><span class="sxs-lookup"><span data-stu-id="17d76-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="17d76-112">Como: expor um contrato para clientes SOAP e da Web</span><span class="sxs-lookup"><span data-stu-id="17d76-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="17d76-113">Descreve como gravar um serviço básico que expõe o mesmo contrato para os clientes SOAP e não SOAP.</span><span class="sxs-lookup"><span data-stu-id="17d76-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="17d76-114">UriTemplate e UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="17d76-114">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="17d76-115">Descreve como controlar o URI usando <xref:System.UriTemplate> e <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="17d76-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="17d76-116">Suporte ao cache para serviços do WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="17d76-116">Caching Support for WCF Web HTTP Services</span></span>](../../../../docs/framework/wcf/feature-details/caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="17d76-117">Descreve como especificar o comportamento do cache para um serviço WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="17d76-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="17d76-118">Formatação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="17d76-118">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 <span data-ttu-id="17d76-119">Descreve como especificar o formato da resposta de um serviço WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="17d76-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="17d76-120">Tratamento de erros HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="17d76-120">WCF Web HTTP Error Handling</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-error-handling.md)  
 <span data-ttu-id="17d76-121">Descreve como retornar erros para clientes WCF Web que incluem os códigos de status do HTTP e dados de erro adicionais definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="17d76-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="17d76-122">Chamando um serviço estilo REST do serviço WCF</span><span class="sxs-lookup"><span data-stu-id="17d76-122">Calling a REST-style service from a WCF service</span></span>](../../../../docs/framework/wcf/feature-details/calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="17d76-123">Descreve como chamar um serviço de estilo REST de dentro de um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="17d76-123">Describes how to call a REST-style service from inside a WCF service.</span></span>
