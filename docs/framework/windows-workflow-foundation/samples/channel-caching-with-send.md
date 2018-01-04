---
title: Canal Caching com enviar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69a2502-25cb-43bf-b8d2-95fbdecb41cb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b12ebe4cc15629125627253200a95b1f8353bbc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ChannelCache`
