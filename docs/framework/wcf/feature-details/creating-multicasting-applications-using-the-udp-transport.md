---
title: Criando aplicativos multicasting usando o transporte UDP
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: 89ac99ffec614eeebd076f9868568dcf2c7b04fd
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360570"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a>Criando aplicativos multicasting usando o transporte UDP
Aplicativos de difusão seletiva enviam mensagens pequenas para um grande número de destinatários ao mesmo tempo sem a necessidade de estabelecer conexões ponto a ponto. A ênfase tais aplicativos é a velocidade ao longo de confiabilidade. Em outras palavras, é mais importante enviar dados em tempo hábil que assegurar que qualquer mensagem específica é realmente recebida. O WCF agora dá suporte a escrever aplicativos multicasting usando o <xref:System.ServiceModel.UdpBinding>. Esse transporte é útil em cenários em que um serviço precisa para enviar mensagens pequenas para um número de clientes simultaneamente. Um aplicativo de cotação da bolsa é um exemplo de um serviço.  
  
## <a name="implementing-a-multicast-application"></a>Implementando um aplicativo de Multicast  
 Para implementar um aplicativo de multicast, definir um contrato de serviço e para cada componente de software que precisa para responder às mensagens de difusão seletiva, implemente o contrato de serviço. Por exemplo, um aplicativo de cotação da bolsa pode definir um contrato de serviço:  
  
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
  
 Cada aplicativo que deseja receber mensagens de multicast deve hospedar um serviço que expõe essa interface.  Por exemplo, aqui está um exemplo de código que ilustra como receber mensagens de multicast:  
  
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
  
 O aplicativo especifica o endereço UDP que todos os serviços serão escutando. Uma nova <xref:System.ServiceModel.ServiceHost> é criado e um ponto de extremidade de serviço é exposto por meio de <xref:System.ServiceModel.UdpBinding>. O <xref:System.ServiceModel.ServiceHost> , em seguida, é aberto e começar a escutar as mensagens de entrada.  
  
 Nesse tipo de cenário é o cliente que, na verdade, envia mensagens de multicast. Cada serviço que está escutando no endereço correto UDP receberá as mensagens de multicast. Aqui está um exemplo de um cliente que envia mensagens de multicast:  
  
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
  
 Esse código gera informações de estoque e, em seguida, usa o contrato de serviço IStockTicker para enviar mensagens de multicast para chamar serviços escutando no endereço correto de UDP.  
  
### <a name="udp-and-reliable-messaging"></a>Sistema de mensagens confiável e de UDP  
 A associação de UDP não oferece suporte a mensagens confiáveis devido à natureza leve do protocolo UDP. Se você precisar confirmar que as mensagens são recebidas por um ponto de extremidade remoto, use um transporte que dá suporte a mensagens confiáveis, como HTTP ou TCP. Para obter mais informações sobre o sistema de mensagens confiável, consulte https://go.microsoft.com/fwlink/?LinkId=231830  
  
### <a name="two-way-multicast-messaging"></a>Mensagens de Multicast bidirecional  
 Enquanto as mensagens de multicast são geralmente unidirecionais, o UdpBinding oferece suporte à troca de mensagens de solicitação/resposta. As mensagens enviadas usando o transporte UDP contêm dois um From e ao endereço. Deve-se ter cuidado ao usar o endereço de quanto poderia ser maliciosamente alterado na rota.  O endereço pode ser verificado usando o seguinte código:  
  
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
  
 Esse código verifica o primeiro byte do endereço de para ver se ele contém 0xE0 que significa que o endereço é um endereço de multicast.  
  
### <a name="security-considerations"></a>Considerações sobre segurança  
 Quando ouvir as mensagens de multicast um pacote ICMP é enviado para o roteador notificando que ele que escuta no endereço de multicast. Qualquer pessoa na sub-rede local que tenha permissões poderia escutar esses tipos de pacotes e determinar qual endereço de multicast e a porta está escutando.  
  
 Não use o endereço IP do remetente para fins de segurança. Essas informações podem ser falsificadas e podem fazer com que um aplicativo enviar respostas ao computador errado. Uma maneira de reduzir essa ameaça é habilitar a segurança em nível de mensagem. No network nível IPSec (Internet Protocol Security) e/ou NAP (proteção de acesso à rede) também pode ser usado.
