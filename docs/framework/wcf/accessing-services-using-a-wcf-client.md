---
title: Usando um cliente WCF para acessar um serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 462d9a3923009f0124c2b90b6fa86dfa9869a3c5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72316537"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="6d322-102">Usando um cliente WCF para acessar um serviço</span><span class="sxs-lookup"><span data-stu-id="6d322-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="6d322-103">Depois de criar um serviço, a próxima etapa é criar um proxy de cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="6d322-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="6d322-104">Um aplicativo cliente usa o proxy do cliente WCF para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="6d322-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="6d322-105">Normalmente, os aplicativos cliente importam os metadados de um serviço para gerar o código do cliente WCF que pode ser usado para invocar o serviço.</span><span class="sxs-lookup"><span data-stu-id="6d322-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="6d322-106">As etapas básicas para criar um cliente WCF incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6d322-106">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="6d322-107">Compile o código do serviço.</span><span class="sxs-lookup"><span data-stu-id="6d322-107">Compile the service code.</span></span>

2. <span data-ttu-id="6d322-108">Gere o proxy do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="6d322-108">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="6d322-109">Crie uma instância do proxy do cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="6d322-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="6d322-110">O proxy do cliente WCF pode ser gerado manualmente usando a ferramenta de utilitário de metadados do modelo de serviço (SvcUtil. exe) para obter mais informações, consulte [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6d322-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="6d322-111">O proxy do cliente WCF também pode ser gerado no Visual Studio usando o recurso **Adicionar referência de serviço** .</span><span class="sxs-lookup"><span data-stu-id="6d322-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="6d322-112">Para gerar o proxy do cliente WCF usando qualquer um dos métodos, o serviço deve estar em execução.</span><span class="sxs-lookup"><span data-stu-id="6d322-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="6d322-113">Se o serviço for auto-hospedado, você deverá executar o host.</span><span class="sxs-lookup"><span data-stu-id="6d322-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="6d322-114">Se o serviço estiver hospedado no IIS/WAS, você não precisará fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="6d322-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="6d322-115">Ferramenta de utilitário de metadados ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6d322-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="6d322-116">A [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) é uma ferramenta de linha de comando para gerar código a partir de metadados.</span><span class="sxs-lookup"><span data-stu-id="6d322-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="6d322-117">O uso a seguir é um exemplo de um comando svcutil. exe básico.</span><span class="sxs-lookup"><span data-stu-id="6d322-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="6d322-118">Como alternativa, você pode usar svcutil. exe com arquivos WSDL (linguagem de descrição de serviços Web) e XSD (XML Schema Definition Language) no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="6d322-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="6d322-119">O resultado é um arquivo de código que contém o código do cliente WCF que o aplicativo cliente pode usar para invocar o serviço.</span><span class="sxs-lookup"><span data-stu-id="6d322-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="6d322-120">Você também pode usar a ferramenta para gerar arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="6d322-120">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="6d322-121">Se apenas um nome de arquivo for fornecido, esse será o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="6d322-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="6d322-122">Se dois nomes de arquivo forem fornecidos, o primeiro arquivo será um arquivo de configuração de entrada cujo conteúdo será mesclado com a configuração gerada e gravado no segundo arquivo.</span><span class="sxs-lookup"><span data-stu-id="6d322-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="6d322-123">Para obter mais informações sobre configuração, consulte [Configurando associações para serviços](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="6d322-123">For more information about configuration, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d322-124">As solicitações de metadados não seguras apresentam determinados riscos da mesma forma que qualquer solicitação de rede não segura: se você não tiver certeza de que o ponto de extremidade com o qual está se comunicando é quem diz ser, as informações recuperadas poderão ser metadados de um serviço mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="6d322-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="6d322-125">Adicionar Referência de Serviço no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6d322-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="6d322-126">Com o serviço em execução, clique com o botão direito do mouse no projeto que conterá o proxy do cliente WCF e selecione **Adicionar** **referência de serviço** > .</span><span class="sxs-lookup"><span data-stu-id="6d322-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="6d322-127">Na **caixa de diálogo Adicionar referência de serviço**, digite a URL para o serviço que você deseja chamar e clique no botão **ir** .</span><span class="sxs-lookup"><span data-stu-id="6d322-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="6d322-128">A caixa de diálogo exibirá uma lista de serviços disponíveis no endereço que você especificar.</span><span class="sxs-lookup"><span data-stu-id="6d322-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="6d322-129">Clique duas vezes no serviço para ver os contratos e as operações disponíveis, especifique um namespace para o código gerado e clique no botão **OK** .</span><span class="sxs-lookup"><span data-stu-id="6d322-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="6d322-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d322-130">Example</span></span>
 <span data-ttu-id="6d322-131">O exemplo de código a seguir mostra um contrato de serviço criado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="6d322-131">The following code example shows a service contract created for a service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 <span data-ttu-id="6d322-132">A ferramenta de utilitário de metadados ServiceModel e o **Adicionar referência de serviço** no Visual Studio geram a seguinte classe de cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="6d322-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="6d322-133">A classe herda da classe <xref:System.ServiceModel.ClientBase%601> genérica e implementa a interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="6d322-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="6d322-134">A ferramenta também gera a interface `ICalculator` (não mostrada aqui).</span><span class="sxs-lookup"><span data-stu-id="6d322-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a><span data-ttu-id="6d322-135">Usando o cliente WCF</span><span class="sxs-lookup"><span data-stu-id="6d322-135">Using the WCF Client</span></span>
 <span data-ttu-id="6d322-136">Para usar o cliente WCF, crie uma instância do cliente WCF e, em seguida, chame seus métodos, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="6d322-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="6d322-137">Exceções de depuração geradas por um cliente</span><span class="sxs-lookup"><span data-stu-id="6d322-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="6d322-138">Muitas exceções geradas por um cliente WCF são causadas por uma exceção no serviço.</span><span class="sxs-lookup"><span data-stu-id="6d322-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="6d322-139">Alguns exemplos disso são:</span><span class="sxs-lookup"><span data-stu-id="6d322-139">Some examples of this are:</span></span>

