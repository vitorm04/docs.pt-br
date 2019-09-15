---
title: Exemplo de introdução
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: 5f5418da63b2bc5fc9b20f5c262890b7a06ce5dd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989917"
---
# <a name="getting-started-sample"></a><span data-ttu-id="c510a-102">Exemplo de introdução</span><span class="sxs-lookup"><span data-stu-id="c510a-102">Getting Started Sample</span></span>

<span data-ttu-id="c510a-103">O exemplo a Introdução demonstra como implementar um serviço típico e um cliente típico usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c510a-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c510a-104">Este exemplo é a base para todos os outros exemplos de tecnologia básica.</span><span class="sxs-lookup"><span data-stu-id="c510a-104">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="c510a-105">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c510a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c510a-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c510a-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c510a-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c510a-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c510a-108">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="c510a-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c510a-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c510a-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="c510a-110">O serviço descreve as operações que ele realiza em um contrato de serviço que ele expõe publicamente como metadados.</span><span class="sxs-lookup"><span data-stu-id="c510a-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="c510a-111">O serviço também contém o código para implementar as operações.</span><span class="sxs-lookup"><span data-stu-id="c510a-111">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="c510a-112">O cliente contém uma definição do contrato de serviço e uma classe de proxy para acessar o serviço.</span><span class="sxs-lookup"><span data-stu-id="c510a-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="c510a-113">O código do proxy é gerado a partir dos metadados de serviço usando a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c510a-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="c510a-114">No [!INCLUDE[wv](../../../../includes/wv-md.md)], o serviço está hospedado no serviço de ativação do Windows (was).</span><span class="sxs-lookup"><span data-stu-id="c510a-114">On [!INCLUDE[wv](../../../../includes/wv-md.md)], the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="c510a-115">No [!INCLUDE[wxp](../../../../includes/wxp-md.md)] e[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], ele é hospedado por serviços de informações da Internet (IIS) e ASP.net.</span><span class="sxs-lookup"><span data-stu-id="c510a-115">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="c510a-116">Hospedar um serviço no IIS ou WAS permite que o serviço seja ativado automaticamente quando é acessado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="c510a-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="c510a-117">Se você preferir começar com um exemplo que hospede o serviço em um aplicativo de console em vez de IIS, consulte o exemplo de hospedagem [interna](../../../../docs/framework/wcf/samples/self-host.md) .</span><span class="sxs-lookup"><span data-stu-id="c510a-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>

<span data-ttu-id="c510a-118">O serviço e o cliente especificam detalhes de acesso nas configurações do arquivo de configuração, que fornecem flexibilidade no momento da implantação.</span><span class="sxs-lookup"><span data-stu-id="c510a-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="c510a-119">Isso inclui uma definição de ponto de extremidade que especifica um endereço, associação e contrato.</span><span class="sxs-lookup"><span data-stu-id="c510a-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="c510a-120">A associação especifica os detalhes de transporte e segurança de como o serviço deve ser acessado.</span><span class="sxs-lookup"><span data-stu-id="c510a-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="c510a-121">O serviço configura um comportamento de tempo de execução para publicar seus metadados.</span><span class="sxs-lookup"><span data-stu-id="c510a-121">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="c510a-122">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="c510a-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c510a-123">O contrato é definido pela `ICalculator` interface, que expõe operações matemáticas (adicionar, subtrair, multiplicar e dividir).</span><span class="sxs-lookup"><span data-stu-id="c510a-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="c510a-124">O cliente faz solicitações para uma determinada operação matemática e o serviço responde com o resultado.</span><span class="sxs-lookup"><span data-stu-id="c510a-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="c510a-125">O serviço implementa um `ICalculator` contrato que é definido no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c510a-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

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

<span data-ttu-id="c510a-126">A implementação do serviço calcula e retorna o resultado apropriado, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c510a-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

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

