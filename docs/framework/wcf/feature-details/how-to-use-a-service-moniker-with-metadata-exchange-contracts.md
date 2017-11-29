---
title: "Como usar um Moniker de serviço com contratos de intercâmbio de metadados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed6ce9b87a5e2d8945a57110c02cce8024439f14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="66771-102">Como usar um Moniker de serviço com contratos de intercâmbio de metadados</span><span class="sxs-lookup"><span data-stu-id="66771-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="66771-103">Depois de desenvolver algumas novas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, você pode decidir que deseja ser capaz de chamar esses serviços de um script ou um aplicativo do Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="66771-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="66771-104">Um método seria gerar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly de cliente, registre o assembly com, instalar o assembly no GAC e faça referência os tipos COM o código do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66771-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="66771-105">Quando você distribui o aplicativo, você precisa distribuir o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly cliente também.</span><span class="sxs-lookup"><span data-stu-id="66771-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="66771-106">O usuário terá, em seguida, registre o assembly de cliente do WCF com e colocá-lo no GAC.</span><span class="sxs-lookup"><span data-stu-id="66771-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="66771-107">Interoperabilidade COM também permite que você faça o mesmo serviço chama sem depender de um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly cliente.</span><span class="sxs-lookup"><span data-stu-id="66771-107"> COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="66771-108">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker permite que você possa chamar qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço em qualquer linguagem compatível COM o com (Visual Basic, VBScript, Visual Basic for Applications (VBA) e assim por diante), especificando um ponto de extremidade do exchange (Mex) de metadados URI que usa o moniker de serviço para extrair informações de tipo sobre o serviço.</span><span class="sxs-lookup"><span data-stu-id="66771-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="66771-109">Este tópico descreve como chamar o guia de Introdução [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de exemplo usando um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker que especifica um ponto de extremidade Mex.</span><span class="sxs-lookup"><span data-stu-id="66771-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66771-110">Os tipos definidos pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assembly cliente nunca são instanciados.</span><span class="sxs-lookup"><span data-stu-id="66771-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="66771-111">O assembly é usado apenas para metadados.</span><span class="sxs-lookup"><span data-stu-id="66771-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="66771-112">Usando o moniker de serviço com um endereço Mex</span><span class="sxs-lookup"><span data-stu-id="66771-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="66771-113">Criar o exemplo de Introdução e usar o Internet Explorer para navegar até a URL (http://localhost/ServiceModelSamples/Service.svc) para garantir que o serviço está funcionando.</span><span class="sxs-lookup"><span data-stu-id="66771-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="66771-114">Crie um script do Visual Basic ou o aplicativo do Visual Basic que contém o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="66771-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="66771-115">Execute o script ou aplicativo do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="66771-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="66771-116">O serviço de chamada deve expor um ponto de extremidade Mex para o moniker para ser capaz de ler os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="66771-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="66771-117">Para obter mais informações, consulte [como: publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="66771-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="66771-118">Se o identificador de origem está malformado ou se o serviço está indisponível, a chamada para `GetObject` retornará um erro dizendo "Sintaxe inválida".</span><span class="sxs-lookup"><span data-stu-id="66771-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="66771-119">Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="66771-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66771-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66771-120">See Also</span></span>  
 [<span data-ttu-id="66771-121">Como: usar o Moniker de serviço do Windows Communication Foundation sem registro</span><span class="sxs-lookup"><span data-stu-id="66771-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="66771-122">Como: usar um Moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="66771-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
