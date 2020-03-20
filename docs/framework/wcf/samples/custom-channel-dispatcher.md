---
title: Distribuidor de canal personalizado
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: ea1bdd470855d1b2f6572a15ce45f9b90d74fdca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145119"
---
# <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado
Esta amostra demonstra como construir a pilha de <xref:System.ServiceModel.ServiceHostBase> canais de forma personalizada, implementando diretamente e como criar um despachante de canais personalizado no ambiente de host web. O despachante <xref:System.ServiceModel.Channels.IChannelListener> de canais interage para aceitar canais e recupera mensagens da pilha de canais. Esta amostra também fornece uma amostra básica para mostrar como construir <xref:System.ServiceModel.Activation.VirtualPathExtension>uma pilha de canais em um ambiente de host web usando .  
  
## <a name="custom-servicehostbase"></a>Base de host de serviço sinuosa de serviços  
 Esta amostra implementa <xref:System.ServiceModel.ServiceHostBase> o <xref:System.ServiceModel.ServiceHost> tipo base em vez de demonstrar como substituir a implementação da pilha wcf (Windows Communication Foundation) por uma camada de manuseio de mensagens personalizada na parte superior da pilha de canais. Você anula o <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> método virtual para construir ouvintes de canal e o despachante do canal.  
  
 Para implementar um serviço hospedado na Web, obtenha a extensão <xref:System.ServiceModel.Activation.VirtualPathExtension> de serviço da <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> coleção e adicione-a <xref:System.ServiceModel.Channels.BindingParameterCollection> ao para que a camada de transporte saiba como configurar o ouvinte de canal com base nas configurações do ambiente de hospedagem, ou seja, as configurações do Serviço de Informações da Internet (IIS)/Serviço de Ativação de Processos do Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado  
 O despachante de <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>canais personalizado estende o tipo . Esse tipo implementa a lógica de programação de camada de canal. Nesta amostra, <xref:System.ServiceModel.Channels.IReplyChannel> apenas é suportado para o padrão de troca de mensagens de resposta de solicitação, mas o despachante de canal personalizado pode ser facilmente estendido a outros tipos de canais.  
  
 O despachante primeiro abre o ouvinte do canal e, em seguida, aceita o canal de resposta singleton. Com o canal, ele começa a enviar mensagens (solicitações) em um loop infinito. Para cada solicitação, ele cria uma mensagem de resposta e a envia de volta para o cliente.  
  
## <a name="creating-a-response-message"></a>Criando uma mensagem de resposta  
 O processamento de mensagens `MyServiceManager`é implementado no tipo . No `HandleRequest` método, `Action` o cabeçalho da mensagem é verificado pela primeira vez para ver se a solicitação é suportada. Uma ação SOAPhttp://tempuri.org/HelloWorld/Hellopredefinida " " é definida para fornecer filtragem de mensagens. Isto é semelhante ao conceito de contrato <xref:System.ServiceModel.ServiceHost>de serviço na implementação do WCF de .  
  
 Para o caso de ação SOAP correto, a amostra recupera os dados da mensagem solicitada <xref:System.ServiceModel.ServiceHost> e gera uma resposta correspondente à solicitação semelhante à que é vista no caso.  
  
 Você lidou especialmente com o verbo HTTP-GET retornando uma mensagem HTML personalizada, neste caso para que você possa navegar no serviço a partir de um navegador para ver se ele é compilado corretamente. Se a ação SOAP não corresponder, envie uma mensagem de falha de volta para indicar que a solicitação não está suportada.  
  
 O cliente desta amostra é um cliente WCF normal que não assume nada do serviço. Assim, o serviço é especialmente projetado para corresponder ao<xref:System.ServiceModel.ServiceHost> que você recebe de uma implementação normal do WCF. Como resultado, apenas um contrato de serviço é necessário para o cliente.  
  
## <a name="using-the-sample"></a>Usando o exemplo  
 A execução do aplicativo cliente produz diretamente a seguinte saída.  
  
```output  
Client is talking to a request/reply WCF service.
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Você também pode navegar pelo serviço a partir de um navegador para que uma mensagem HTTP-GET seja processada no servidor. Isso faz com que você tenha um texto HTML bem formatado de volta.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
