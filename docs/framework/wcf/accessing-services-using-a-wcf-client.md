---
title: Usando um cliente WCF para acessar um serviço
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 97340f8583ef0900645f6db5c453475e85549c55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620182"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="b51ba-102">Usando um cliente WCF para acessar um serviço</span><span class="sxs-lookup"><span data-stu-id="b51ba-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="b51ba-103">Depois de criar um serviço, a próxima etapa é criar um proxy de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="b51ba-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="b51ba-104">Um aplicativo cliente usa o proxy de cliente do WCF para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="b51ba-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="b51ba-105">Normalmente, aplicativos cliente importar metadados de um serviço para gerar o código de cliente do WCF que pode ser usado para invocar o serviço.</span><span class="sxs-lookup"><span data-stu-id="b51ba-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="b51ba-106">As etapas básicas para a criação de um cliente WCF incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b51ba-106">The basic steps for creating a WCF client include the following:</span></span>

1.  <span data-ttu-id="b51ba-107">Compile o código de serviço.</span><span class="sxs-lookup"><span data-stu-id="b51ba-107">Compile the service code.</span></span>

2.  <span data-ttu-id="b51ba-108">Gere o proxy de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="b51ba-108">Generate the WCF client proxy.</span></span>

3.  <span data-ttu-id="b51ba-109">Instancie o proxy de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="b51ba-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="b51ba-110">O proxy de cliente do WCF pode ser gerado manualmente usando a ferramenta Utilitário de serviço de modelo de metadados (SvcUtil.exe) para obter mais informações, consulte [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b51ba-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b51ba-111">O proxy de cliente do WCF também pode ser gerado dentro do Visual Studio usando o **adicionar referência de serviço** recurso.</span><span class="sxs-lookup"><span data-stu-id="b51ba-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="b51ba-112">Para gerar o proxy de cliente do WCF usando um método de serviço deve estar em execução.</span><span class="sxs-lookup"><span data-stu-id="b51ba-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="b51ba-113">Se o serviço for auto-hospedado, você deve executar o host.</span><span class="sxs-lookup"><span data-stu-id="b51ba-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="b51ba-114">Se o serviço está hospedado no IIS / WAS não é preciso fazer mais nada.</span><span class="sxs-lookup"><span data-stu-id="b51ba-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="b51ba-115">Ferramenta Utilitário de metadados de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b51ba-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="b51ba-116">O [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) é uma ferramenta de linha de comando para gerar o código dos metadados.</span><span class="sxs-lookup"><span data-stu-id="b51ba-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="b51ba-117">O uso a seguir é um exemplo de um comando Svcutil.exe básico.</span><span class="sxs-lookup"><span data-stu-id="b51ba-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="b51ba-118">Como alternativa, você pode usar Svcutil.exe com arquivos de idioma (XSD) de definição descrição linguagem WSDL (Web Services) e o esquema XML no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="b51ba-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="b51ba-119">O resultado é um arquivo de código que contém o código de cliente do WCF que o aplicativo cliente pode usar para invocar o serviço.</span><span class="sxs-lookup"><span data-stu-id="b51ba-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="b51ba-120">Você também pode usar a ferramenta para gerar arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="b51ba-120">You can also use the tool to generate configuration files.</span></span>

