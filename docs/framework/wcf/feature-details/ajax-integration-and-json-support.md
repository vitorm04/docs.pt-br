---
title: Integração de AJAX e suporte para JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 54942386bb4fb88e72a86b5e25f12cee4776a126
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625634"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="90800-102">Integração de AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="90800-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="90800-103">O suporte do Windows Communication Foundation (WCF) para ASP.NET Asynchronous JavaScript and XML (AJAX) e o formato de dados de objeto notação JSON (JavaScript) permitem que os serviços WCF exponham operações a clientes AJAX.</span><span class="sxs-lookup"><span data-stu-id="90800-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="90800-104">Clientes AJAX são páginas da Web executando o código JavaScript e o acesso a esses serviços WCF usando solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="90800-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="90800-105">Os tópicos nesta seção fornecem informações sobre esse suporte e sobre como implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="90800-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="90800-106">Para obter mais informações sobre o ASP.NET AJAX e sua integração com o ASP.NET 2.0, consulte [visão geral do ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="90800-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90800-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="90800-107">In This Section</span></span>  
 [<span data-ttu-id="90800-108">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="90800-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="90800-109">Descreve como um serviço WCF pode ser exposto a clientes AJAX, adicionando o ponto de extremidade apropriado do AJAX seja por meio da configuração ou usando uma fábrica de host de serviço personalizada para gerar um host de serviço que configura o ponto de extremidade AJAX automaticamente.</span><span class="sxs-lookup"><span data-stu-id="90800-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="90800-110">Criando serviços WCF AJAX sem ASP.NET</span><span class="sxs-lookup"><span data-stu-id="90800-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="90800-111">Descreve como criar um serviço do WCF sem usar o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="90800-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="90800-112">Suporte para JSON e outros formatos de transferência de dados</span><span class="sxs-lookup"><span data-stu-id="90800-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="90800-113">Descreve o suporte do formato JSON normalmente usado (em vez de XML) para mensagens com os serviços do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="90800-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="90800-114">Como: Migrar serviços Web do ASP.NET habilitado para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="90800-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="90800-115">Descreve como migrar um serviço Web do ASP.NET AJAX ativado para um serviço Web WCF.</span><span class="sxs-lookup"><span data-stu-id="90800-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90800-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90800-116">See also</span></span>
- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="90800-117">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="90800-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
