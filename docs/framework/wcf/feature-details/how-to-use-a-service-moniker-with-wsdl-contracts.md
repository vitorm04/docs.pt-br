---
title: 'Como: usar um moniker de serviço com contratos WSDL'
ms.date: 03/30/2017
ms.assetid: a88d9650-bb50-4f48-8c85-12f5ce98a83a
ms.openlocfilehash: b8729055c82e3ce1273e8a0cfae53a1f6d3c14e3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081658"
---
# <a name="how-to-use-a-service-moniker-with-wsdl-contracts"></a><span data-ttu-id="86d9c-102">Como: usar um moniker de serviço com contratos WSDL</span><span class="sxs-lookup"><span data-stu-id="86d9c-102">How to: Use a Service Moniker with WSDL Contracts</span></span>
<span data-ttu-id="86d9c-103">Essas são situações em que talvez você queira que um cliente de interoperabilidade COM totalmente independente.</span><span class="sxs-lookup"><span data-stu-id="86d9c-103">There are situations when you may want to have a completely self-contained COM Interop client.</span></span> <span data-ttu-id="86d9c-104">O serviço que você deseja chamar não pode expor um ponto de extremidade MEX e o cliente do WCF com que dll não pode ser registrado para interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="86d9c-104">The service you want to call may not expose a MEX endpoint, and the WCF client DLL may not be registered for COM interop.</span></span> <span data-ttu-id="86d9c-105">Nesses casos, você pode criar um arquivo WSDL que descreve o serviço e passá-la para o moniker de serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="86d9c-105">In these cases, you can create a WSDL file that describes the service and pass it into the WCF service moniker.</span></span> <span data-ttu-id="86d9c-106">Este tópico descreve como chamar o exemplo de Introdução ao WCF usando um moniker de WCF WSDL.</span><span class="sxs-lookup"><span data-stu-id="86d9c-106">This topic describes how to call the Getting Started WCF sample using a WCF WSDL moniker.</span></span>  
  
### <a name="using-the-wsdl-service-moniker"></a><span data-ttu-id="86d9c-107">Usando o moniker de serviço WSDL</span><span class="sxs-lookup"><span data-stu-id="86d9c-107">Using the WSDL service moniker</span></span>  
  
1.  <span data-ttu-id="86d9c-108">Abrir e criar a solução de exemplo GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="86d9c-108">Open and build the GettingStarted sample solution.</span></span>  
  
2.  <span data-ttu-id="86d9c-109">Abra o Internet Explorer e navegue até `http://localhost/ServiceModelSamples/Service.svc` para certificar-se de que o serviço está funcionando.</span><span class="sxs-lookup"><span data-stu-id="86d9c-109">Open Internet Explorer and browse to `http://localhost/ServiceModelSamples/Service.svc` to make sure that the service is working.</span></span>  
  
3.  <span data-ttu-id="86d9c-110">No arquivo Service.cs, adicione o seguinte atributo na classe CalculatorService:</span><span class="sxs-lookup"><span data-stu-id="86d9c-110">In the Service.cs file, add the following attribute on the CalculatorService class:</span></span>  
  
     [!code-csharp[S_WSDL_Client#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wsdl_client/cs/service.cs#0)]  
  
4.  <span data-ttu-id="86d9c-111">Adicione um namespace de associação para o serviço de App. config:</span><span class="sxs-lookup"><span data-stu-id="86d9c-111">Add a binding namespace to the service App.config:</span></span>  

5.  <span data-ttu-id="86d9c-112">Crie um arquivo WSDL para o aplicativo ler.</span><span class="sxs-lookup"><span data-stu-id="86d9c-112">Create a WSDL file for the application to read.</span></span> <span data-ttu-id="86d9c-113">Como os namespaces foram adicionados nas etapas 3 e 4, você pode usar o IE para consultar a descrição inteira de WSDL do serviço, navegando até `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="86d9c-113">Because the namespaces were added in steps 3 and 4, you can use IE to query for the entire WSDL description of the service by browsing to `http://localhost/ServiceModelSamples/Service.svc?wsdl`.</span></span> <span data-ttu-id="86d9c-114">Você pode salvar o arquivo do Internet Explorer como serviceWSDL.xml.</span><span class="sxs-lookup"><span data-stu-id="86d9c-114">You can then save the file from Internet Explorer as serviceWSDL.xml.</span></span> <span data-ttu-id="86d9c-115">Se você não especificar os namespaces nas etapas 3 e 4, o documento WSDL retornado das consultas URL acima não será concluída WSDL.</span><span class="sxs-lookup"><span data-stu-id="86d9c-115">If you do not specify the namespaces in steps 3 and 4, the WSDL document returned from querying the above URL will not be the complete WSDL.</span></span> <span data-ttu-id="86d9c-116">O documento WSDL retornado incluirá várias instruções de importação que importar outros documentos WSDL.</span><span class="sxs-lookup"><span data-stu-id="86d9c-116">The WSDL document returned will include several import statements that import other WSDL documents.</span></span> <span data-ttu-id="86d9c-117">Você precisará passar por cada instrução de importação e compilar todo o documento WSDL, combinando o WSDL retornado do serviço com o WSDL importado.</span><span class="sxs-lookup"><span data-stu-id="86d9c-117">You will have to go through each import statement and build the complete WSDL document, combining the WSDL returned from the service with the WSDL imported.</span></span>  
  
6.  <span data-ttu-id="86d9c-118">Abra o Visual Basic 6.0 e crie um novo arquivo .exe padrão.</span><span class="sxs-lookup"><span data-stu-id="86d9c-118">Open Visual Basic 6.0 and create a new Standard .exe file.</span></span> <span data-ttu-id="86d9c-119">Adicione um botão ao formulário e clique duas vezes no botão para adicionar o seguinte código ao manipulador de cliques:</span><span class="sxs-lookup"><span data-stu-id="86d9c-119">Add a button to the form and double-click the button to add the following code to the Click handler:</span></span>  
  
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
    >  Se o moniker está mal formado ou se o serviço está indisponível a chamada para `GetObject` retornará um erro informando que "Sintaxe inválida".  <span data-ttu-id="86d9c-121">Se você receber esse erro, verifique se você estiver usando o identificador de origem está correto e o serviço está disponível.</span><span class="sxs-lookup"><span data-stu-id="86d9c-121">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
7.  <span data-ttu-id="86d9c-122">Execute o aplicativo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="86d9c-122">Run the Visual Basic application.</span></span> <span data-ttu-id="86d9c-123">Caixa de mensagem será exibida com os resultados da subtração de chamada (145, 76.54).</span><span class="sxs-lookup"><span data-stu-id="86d9c-123">A message box will be displayed with the results of calling Subtract(145, 76.54).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d9c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86d9c-124">See also</span></span>

- [<span data-ttu-id="86d9c-125">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="86d9c-125">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="86d9c-126">Integração com visão geral de aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="86d9c-126">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)
