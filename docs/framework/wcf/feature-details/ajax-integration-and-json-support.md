---
title: Integração de AJAX e suporte para JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 0b392044db3fbc926bf77ac305ece294880216d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488823"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="53456-102">Integração de AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="53456-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="53456-103">O suporte do Windows Communication Foundation (WCF) para ASP.NET assíncrona AJAX JavaScript and XML () e o formato de dados (JSON JavaScript Object Notation) permitem que os serviços WCF expor operações para clientes AJAX.</span><span class="sxs-lookup"><span data-stu-id="53456-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="53456-104">Clientes AJAX são páginas da Web que executa o código JavaScript e acesso a estes serviços WCF usando solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="53456-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="53456-105">Os tópicos nesta seção fornecem informações sobre esse suporte e como implementá-la.</span><span class="sxs-lookup"><span data-stu-id="53456-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="53456-106">Para obter mais informações sobre o ASP.NET AJAX e sua integração com o ASP.NET 2.0, consulte [visão geral do ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="53456-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53456-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="53456-107">In This Section</span></span>  
 [<span data-ttu-id="53456-108">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="53456-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="53456-109">Descreve como um serviço WCF pode ser exposto para clientes AJAX adicionando o ponto de extremidade AJAX apropriado tanto por meio da configuração ou usando uma fábrica de host de serviço personalizada para gerar um host de serviço que configura o ponto de extremidade AJAX automaticamente.</span><span class="sxs-lookup"><span data-stu-id="53456-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="53456-110">Criando serviços WCF AJAX sem ASP.NET</span><span class="sxs-lookup"><span data-stu-id="53456-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="53456-111">Descreve como criar um serviço WCF sem o uso de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="53456-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="53456-112">Suporte para JSON e outros formatos de transferência de dados</span><span class="sxs-lookup"><span data-stu-id="53456-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="53456-113">Descreve o suporte do formato JSON normalmente usado (em vez de XML) para mensagens com os serviços ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="53456-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="53456-114">Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="53456-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="53456-115">Descreve como migrar um serviço Web habilitado para AJAX do ASP.NET para um serviço Web WCF.</span><span class="sxs-lookup"><span data-stu-id="53456-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53456-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53456-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="53456-117">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="53456-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
