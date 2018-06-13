---
title: Exemplo de introdução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: dfba7062d4226f3644aa6c4cc0efcd7c5fb9eab8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505763"
---
# <a name="getting-started-sample"></a><span data-ttu-id="21183-102">Exemplo de introdução</span><span class="sxs-lookup"><span data-stu-id="21183-102">Getting Started Sample</span></span>
<span data-ttu-id="21183-103">O guia de Introdução demonstra como implementar um serviço típico e um cliente típico usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="21183-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="21183-104">Este exemplo é a base para todos os outros exemplos de tecnologia básico.</span><span class="sxs-lookup"><span data-stu-id="21183-104">This sample is the basis for all other basic technology samples.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21183-105">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="21183-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="21183-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="21183-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="21183-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="21183-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="21183-108">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="21183-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="21183-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="21183-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\GettingStarted\GettingStarted`  
  
 <span data-ttu-id="21183-110">O serviço descreve as operações que ele executa em um contrato de serviço que expõe publicamente como metadados.</span><span class="sxs-lookup"><span data-stu-id="21183-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="21183-111">O serviço também contém o código para implementar as operações.</span><span class="sxs-lookup"><span data-stu-id="21183-111">The service also contains the code to implement the operations.</span></span>  
  
 <span data-ttu-id="21183-112">O cliente contém uma definição de contrato de serviço e uma classe de proxy para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="21183-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="21183-113">O código de proxy é gerado a partir de metadados de serviço usando o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="21183-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 <span data-ttu-id="21183-114">Em [!INCLUDE[wv](../../../../includes/wv-md.md)], o serviço está hospedado no serviço de ativação do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="21183-114">On [!INCLUDE[wv](../../../../includes/wv-md.md)], the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="21183-115">Em [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ele é hospedado pelo Internet Information Services (IIS) e ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="21183-115">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="21183-116">Hospedar um serviço em IIS ou do WAS permite que o serviço seja ativado automaticamente quando ele é acessado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="21183-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21183-117">Se você prefere começar com um exemplo que hospeda o serviço em um aplicativo de console, em vez de IIS, consulte o [auto-host](../../../../docs/framework/wcf/samples/self-host.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="21183-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>  
  
 <span data-ttu-id="21183-118">O serviço e o cliente especificam detalhes de acesso no arquivo de configuração, que fornecem flexibilidade no momento da implantação.</span><span class="sxs-lookup"><span data-stu-id="21183-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="21183-119">Isso inclui uma definição de ponto de extremidade que especifica um endereço, associação e contrato.</span><span class="sxs-lookup"><span data-stu-id="21183-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="21183-120">A associação especifica os detalhes de transporte e segurança para como o serviço deve ser acessado.</span><span class="sxs-lookup"><span data-stu-id="21183-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>  
  
 <span data-ttu-id="21183-121">O serviço define um comportamento de tempo de execução para publicar seus metadados.</span><span class="sxs-lookup"><span data-stu-id="21183-121">The service configures a run-time behavior to publish its metadata.</span></span>  
  
 <span data-ttu-id="21183-122">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="21183-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="21183-123">O contrato é definido pelo `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="21183-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="21183-124">O cliente faz solicitações para uma operação matemática determinado e as respostas do serviço com o resultado.</span><span class="sxs-lookup"><span data-stu-id="21183-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="21183-125">O serviço implementa uma `ICalculator` contrato que é definido no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="21183-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>  
  
```vb  
' Define a service contract.  
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>  
     Public Interface ICalculator  
        <OperationContract()>  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()>  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
```  
  
```csharp  
// Define a service contract.  
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
  
 <span data-ttu-id="21183-126">A implementação do serviço calcula e retorna o resultado apropriado, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="21183-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>  
  
```vb  
' Service class which implements the service contract.  
Public Class CalculatorService  
Implements ICalculator  
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
Return n1 + n2  
End Function  
  
Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
Return n1 - n2  
End Function  
  
Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
Return n1 * n2  
End Function  
  
Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
Return n1 / n2  
End Function  
End Class  
```  
  
```csharp  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="21183-127">O serviço expõe um ponto de extremidade de comunicação com o serviço, definido usando um arquivo de configuração (Web. config), conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="21183-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>  
  
