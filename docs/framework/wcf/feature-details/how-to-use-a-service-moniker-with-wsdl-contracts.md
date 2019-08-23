---
title: 'Como: usar um moniker de serviço com contratos WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: 80b0d034b92123862d0500106f81d4a566cac467
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968775"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="b5d42-102">Como: usar um moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="b5d42-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="b5d42-103">Há situações em que você talvez queira ter um cliente de interoperabilidade COM totalmente independente.</span><span class="sxs-lookup"><span data-stu-id="b5d42-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="b5d42-104">O serviço que você deseja chamar pode não expor um ponto de extremidade MEX e a DLL do cliente do WCF pode não estar registrada para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="b5d42-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="b5d42-105">Nesses casos, você pode criar um arquivo WSDL que descreve o serviço e passá-lo para o moniker do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="b5d42-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="b5d42-106">Este tópico descreve como chamar o Introdução exemplo do WCF usando um moniker WSDL do WCF.</span><span class="sxs-lookup"><span data-stu-id="b5d42-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="b5d42-107">Usando o moniker do serviço WSDL</span><span class="sxs-lookup"><span data-stu-id="b5d42-107">Using the WSDL service moniker</span></span>  
  
1. <span data-ttu-id="b5d42-108">Abra e crie a solução de exemplo GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="b5d42-108">Open and build the GettingStarted sample solution.</span></span>  
  
2. <span data-ttu-id="b5d42-109">Abra o Internet Explorer e navegue `http://localhost/ServiceModelSamples/Service.svc` até para certificar-se de que o serviço está funcionando.</span><span class="sxs-lookup"><span data-stu-id="b5d42-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3. <span data-ttu-id="b5d42-110">No arquivo Service.cs, adicione o seguinte atributo na classe CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="b5d42-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4. <span data-ttu-id="b5d42-111">Adicione um namespace de associação ao aplicativo de serviço. config:</span><span class="sxs-lookup"><span data-stu-id="b5d42-111">Add a binding namespace to the service App.config:</span></span>  

5. <span data-ttu-id="b5d42-112">Crie um arquivo WSDL para que o aplicativo Leia.</span><span class="sxs-lookup"><span data-stu-id="b5d42-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="b5d42-113">Como os namespaces foram adicionados nas etapas 3 e 4, você pode usar o IE para consultar toda a descrição WSDL do serviço navegando até `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="b5d42-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="b5d42-114">Em seguida, você pode salvar o arquivo do Internet Explorer como arquivo. xml.</span><span class="sxs-lookup"><span data-stu-id="b5d42-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="b5d42-115">Se você não especificar os namespaces nas etapas 3 e 4, o documento WSDL retornado da consulta da URL acima não será o WSDL completo.</span><span class="sxs-lookup"><span data-stu-id="b5d42-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="b5d42-116">O documento WSDL retornado incluirá várias instruções de importação que importam outros documentos WSDL.</span><span class="sxs-lookup"><span data-stu-id="b5d42-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="b5d42-117">Você precisará percorrer cada instrução de importação e criar o documento WSDL completo, combinando o WSDL retornado do serviço com o WSDL importado.</span><span class="sxs-lookup"><span data-stu-id="b5d42-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6. <span data-ttu-id="b5d42-118">Abra Visual Basic 6,0 e crie um novo arquivo Standard. exe.</span><span class="sxs-lookup"><span data-stu-id="b5d42-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="b5d42-119">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="b5d42-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
    ```  
    ' Open the WSDL contract file and read it all into the wsdlContract string.  
    Const ForReading = 1  
    Set objFSO = CreateObject("Scripting.FileSystemObject")  
    Set objFile = objFSO.OpenTextFile("c:\serviceWsdl.xml", ForReading)  
    wsdlContract = objFile.ReadAll  
    objFile.Close  
  
    ' Create a string for the service moniker including the content of the WSDL contract file.  
    wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
    wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
    wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
    wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
    ' Create the service moniker object.  
    Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
  
    ' Call the service operations using the moniker object.  
    MsgBox "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
    ```  
  
    > [!NOTE]
    > Se o moniker estiver malformado ou se o serviço não estiver disponível, `GetObject` a chamada para retornará um erro dizendo "sintaxe inválida".  <span data-ttu-id="b5d42-121">Se você receber esse erro, verifique se o moniker que você está usando está correto e se o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="b5d42-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7. <span data-ttu-id="b5d42-122">Execute o aplicativo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5d42-122">Run the Visual Basic application.</span></span> <span data-ttu-id="b5d42-123">Uma caixa de mensagem será exibida com os resultados da chamada de subtração (145, 76,54).</span><span class="sxs-lookup"><span data-stu-id="b5d42-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d42-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5d42-124">See also</span></span>

- [<span data-ttu-id="b5d42-125">Introdução</span><span class="sxs-lookup"><span data-stu-id="b5d42-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="b5d42-126">Visão geral da integração de aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="b5d42-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
