---
title: Usando o WCF Moniker com clientes COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183228"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="83738-102">Usando o WCF Moniker com clientes COM</span><span class="sxs-lookup"><span data-stu-id="83738-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="83738-103">Esta amostra demonstra como usar o apelido de serviço da Windows Communication Foundation (WCF) para integrar serviços web em ambientes de desenvolvimento baseados em COM, como o Microsoft Office Visual Basic for Applications (Office VBA) ou o Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="83738-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="83738-104">Esta amostra consiste em um cliente Windows Script Host (.vbs), uma biblioteca de clientes de suporte (.dll) e uma biblioteca de serviços (.dll) hospedada pelo Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="83738-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="83738-105">O serviço é um serviço de calculadora e o cliente COM chama operações matemáticas — Adicionar, Subtrair, Multiplicar e Dividir — no serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="83738-106">A atividade do cliente é visível nas janelas da caixa de mensagens.</span><span class="sxs-lookup"><span data-stu-id="83738-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83738-107">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="83738-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="83738-108">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="83738-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="83738-109">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="83738-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="83738-110">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="83738-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83738-111">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="83738-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="83738-112">O serviço implementa um `ICalculator` contrato definido como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="83738-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="83738-113">A amostra demonstra as três abordagens alternativas para o uso do apelido:</span><span class="sxs-lookup"><span data-stu-id="83738-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="83738-114">Contrato digitado – O contrato é registrado como um tipo visível COM no computador do cliente.</span><span class="sxs-lookup"><span data-stu-id="83738-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="83738-115">Contrato WSDL – O contrato é fornecido a forma de um documento WSDL.</span><span class="sxs-lookup"><span data-stu-id="83738-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="83738-116">Contrato de Troca de Metadados – O contrato é recuperado em tempo de execução a partir de um ponto final da Metadata Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="83738-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="83738-117">Contrato Digitado</span><span class="sxs-lookup"><span data-stu-id="83738-117">Typed Contract</span></span>  
 <span data-ttu-id="83738-118">Para utilizar o apelido com uso de contrato digitado, os tipos devidamente atribuídos ao contrato de serviço devem ser registrados no COM.</span><span class="sxs-lookup"><span data-stu-id="83738-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="83738-119">Primeiro, um cliente deve ser gerado usando a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="83738-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="83738-120">Execute o seguinte comando a partir de um prompt de comando no diretório do cliente para gerar o proxy digitado.</span><span class="sxs-lookup"><span data-stu-id="83738-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="83738-121">Esta classe deve ser incluída em um projeto e o projeto deve ser configurado para gerar uma montagem assinada e visível com COM quando compilado.</span><span class="sxs-lookup"><span data-stu-id="83738-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="83738-122">O seguinte atributo deve ser incluído no arquivo AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="83738-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="83738-123">Após a construção do projeto, registre `regasm` os tipos visíveis com usando como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="83738-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="83738-124">A montagem criada deve ser adicionada ao Cache de Montagem Global.</span><span class="sxs-lookup"><span data-stu-id="83738-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="83738-125">Embora não seja estritamente necessário, isso simplifica o processo de localização do conjunto em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="83738-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="83738-126">O comando a seguir adiciona a montagem ao Cache de Montagem Global.</span><span class="sxs-lookup"><span data-stu-id="83738-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="83738-127">O apelido de serviço requer apenas o registro do tipo e não usa o proxy para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="83738-128">O aplicativo cliente ComCalcClient.vbs usa a `GetObject` função para construir um proxy para o serviço, usando a sintaxe de apelido de serviço para especificar o endereço, a vinculação e o contrato do serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="83738-129">Os parâmetros utilizados pelo apelido especificam:</span><span class="sxs-lookup"><span data-stu-id="83738-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="83738-130">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="83738-131">A vinculação que o cliente deve usar para se conectar com esse ponto final.</span><span class="sxs-lookup"><span data-stu-id="83738-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="83738-132">Neste caso, o wsHttpBinding definido pelo sistema é usado, embora as vinculações personalizadas possam ser definidas em arquivos de configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="83738-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="83738-133">Para uso com o Windows Script Host, a vinculação personalizada é definida em um arquivo Cscript.exe.config no mesmo diretório que Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="83738-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="83738-134">O tipo de contrato que é suportado no ponto final.</span><span class="sxs-lookup"><span data-stu-id="83738-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="83738-135">Este é o tipo que foi gerado e registrado acima.</span><span class="sxs-lookup"><span data-stu-id="83738-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="83738-136">Como o script Visual Basic não fornece um ambiente COM fortemente digitado, um identificador para o contrato deve ser especificado.</span><span class="sxs-lookup"><span data-stu-id="83738-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="83738-137">Este GUID `interfaceID` é o de CalcProxy.tlb, que pode ser visualizado usando ferramentas COM como o OLE/COM Object Viewer (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="83738-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="83738-138">Para ambientes fortemente digitados, como o Office VBA ou o Visual Basic 6.0, adicionar uma referência explícita à biblioteca do tipo e, em seguida, declarar o tipo do objeto proxy pode ser usado no lugar do parâmetro do contrato.</span><span class="sxs-lookup"><span data-stu-id="83738-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="83738-139">Isso também fornece suporte ao IntelliSense durante o desenvolvimento de aplicativos clientes.</span><span class="sxs-lookup"><span data-stu-id="83738-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="83738-140">Tendo construído a instância proxy com o apelido de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de apelido de serviço chamando as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="83738-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Quando você executa a amostra, a resposta de operação é exibida em uma janela de caixa de mensagens do Windows Script Host. Isso demonstra um cliente COM fazendo chamadas COM usando o apelido digitado para se comunicar com um serviço WCF. <span data-ttu-id="83738-143">Apesar do uso do COM no aplicativo do cliente, a comunicação com o serviço consiste apenas em chamadas de serviço web.</span><span class="sxs-lookup"><span data-stu-id="83738-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="83738-144">Contrato WSDL</span><span class="sxs-lookup"><span data-stu-id="83738-144">WSDL Contract</span></span>  
 <span data-ttu-id="83738-145">Para usar o apelido com um contrato WSDL, nenhum registro de biblioteca de clientes é necessário, mas o contrato WSDL para o serviço deve ser recuperado através de um mecanismo fora de banda, como usar um navegador para acessar o ponto final do WSDL para o serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="83738-146">O apelido pode então acessar esse contrato na hora da execução.</span><span class="sxs-lookup"><span data-stu-id="83738-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="83738-147">O aplicativo cliente ComCalcClient.vbs usa o `FileSystemObject` para acessar o arquivo WSDL salvo localmente e, em seguida, novamente usa a `GetObject` função para construir um proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
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
  
 <span data-ttu-id="83738-148">Os parâmetros utilizados pelo apelido especificam:</span><span class="sxs-lookup"><span data-stu-id="83738-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="83738-149">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="83738-150">A vinculação que o cliente deve usar para se conectar com esse ponto final e o namespace no qual essa vinculação é definida.</span><span class="sxs-lookup"><span data-stu-id="83738-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="83738-151">Neste caso, `wsHttpBinding_ICalculator` o é usado.</span><span class="sxs-lookup"><span data-stu-id="83738-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="83738-152">O WSDL que define o contrato.</span><span class="sxs-lookup"><span data-stu-id="83738-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="83738-153">Neste caso, esta é a string que foi lida a partir do arquivo serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="83738-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="83738-154">O nome e o espaço do contrato.</span><span class="sxs-lookup"><span data-stu-id="83738-154">The name and namespace of the contract.</span></span> <span data-ttu-id="83738-155">Esta identificação é necessária porque o WSDL pode conter mais de um contrato.</span><span class="sxs-lookup"><span data-stu-id="83738-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="83738-156">Por padrão, os serviços WCF geram arquivos WSDL separados para cada namespace que o uso.</span><span class="sxs-lookup"><span data-stu-id="83738-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="83738-157">Estes estão ligados ao uso da construção de importação WSDL.</span><span class="sxs-lookup"><span data-stu-id="83738-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="83738-158">Como o apelido espera uma única definição de WSDL, o serviço deve usar um único namespace como demonstrado nesta amostra ou os arquivos separados devem ser mesclados manualmente.</span><span class="sxs-lookup"><span data-stu-id="83738-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="83738-159">Tendo construído a instância proxy com o apelido de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de apelido de serviço chamando as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="83738-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Quando você executa a amostra, a resposta de operação é exibida em uma janela de caixa de mensagens do Windows Script Host. <span data-ttu-id="83738-161">Isso demonstra um cliente COM fazendo chamadas COM usando o apelido com um contrato WSDL para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="83738-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="83738-162">Contrato de Troca de Metadados</span><span class="sxs-lookup"><span data-stu-id="83738-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="83738-163">Para usar o apelido com um contrato MEX, como no contrato WSDL, não é necessário registro de cliente.</span><span class="sxs-lookup"><span data-stu-id="83738-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="83738-164">O contrato para o serviço é recuperado no momento da execução através do uso interno do Metadata Exchange.</span><span class="sxs-lookup"><span data-stu-id="83738-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="83738-165">O aplicativo cliente ComCalcClient.vbs `GetObject` novamente usa a função para construir um proxy para o serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="83738-166">Os parâmetros utilizados pelo apelido especificam:</span><span class="sxs-lookup"><span data-stu-id="83738-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="83738-167">O endereço do ponto final de troca de metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="83738-168">O endereço do ponto de extremidade de serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="83738-169">A vinculação que o cliente deve usar para se conectar com esse ponto final e o namespace no qual essa vinculação é definida.</span><span class="sxs-lookup"><span data-stu-id="83738-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="83738-170">Neste caso, `wsHttpBinding_ICalculator` o é usado.</span><span class="sxs-lookup"><span data-stu-id="83738-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="83738-171">O nome e o espaço do contrato.</span><span class="sxs-lookup"><span data-stu-id="83738-171">The name and namespace of the contract.</span></span> <span data-ttu-id="83738-172">Esta identificação é necessária porque o WSDL pode conter mais de um contrato.</span><span class="sxs-lookup"><span data-stu-id="83738-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="83738-173">Tendo construído a instância proxy com o apelido de serviço, o aplicativo cliente pode chamar métodos no proxy, o que resulta na infra-estrutura de apelido de serviço chamando as operações de serviço correspondentes.</span><span class="sxs-lookup"><span data-stu-id="83738-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Quando você executa a amostra, a resposta de operação é exibida em uma janela de caixa de mensagens do Windows Script Host. <span data-ttu-id="83738-175">Isso demonstra um cliente COM fazendo chamadas COM usando o apelido com um contrato MEX para se comunicar com um serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="83738-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="83738-176">Para configurar e construir a amostra</span><span class="sxs-lookup"><span data-stu-id="83738-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="83738-177">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="83738-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="83738-178">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="83738-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="83738-179">A partir de um prompt de comando de desenvolvedor para o Visual Studio, abra a pasta \client\bin, na pasta específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="83738-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="83738-180">Se você estiver usando o Windows Vista, Windows Server 2008, Windows 7 ou Windows Server 2008 R2, certifique-se de executar o prompt de comando com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="83738-180">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="83738-181">Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar o dll para um arquivo tlb.</span><span class="sxs-lookup"><span data-stu-id="83738-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="83738-182">Um "Aviso de exportador de biblioteca tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="83738-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="83738-183">Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM.</span><span class="sxs-lookup"><span data-stu-id="83738-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="83738-184">Um "Aviso de exportador de biblioteca tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="83738-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="83738-185">Digite `gacutil.exe /i client.dll` para adicionar o conjunto ao Cache de Montagem Global.</span><span class="sxs-lookup"><span data-stu-id="83738-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="83738-186">Para executar a amostra no mesmo computador</span><span class="sxs-lookup"><span data-stu-id="83738-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="83738-187">Teste que você pode acessar o serviço usando um `http://localhost/servicemodelsamples/service.svc`navegador digitando no seguinte endereço: .</span><span class="sxs-lookup"><span data-stu-id="83738-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="83738-188">Uma página de confirmação deve ser exibida em resposta.</span><span class="sxs-lookup"><span data-stu-id="83738-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="83738-189">Execute ComCalcClient.vbs a partir de \client, a partir da pasta específica do idioma.</span><span class="sxs-lookup"><span data-stu-id="83738-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="83738-190">A atividade do cliente é exibida nas janelas da caixa de mensagens.</span><span class="sxs-lookup"><span data-stu-id="83738-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="83738-191">Se o cliente e o serviço não forem capazes de se comunicar, consulte [Dicas de solução de problemas para amostras wcf](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="83738-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="83738-192">Para executar a amostra através de computadores</span><span class="sxs-lookup"><span data-stu-id="83738-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="83738-193">No computador de serviço, crie um diretório virtual chamado ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="83738-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="83738-194">O script Setupvroot.bat incluído na amostra pode ser usado para criar o diretório de disco e o diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="83738-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="83738-195">Copie os arquivos do programa de serviço de %SystemDrive%\Inetpub\wwwroot\servicemodelsamples para o diretório virtual ServiceModelSamples no computador de serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="83738-196">Certifique-se de incluir os arquivos no diretório \bin.</span><span class="sxs-lookup"><span data-stu-id="83738-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="83738-197">Copie o arquivo de script cliente da pasta \client, a pasta específica do idioma, para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="83738-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="83738-198">No arquivo de script, altere o valor de endereço da definição de ponto final para corresponder ao novo endereço do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="83738-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="83738-199">Substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="83738-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="83738-200">Copie o arquivo WSDL para o computador cliente.</span><span class="sxs-lookup"><span data-stu-id="83738-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="83738-201">No arquivo WSDL, serviceWsdl.xml, substitua quaisquer referências a "localhost" por um nome de domínio totalmente qualificado no endereço.</span><span class="sxs-lookup"><span data-stu-id="83738-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="83738-202">Copie a biblioteca Client.dll da pasta \client\bin, na pasta específica do idioma, para um diretório no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="83738-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="83738-203">A partir de um prompt de comando, navegue até o diretório de destino no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="83738-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="83738-204">Se estiver usando o Windows Vista ou o Windows Server 2008, certifique-se de executar o prompt de comando como Administrador.</span><span class="sxs-lookup"><span data-stu-id="83738-204">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="83738-205">Digite `tlbexp.exe client.dll /out:CalcProxy.tlb` para exportar o dll para um arquivo tlb.</span><span class="sxs-lookup"><span data-stu-id="83738-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="83738-206">Um "Aviso de exportador de biblioteca tipo" é esperado, mas não é um problema porque o tipo genérico não é necessário.</span><span class="sxs-lookup"><span data-stu-id="83738-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="83738-207">Digite `regasm.exe /tlb:CalcProxy.tlb client.dll` para registrar os tipos com COM.</span><span class="sxs-lookup"><span data-stu-id="83738-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="83738-208">Certifique-se de que o caminho `regasm.exe` foi definido para a pasta que contém antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="83738-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="83738-209">Digite `gacutil.exe /i client.dll` para adicionar o conjunto ao Cache de Montagem Global.</span><span class="sxs-lookup"><span data-stu-id="83738-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="83738-210">Certifique-se de que o caminho `gacutil.exe` foi definido para a pasta que contém antes de executar o comando.</span><span class="sxs-lookup"><span data-stu-id="83738-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="83738-211">Teste que você pode acessar o serviço a partir do computador cliente usando um navegador.</span><span class="sxs-lookup"><span data-stu-id="83738-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="83738-212">No computador cliente, inicie ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="83738-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="83738-213">Para limpar depois da amostra</span><span class="sxs-lookup"><span data-stu-id="83738-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="83738-214">Para efeitos de segurança, remova a definição de diretório virtual e as permissões concedidas nas etapas de configuração quando terminar com as amostras.</span><span class="sxs-lookup"><span data-stu-id="83738-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