```xaml  
<services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- ICalculator is exposed at the base address provided by  
         host: http://localhost/servicemodelsamples/service.svc.  -->  
       <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
       ...  
    </service>  
</services>  
```  
  
 <span data-ttu-id="21183-128">O serviço expõe o ponto de extremidade no endereço base fornecido pelo host do IIS ou do WAS.</span><span class="sxs-lookup"><span data-stu-id="21183-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="21183-129">A associação está configurada com um padrão <xref:System.ServiceModel.WSHttpBinding>, que fornece comunicação HTTP e protocolos padrão do serviço da Web para endereçamento e segurança.</span><span class="sxs-lookup"><span data-stu-id="21183-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="21183-130">O contrato é o `ICalculator` implementados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="21183-130">The contract is the `ICalculator` implemented by the service.</span></span>  
  
 <span data-ttu-id="21183-131">Conforme configurado, o serviço pode ser acessado em http://localhost/servicemodelsamples/service.svc por um cliente no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="21183-131">As configured, the service can be accessed at http://localhost/servicemodelsamples/service.svc by a client on the same computer.</span></span> <span data-ttu-id="21183-132">Para clientes de acesso remoto computersto o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="21183-132">For clients on remote computersto access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>  
  
 <span data-ttu-id="21183-133">A estrutura não expõem metadados por padrão.</span><span class="sxs-lookup"><span data-stu-id="21183-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="21183-134">Como tal, o serviço ativa o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e expõe um ponto de extremidade do exchange (MEX) de metadados em http://localhost/servicemodelsamples/service.svc/mex.</span><span class="sxs-lookup"><span data-stu-id="21183-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="21183-135">A configuração a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="21183-135">The following configuration demonstrates this.</span></span>  
  
```xaml  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- the mex endpoint is explosed at  
       http://localhost/servicemodelsamples/service.svc/mex -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults  
   attribute to true-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="21183-136">O cliente se comunica usando um tipo de dado contrato usando uma classe cliente gerada pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="21183-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="21183-137">Esse cliente gerado está contido no arquivo generatedClient.cs ou generatedClient.vb.</span><span class="sxs-lookup"><span data-stu-id="21183-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="21183-138">Esse utilitário recupera metadados para um determinado serviço e gera um cliente para uso pelo aplicativo cliente para se comunicar usando um tipo de dado contrato.</span><span class="sxs-lookup"><span data-stu-id="21183-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="21183-139">O serviço hospedado deve estar disponível para gerar o código de cliente, porque o serviço é usado para recuperar os metadados atualizados.</span><span class="sxs-lookup"><span data-stu-id="21183-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>  
  
 <span data-ttu-id="21183-140">Execute o seguinte comando no prompt de comando do SDK no diretório do cliente para gerar o proxy do tipo:</span><span class="sxs-lookup"><span data-stu-id="21183-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
```  
  
 <span data-ttu-id="21183-141">Para gerar o cliente no Visual Basic digite o seguinte no prompt de comando do SDK:</span><span class="sxs-lookup"><span data-stu-id="21183-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>  
  
 `Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`  
  
 <span data-ttu-id="21183-142">Usando o cliente gerado, o cliente pode acessar um ponto de extremidade do serviço em questão, configurando o endereço apropriado e associação.</span><span class="sxs-lookup"><span data-stu-id="21183-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="21183-143">Como o serviço, o cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade com o qual deseja se comunicar.</span><span class="sxs-lookup"><span data-stu-id="21183-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="21183-144">A configuração do ponto de extremidade cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="21183-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>  
  
```xaml  
<client>  
     <endpoint  
         address="http://localhost/servicemodelsamples/service.svc"   
         binding="wsHttpBinding"   
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="21183-145">A implementação do cliente cria uma instância do cliente e usa a interface do tipo para começar a se comunicar com o serviço, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="21183-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>  
  
```vb  
' Create a client  
Dim client As New CalculatorClient()  
  
' Call the Add service operation.  
            Dim value1 = 100.0R  
            Dim value2 = 15.99R  
            Dim result = client.Add(value1, value2)  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
' Call the Subtract service operation.  
value1 = 145.00R  
value2 = 76.54R  
result = client.Subtract(value1, value2)  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
' Call the Multiply service operation.  
value1 = 9.00R  
value2 = 81.25R  
result = client.Multiply(value1, value2)  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
' Call the Divide service operation.  
value1 = 22.00R  
value2 = 7.00R  
result = client.Divide(value1, value2)  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
'Closing the client gracefully closes the connection and cleans up resources  
```  
  
```csharp  
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
// Call the Subtract service operation.  
value1 = 145.00D;  
value2 = 76.54D;  
result = client.Subtract(value1, value2);  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
// Call the Multiply service operation.  
value1 = 9.00D;  
value2 = 81.25D;  
result = client.Multiply(value1, value2);  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
// Call the Divide service operation.  
value1 = 22.00D;  
value2 = 7.00D;  
result = client.Divide(value1, value2);  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
//Closing the client releases all communication resources.  
client.Close();  
```  
  
 <span data-ttu-id="21183-146">Quando você executar o exemplo, as respostas e solicitações de operação são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="21183-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="21183-147">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="21183-147">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="21183-148">O exemplo de introdução mostra o modo padrão para criar um serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="21183-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="21183-149">O outro [básica](../../../../docs/framework/wcf/samples/basic-sample.md) criar este exemplo para demonstrar os recursos de produto específico.</span><span class="sxs-lookup"><span data-stu-id="21183-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="21183-150">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="21183-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="21183-151">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21183-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="21183-152">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21183-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="21183-153">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="21183-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21183-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21183-154">See Also</span></span>  
 [<span data-ttu-id="21183-155">Como hospedar um serviço do WCF em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="21183-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)  
 [<span data-ttu-id="21183-156">Como hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="21183-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
