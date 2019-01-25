---
title: Cabeçalhos de endereço
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 1c4a64b80ac629c740aea3dbdec2ab270ab061c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632927"
---
# <a name="address-headers"></a><span data-ttu-id="84f0b-102">Cabeçalhos de endereço</span><span class="sxs-lookup"><span data-stu-id="84f0b-102">Address Headers</span></span>
<span data-ttu-id="84f0b-103">O exemplo de cabeçalhos de endereço demonstra como os clientes podem passar parâmetros de referência a um serviço usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="84f0b-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using Windows Communication Foundation (WCF).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84f0b-104">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="84f0b-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="84f0b-105">A especificação de WS-Addressing define a noção de uma referência de ponto de extremidade como uma maneira de resolver um ponto de extremidade de serviço Web específico.</span><span class="sxs-lookup"><span data-stu-id="84f0b-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="84f0b-106">No WCF, referências de ponto de extremidade são modeladas usando o `EndpointAddress` classe - `EndpointAddress` é o tipo de campo de endereço do `ServiceEndpoint` classe.</span><span class="sxs-lookup"><span data-stu-id="84f0b-106">In WCF, endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="84f0b-107">Parte do modelo de referência de ponto de extremidade é que cada referência pode executar alguns parâmetros de referência que adicionar informações de identificação extra.</span><span class="sxs-lookup"><span data-stu-id="84f0b-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="84f0b-108">No WCF, esses parâmetros de referência são modelados como instâncias de `AddressHeader` classe.</span><span class="sxs-lookup"><span data-stu-id="84f0b-108">In WCF, these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="84f0b-109">Neste exemplo, o cliente adiciona um parâmetro de referência para o `EndpointAddress` do ponto de extremidade de cliente.</span><span class="sxs-lookup"><span data-stu-id="84f0b-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="84f0b-110">O serviço procura esse parâmetro de referência e use seu valor na lógica de sua operação de serviço "Hello".</span><span class="sxs-lookup"><span data-stu-id="84f0b-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="84f0b-111">Cliente</span><span class="sxs-lookup"><span data-stu-id="84f0b-111">Client</span></span>  
 <span data-ttu-id="84f0b-112">Para o cliente enviar um parâmetro de referência, ele deve adicionar um `AddressHeader` para o `EndpointAddress` da `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="84f0b-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="84f0b-113">Porque o `EndpointAddress` classe é imutável, a modificação de um endereço de ponto de extremidade deve ser feita usando o `EndpointAddressBuilder` classe.</span><span class="sxs-lookup"><span data-stu-id="84f0b-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="84f0b-114">O código a seguir inicializa o cliente para enviar um parâmetro de referência como parte de sua mensagem.</span><span class="sxs-lookup"><span data-stu-id="84f0b-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="84f0b-115">O código cria um `EndpointAddressBuilder` usando o original `EndpointAddress` como um valor inicial.</span><span class="sxs-lookup"><span data-stu-id="84f0b-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="84f0b-116">Depois, ele adiciona um cabeçalho de endereço recém-criado. a chamada para `CreateAddressHeadercreates` um cabeçalho com um determinado nome, namespace e valor.</span><span class="sxs-lookup"><span data-stu-id="84f0b-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="84f0b-117">Aqui, o valor é "John".</span><span class="sxs-lookup"><span data-stu-id="84f0b-117">Here the value is "John".</span></span> <span data-ttu-id="84f0b-118">Depois que o cabeçalho é adicionado ao construtor, o `ToEndpointAddress()` método converte o construtor (mutável) volta para um endereço de ponto de extremidade (imutáveis), que é atribuído de volta ao campo de endereço do ponto de extremidade de cliente.</span><span class="sxs-lookup"><span data-stu-id="84f0b-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="84f0b-119">Agora quando o cliente chama `Console.WriteLine(client.Hello());`, o serviço é capaz de obter o valor desse parâmetro de endereço, como mostra a saída resultante do cliente.</span><span class="sxs-lookup"><span data-stu-id="84f0b-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="84f0b-120">Servidor</span><span class="sxs-lookup"><span data-stu-id="84f0b-120">Server</span></span>  
 <span data-ttu-id="84f0b-121">A implementação da operação de serviço `Hello()` usa atual `OperationContext` para inspecionar os valores dos cabeçalhos na mensagem de entrada.</span><span class="sxs-lookup"><span data-stu-id="84f0b-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
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
  
 <span data-ttu-id="84f0b-122">O código itera em todos os cabeçalhos na mensagem de entrada, procurando os cabeçalhos que são parâmetros de referência com o nome específico e.</span><span class="sxs-lookup"><span data-stu-id="84f0b-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="84f0b-123">Quando o parâmetro for encontrado, ele lê o valor do parâmetro e o armazena na variável "id".</span><span class="sxs-lookup"><span data-stu-id="84f0b-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="84f0b-124">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="84f0b-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="84f0b-125">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84f0b-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="84f0b-126">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84f0b-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="84f0b-127">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84f0b-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84f0b-128">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="84f0b-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="84f0b-129">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="84f0b-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="84f0b-130">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="84f0b-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84f0b-131">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="84f0b-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="84f0b-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84f0b-132">See also</span></span>