<span data-ttu-id="c510a-127">O serviço expõe um ponto de extremidade para se comunicar com o serviço, definido usando um arquivo de configuração (Web. config), conforme mostrado na seguinte configuração de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c510a-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="c510a-128">O serviço expõe o ponto de extremidade no endereço base fornecido pelo IIS ou pelo host.</span><span class="sxs-lookup"><span data-stu-id="c510a-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="c510a-129">A associação é configurada com <xref:System.ServiceModel.WSHttpBinding>um padrão, que fornece comunicação http e protocolos de serviço Web padrão para endereçamento e segurança.</span><span class="sxs-lookup"><span data-stu-id="c510a-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="c510a-130">O contrato é `ICalculator` implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="c510a-130">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="c510a-131">Conforme configurado, o serviço pode ser acessado pelo `http://localhost/servicemodelsamples/service.svc` cliente do no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="c510a-131">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="c510a-132">Para clientes em computadores remotos acessarem o serviço, um nome de domínio totalmente qualificado deve ser especificado em vez de localhost.</span><span class="sxs-lookup"><span data-stu-id="c510a-132">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="c510a-133">A estrutura não expõe metadados por padrão.</span><span class="sxs-lookup"><span data-stu-id="c510a-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="c510a-134">Como tal, o serviço ativa o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> e expõe um ponto de extremidade de intercâmbio de metadados (MEX) em. `http://localhost/servicemodelsamples/service.svc/mex`</span><span class="sxs-lookup"><span data-stu-id="c510a-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="c510a-135">A configuração a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="c510a-135">The following configuration demonstrates this.</span></span>

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
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

<span data-ttu-id="c510a-136">O cliente se comunica usando um determinado tipo de contrato usando uma classe de cliente que é gerada pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c510a-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="c510a-137">Esse cliente gerado está contido no arquivo generatedClient.cs ou generatedClient. vb.</span><span class="sxs-lookup"><span data-stu-id="c510a-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="c510a-138">Esse utilitário recupera metadados para um determinado serviço e gera um cliente para ser usado pelo aplicativo cliente para se comunicar usando um determinado tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="c510a-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="c510a-139">O serviço hospedado deve estar disponível para gerar o código do cliente, pois o serviço é usado para recuperar os metadados atualizados.</span><span class="sxs-lookup"><span data-stu-id="c510a-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="c510a-140">Execute o seguinte comando no prompt de comando do SDK no diretório do cliente para gerar o proxy de tipo:</span><span class="sxs-lookup"><span data-stu-id="c510a-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="c510a-141">Para gerar o cliente no Visual Basic Digite o seguinte no prompt de comando do SDK:</span><span class="sxs-lookup"><span data-stu-id="c510a-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="c510a-142">Usando o cliente gerado, o cliente pode acessar um determinado ponto de extremidade de serviço Configurando o endereço e a associação apropriados.</span><span class="sxs-lookup"><span data-stu-id="c510a-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="c510a-143">Assim como o serviço, o cliente usa um arquivo de configuração (App. config) para especificar o ponto de extremidade com o qual deseja se comunicar.</span><span class="sxs-lookup"><span data-stu-id="c510a-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="c510a-144">A configuração de ponto de extremidade do cliente consiste em um endereço absoluto para o ponto de extremidade de serviço, a associação e o contrato, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c510a-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="c510a-145">A implementação do cliente instancia o cliente e usa a interface digitada para começar a se comunicar com o serviço, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c510a-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

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

<span data-ttu-id="c510a-146">Quando você executa o exemplo, as solicitações de operação e as respostas são exibidas na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="c510a-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c510a-147">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="c510a-147">Press ENTER in the client window to shut down the client.</span></span>

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="c510a-148">O exemplo a Introdução mostra a maneira padrão de criar um serviço e um cliente.</span><span class="sxs-lookup"><span data-stu-id="c510a-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="c510a-149">A outra compilação [básica](../../../../docs/framework/wcf/samples/basic-sample.md) neste exemplo para demonstrar recursos específicos do produto.</span><span class="sxs-lookup"><span data-stu-id="c510a-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c510a-150">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="c510a-150">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c510a-151">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c510a-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c510a-152">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c510a-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="c510a-153">Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c510a-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c510a-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c510a-154">See also</span></span>

- [<span data-ttu-id="c510a-155">Como: Hospedar um serviço WCF em um aplicativo gerenciado</span><span class="sxs-lookup"><span data-stu-id="c510a-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="c510a-156">Como: Hospedar um serviço WCF no IIS</span><span class="sxs-lookup"><span data-stu-id="c510a-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
