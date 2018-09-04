---
title: Usando o WCF Moniker com clientes COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: f052504648d381d6fb19fb6db0ebb1dd1086ed3c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515713"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="a0f82-102">Usando o WCF Moniker com clientes COM</span><span class="sxs-lookup"><span data-stu-id="a0f82-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="a0f82-103">Este exemplo demonstra como usar o moniker de serviço do Windows Communication Foundation (WCF) para integrar serviços da Web em ambientes de desenvolvimento baseado em COM, como o Microsoft Office Visual Basic for Applications (VBA do Office) ou Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="a0f82-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="a0f82-104">Esse exemplo consiste em um cliente do Windows Script Host (. vbs), uma biblioteca de cliente com suporte (. dll) e uma biblioteca de serviço (. dll) hospedado pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="a0f82-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="a0f82-105">O serviço é um serviço de Calculadora e o cliente COM chama operações matemáticas — adicionar, subtrair, multiplicar e dividir — no serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="a0f82-106">Atividade do cliente está visível nas janelas de caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a0f82-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0f82-107">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="a0f82-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a0f82-108">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a0f82-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a0f82-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a0f82-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0f82-110">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a0f82-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0f82-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a0f82-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="a0f82-112">O serviço implementa um `ICalculator` contrato definido conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0f82-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="a0f82-113">O exemplo demonstra as três abordagens alternativas para usar o moniker:</span><span class="sxs-lookup"><span data-stu-id="a0f82-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="a0f82-114">Contrato tipado – o contrato é registrado como um tipo visível de COM no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="a0f82-115">Contrato WSDL – o contrato é fornecido na forma de um documento WSDL.</span><span class="sxs-lookup"><span data-stu-id="a0f82-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="a0f82-116">Contrato de troca de metadados – o contrato é recuperado em tempo de execução de um ponto de extremidade de troca de metadados (MEX).</span><span class="sxs-lookup"><span data-stu-id="a0f82-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="a0f82-117">Tipo de contrato</span><span class="sxs-lookup"><span data-stu-id="a0f82-117">Typed Contract</span></span>  
 <span data-ttu-id="a0f82-118">Para usar o moniker com um contrato com tipo de uso, tipos de atributo adequadamente para o contrato de serviço devem ser registrados com.</span><span class="sxs-lookup"><span data-stu-id="a0f82-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="a0f82-119">Primeiro, um cliente deve ser gerado usando o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a0f82-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="a0f82-120">Execute o seguinte comando em um prompt de comando no diretório do cliente para gerar o proxy tipado.</span><span class="sxs-lookup"><span data-stu-id="a0f82-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="a0f82-121">Essa classe deve ser incluída em um projeto e o projeto deve ser configurado para gerar um visível em COM, assinado assembly quando compilado.</span><span class="sxs-lookup"><span data-stu-id="a0f82-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="a0f82-122">O seguinte atributo deve ser incluído no arquivo AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="a0f82-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```  
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="a0f82-123">Depois de criar o projeto, registrar os tipos visível usando `regasm` conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0f82-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="a0f82-124">O assembly que é criado deve ser adicionado ao Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="a0f82-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="a0f82-125">Embora não seja estritamente necessário, isso simplifica o processo de tempo de execução localizar o assembly.</span><span class="sxs-lookup"><span data-stu-id="a0f82-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="a0f82-126">O comando a seguir adiciona o assembly no cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="a0f82-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="a0f82-127">O moniker de serviço requer somente o registro do tipo e não usa o proxy para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="a0f82-128">Aplicativo de cliente ComCalcClient.vbs usa o `GetObject` função para construir um proxy para o serviço, usando a sintaxe de moniker de serviço para especificar o endereço, associação e de contrato para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="a0f82-129">Especificam os parâmetros usados pelo moniker:</span><span class="sxs-lookup"><span data-stu-id="a0f82-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="a0f82-130">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="a0f82-131">A associação que o cliente deve usar para se conectar com esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a0f82-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="a0f82-132">Nesse caso, wsHttpBinding definida pelo sistema é usado, apesar de ligações personalizadas podem ser definidas em arquivos de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="a0f82-133">Para uso com o Windows Script Host, a associação personalizada é definida em um arquivo de Cscript.exe.config no mesmo diretório que Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="a0f82-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="a0f82-134">O tipo do contrato que tem suporte no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="a0f82-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="a0f82-135">Esse é o tipo que foi gerado e registrado acima.</span><span class="sxs-lookup"><span data-stu-id="a0f82-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="a0f82-136">Como o script do Visual Basic fornece um ambiente de COM rigidez de tipos, um identificador para o contrato deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="a0f82-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="a0f82-137">Esse GUID é o `interfaceID` de CalcProxy.tlb, que podem ser exibido usando COM ferramentas como o Visualizador de objeto OLE/COM (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="a0f82-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="a0f82-138">Para ambientes fortemente tipadas, como Office VBA ou Visual Basic 6.0, adicionando uma referência explícita à biblioteca de tipos e, em seguida, declarar o tipo do objeto proxy podem ser usados no lugar do parâmetro de contrato.</span><span class="sxs-lookup"><span data-stu-id="a0f82-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="a0f82-139">Isso também oferece suporte ao IntelliSense durante o desenvolvimento de aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="a0f82-140">Ter construído a instância do proxy com o moniker de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de moniker de serviço chamar as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a0f82-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Quando você executar o exemplo, a resposta da operação é exibida em uma janela de caixa de mensagem do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o moniker tipado para se comunicar com um serviço WCF. <span data-ttu-id="a0f82-143">Apesar do uso de COM no aplicativo cliente, a comunicação com o serviço consiste apenas chamadas de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="a0f82-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="a0f82-144">Contrato WSDL</span><span class="sxs-lookup"><span data-stu-id="a0f82-144">WSDL Contract</span></span>  
 <span data-ttu-id="a0f82-145">Para usar o moniker com um contrato WSDL, nenhum registro da biblioteca de cliente é necessário, mas o contrato WSDL para o serviço deve ser recuperado por meio de um mecanismo fora de banda, como usando um navegador para acessar o ponto de extremidade WSDL para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="a0f82-146">O identificador de origem, em seguida, pode acessar esse contrato em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0f82-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="a0f82-147">O aplicativo de cliente ComCalcClient.vbs usa o `FileSystemObject` para acessar o arquivo WSDL salvo localmente e, em seguida, novamente usa o `GetObject` função para construir um proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="a0f82-148">Especificam os parâmetros usados pelo moniker:</span><span class="sxs-lookup"><span data-stu-id="a0f82-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="a0f82-149">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="a0f82-150">A associação que o cliente deve usar para se conectar com esse ponto de extremidade e o namespace no qual essa associação é definida.</span><span class="sxs-lookup"><span data-stu-id="a0f82-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="a0f82-151">Nesse caso, o `wsHttpBinding_ICalculator` é usado.</span><span class="sxs-lookup"><span data-stu-id="a0f82-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="a0f82-152">O WSDL que define o contrato.</span><span class="sxs-lookup"><span data-stu-id="a0f82-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="a0f82-153">Nesse caso, isso é a cadeia de caracteres que foi lido do arquivo serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="a0f82-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="a0f82-154">O nome e o namespace do contrato.</span><span class="sxs-lookup"><span data-stu-id="a0f82-154">The name and namespace of the contract.</span></span> <span data-ttu-id="a0f82-155">Essa identificação é necessária porque a WSDL pode conter mais de um contrato.</span><span class="sxs-lookup"><span data-stu-id="a0f82-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0f82-156">Por padrão, o WCF services geram arquivos WSDL separados para cada namespace que o uso.</span><span class="sxs-lookup"><span data-stu-id="a0f82-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="a0f82-157">Eles são vinculados com o uso da construção de importação WSDL.</span><span class="sxs-lookup"><span data-stu-id="a0f82-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="a0f82-158">Porque o moniker espera que uma única definição de WSDL, o serviço deve usar um único namespace conforme demonstrado neste exemplo, ou os arquivos separados devem ser mesclados manualmente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="a0f82-159">Ter construído a instância do proxy com o moniker de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de moniker de serviço chamar as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a0f82-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Quando você executar o exemplo, a resposta da operação é exibida em uma janela de caixa de mensagem do Windows Script Host. <span data-ttu-id="a0f82-161">Isso demonstra um cliente COM fazendo chamadas COM usando o moniker com um contrato WSDL para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a0f82-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="a0f82-162">Contrato de troca de metadados</span><span class="sxs-lookup"><span data-stu-id="a0f82-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="a0f82-163">Para usar o moniker com um contrato MEX, assim como acontece com o contrato WSDL, nenhum registro de cliente é necessário.</span><span class="sxs-lookup"><span data-stu-id="a0f82-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="a0f82-164">O contrato para o serviço é recuperado em tempo de execução através do uso interno de troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="a0f82-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="a0f82-165">O aplicativo de cliente ComCalcClient.vbs novamente usa o `GetObject` função para construir um proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="a0f82-166">Especificam os parâmetros usados pelo moniker:</span><span class="sxs-lookup"><span data-stu-id="a0f82-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="a0f82-167">O endereço do ponto de extremidade de troca de metadados de serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="a0f82-168">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="a0f82-169">A associação que o cliente deve usar para se conectar com esse ponto de extremidade e o namespace no qual essa associação é definida.</span><span class="sxs-lookup"><span data-stu-id="a0f82-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="a0f82-170">Nesse caso, o `wsHttpBinding_ICalculator` é usado.</span><span class="sxs-lookup"><span data-stu-id="a0f82-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="a0f82-171">O nome e o namespace do contrato.</span><span class="sxs-lookup"><span data-stu-id="a0f82-171">The name and namespace of the contract.</span></span> <span data-ttu-id="a0f82-172">Essa identificação é necessária porque a WSDL pode conter mais de um contrato.</span><span class="sxs-lookup"><span data-stu-id="a0f82-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="a0f82-173">Ter construído a instância do proxy com o moniker de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de moniker de serviço chamar as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="a0f82-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Quando você executar o exemplo, a resposta da operação é exibida em uma janela de caixa de mensagem do Windows Script Host. <span data-ttu-id="a0f82-175">Isso demonstra um cliente COM fazendo chamadas COM usando o moniker com um contrato MEX para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="a0f82-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a0f82-176">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a0f82-176">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="a0f82-177">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0f82-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a0f82-178">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a0f82-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a0f82-179">Em um prompt de comando do Visual Studio, abra a pasta de \Client\Bin., sob a pasta de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="a0f82-179">From a Visual Studio command prompt, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0f82-180">Se você estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 ou Windows Server 2008 R2, certifique-se de que você execute o prompt de comando com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="a0f82-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="a0f82-181">Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar a dll para um arquivo tlb.</span><span class="sxs-lookup"><span data-stu-id="a0f82-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="a0f82-182">"Aviso de exportador da biblioteca de tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="a0f82-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5.  <span data-ttu-id="a0f82-183">Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM.</span><span class="sxs-lookup"><span data-stu-id="a0f82-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="a0f82-184">"Aviso de exportador da biblioteca de tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="a0f82-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6.  <span data-ttu-id="a0f82-185">Digite `gacutil.exe /i client.dll` para adicionar o assembly no cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="a0f82-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a0f82-186">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="a0f82-186">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="a0f82-187">Teste que você pode acessar o serviço usando um navegador, digitando o seguinte endereço: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="a0f82-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="a0f82-188">Uma página de confirmação deve ser exibida na resposta.</span><span class="sxs-lookup"><span data-stu-id="a0f82-188">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="a0f82-189">Execute ComCalcClient.vbs de \cliente, sob a pasta de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="a0f82-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="a0f82-190">Atividade do cliente é exibida nas janelas da caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a0f82-190">Client activity is displayed in message box windows.</span></span>  
  
3.  <span data-ttu-id="a0f82-191">Se o cliente e o serviço não for capazes de se comunicar, consulte [dicas de solução de problemas](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="a0f82-191">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a0f82-192">Para executar o exemplo em computadores</span><span class="sxs-lookup"><span data-stu-id="a0f82-192">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="a0f82-193">No computador do serviço, crie um diretório virtual chamado ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="a0f82-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="a0f82-194">O script de Setupvroot.bat incluído no exemplo pode ser usado para criar o diretório de disco e o diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="a0f82-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2.  <span data-ttu-id="a0f82-195">Copie os arquivos de programa do serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples ao diretório virtual ServiceModelSamples no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="a0f82-196">Certifique-se de incluir os arquivos no diretório \bin.</span><span class="sxs-lookup"><span data-stu-id="a0f82-196">Be sure to include the files in the \bin directory.</span></span>  
  
3.  <span data-ttu-id="a0f82-197">Copie o arquivo de script de cliente na pasta \client, na pasta de idioma específico, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4.  <span data-ttu-id="a0f82-198">No arquivo de script, altere o valor do endereço da definição do ponto de extremidade para coincidir com o novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="a0f82-199">Substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5.  <span data-ttu-id="a0f82-200">Copie o arquivo WSDL para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="a0f82-201">No arquivo WSDL, serviceWsdl.xml, substitua todas as referências a "localhost" com um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="a0f82-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6.  <span data-ttu-id="a0f82-202">Copie a biblioteca Client da pasta \Client\Bin., sob a pasta de idioma específico, para um diretório no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="a0f82-203">Em um prompt de comando, navegue até esse diretório de destino no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="a0f82-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="a0f82-204">Se usando [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], certifique-se de executar o prompt de comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="a0f82-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8.  <span data-ttu-id="a0f82-205">Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar a dll para um arquivo tlb.</span><span class="sxs-lookup"><span data-stu-id="a0f82-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="a0f82-206">"Aviso de exportador da biblioteca de tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="a0f82-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="a0f82-207">Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM.</span><span class="sxs-lookup"><span data-stu-id="a0f82-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="a0f82-208">Verifique se esse caminho foi definido para a pasta que contém `regasm.exe` antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="a0f82-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="a0f82-209">Digite `gacutil.exe /i client.dll` para adicionar o assembly no cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="a0f82-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="a0f82-210">Verifique se esse caminho foi definido para a pasta que contém `gacutil.exe` antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="a0f82-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="a0f82-211">Teste que você pode acessar o serviço do computador cliente usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="a0f82-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="a0f82-212">No computador cliente, inicie ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="a0f82-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a0f82-213">Para limpar após a amostra</span><span class="sxs-lookup"><span data-stu-id="a0f82-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="a0f82-214">Para fins de segurança, remova a definição do diretório virtual e as permissões concedidas nas etapas de configuração quando tiver terminado com os exemplos.</span><span class="sxs-lookup"><span data-stu-id="a0f82-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f82-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0f82-215">See Also</span></span>
