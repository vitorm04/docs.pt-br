---
title: "Integração de AJAX e suporte para JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4889c88dab77759f854da0069bb300d63ebb1a08
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="bf243-102">Integração de AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="bf243-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="bf243-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] suporte para JavaScript assíncrona do ASP.NET e XML (AJAX) e o formato de dados JSON JavaScript Object Notation () permite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços expor operações para clientes AJAX.</span><span class="sxs-lookup"><span data-stu-id="bf243-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="bf243-104">Clientes AJAX são páginas da Web que executa o código JavaScript e acessá-los [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços usando solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="bf243-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="bf243-105">Os tópicos nesta seção fornecem informações sobre esse suporte e como implementá-la.</span><span class="sxs-lookup"><span data-stu-id="bf243-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="bf243-106">O ASP.NET AJAX e sua integração com o ASP.NET 2.0, consulte [visão geral do ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="bf243-106"> ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf243-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bf243-107">In This Section</span></span>  
 [<span data-ttu-id="bf243-108">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="bf243-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="bf243-109">Descreve como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço pode ser exposto para clientes AJAX adicionando o ponto de extremidade AJAX apropriado por meio da configuração ou usando uma fábrica de host de serviço personalizado para gerar um host de serviço que configura o ponto de extremidade AJAX automaticamente.</span><span class="sxs-lookup"><span data-stu-id="bf243-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="bf243-110">Criando serviços WCF AJAX sem ASP.NET</span><span class="sxs-lookup"><span data-stu-id="bf243-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="bf243-111">Descreve como criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço sem o uso de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="bf243-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="bf243-112">Suporte para JSON e outros dados formatos de transferência</span><span class="sxs-lookup"><span data-stu-id="bf243-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="bf243-113">Descreve o suporte do formato JSON normalmente usado (em vez de XML) para mensagens com os serviços ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="bf243-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="bf243-114">Como: migrar serviços Web do ASP.NET AJAX habilitado para o WCF</span><span class="sxs-lookup"><span data-stu-id="bf243-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="bf243-115">Descreve como migrar um serviço da Web habilitado para AJAX do ASP.NET para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço Web.</span><span class="sxs-lookup"><span data-stu-id="bf243-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf243-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf243-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="bf243-117">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="bf243-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
