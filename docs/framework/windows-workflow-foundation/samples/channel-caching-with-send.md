---
title: Canal Caching com enviar
ms.date: 03/30/2017
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
ms.openlocfilehash: c26d81b9cd85ba75189fafddd82c3fb4673c7fae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
  
3.  Execute o aplicativo EchoWorkflowClient gerado em .\EchoWorkflowClient\bin\debug.  
  
4.  O cliente chama a operação de eco no serviço e imprime os resultados. Quando os resultados foram impressos, pressione ENTER para sair do cliente e o serviço.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