```
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="b51ba-121">Se apenas um nome de arquivo for fornecido, que é o nome do arquivo de saída.</span><span class="sxs-lookup"><span data-stu-id="b51ba-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="b51ba-122">Se dois nomes de arquivo fornecidos, o primeiro arquivo é um arquivo de configuração de entrada cujo conteúdo é mesclado com a configuração gerada e gravado no segundo arquivo.</span><span class="sxs-lookup"><span data-stu-id="b51ba-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="b51ba-123">Para obter mais informações sobre a configuração, consulte [configurando associações para serviços](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b51ba-123">For more information about configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b51ba-124">Solicitações de metadados não segura representam certos riscos da mesma maneira que faz a qualquer solicitação de rede não segura: Se não tiver certeza de que você está se comunicando com o ponto de extremidade é quem diz ser, as informações recuperadas podem ser metadados de um serviço mal-intencionado.</span><span class="sxs-lookup"><span data-stu-id="b51ba-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="b51ba-125">Adicionar referência de serviço no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b51ba-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="b51ba-126">Com o serviço em execução com o botão direito do mouse no projeto que conterá o proxy de cliente do WCF e selecione **Add** > **referência de serviço**.</span><span class="sxs-lookup"><span data-stu-id="b51ba-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="b51ba-127">No **adicionar referência de caixa de diálogo serviço**, digite a URL para o serviço que você deseja chamar e clique no **vá** botão.</span><span class="sxs-lookup"><span data-stu-id="b51ba-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="b51ba-128">A caixa de diálogo exibirá uma lista de serviços disponíveis no endereço que você especificar.</span><span class="sxs-lookup"><span data-stu-id="b51ba-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="b51ba-129">Clique duas vezes o serviço para ver os contratos e operações disponíveis, especifique um namespace para o código gerado e clique no **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="b51ba-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="b51ba-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b51ba-130">Example</span></span>
 <span data-ttu-id="b51ba-131">O exemplo de código a seguir mostra um contrato de serviço criado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b51ba-131">The following code example shows a service contract created for a service.</span></span>

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

 <span data-ttu-id="b51ba-132">A ferramenta de utilitário ServiceModel Metadata e **adicionar referência de serviço** no Visual Studio gera a seguinte classe de cliente do WCF.</span><span class="sxs-lookup"><span data-stu-id="b51ba-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="b51ba-133">A classe herda de genéricos <xref:System.ServiceModel.ClientBase%601> classe e implementa o `ICalculator` interface.</span><span class="sxs-lookup"><span data-stu-id="b51ba-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="b51ba-134">A ferramenta também gera o `ICalculator` interface (não mostrado aqui).</span><span class="sxs-lookup"><span data-stu-id="b51ba-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

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

## <a name="using-the-wcf-client"></a><span data-ttu-id="b51ba-135">Usando o cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="b51ba-135">Using the WCF Client</span></span>
 <span data-ttu-id="b51ba-136">Para usar o cliente do WCF, crie uma instância do cliente WCF e, em seguida, chamar seus métodos, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b51ba-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

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

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="b51ba-137">Depuração de exceções geradas por um cliente</span><span class="sxs-lookup"><span data-stu-id="b51ba-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="b51ba-138">Muitas exceções geradas por um cliente WCF são causadas por uma exceção no serviço.</span><span class="sxs-lookup"><span data-stu-id="b51ba-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="b51ba-139">Alguns exemplos disso são:</span><span class="sxs-lookup"><span data-stu-id="b51ba-139">Some examples of this are:</span></span>

-   <span data-ttu-id="b51ba-140"><xref:System.Net.Sockets.SocketException>: Uma conexão existente foi fechada forçadamente pelo host remoto.</span><span class="sxs-lookup"><span data-stu-id="b51ba-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

-   <span data-ttu-id="b51ba-141"><xref:System.ServiceModel.CommunicationException>: A conexão subjacente foi fechado inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="b51ba-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

-   <span data-ttu-id="b51ba-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: A conexão de soquete foi anulada.</span><span class="sxs-lookup"><span data-stu-id="b51ba-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="b51ba-143">Isso pode ser causado por um erro ao processar a mensagem, um tempo limite de recebimento foi excedido pelo host remoto ou um problema de recurso de rede subjacente.</span><span class="sxs-lookup"><span data-stu-id="b51ba-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="b51ba-144">Quando esses tipos de exceções ocorrem, a melhor maneira de resolver o problema é ativar o rastreamento no lado do serviço e determinar qual exceção ocorreu lá.</span><span class="sxs-lookup"><span data-stu-id="b51ba-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="b51ba-145">Para obter mais informações sobre rastreamento, consulte [rastreamento](../../../docs/framework/wcf/diagnostics/tracing/index.md) e [usando o rastreamento para solucionar problemas de seu aplicativo](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="b51ba-145">For more information about tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b51ba-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b51ba-146">See also</span></span>

- [<span data-ttu-id="b51ba-147">Como: Criar um cliente</span><span class="sxs-lookup"><span data-stu-id="b51ba-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="b51ba-148">Como: Serviços do Access com um contrato Duplex</span><span class="sxs-lookup"><span data-stu-id="b51ba-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="b51ba-149">Como: Chamar operações de serviço de forma assíncrona</span><span class="sxs-lookup"><span data-stu-id="b51ba-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="b51ba-150">Como: Acessar os serviços com unidirecional e contratos de solicitação-resposta</span><span class="sxs-lookup"><span data-stu-id="b51ba-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="b51ba-151">Como: Acessar um WSE 3.0 Service</span><span class="sxs-lookup"><span data-stu-id="b51ba-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="b51ba-152">Entendendo o código do cliente gerado</span><span class="sxs-lookup"><span data-stu-id="b51ba-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="b51ba-153">Como: Melhorar o tempo de inicialização do WCF cliente aplicativos usando o XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b51ba-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="b51ba-154">Especificando o comportamento em tempo de execução do cliente</span><span class="sxs-lookup"><span data-stu-id="b51ba-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="b51ba-155">Configurando comportamentos do cliente</span><span class="sxs-lookup"><span data-stu-id="b51ba-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
