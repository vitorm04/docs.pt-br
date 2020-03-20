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
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Criando aplicativos multicasting usando o transporte UDP
Aplicativos de multicasting enviam pequenas mensagens para um grande número de destinatários ao mesmo tempo sem a necessidade de estabelecer conexões ponto a ponto. A ênfase de tais aplicações é a velocidade sobre a confiabilidade. Em outras palavras, é mais importante enviar dados oportunos do que garantir que qualquer mensagem específica seja realmente recebida. O WCF agora suporta a gravação <xref:System.ServiceModel.UdpBinding>de aplicativos de multicasting usando o . Este transporte é útil em cenários onde um serviço precisa enviar pequenas mensagens para um número de clientes simultaneamente. Um aplicativo de ticker de ações é um exemplo de tal serviço.  
  
## <a name="implementing-a-multicast-application"></a>Implementando um aplicativo multicast  
 Para implementar um aplicativo multicast, defina um contrato de serviço e para cada componente de software que precise responder às mensagens multicast, implemente o contrato de serviço. Por exemplo, um aplicativo de ticker de ações pode definir um contrato de serviço:  
  
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
  
 Cada aplicativo que deseja receber mensagens multicast deve hospedar um serviço que exponha essa interface.  Por exemplo, aqui está uma amostra de código que ilustra como receber mensagens multicast:  
  
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
  
 O aplicativo especifica o endereço UDP que todos os serviços estarão ouvindo. Um <xref:System.ServiceModel.ServiceHost> novo é criado e um ponto final <xref:System.ServiceModel.UdpBinding>de serviço é exposto usando o . O <xref:System.ServiceModel.ServiceHost> é então aberto e começará a ouvir as mensagens recebidas.  
  
 Nesse tipo de cenário é o cliente que realmente envia mensagens multicast. Cada serviço que estiver ouvindo no endereço UDP correto receberá as mensagens multicast. Aqui está um exemplo de um cliente que envia mensagens multicast:  
  
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
  
 Esse código gera informações de estoque e, em seguida, usa o contrato de serviço IStockTicker para enviar mensagens multicast para chamar serviços ouvindo no endereço UDP correto.  
  
### <a name="udp-and-reliable-messaging"></a>UDP e Mensagens Confiáveis  
 A vinculação UDP não suporta mensagens confiáveis devido à natureza leve do protocolo UDP. Se você precisar confirmar se as mensagens são recebidas por um ponto final remoto, use um transporte que suporte mensagens confiáveis como HTTP ou TCP. Para obter mais informações sobre mensagens confiáveis, consultehttps://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Mensagens multi-vias de duas vias  
 Embora as mensagens multicast sejam geralmente unidirecionais, o UdpBinding faz suporte à troca de mensagens de solicitação/resposta. As mensagens enviadas usando o transporte UDP contêm um de e para o endereço. Deve-se tomar cuidado ao usar o endereço De, pois ele pode ser alterado maliciosamente no caminho.  O endereço pode ser verificado usando o seguinte código:  
  
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
  
 Este código verifica o primeiro byte do endereço De para ver se ele contém 0xE0, o que significa que o endereço é um endereço multi-cast.  
  
### <a name="security-considerations"></a>Considerações de segurança  
 Ao ouvir mensagens multicast, um pacote ICMP é enviado ao roteador notificando-o que você está ouvindo no endereço multicast. Qualquer pessoa na sub-rede local que tenha permissões poderia ouvir esses tipos de pacotes e determinar qual endereço multicast e porta você está ouvindo.  
  
 Não use o endereço IP do remetente para fins de segurança. Essas informações podem ser falsificadas e podem fazer com que um aplicativo envie respostas para a máquina errada. Uma maneira de mitigar essa ameaça é ativar a segurança do nível de mensagem. No nível de rede, ipsec (Internet Protocol Security) e/ou NAP (Network Access Protection) também podem ser usados.
