---
title: 'Como: usar um moniker de serviço com contratos de intercâmbio de metadados'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 00aa1bbde95c0636391f213f830fc67b2dedf459
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968799"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="036bd-102">Como: usar um moniker de serviço com contratos de intercâmbio de metadados</span><span class="sxs-lookup"><span data-stu-id="036bd-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="036bd-103">Depois de desenvolver alguns novos serviços WCF, você pode decidir que deseja ser capaz de chamar esses serviços de um script ou de um aplicativo Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="036bd-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="036bd-104">Um método seria gerar um assembly de cliente WCF, registrar o assembly com COM, instalar o assembly no GAC e, em seguida, fazer referência aos tipos COM do seu código Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="036bd-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="036bd-105">Ao distribuir o aplicativo, você também precisará distribuir o assembly do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="036bd-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="036bd-106">O usuário precisará registrar o assembly do cliente WCF com com e colocá-lo no GAC.</span><span class="sxs-lookup"><span data-stu-id="036bd-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="036bd-107">A interoperabilidade COM do WCF também permite que você faça as mesmas chamadas de serviço sem depender de um assembly de cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="036bd-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="036bd-108">O moniker do WCF permite chamar qualquer serviço WCF de qualquer linguagem compatível COM COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) e assim por diante) especificando um URI de ponto de extremidade de intercâmbio de metadados (MEX) que o moniker do serviço usa para extrair o tipo informações sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="036bd-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="036bd-109">Este tópico descreve como chamar o Introdução exemplo do WCF usando um moniker do WCF que especifica um ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="036bd-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="036bd-110">Os tipos definidos pelo assembly do cliente WCF nunca são instanciados na verdade.</span><span class="sxs-lookup"><span data-stu-id="036bd-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="036bd-111">O assembly é usado somente para metadados.</span><span class="sxs-lookup"><span data-stu-id="036bd-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="036bd-112">Usando o moniker do serviço com um endereço MEX</span><span class="sxs-lookup"><span data-stu-id="036bd-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="036bd-113">Crie o introdução exemplo e use o Internet Explorer para navegar até sua URL http://localhost/ServiceModelSamples/Service.svc) (para garantir que o serviço esteja funcionando.</span><span class="sxs-lookup"><span data-stu-id="036bd-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="036bd-114">Crie um script de Visual Basic ou Visual Basic aplicativo que contenha o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="036bd-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="036bd-115">Execute o aplicativo Visual Basic ou o script.</span><span class="sxs-lookup"><span data-stu-id="036bd-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="036bd-116">O serviço que você está chamando deve expor um ponto de extremidade MEX para que o moniker possa ler os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="036bd-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="036bd-117">Para obter mais informações, confira [Como: Publicar metadados para um serviço usando um arquivo](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)de configuração.</span><span class="sxs-lookup"><span data-stu-id="036bd-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="036bd-118">Se o moniker estiver malformado ou se o serviço estiver indisponível, a `GetObject` chamada para retornará um erro dizendo "sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="036bd-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="036bd-119">Se você receber esse erro, verifique se o moniker que você está usando está correto e se o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="036bd-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036bd-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="036bd-120">See also</span></span>

- [<span data-ttu-id="036bd-121">Como: Usar o moniker do serviço Windows Communication Foundation sem registro</span><span class="sxs-lookup"><span data-stu-id="036bd-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="036bd-122">Como: Usar um moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="036bd-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
