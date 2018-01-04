---
title: "Correlação conteudo base"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8638b5d6-1d59-456d-8acd-179a5b39b260
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971636df3393adda96dff779c1533969f67bf57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="content-based-correlation"></a>Correlação conteudo base
Este exemplo demonstra como as atividades de mensagens (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, e <xref:System.ServiceModel.Activities.ReceiveReply>) podem ser usadas com correlação conteudo com base correlations.and conteudo com múltiplas. Nesse cenário, uma correlação primeiro é inicializada com base em um ID de ordem de compras, e outra correlação é criada em posteriormente com base na identificação do cliente Isso mostra como uma atividade de <xref:System.ServiceModel.Activities.Receive> pode seguir uma correlação existente e inicializar uma nova correlação com base na mesma mensagem de entrada.  
  
## <a name="demonstrates"></a>Demonstra  
 Atividades de mensagem e correlação conteudo base  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como usar correlações conteudo baseadas em múltiplas.  Nesse cenário, uma correlação primeiro é inicializada com base em um ID de ordem de compras, e outra correlação é criada em posteriormente com base na identificação do cliente  Se correlaciona são conectadas usando uma atividade de <xref:System.ServiceModel.Activities.Receive> que segue uma correlação existente (PurchaseOrderId) e inicializa uma nova correlação (CustomerId) com base na mesma mensagem de entrada.  Para fazer isso, a atividade de <xref:System.ServiceModel.Activities.Receive> usa <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> e propriedades de <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> .  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] com permissões elevadas, clicando com o [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ícone e selecionando **executar como administrador**.  
  
2.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CascadingCorrelation.sln.  
  
3.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
4.  Para executar o servidor, pressione F5.  
  
5.  Uma vez que o serviço está pronto e escutar mensagens, em Solution Explorer, clique com o botão direito do mouse no projeto do cliente e executá-lo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\ContentBasedCorrelation`