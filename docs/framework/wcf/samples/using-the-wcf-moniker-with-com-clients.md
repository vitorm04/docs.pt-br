---
title: Usando o WCF Moniker com clientes COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 321d59285b0ef86e4631634d90229a0d8e79657b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424717"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="16a31-102">Usando o WCF Moniker com clientes COM</span><span class="sxs-lookup"><span data-stu-id="16a31-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="16a31-103">Este exemplo demonstra como usar o moniker do serviço Windows Communication Foundation (WCF) para integrar serviços Web em ambientes de desenvolvimento baseados em COM, como Microsoft Office Visual Basic for Applications (Office VBA) ou Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="16a31-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="16a31-104">Este exemplo consiste em um cliente do Windows Script Host (. vbs), uma biblioteca de cliente de suporte (. dll) e uma biblioteca de serviço (. dll) hospedada pelo Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="16a31-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="16a31-105">O serviço é um serviço de calculadora e o cliente COM chama operações matemáticas — adicionar, subtrair, multiplicar e dividir — no serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="16a31-106">A atividade do cliente fica visível nas janelas da caixa de mensagens.</span><span class="sxs-lookup"><span data-stu-id="16a31-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16a31-107">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="16a31-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="16a31-108">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="16a31-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="16a31-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="16a31-109">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="16a31-110">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="16a31-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16a31-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="16a31-111">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="16a31-112">O serviço implementa um contrato de `ICalculator` definido, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="16a31-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="16a31-113">O exemplo demonstra as três abordagens alternativas para usar o moniker:</span><span class="sxs-lookup"><span data-stu-id="16a31-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="16a31-114">Contrato tipado – o contrato é registrado como um tipo visível COM no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="16a31-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="16a31-115">Contrato WSDL – o contrato é fornecido na forma de um documento WSDL.</span><span class="sxs-lookup"><span data-stu-id="16a31-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="16a31-116">Contrato de troca de metadados – o contrato é recuperado em tempo de execução de um ponto de extremidade de intercâmbio de metadados (MEX).</span><span class="sxs-lookup"><span data-stu-id="16a31-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="16a31-117">Contrato digitado</span><span class="sxs-lookup"><span data-stu-id="16a31-117">Typed Contract</span></span>  
 <span data-ttu-id="16a31-118">Para usar o moniker com um uso de contrato tipado, os tipos atribuídos adequadamente para o contrato de serviço devem ser registrados com com.</span><span class="sxs-lookup"><span data-stu-id="16a31-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="16a31-119">Primeiro, um cliente deve ser gerado usando a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="16a31-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="16a31-120">Execute o comando a seguir em um prompt de comando no diretório do cliente para gerar o proxy de tipo.</span><span class="sxs-lookup"><span data-stu-id="16a31-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="16a31-121">Essa classe deve ser incluída em um projeto e o projeto deve ser configurado para gerar um assembly assinado COM e visível quando compilado.</span><span class="sxs-lookup"><span data-stu-id="16a31-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="16a31-122">O atributo a seguir deve ser incluído no arquivo AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="16a31-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="16a31-123">Depois de criar o projeto, registre os tipos visíveis COM usando `regasm`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="16a31-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="16a31-124">O assembly criado deve ser adicionado ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="16a31-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="16a31-125">Embora não seja estritamente necessário, isso simplifica o processo de tempo de execução que localiza o assembly.</span><span class="sxs-lookup"><span data-stu-id="16a31-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="16a31-126">O comando a seguir adiciona o assembly ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="16a31-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="16a31-127">O moniker do serviço requer apenas o registro do tipo e não usa o proxy para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="16a31-128">O aplicativo cliente ComCalcClient. vbs usa a função `GetObject` para construir um proxy para o serviço, usando a sintaxe do moniker do serviço para especificar o endereço, a associação e o contrato para o serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="16a31-129">Os parâmetros usados pelo moniker especificam:</span><span class="sxs-lookup"><span data-stu-id="16a31-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="16a31-130">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="16a31-131">A associação que o cliente deve usar para se conectar com esse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="16a31-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="16a31-132">Nesse caso, a wsHttpBinding definida pelo sistema é usada por meio de associações personalizadas que podem ser definidas em arquivos de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="16a31-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="16a31-133">Para uso com o Windows Script Host, a associação personalizada é definida em um arquivo cscript. exe. config no mesmo diretório que cscript. exe.</span><span class="sxs-lookup"><span data-stu-id="16a31-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="16a31-134">O tipo de contrato com suporte no ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="16a31-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="16a31-135">Esse é o tipo que foi gerado e registrado acima.</span><span class="sxs-lookup"><span data-stu-id="16a31-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="16a31-136">Como Visual Basic script não fornece um ambiente COM fortemente tipado, um identificador para o contrato deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="16a31-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="16a31-137">Esse GUID é o `interfaceID` de CalcProxy. tlb, que pode ser exibido usando ferramentas COM, como o Visualizador de objetos OLE/COM (OleView. exe).</span><span class="sxs-lookup"><span data-stu-id="16a31-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="16a31-138">Para ambientes fortemente tipados, como o Office VBA ou o Visual Basic 6,0, adicionar uma referência explícita à biblioteca de tipos e, em seguida, declarar o tipo do objeto proxy pode ser usado no lugar do parâmetro Contract.</span><span class="sxs-lookup"><span data-stu-id="16a31-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="16a31-139">Isso também fornece suporte ao IntelliSense durante o desenvolvimento de aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="16a31-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="16a31-140">Tendo construído a instância de proxy com o moniker do serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infraestrutura do moniker do serviço que chama as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="16a31-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Quando você executa o exemplo, a resposta da operação é exibida em uma janela da caixa de mensagem do host de script do Windows. Isso demonstra um cliente COM fazendo chamadas COM usando o moniker tipado para se comunicar com um serviço WCF. <span data-ttu-id="16a31-143">Apesar do uso de COM no aplicativo cliente, a comunicação com o serviço consiste apenas em chamadas de serviço Web.</span><span class="sxs-lookup"><span data-stu-id="16a31-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="16a31-144">Contrato WSDL</span><span class="sxs-lookup"><span data-stu-id="16a31-144">WSDL Contract</span></span>  
 <span data-ttu-id="16a31-145">Para usar o moniker com um contrato WSDL, nenhum registro de biblioteca de cliente é necessário, mas o contrato WSDL para o serviço deve ser recuperado por meio de um mecanismo fora de banda, como usar um navegador para acessar o ponto de extremidade WSDL para o serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="16a31-146">O moniker pode então acessar esse contrato no momento da execução.</span><span class="sxs-lookup"><span data-stu-id="16a31-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="16a31-147">O aplicativo cliente ComCalcClient. vbs usa o `FileSystemObject` para acessar o arquivo WSDL salvo localmente e, em seguida, usa a função `GetObject` para construir um proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
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
  
 <span data-ttu-id="16a31-148">Os parâmetros usados pelo moniker especificam:</span><span class="sxs-lookup"><span data-stu-id="16a31-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="16a31-149">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="16a31-150">A associação que o cliente deve usar para se conectar com esse ponto de extremidade e o namespace no qual essa associação está definida.</span><span class="sxs-lookup"><span data-stu-id="16a31-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="16a31-151">Nesse caso, o `wsHttpBinding_ICalculator` é usado.</span><span class="sxs-lookup"><span data-stu-id="16a31-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="16a31-152">O WSDL que define o contrato.</span><span class="sxs-lookup"><span data-stu-id="16a31-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="16a31-153">Nesse caso, essa é a cadeia de caracteres que foi lida do arquivo. xml.</span><span class="sxs-lookup"><span data-stu-id="16a31-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="16a31-154">O nome e o namespace do contrato.</span><span class="sxs-lookup"><span data-stu-id="16a31-154">The name and namespace of the contract.</span></span> <span data-ttu-id="16a31-155">Essa identificação é necessária porque o WSDL pode conter mais de um contrato.</span><span class="sxs-lookup"><span data-stu-id="16a31-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="16a31-156">Por padrão, os serviços WCF geram arquivos WSDL separados para cada namespace usado pelo.</span><span class="sxs-lookup"><span data-stu-id="16a31-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="16a31-157">Eles são vinculados com o uso da construção de importação WSDL.</span><span class="sxs-lookup"><span data-stu-id="16a31-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="16a31-158">Como o moniker espera uma única definição WSDL, o serviço deve usar um único namespace, como demonstrado neste exemplo, ou os arquivos separados devem ser mesclados manualmente.</span><span class="sxs-lookup"><span data-stu-id="16a31-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="16a31-159">Tendo construído a instância de proxy com o moniker do serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infraestrutura do moniker do serviço que chama as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="16a31-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Quando você executa o exemplo, a resposta da operação é exibida em uma janela da caixa de mensagem do host de script do Windows. <span data-ttu-id="16a31-161">Isso demonstra um cliente COM fazendo chamadas COM usando o moniker com um contrato WSDL para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="16a31-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="16a31-162">Contrato de troca de metadados</span><span class="sxs-lookup"><span data-stu-id="16a31-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="16a31-163">Para usar o moniker com um contrato MEX, como com o contrato WSDL, nenhum registro de cliente é necessário.</span><span class="sxs-lookup"><span data-stu-id="16a31-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="16a31-164">O contrato para o serviço é recuperado no momento da execução por meio do uso interno da troca de metadados.</span><span class="sxs-lookup"><span data-stu-id="16a31-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="16a31-165">O aplicativo cliente ComCalcClient. vbs usa novamente a função `GetObject` para construir um proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="16a31-166">Os parâmetros usados pelo moniker especificam:</span><span class="sxs-lookup"><span data-stu-id="16a31-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="16a31-167">O endereço do ponto de extremidade de troca de metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="16a31-168">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="16a31-169">A associação que o cliente deve usar para se conectar com esse ponto de extremidade e o namespace no qual essa associação está definida.</span><span class="sxs-lookup"><span data-stu-id="16a31-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="16a31-170">Nesse caso, o `wsHttpBinding_ICalculator` é usado.</span><span class="sxs-lookup"><span data-stu-id="16a31-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="16a31-171">O nome e o namespace do contrato.</span><span class="sxs-lookup"><span data-stu-id="16a31-171">The name and namespace of the contract.</span></span> <span data-ttu-id="16a31-172">Essa identificação é necessária porque o WSDL pode conter mais de um contrato.</span><span class="sxs-lookup"><span data-stu-id="16a31-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="16a31-173">Tendo construído a instância de proxy com o moniker do serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infraestrutura do moniker do serviço que chama as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="16a31-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Quando você executa o exemplo, a resposta da operação é exibida em uma janela da caixa de mensagem do host de script do Windows. <span data-ttu-id="16a31-175">Isso demonstra um cliente COM fazendo chamadas COM usando o moniker com um contrato MEX para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="16a31-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="16a31-176">Para configurar e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="16a31-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="16a31-177">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16a31-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="16a31-178">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="16a31-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="16a31-179">Em um Prompt de Comando do Desenvolvedor para o Visual Studio, abra a pasta \client\bin, na pasta específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="16a31-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="16a31-180">Se você estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 ou Windows Server 2008 R2, certifique-se de executar o prompt de comando com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="16a31-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="16a31-181">Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar a dll para um arquivo tlb.</span><span class="sxs-lookup"><span data-stu-id="16a31-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="16a31-182">Um "aviso de exportador da biblioteca de tipos" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="16a31-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="16a31-183">Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com com.</span><span class="sxs-lookup"><span data-stu-id="16a31-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="16a31-184">Um "aviso de exportador da biblioteca de tipos" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="16a31-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="16a31-185">Digite `gacutil.exe /i client.dll` para adicionar o assembly ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="16a31-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="16a31-186">Para executar o exemplo no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="16a31-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="16a31-187">Teste se você pode acessar o serviço usando um navegador digitando o seguinte endereço: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="16a31-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="16a31-188">Uma página de confirmação deve ser exibida em resposta.</span><span class="sxs-lookup"><span data-stu-id="16a31-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="16a31-189">Execute ComCalcClient. vbs de \Client, de dentro da pasta específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="16a31-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="16a31-190">A atividade do cliente é exibida nas janelas da caixa de mensagens.</span><span class="sxs-lookup"><span data-stu-id="16a31-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="16a31-191">Se o cliente e o serviço não puderem se comunicar, consulte [dicas de solução de problemas para exemplos do WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="16a31-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="16a31-192">Para executar o exemplo entre computadores</span><span class="sxs-lookup"><span data-stu-id="16a31-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="16a31-193">No computador do serviço, crie um diretório virtual chamado ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="16a31-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="16a31-194">O script Setupvroot. bat incluído com o exemplo pode ser usado para criar o diretório de disco e o diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="16a31-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="16a31-195">Copie os arquivos de programa do serviço de%SystemDrive%\Inetpub\wwwroot\servicemodelsamples para o diretório virtual ServiceModelSamples no computador do serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="16a31-196">Certifique-se de incluir os arquivos no diretório \bin.</span><span class="sxs-lookup"><span data-stu-id="16a31-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="16a31-197">Copie o arquivo de script do cliente da pasta \Client, na pasta específica do idioma, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="16a31-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="16a31-198">No arquivo de script, altere o valor de endereço da definição do ponto de extremidade para corresponder ao novo endereço do serviço.</span><span class="sxs-lookup"><span data-stu-id="16a31-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="16a31-199">Substitua todas as referências a "localhost" por um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="16a31-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="16a31-200">Copie o arquivo WSDL no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="16a31-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="16a31-201">No arquivo WSDL, Service WSDL. xml, substitua todas as referências a "localhost" por um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="16a31-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="16a31-202">Copie a biblioteca Client. dll da pasta \client\bin, na pasta específica do idioma, para um diretório no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="16a31-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="16a31-203">Em um prompt de comando, navegue até o diretório de destino no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="16a31-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="16a31-204">Se estiver usando [!INCLUDE[wv](../../../../includes/wv-md.md)] ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], certifique-se de executar o prompt de comando como administrador.</span><span class="sxs-lookup"><span data-stu-id="16a31-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="16a31-205">Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar a dll para um arquivo tlb.</span><span class="sxs-lookup"><span data-stu-id="16a31-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="16a31-206">Um "aviso de exportador da biblioteca de tipos" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="16a31-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="16a31-207">Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com com.</span><span class="sxs-lookup"><span data-stu-id="16a31-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="16a31-208">Verifique se o caminho foi definido para a pasta que contém `regasm.exe` antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="16a31-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="16a31-209">Digite `gacutil.exe /i client.dll` para adicionar o assembly ao cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="16a31-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="16a31-210">Verifique se o caminho foi definido para a pasta que contém `gacutil.exe` antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="16a31-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="16a31-211">Teste se você pode acessar o serviço do computador cliente usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="16a31-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="16a31-212">No computador cliente, inicie o ComCalcClient. vbs.</span><span class="sxs-lookup"><span data-stu-id="16a31-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="16a31-213">Para limpar após o exemplo</span><span class="sxs-lookup"><span data-stu-id="16a31-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="16a31-214">Para fins de segurança, remova a definição de diretório virtual e as permissões concedidas nas etapas de instalação quando você tiver concluído os exemplos.</span><span class="sxs-lookup"><span data-stu-id="16a31-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
