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
ms.openlocfilehash: 292892ef572bd63fff055aeed88073573fadb934
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491836"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="472b3-102">Integração com aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="472b3-102">Integrating with COM Applications</span></span>
<span data-ttu-id="472b3-103">Serviços Windows Communication Foundation (WCF) podem ser integrados diretamente em seu código existente usando o moniker de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="472b3-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="472b3-104">O moniker de serviço pode ser usado em ambientes de desenvolvimento todo com base no intervalo de COM, como Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="472b3-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="472b3-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="472b3-105">In This Section</span></span>  
 [<span data-ttu-id="472b3-106">Visão geral da integração de aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="472b3-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="472b3-107">Fornece uma visão geral das partes principais do processo de integração.</span><span class="sxs-lookup"><span data-stu-id="472b3-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="472b3-108">Como registrar e configurar um moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="472b3-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="472b3-109">Para usar o moniker de serviço WCF em um aplicativo COM, registrar os tipos de atributo necessários com e configurar o aplicativo COM e o moniker com a configuração de associação necessária.</span><span class="sxs-lookup"><span data-stu-id="472b3-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="472b3-110">Como usar o moniker de serviço do Windows Communication Foundation sem Registro</span><span class="sxs-lookup"><span data-stu-id="472b3-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="472b3-111">Explica como obter a definição de contrato na forma de um documento WSDL Web Services Definition Language () ou de um ponto de extremidade do WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="472b3-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="472b3-112">Como usar um moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="472b3-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="472b3-113">Descreve como chamar um exemplo do WCF usando um moniker de WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="472b3-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="472b3-114">Como usar um moniker de serviço com contratos de troca de metadados</span><span class="sxs-lookup"><span data-stu-id="472b3-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="472b3-115">Descreve como chamar um exemplo do WCF usando um moniker WCF que especifica um ponto de extremidade Mex.</span><span class="sxs-lookup"><span data-stu-id="472b3-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="472b3-116">Como especificar as credenciais de segurança de canal</span><span class="sxs-lookup"><span data-stu-id="472b3-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="472b3-117">O moniker de serviço WCF oferece suporte a `IChannelCredentials` interface que permite uma variedade de métodos alternativos para especificar credenciais de canal.</span><span class="sxs-lookup"><span data-stu-id="472b3-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="472b3-118">Referência</span><span class="sxs-lookup"><span data-stu-id="472b3-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="472b3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="472b3-119">See Also</span></span>  
 [<span data-ttu-id="472b3-120">Integração de aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="472b3-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
