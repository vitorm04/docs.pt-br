---
title: Criando aplicativos multicasting usando o transporte UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 84b36029416a66ef03768aed7d0c789a41eed8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490419"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Criando aplicativos multicasting usando o transporte UDP
Aplicativos de difusão seletiva enviam mensagens pequenas em um grande número de destinatários ao mesmo tempo sem a necessidade de estabelecer conexões ponto a ponto. A ênfase desses aplicativos é velocidade de confiabilidade. Em outras palavras, é mais importante enviar dados em tempo hábil que assegurar que qualquer mensagem específica for realmente recebida. WCF agora dá suporte ao escrever aplicativos multicasting usando o <xref:System.ServiceModel.UdpBinding>. Esse transporte é útil em cenários onde um serviço precisa enviar mensagens pequenas para vários clientes simultaneamente. Um aplicativo de cotações da bolsa é um exemplo de um serviço.  
  
## <a name="implementing-a-multicast-application"></a>Implementando um aplicativo de Multicast  
 Para implementar um aplicativo de multicast, definir um contrato de serviço e para cada componente de software que precisa para responder às mensagens de difusão seletiva, implemente o contrato de serviço. Por exemplo, um aplicativo de cotações da bolsa pode definir um contrato de serviço:  
  
```  
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
  
 Cada aplicativo que deseja receber mensagens de difusão seletiva deve hospedar um serviço que expõe essa interface.  Por exemplo, aqui está um exemplo de código que ilustra como receber mensagens de multicast:  
  
```  
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
  
 O aplicativo especifica o endereço UDP que todos os serviços estará escutando. Um novo <xref:System.ServiceModel.ServiceHost> é criado e um ponto de extremidade de serviço é exposto usando o <xref:System.ServiceModel.UdpBinding>. O <xref:System.ServiceModel.ServiceHost> é aberto e comece a escutar mensagens de entrada.  
  
 Nesse tipo de um cenário é o cliente que realmente envia mensagens de multicast. Cada serviço que está escutando no endereço correto UDP receberá as mensagens de multicast. Aqui está um exemplo de um cliente que envia mensagens de multicast:  
  
```  
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
    Console.WriteLine(String.Format("sent stock info at {0}", DateTime.Now));
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 Esse código gera informações de estoque e, em seguida, usa o contrato de serviço IStockTicker para enviar mensagens de multicast para chamar serviços de escuta no endereço UDP correto.  
  
### <a name="udp-and-reliable-messaging"></a>UDP e mensagens confiáveis  
 A associação de UDP não oferece suporte a mensagens confiáveis devido à natureza leve do protocolo UDP. Se você precisa confirmar que as mensagens são recebidas por um ponto de extremidade, use um transporte que dá suporte a mensagens confiáveis como HTTP ou TCP. Para obter mais informações sobre o sistema de mensagens confiável, consulte http://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Mensagens de Multicast bidirecional  
 Enquanto as mensagens multicast são geralmente unidirecionais, o UdpBinding oferece suporte à troca de mensagens de solicitação/resposta. As mensagens enviadas usando o transporte UDP contêm um de dois e ao endereço. Deve-se ter cuidado ao usar o endereço de como pode ser maliciosa alterada na rota.  O endereço pode ser verificado usando o seguinte código:  
  
```  
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
  
 Esse código verifica se o primeiro byte do endereço de para ver se ele contém 0xE0 que significa que o endereço é um endereço de multicast várias.  
  
### <a name="security-considerations"></a>Considerações sobre segurança  
 Quando escutar mensagens de multicast de um pacote ICMP é enviado para o roteador notificando que escuta no endereço de multicast. Qualquer pessoa na sub-rede local que tenha permissões poderia escutar esses tipos de pacotes e determinar quais endereços multicast e porta de escuta no.  
  
 Não use o endereço IP do remetente para fins de segurança. Essas informações podem ser falsificadas e podem fazer com que um aplicativo enviar respostas para o computador errado. Uma maneira de reduzir essa ameaça é para habilitar a segurança em nível de mensagem. Na rede nível IPSec (Internet Protocol Security) e/ou NAP (proteção de acesso à rede) também pode ser usado.
