---
title: 'Como: usar um moniker de serviço com contratos de intercâmbio de metadados'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 367cbd4a2bfbde3d4ab0a74eeeaf5d5f5662ec27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59319827"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="41748-102">Como: usar um moniker de serviço com contratos de intercâmbio de metadados</span><span class="sxs-lookup"><span data-stu-id="41748-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="41748-103">Após desenvolver alguns novos serviços do WCF, você pode decidir o que você deseja ser capaz de chamar esses serviços de um script ou um aplicativo Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="41748-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="41748-104">Um método seria gerar um assembly de cliente do WCF, registre o assembly com, instale o assembly no GAC e, em seguida, referenciar os tipos COM seu código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41748-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="41748-105">Quando você distribui o aplicativo, você precisará distribuir o assembly de cliente WCF também.</span><span class="sxs-lookup"><span data-stu-id="41748-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="41748-106">O usuário, em seguida, será preciso registrar o assembly de cliente do WCF com e colocá-lo no GAC.</span><span class="sxs-lookup"><span data-stu-id="41748-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="41748-107">Interoperabilidade de COM do WCF também permite que você faça as mesmas chamadas de serviço sem depender de um assembly de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="41748-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="41748-108">O WCF moniker permite que você chame qualquer serviço WCF em qualquer linguagem compatível COM (Visual Basic, VBScript, Visual Basic for Applications (VBA) e assim por diante), especificando um ponto de extremidade do exchange (Mex) de metadados URI que o moniker de serviço usa para extrair o tipo informações sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="41748-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="41748-109">Este tópico descreve como chamar o exemplo de Introdução ao WCF usando um moniker WCF que especifica um ponto de extremidade de Mex.</span><span class="sxs-lookup"><span data-stu-id="41748-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41748-110">Os tipos definidos pelo assembly de cliente de WCF, na verdade, nunca são instanciados.</span><span class="sxs-lookup"><span data-stu-id="41748-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="41748-111">O assembly é usado apenas para metadados.</span><span class="sxs-lookup"><span data-stu-id="41748-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="41748-112">Usando o moniker de serviço com um endereço Mex</span><span class="sxs-lookup"><span data-stu-id="41748-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="41748-113">Criar o exemplo de Introdução e usar o Internet Explorer para navegar até a URL (http://localhost/ServiceModelSamples/Service.svc) para garantir que o serviço está funcionando.</span><span class="sxs-lookup"><span data-stu-id="41748-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="41748-114">Crie um script do Visual Basic ou o aplicativo Visual Basic que contém o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="41748-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="41748-115">Execute o script ou aplicativo do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41748-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41748-116">O serviço que você está chamando deve expor um ponto de extremidade de Mex para o moniker a ser capaz de ler os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="41748-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="41748-117">Para obter mais informações, confira [Como: Publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="41748-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="41748-118">Se o moniker está mal formado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro informando que "Sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="41748-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="41748-119">Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="41748-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41748-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41748-120">See also</span></span>

- [<span data-ttu-id="41748-121">Como: Use o Moniker de serviço do Windows Communication Foundation sem registro</span><span class="sxs-lookup"><span data-stu-id="41748-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="41748-122">Como: Usar um Moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="41748-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