- <span data-ttu-id="6d322-140"><xref:System.Net.Sockets.SocketException>: uma conexão existente foi fechada forçosamente pelo host remoto.</span><span class="sxs-lookup"><span data-stu-id="6d322-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="6d322-141"><xref:System.ServiceModel.CommunicationException>: a conexão subjacente foi fechada inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="6d322-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="6d322-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: a conexão de soquete foi anulada.</span><span class="sxs-lookup"><span data-stu-id="6d322-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="6d322-143">Isso pode ser causado por um erro ao processar sua mensagem, um tempo limite de recebimento excedido pelo host remoto ou um problema de recurso de rede subjacente.</span><span class="sxs-lookup"><span data-stu-id="6d322-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="6d322-144">Quando ocorrem esses tipos de exceções, a melhor maneira de resolver o problema é ativar o rastreamento no lado do serviço e determinar qual exceção ocorreu lá.</span><span class="sxs-lookup"><span data-stu-id="6d322-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="6d322-145">Para obter mais informações sobre rastreamento, consulte [rastreamento](./diagnostics/tracing/index.md) e [uso de rastreamento para solucionar problemas de seu aplicativo](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="6d322-145">For more information about tracing, see [Tracing](./diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6d322-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d322-146">See also</span></span>

- [<span data-ttu-id="6d322-147">Como criar um cliente</span><span class="sxs-lookup"><span data-stu-id="6d322-147">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="6d322-148">Como acessar serviços com um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="6d322-148">How to: Access Services with a Duplex Contract</span></span>](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="6d322-149">Como chamar operações de serviço de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="6d322-149">How to: Call Service Operations Asynchronously</span></span>](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="6d322-150">Como acessar os serviços com contratos unidirecionais e de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="6d322-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="6d322-151">Como acessar um WSE 3.0 Service</span><span class="sxs-lookup"><span data-stu-id="6d322-151">How to: Access a WSE 3.0 Service</span></span>](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="6d322-152">Entendendo o código do cliente gerado</span><span class="sxs-lookup"><span data-stu-id="6d322-152">Understanding Generated Client Code</span></span>](./feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="6d322-153">Como melhorar o tempo de inicialização de aplicativos clientes WCF usando o XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="6d322-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="6d322-154">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="6d322-154">Specifying Client Run-Time Behavior</span></span>](specifying-client-run-time-behavior.md)
- [<span data-ttu-id="6d322-155">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="6d322-155">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
