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
ms.openlocfilehash: dc3bbe0ee72ca5583b1e52a61c914ad866a22a05
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596804"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="c3ef1-102">Integração com aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="c3ef1-102">Integrating with COM Applications</span></span>
<span data-ttu-id="c3ef1-103">Os serviços do Windows Communication Foundation (WCF) podem ser integrados diretamente ao seu código existente usando o moniker do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="c3ef1-104">O moniker do serviço pode ser usado em uma ampla variedade de ambientes de desenvolvimento baseados em COM, como o Office VBA, Visual Basic 6,0 ou Visual C++ 6,0.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3ef1-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c3ef1-105">In This Section</span></span>  
 [<span data-ttu-id="c3ef1-106">Visão geral da integração com aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="c3ef1-106">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="c3ef1-107">Fornece uma visão geral das principais partes do processo de integração.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="c3ef1-108">Como registrar e configurar um Moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="c3ef1-108">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="c3ef1-109">Para usar o moniker do serviço WCF em um aplicativo COM, registre os tipos atribuídos necessários com com e configure o aplicativo COM e o moniker com a configuração de associação necessária.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="c3ef1-110">Como usar o Moniker de serviço do Windows Communication Foundation sem registro</span><span class="sxs-lookup"><span data-stu-id="c3ef1-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="c3ef1-111">Explica como obter a definição do contrato na forma de um documento WSDL (Web Services Definition Language) ou de um ponto de extremidade WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="c3ef1-112">Como usar um Moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="c3ef1-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="c3ef1-113">Descreve como chamar um exemplo do WCF usando um moniker WSDL do WCF.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="c3ef1-114">Como usar um moniker de serviço com contratos de troca de metadados</span><span class="sxs-lookup"><span data-stu-id="c3ef1-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="c3ef1-115">Descreve como chamar um exemplo do WCF usando um moniker do WCF que especifica um ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="c3ef1-116">Como especificar credenciais de segurança de canal</span><span class="sxs-lookup"><span data-stu-id="c3ef1-116">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="c3ef1-117">O moniker do serviço WCF dá suporte à `IChannelCredentials` interface que permite um intervalo de métodos alternativos para especificar credenciais de canal.</span><span class="sxs-lookup"><span data-stu-id="c3ef1-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c3ef1-118">Referência</span><span class="sxs-lookup"><span data-stu-id="c3ef1-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="c3ef1-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3ef1-119">See also</span></span>

- [<span data-ttu-id="c3ef1-120">Integração com aplicativos COM+</span><span class="sxs-lookup"><span data-stu-id="c3ef1-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
