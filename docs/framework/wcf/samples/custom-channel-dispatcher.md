---
title: Distribuidor de canal personalizado
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 20574b4c849f312cb2cf55709d8d5e2a9b5dbca7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43462373"
---
# <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado
Este exemplo demonstra como criar a pilha de canais de forma personalizada, implementando <xref:System.ServiceModel.ServiceHostBase> diretamente e como criar um dispatcher de canal personalizado no ambiente de host da Web. O dispatcher do canal interage com <xref:System.ServiceModel.Channels.IChannelListener> para aceitar canais e recupera mensagens da pilha de canal. Este exemplo também fornece um exemplo básico para mostrar como criar uma pilha de canais em um ambiente de host da Web usando <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>ServiceHostBase personalizado  
 Este exemplo implementa o tipo de base <xref:System.ServiceModel.ServiceHostBase> em vez de <xref:System.ServiceModel.ServiceHost> para demonstrar como substituir a implementação de pilha do Windows Communication Foundation (WCF) com uma mensagem personalizada de tratamento de camada no topo da pilha de canal. Substituir o método virtual <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> para compilar ouvintes de canal e o dispatcher do canal.  
  
 Para implementar um serviço hospedado na Web, obter a extensão de serviço <xref:System.ServiceModel.Activation.VirtualPathExtension> do <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> coleção e adicioná-lo para o <xref:System.ServiceModel.Channels.BindingParameterCollection> para que a camada de transporte Saiba como configurar o ouvinte de canais com base nas configurações de ambiente de hospedagem que é o Internet Information Services (IIS) / configurações de serviço de ativação de processos do Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado  
 O dispatcher de canal personalizado estende o tipo <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Esse tipo implementa a lógica de programação de camada de canais. Neste exemplo, apenas <xref:System.ServiceModel.Channels.IReplyChannel> há suporte para o padrão de troca de mensagem de solicitação-resposta, mas o dispatcher de canal personalizado pode ser facilmente estendido para outros tipos de canal.  
  
 O dispatcher primeiro abre o ouvinte de canais e, em seguida, aceita o canal de resposta de singleton. Com o canal, ele começa a enviar mensagens (solicitações) em um loop infinito. Para cada solicitação, ele cria uma mensagem de resposta e o envia de volta para o cliente.  
  
## <a name="creating-a-response-message"></a>Criação de uma mensagem de resposta  
 O processamento da mensagem é implementado no tipo `MyServiceManager`. No `HandleRequest` método, o `Action` cabeçalho da mensagem é verificado para ver se a solicitação tem suporte. A ação SOAP de predefinidas "http://tempuri.org/HelloWorld/Hello" é definido para fornecer filtragem de mensagens. Isso é semelhante ao conceito de contrato de serviço na implementação de WCF <xref:System.ServiceModel.ServiceHost>.  
  
 No caso de ação SOAP correto, o exemplo recupera os dados de mensagem solicitada e gera uma resposta correspondente à solicitação semelhante ao que é visto no <xref:System.ServiceModel.ServiceHost> caso.  
  
 Especialmente, você tratou o verbo HTTP GET, retornando uma mensagem personalizada de HTML, nesse ponto, caso para que você possa procurar o serviço em um navegador para ver o que é compilado corretamente. Se não coincide com a ação de SOAP, envie uma falha de volta de mensagem para indicar que a solicitação não é suportada.  
  
 O cliente deste exemplo é um cliente do WCF normal que não presuma nada usando o serviço. Portanto, o serviço é especialmente projetado para corresponder ao que você obtém de um WCF normal<xref:System.ServiceModel.ServiceHost> implementação. Como resultado, somente um contrato de serviço é necessário no cliente.  
  
## <a name="using-the-sample"></a>Usando o exemplo  
 Executar o aplicativo cliente diretamente produz a saída a seguir.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Você também pode procurar o serviço em um navegador para que uma mensagem HTTP GET é processada no servidor. Isso obtém você bem formatado texto HTML novamente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
