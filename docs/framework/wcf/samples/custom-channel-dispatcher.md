---
title: Distribuidor de canal personalizado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5814850b3d5a25f5f3c118e732930168f9489d9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado
Este exemplo demonstra como criar a pilha de canais de forma personalizada implementando <xref:System.ServiceModel.ServiceHostBase> diretamente e como criar um distribuidor de canal personalizado no ambiente de host da Web. O dispatcher do canal interage com <xref:System.ServiceModel.Channels.IChannelListener> para aceitar mensagens de canais e recupera da pilha de canais. Este exemplo também fornece um exemplo básico para mostrar como criar uma pilha de canais em um ambiente de host da Web usando <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>ServiceHostBase personalizado  
 Este exemplo implementa o tipo base <xref:System.ServiceModel.ServiceHostBase> em vez de <xref:System.ServiceModel.ServiceHost> para demonstrar como substituir o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementação de pilha com uma camada sobre a pilha de canais de tratamento de mensagens personalizadas. Substituir o método virtual <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> para compilar ouvintes de canal e o distribuidor de canal.  
  
 Para implementar um serviço Web hospedado, obter a extensão do serviço <xref:System.ServiceModel.Activation.VirtualPathExtension> do <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> coleta e adicioná-lo para o <xref:System.ServiceModel.Channels.BindingParameterCollection> para que a camada de transporte Saiba como configurar o ouvinte de canal com base nas configurações de ambiente de hospedagem, que é o Internet Information Services (IIS) / configurações de serviço de ativação de processos do Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Distribuidor de canal personalizado  
 O dispatcher de canal personalizado estende o tipo <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Este tipo implementa a lógica de programação de camada do canal. Neste exemplo, apenas <xref:System.ServiceModel.Channels.IReplyChannel> há suporte para o padrão de troca de mensagem de solicitação-resposta, mas o distribuidor de canal personalizado pode ser facilmente estendido a outros tipos de canal.  
  
 O dispatcher abre pela primeira vez o ouvinte de canal e, em seguida, aceita o canal de resposta de singleton. Com o canal, ele começa a enviar mensagens (solicitações) em um loop infinito. Para cada solicitação, ele cria uma mensagem de resposta e envia de volta para o cliente.  
  
## <a name="creating-a-response-message"></a>Criar uma mensagem de resposta  
 O processamento da mensagem é implementado no tipo `MyServiceManager`. No `HandleRequest` método, o `Action` cabeçalho da mensagem é verificado para ver se a solicitação tem suporte. Uma ação de SOAP predefinida "http://tempuri.org/HelloWorld/Hello" é definida para fornecer a filtragem de mensagens. Isso é semelhante ao conceito de contrato de serviço no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementação de <xref:System.ServiceModel.ServiceHost>.  
  
 Para o caso de ação SOAP correto, o exemplo recupera os dados de mensagem solicitada e gera uma resposta correspondente à solicitação semelhante ao que é visto no <xref:System.ServiceModel.ServiceHost> caso.  
  
 Você tratados especialmente o verbo HTTP GET, retornando uma mensagem personalizada de HTML, nesse ponto, caso para que você possa procurar o serviço de um navegador para ver o que ele foi compilado corretamente. Se não coincide com a ação de SOAP, envie uma falha de voltar de mensagem para indicar que a solicitação não é suportada.  
  
 O cliente deste exemplo é um normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente que não herda nada do serviço. Portanto, o serviço é especialmente projetado para coincidir com o que você obtém de um normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.ServiceHost> implementação. Como resultado, um contrato de serviço é necessário no cliente.  
  
## <a name="using-the-sample"></a>Usando o exemplo  
 Executando o aplicativo cliente diretamente produz a saída a seguir.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Você também pode procurar o serviço de um navegador para que uma mensagem HTTP GET é processada no servidor. Obtém volta você bem texto com formatação HTML.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
