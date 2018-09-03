---
title: Canal Caching com enviar
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: 619088def1f5e443a31244516655d75d1e25c9cb
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475849"
---
# <a name="channel-caching-with-send"></a>Canal Caching com enviar
<xref:System.ServiceModel.Activities.SendMessageChannelCache> permite que os usuários para ter diferentes níveis de cachê do canal com <xref:System.ServiceModel.Activities.Send> e atividades de <xref:System.ServiceModel.Activities.SendParametersContent> . o cachê de instância é habilitado por padrão e este exemplo demonstra os seguintes recursos:  
  
1.  Compartilhar <xref:System.ServiceModel.Activities.SendMessageChannelCache> através de um domínio de aplicativo.  
  
2.  Desativar o cachê do canal.  
  
3.  Compartilhar <xref:System.ServiceModel.Activities.SendMessageChannelCache> entre instâncias de fluxo de trabalho em <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
## <a name="demonstrates"></a>Demonstra  
 extensão de<xref:System.ServiceModel.Activities.SendMessageChannelCache> , <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.ReceiveContent> e atividades de <xref:System.ServiceModel.Activities.SendReply> .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.  
  
2.  Executar em gerado aplicativo de EchoWorkflowService EchoWorkflowService \ \ bin \ debug.  
  
3.  Executam EchoWorkflowClient aplicativo gerado no .\EchoWorkflowClient\bin\debug.  
  
4.  O cliente chama a operação de eco no serviço e imprime os resultados. Quando os resultados foram impressos, pressione ENTER para sair do cliente e o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
