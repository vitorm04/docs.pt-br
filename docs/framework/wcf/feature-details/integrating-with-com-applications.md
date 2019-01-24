---
title: Integração com aplicativos COM
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: 8fa802ce20bfde3579258a5d34bc5d7f68aaaea3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657396"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="8eec5-102">Integração com aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="8eec5-102">Integrating with COM Applications</span></span>
<span data-ttu-id="8eec5-103">Serviços Windows Communication Foundation (WCF) podem ser integrados diretamente em seu código existente, usando o moniker de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="8eec5-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="8eec5-104">O moniker de serviço pode ser usado em ambientes um amplo intervalo de COM base em desenvolvimento, como Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="8eec5-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8eec5-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8eec5-105">In This Section</span></span>  
 [<span data-ttu-id="8eec5-106">Visão geral da integração de aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="8eec5-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="8eec5-107">Fornece uma visão geral das principais partes do processo de integração.</span><span class="sxs-lookup"><span data-stu-id="8eec5-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="8eec5-108">Como: Registrar e configurar um Moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="8eec5-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="8eec5-109">Para usar o moniker de serviço WCF dentro de um aplicativo COM, registrar os tipos de atributo necessários com e configurar o aplicativo COM e o moniker com a configuração de associação necessários.</span><span class="sxs-lookup"><span data-stu-id="8eec5-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="8eec5-110">Como: Use o Moniker de serviço do Windows Communication Foundation sem registro</span><span class="sxs-lookup"><span data-stu-id="8eec5-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="8eec5-111">Explica como obter a definição do contrato na forma de um documento WSDL Web Services Definition Language () ou de um ponto de extremidade do WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="8eec5-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="8eec5-112">Como: Usar um Moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="8eec5-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="8eec5-113">Descreve como chamar um exemplo do WCF usando um moniker de WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="8eec5-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="8eec5-114">Como: Usar um Moniker de serviço com contratos de troca de metadados</span><span class="sxs-lookup"><span data-stu-id="8eec5-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="8eec5-115">Descreve como chamar um exemplo do WCF usando um moniker WCF que especifica um ponto de extremidade de Mex.</span><span class="sxs-lookup"><span data-stu-id="8eec5-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="8eec5-116">Como: Especifique as credenciais de segurança de canal</span><span class="sxs-lookup"><span data-stu-id="8eec5-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="8eec5-117">O moniker de serviço do WCF dá suporte a `IChannelCredentials` interface que permite que uma variedade de métodos alternativos para especificar credenciais de canal.</span><span class="sxs-lookup"><span data-stu-id="8eec5-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8eec5-118">Referência</span><span class="sxs-lookup"><span data-stu-id="8eec5-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="8eec5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8eec5-119">See also</span></span>
- [<span data-ttu-id="8eec5-120">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="8eec5-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
