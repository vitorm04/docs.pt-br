---
title: Distribuidor de canal personalizado
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 00caa5eda37e5da9462286e71bbdbc2ff50d5081
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716870"
---
# <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado
Este exemplo demonstra como criar a pilha de canais de forma personalizada, implementando <xref:System.ServiceModel.ServiceHostBase> diretamente e como criar um Dispatcher de canal personalizado no ambiente de host da Web. O Dispatcher do canal interage com <xref:System.ServiceModel.Channels.IChannelListener> para aceitar canais e recupera mensagens da pilha de canais. Este exemplo também fornece um exemplo básico para mostrar como criar uma pilha de canais em um ambiente de host da Web usando <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>ServiceHostBase personalizada  
 Este exemplo implementa o tipo base <xref:System.ServiceModel.ServiceHostBase> em vez de <xref:System.ServiceModel.ServiceHost> para demonstrar como substituir a implementação da pilha Windows Communication Foundation (WCF) por uma camada de manipulação de mensagens personalizada na parte superior da pilha do canal. Você substitui o método virtual <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> para criar ouvintes de canal e o Dispatcher do canal.  
  
 Para implementar um serviço hospedado na Web, obtenha a extensão de serviço <xref:System.ServiceModel.Activation.VirtualPathExtension> da coleção de <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> e adicione-a à <xref:System.ServiceModel.Channels.BindingParameterCollection> para que a camada de transporte saiba como configurar o ouvinte de canal com base nas configurações do ambiente de hospedagem, ou seja, as configurações do/Windows (IIS) (serviço de ativação de processos) do Serviços de Informações da Internet).  
  
## <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado  
 O Dispatcher do canal personalizado estende o tipo <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Esse tipo implementa a lógica de programação de camada de canal. Neste exemplo, somente <xref:System.ServiceModel.Channels.IReplyChannel> tem suporte para o padrão de troca de mensagens de solicitação-resposta, mas o Dispatcher do canal personalizado pode ser facilmente estendido para outros tipos de canal.  
  
 O Dispatcher abre primeiro o ouvinte do canal e, em seguida, aceita o canal de resposta singleton. Com o canal, ele começa a enviar mensagens (solicitações) em um loop infinito. Para cada solicitação, ele cria uma mensagem de resposta e a envia de volta para o cliente.  
  
## <a name="creating-a-response-message"></a>Criando uma mensagem de resposta  
 O processamento da mensagem é implementado no tipo `MyServiceManager`. No método `HandleRequest`, o cabeçalho `Action` da mensagem é verificado primeiro para ver se há suporte para a solicitação. Uma ação SOAP predefinida "http://tempuri.org/HelloWorld/Hello" é definida para fornecer filtragem de mensagens. Isso é semelhante ao conceito de contrato de serviço na implementação do WCF de <xref:System.ServiceModel.ServiceHost>.  
  
 Para o caso de ação SOAP correto, o exemplo recupera os dados de mensagem solicitados e gera uma resposta correspondente para a solicitação semelhante ao que é visto no caso de <xref:System.ServiceModel.ServiceHost>.  
  
 Você tratou especialmente do verbo HTTP-GET retornando uma mensagem HTML personalizada, neste caso, para que você possa procurar o serviço em um navegador para ver se ele foi compilado corretamente. Se a ação SOAP não corresponder, envie uma mensagem de falha de volta para indicar que não há suporte para a solicitação.  
  
 O cliente deste exemplo é um cliente WCF normal que não assume nada do serviço. Portanto, o serviço é especialmente projetado para corresponder ao que você obtém de uma implementação normal de<xref:System.ServiceModel.ServiceHost> do WCF. Como resultado, apenas um contrato de serviço é necessário no cliente.  
  
## <a name="using-the-sample"></a>Usando o exemplo  
 Executar o aplicativo cliente diretamente produz a saída a seguir.  
  
```output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Você também pode procurar o serviço em um navegador para que uma mensagem HTTP-GET seja processada no servidor. Isso Obtém um texto HTML bem formatado de volta.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
