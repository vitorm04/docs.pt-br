---
title: Configurando valores de tempo limite em uma associação
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185285"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Configurando valores de tempo limite em uma associação
Há uma série de configurações de tempo total disponíveis nas ligações WCF. Definir corretamente essas configurações de tempo limitado pode melhorar não apenas o desempenho do seu serviço, mas também desempenhar um papel na usabilidade e segurança do seu serviço. Os seguintes intervalos estão disponíveis nas ligações WCF:  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. SendTimeout  
  
4. Receivetimeout  
  
## <a name="wcf-binding-timeouts"></a>Tempos de ligação WCF  
 Cada uma das configurações discutidas neste tópico são feitas na própria vinculação, seja em código ou configuração. O código a seguir mostra como definir programáticamente tempos outs em uma vinculação WCF no contexto de um serviço auto-hospedado.  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");

    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));

        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);

        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 O exemplo a seguir mostra como configurar tempos outs em uma vinculação em um arquivo de configuração.  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00"
                 closeTimeout="00:10:00"
                 sendTimeout="00:10:00"
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 Mais informações sobre essas configurações podem ser <xref:System.ServiceModel.Channels.Binding> encontradas na documentação da classe.  
  
### <a name="client-side-timeouts"></a>Tempos fora do cliente  
 No lado do cliente:  
  
1. SendTimeout – usado para inicializar o OperationTimeout, que rege todo o processo de envio de uma mensagem, incluindo o recebimento de uma mensagem de resposta para uma operação de serviço de solicitação/resposta. Esse tempo não é válido também ao enviar mensagens de resposta de um método de contrato de retorno de chamada.  
  
2. OpenTimeout – usado ao abrir canais quando nenhum valor de tempo livre explícito é especificado.  
  
3. CloseTimeout – usado quando os canais de fechamento não são especificados.  
  
4. ReceiveTimeout – não é usado.  
  
### <a name="service-side-timeouts"></a>Tempos fora do serviço  
 No lado do serviço:  
  
1. SendTimeout, OpenTimeout, CloseTimeout são os mesmos do cliente.  
  
2. ReceiveTimeout – usado pela Camada de Estrutura de Serviço para inicializar o tempo de espera de sessão que controla quanto tempo uma sessão pode ficar ociosa antes de cronometrar.
