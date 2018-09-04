---
title: Canal de reconhecimento de HTTP
ms.date: 03/30/2017
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
ms.openlocfilehash: d83f3aa590471aa3d83b8f7bd1464ec1e6e106fc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559537"
---
# <a name="http-acknowledgement-channel"></a>Canal de reconhecimento de HTTP
O canal de reconhecimento de HTTP é um exemplo de um canal em camadas que altera o padrão de mensagens unidirecional, permitindo que um serviço para confirmar ou recusar mensagens de entrada em vez de enviar automaticamente uma confirmação após o recebimento. O canal de reconhecimento de HTTP também permite que o serviço de confirmação de atraso até que ele pode fazer uma garantia de nível de negócios que a mensagem será processada.  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.ServiceModel.Channels.ReceiveContext>, O exemplo de canal em camadas (canal de reconhecimento de HTTP).  
  
## <a name="discussion"></a>Discussão  
 O canal de reconhecimento de HTTP implementa <xref:System.ServiceModel.Channels.ReceiveContext> reformatar o padrão de mensagens de solicitação-resposta HTTP a um padrão unidirecional com confirmação atrasada. Usando esse novo padrão, um serviço pode garantir processamento de mensagens ao enviar uma confirmação na forma de um código de status HTTP Okey de 200 sem bloquear o cliente até que o processamento de mensagens seja concluído ou pode enviar uma mensagem de falha para o cliente na forma de um HTTP Servidor status código de erro interno de 500. Por exemplo, um serviço pode enviar uma confirmação depois de gravar uma mensagem para uma fila e, em seguida, continuar a processar a mensagem de forma assíncrona. Nesse cenário, um cliente pode ter certeza de que suas mensagens foram processadas pelo menos uma vez pelo serviço, se ele enviado novamente cada mensagem até que ele recebeu uma confirmação do serviço. Observe que, se um serviço requer mensagem rápida assíncrona processamento via HTTP, sem garantias de, no processamento de mensagens o <xref:System.ServiceModel.Channels.OneWayBindingElement> é uma opção mais apropriada.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> é usado para manter a mensagem em vigor enquanto ele é determinado se a mensagem pode ser processada no serviço. A capacidade de processar com êxito a mensagem de um serviço é indicada pela chamada concluir na <xref:System.ServiceModel.Channels.ReceiveContext> objeto que envia um código de status HTTP Okey e se o serviço pode processar a mensagem é indicado por meio da chamada <xref:System.ServiceModel.Channels.ReceiveContext>do `Abandon` método sobre o <xref:System.ServiceModel.Channels.ReceiveContext> objeto, que envia um código de status de erro interno do servidor HTTP.  
  
 Neste exemplo, o cliente solicita informações de processamento, enviando uma ID de funcionário. No lado do serviço, se a ID do funcionário recebida é maior que 50, o serviço envia um código de HTTP Status 500 (erro interno do servidor) para o cliente, caso contrário, supõe-se que o processamento pode ser feito com êxito e envia um código de HTTP Status de 200 ( Concluída com êxito) para o cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Abra [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] com privilégios de administrador.  
  
2.  Abra o **HttpAckChannel** solução.  
  
3.  Inicie uma nova instância do **Service** projeto clicando com o botão direito no projeto no **Gerenciador de soluções**e selecionando **depurar**, **iniciar nova instância** no menu de contexto.  
  
4.  Inicie uma nova instância das **cliente** projeto clicando com o botão direito no projeto no **Gerenciador de soluções**e selecionando **depurar**, e **iniciar nova instância** no menu de contexto.  
  
5.  Depois que o serviço for iniciado, pressione ENTER na janela do cliente para permitir que o cliente enviar uma mensagem para o serviço.  
  
6.  A primeira mensagem é processada no serviço e envia um código de status HTTP Okey volta ao cliente.  
  
7.  A segunda mensagem não for bem-sucedida e envia um código de status de erro interno do servidor HTTP para o cliente, que gera um <xref:System.ServiceModel.CommunicationException> no cliente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
