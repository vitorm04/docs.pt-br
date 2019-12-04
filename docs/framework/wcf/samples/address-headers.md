---
title: Cabeçalhos de endereço
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 3bc8512fb2492a7249c81fc33a3c7b83904f1ccd
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715223"
---
# <a name="address-headers"></a><span data-ttu-id="39cd6-102">Cabeçalhos de endereço</span><span class="sxs-lookup"><span data-stu-id="39cd6-102">Address Headers</span></span>

<span data-ttu-id="39cd6-103">O exemplo de cabeçalhos de endereço demonstra como os clientes podem passar parâmetros de referência para um serviço usando Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="39cd6-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>

> [!NOTE]
> <span data-ttu-id="39cd6-104">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="39cd6-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="39cd6-105">A especificação WS-Addressing define a noção de uma referência de ponto de extremidade como uma maneira de resolver um ponto de extremidade de serviço Web específico.</span><span class="sxs-lookup"><span data-stu-id="39cd6-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="39cd6-106">No WCF, as referências de ponto de extremidade são modeladas usando o `EndpointAddress` classe-`EndpointAddress` é o tipo do campo de endereço da classe `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>

<span data-ttu-id="39cd6-107">Parte do modelo de referência do ponto de extremidade é que cada referência pode executar alguns parâmetros de referência que adicionam informações de identificação extras.</span><span class="sxs-lookup"><span data-stu-id="39cd6-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="39cd6-108">No WCF, esses parâmetros de referência são modelados como instâncias da classe `AddressHeader`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>

<span data-ttu-id="39cd6-109">Neste exemplo, o cliente adiciona um parâmetro de referência à `EndpointAddress` do ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="39cd6-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="39cd6-110">O serviço procura esse parâmetro de referência e usa seu valor na lógica de sua operação de serviço "Olá".</span><span class="sxs-lookup"><span data-stu-id="39cd6-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>

## <a name="client"></a><span data-ttu-id="39cd6-111">Cliente</span><span class="sxs-lookup"><span data-stu-id="39cd6-111">Client</span></span>

<span data-ttu-id="39cd6-112">Para que o cliente envie um parâmetro de referência, ele deve adicionar um `AddressHeader` ao `EndpointAddress` do `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="39cd6-113">Como a classe `EndpointAddress` é imutável, a modificação de um endereço de ponto de extremidade deve ser feita usando a classe `EndpointAddressBuilder`.</span><span class="sxs-lookup"><span data-stu-id="39cd6-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="39cd6-114">O código a seguir inicializa o cliente para enviar um parâmetro de referência como parte de sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="39cd6-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

<span data-ttu-id="39cd6-115">O código cria um `EndpointAddressBuilder` usando o `EndpointAddress` original como um valor inicial.</span><span class="sxs-lookup"><span data-stu-id="39cd6-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="39cd6-116">Em seguida, ele adiciona um cabeçalho de endereço recém-criado; a chamada para `CreateAddressHeader` cria um cabeçalho com um nome, namespace e valor específicos.</span><span class="sxs-lookup"><span data-stu-id="39cd6-116">It then adds a newly created address header; the call to `CreateAddressHeader` creates a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="39cd6-117">Aqui, o valor é "João".</span><span class="sxs-lookup"><span data-stu-id="39cd6-117">Here the value is "John".</span></span> <span data-ttu-id="39cd6-118">Depois que o cabeçalho é adicionado ao construtor, o método `ToEndpointAddress()` converte o Construtor (mutável) de volta em um endereço de ponto de extremidade (imutável), que é atribuído de volta ao campo de endereço do ponto de extremidade do cliente.</span><span class="sxs-lookup"><span data-stu-id="39cd6-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>

<span data-ttu-id="39cd6-119">Agora, quando o cliente chama `Console.WriteLine(client.Hello());`, o serviço é capaz de obter o valor desse parâmetro de endereço, como visto na saída resultante do cliente.</span><span class="sxs-lookup"><span data-stu-id="39cd6-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>

`Hello, John`

## <a name="server"></a><span data-ttu-id="39cd6-120">Server</span><span class="sxs-lookup"><span data-stu-id="39cd6-120">Server</span></span>

<span data-ttu-id="39cd6-121">A implementação da operação de serviço `Hello()` usa o `OperationContext` atual para inspecionar os valores dos cabeçalhos na mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="39cd6-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>

```csharp
string id = null;
// look at headers on incoming message
for (int i = 0;
     i < OperationContext.Current.IncomingMessageHeaders.Count;
     ++i)
{
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];
    // for any reference parameters with the correct name & namespace
    if (h.IsReferenceParameter &&
        h.Name == IDName &&
        h.Namespace == IDNamespace)
    {
        // read the value of that header
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);
        id = xr.ReadElementContentAsString();
    }
}
return "Hello, " + id;
```

<span data-ttu-id="39cd6-122">O código itera em todos os cabeçalhos na mensagem de entrada, procurando cabeçalhos que são parâmetros de referência com o nome específico e.</span><span class="sxs-lookup"><span data-stu-id="39cd6-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="39cd6-123">Quando o parâmetro é encontrado, ele lê o valor do parâmetro e o armazena na variável "ID".</span><span class="sxs-lookup"><span data-stu-id="39cd6-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="39cd6-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="39cd6-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="39cd6-125">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="39cd6-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="39cd6-126">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="39cd6-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="39cd6-127">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="39cd6-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39cd6-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="39cd6-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="39cd6-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="39cd6-129">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="39cd6-130">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="39cd6-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="39cd6-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="39cd6-131">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
