---
title: Integração de AJAX e suporte para JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 3054c3c6faa8dfe621c706d8df031c23d497da0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576506"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="824bf-102">Integração de AJAX e suporte para JSON</span><span class="sxs-lookup"><span data-stu-id="824bf-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="824bf-103">O suporte do Windows Communication Foundation (WCF) para JavaScript e XML assíncronos ASP.NET (AJAX) e o formato de dados JavaScript Object Notation (JSON) permitem que os serviços WCF exponham operações a clientes AJAX.</span><span class="sxs-lookup"><span data-stu-id="824bf-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="824bf-104">Os clientes AJAX são páginas da Web que executam código JavaScript e acessam esses serviços WCF usando solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="824bf-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="824bf-105">Os tópicos nesta seção fornecem informações sobre esse suporte e sobre como implementá-lo.</span><span class="sxs-lookup"><span data-stu-id="824bf-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="824bf-106">Para obter mais informações sobre o ASP.NET AJAX e sua integração com o ASP.NET 2,0, consulte [visão geral do ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="824bf-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="824bf-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="824bf-107">In This Section</span></span>  
 [<span data-ttu-id="824bf-108">Criando serviços do WCF para o AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="824bf-108">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="824bf-109">Descreve como um serviço WCF pode ser exposto a clientes AJAX adicionando o ponto de extremidade AJAX apropriado por meio da configuração ou usando uma fábrica de host de serviço personalizada para gerar um host de serviço que configura o ponto de extremidade AJAX automaticamente.</span><span class="sxs-lookup"><span data-stu-id="824bf-109">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="824bf-110">Criando serviços WCF AJAX sem ASP.NET</span><span class="sxs-lookup"><span data-stu-id="824bf-110">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="824bf-111">Descreve como criar um serviço WCF sem usar o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="824bf-111">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="824bf-112">Suporte para JSON e outros formatos de transferência de dados</span><span class="sxs-lookup"><span data-stu-id="824bf-112">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="824bf-113">Descreve o suporte do formato JSON normalmente usado (em vez de XML) para mensagens com serviços AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="824bf-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="824bf-114">Como migrar serviços habilitados para AJAX ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="824bf-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="824bf-115">Descreve como migrar um serviço Web ASP.NET habilitado para AJAX para um serviço Web WCF.</span><span class="sxs-lookup"><span data-stu-id="824bf-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="824bf-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="824bf-116">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="824bf-117">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="824bf-117">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
