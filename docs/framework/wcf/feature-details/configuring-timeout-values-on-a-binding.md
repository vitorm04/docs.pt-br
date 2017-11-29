---
title: "Configurando valores de tempo limite em uma associação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 458f2143021ac40bfcaddbe957113e400bd5f3c5
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a>Configurando valores de tempo limite em uma associação
Há um número de configurações de tempo limite em associações do WCF. Definir esses tempo limite configurações corretamente podem melhorar não apenas o serviço desempenho, mas também executar uma função na usabilidade e segurança de seu serviço. Limite a seguir estão disponíveis em associações do WCF:  
  
1.  openTimeout  
  
2.  closeTimeout  
  
3.  sendTimeout  
  
4.  ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Tempos limite de ligação do WCF  
 Cada uma das configurações abordadas neste tópico são feitas na associação, na configuração ou código. O código a seguir mostra como definir o tempo limite em uma associação WCF no contexto de um serviço auto-hospedado programaticamente.  
  
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
  
 O exemplo a seguir mostra como configurar o tempo limite em uma associação em um arquivo de configuração.  
  
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
  
1.  SendTimeout – usado para inicializar o OperationTimeout, que controla todo o processo de enviar uma mensagem, incluindo recebendo uma mensagem de resposta para uma operação de serviço de solicitação/resposta. Esse tempo limite também se aplica ao enviar mensagens de resposta de um método de contrato de retorno de chamada.  
  
2.  OpenTimeout – usada ao abrir canais quando nenhum valor de tempo limite explícito for especificado  
  
3.  CloseTimeout – usado ao fechar canais quando nenhum valor de tempo limite explícito for especificado  
  
4.  ReceiveTimeout – não é usado.  
  
### <a name="service-side-timeouts"></a>Tempos limite do lado do serviço  
 No lado do serviço:  
  
1.  SendTimeout, OpentTimeout, CloseTimeout são os mesmos que no cliente  
  
2.  ReceiveTimeout – usado pela camada de estrutura de serviço para inicializar o tempo limite de ociosidade de sessão, que controla quanto tempo uma sessão pode ficar ociosa antes do tempo limite.
