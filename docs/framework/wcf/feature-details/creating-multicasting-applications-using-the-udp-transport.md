---
title: Criando aplicativos multicasting usando o transporte UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 6825aaafe87ae362fd9266f7c7a82a36d054a69f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185248"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="8a3c3-102">Criando aplicativos multicasting usando o transporte UDP</span><span class="sxs-lookup"><span data-stu-id="8a3c3-102">Creating Multicasting Applications using the UDP Transport</span></span>
<span data-ttu-id="8a3c3-103">Aplicativos de multicasting enviam pequenas mensagens para um grande número de destinatários ao mesmo tempo sem a necessidade de estabelecer conexões ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-103">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="8a3c3-104">A ênfase de tais aplicações é a velocidade sobre a confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-104">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="8a3c3-105">Em outras palavras, é mais importante enviar dados oportunos do que garantir que qualquer mensagem específica seja realmente recebida.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-105">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="8a3c3-106">O WCF agora suporta a gravação <xref:System.ServiceModel.UdpBinding>de aplicativos de multicasting usando o .</span><span class="sxs-lookup"><span data-stu-id="8a3c3-106">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="8a3c3-107">Este transporte é útil em cenários onde um serviço precisa enviar pequenas mensagens para um número de clientes simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-107">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="8a3c3-108">Um aplicativo de ticker de ações é um exemplo de tal serviço.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-108">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="8a3c3-109">Implementando um aplicativo multicast</span><span class="sxs-lookup"><span data-stu-id="8a3c3-109">Implementing a Multicast Application</span></span>  
 <span data-ttu-id="8a3c3-110">Para implementar um aplicativo multicast, defina um contrato de serviço e para cada componente de software que precise responder às mensagens multicast, implemente o contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-110">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="8a3c3-111">Por exemplo, um aplicativo de ticker de ações pode definir um contrato de serviço:</span><span class="sxs-lookup"><span data-stu-id="8a3c3-111">For example, a stock ticker application might define a service contract:</span></span>  
  
```csharp
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="8a3c3-112">Cada aplicativo que deseja receber mensagens multicast deve hospedar um serviço que exponha essa interface.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-112">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="8a3c3-113">Por exemplo, aqui está uma amostra de código que ilustra como receber mensagens multicast:</span><span class="sxs-lookup"><span data-stu-id="8a3c3-113">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```csharp
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="8a3c3-114">O aplicativo especifica o endereço UDP que todos os serviços estarão ouvindo.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-114">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="8a3c3-115">Um <xref:System.ServiceModel.ServiceHost> novo é criado e um ponto final <xref:System.ServiceModel.UdpBinding>de serviço é exposto usando o .</span><span class="sxs-lookup"><span data-stu-id="8a3c3-115">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="8a3c3-116">O <xref:System.ServiceModel.ServiceHost> é então aberto e começará a ouvir as mensagens recebidas.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-116">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="8a3c3-117">Nesse tipo de cenário é o cliente que realmente envia mensagens multicast.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-117">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="8a3c3-118">Cada serviço que estiver ouvindo no endereço UDP correto receberá as mensagens multicast.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-118">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="8a3c3-119">Aqui está um exemplo de um cliente que envia mensagens multicast:</span><span class="sxs-lookup"><span data-stu-id="8a3c3-119">Here is an example of a client that sends out multicast messages:</span></span>  
  
```csharp
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="8a3c3-120">Esse código gera informações de estoque e, em seguida, usa o contrato de serviço IStockTicker para enviar mensagens multicast para chamar serviços ouvindo no endereço UDP correto.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-120">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="8a3c3-121">UDP e Mensagens Confiáveis</span><span class="sxs-lookup"><span data-stu-id="8a3c3-121">UDP and Reliable Messaging</span></span>  
 <span data-ttu-id="8a3c3-122">A vinculação UDP não suporta mensagens confiáveis devido à natureza leve do protocolo UDP.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-122">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="8a3c3-123">Se você precisar confirmar se as mensagens são recebidas por um ponto final remoto, use um transporte que suporte mensagens confiáveis como HTTP ou TCP.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-123">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="8a3c3-124">Para obter mais informações sobre mensagens confiáveis, consultehttps://go.microsoft.com/fwlink/?LinkId=231830</span><span class="sxs-lookup"><span data-stu-id="8a3c3-124">For more information about reliable messaging see https://go.microsoft.com/fwlink/?LinkId=231830</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="8a3c3-125">Mensagens multi-vias de duas vias</span><span class="sxs-lookup"><span data-stu-id="8a3c3-125">Two-way Multicast Messaging</span></span>  
 <span data-ttu-id="8a3c3-126">Embora as mensagens multicast sejam geralmente unidirecionais, o UdpBinding faz suporte à troca de mensagens de solicitação/resposta.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-126">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="8a3c3-127">As mensagens enviadas usando o transporte UDP contêm um de e para o endereço.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-127">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="8a3c3-128">Deve-se tomar cuidado ao usar o endereço De, pois ele pode ser alterado maliciosamente no caminho.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-128">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="8a3c3-129">O endereço pode ser verificado usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8a3c3-129">The address can be checked using the following code:</span></span>  
  
```csharp
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="8a3c3-130">Este código verifica o primeiro byte do endereço De para ver se ele contém 0xE0, o que significa que o endereço é um endereço multi-cast.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-130">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="8a3c3-131">Considerações de segurança</span><span class="sxs-lookup"><span data-stu-id="8a3c3-131">Security Considerations</span></span>  
 <span data-ttu-id="8a3c3-132">Ao ouvir mensagens multicast, um pacote ICMP é enviado ao roteador notificando-o que você está ouvindo no endereço multicast.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-132">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="8a3c3-133">Qualquer pessoa na sub-rede local que tenha permissões poderia ouvir esses tipos de pacotes e determinar qual endereço multicast e porta você está ouvindo.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-133">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="8a3c3-134">Não use o endereço IP do remetente para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-134">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="8a3c3-135">Essas informações podem ser falsificadas e podem fazer com que um aplicativo envie respostas para a máquina errada.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-135">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="8a3c3-136">Uma maneira de mitigar essa ameaça é ativar a segurança do nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-136">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="8a3c3-137">No nível de rede, ipsec (Internet Protocol Security) e/ou NAP (Network Access Protection) também podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="8a3c3-137">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
