---
title: Configurando valores de tempo limite em uma associação
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: f323dfff338f8a3ba24caab6df3b3916d3ae0d13
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339756"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Configurando valores de tempo limite em uma associação
Há uma série de configurações de tempo limite em associações do WCF. Definir tempo limite dessas configurações corretamente podem melhorar não apenas seu serviço desempenho, mas também play uma função na usabilidade e a segurança do seu serviço. Limite a seguir estão disponíveis em associações do WCF:  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. sendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Tempos limite de associação do WCF  
 Cada uma das configurações discutidas neste tópico são feitas na associação em si, no código ou na configuração. O código a seguir mostra como definir o tempo limite programaticamente uma associação do WCF no contexto de um serviço auto-hospedado.  
  
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
  
 O exemplo a seguir mostra como configurar tempos limite em uma associação em um arquivo de configuração.  
  
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
  
 Para obter mais informações sobre essas configurações podem ser encontradas na documentação para o <xref:System.ServiceModel.Channels.Binding> classe.  
  
### <a name="client-side-timeouts"></a>Tempos limite do lado do cliente  
 No lado do cliente:  
  
1. SendTimeout – usado para inicializar o OperationTimeout, que governa o todo o processo de envio de uma mensagem, incluindo recebendo uma mensagem de resposta para uma operação de serviço de solicitação/resposta. Esse tempo limite também se aplica ao enviar mensagens de resposta de um método de contrato de retorno de chamada.  
  
2. OpenTimeout – usado ao abrir canais quando nenhum valor de tempo limite explícito for especificado.  
  
3. CloseTimeout – usado ao fechar canais quando nenhum valor de tempo limite explícito for especificado.  
  
4. ReceiveTimeout – não é usado.  
  
### <a name="service-side-timeouts"></a>Tempos limite do lado do serviço  
 No lado do serviço:  
  
1. SendTimeout, OpenTimeout, CloseTimeout são os mesmos como no cliente.  
  
2. ReceiveTimeout – usada pela camada de serviço de estrutura para inicializar o tempo limite de ociosidade de sessão, que controla quanto tempo uma sessão pode ficar ociosa antes do tempo limite.
