---
title: Aninhamento de TransactionScope em um serviço
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: 9c556df417548ab348d1dd5bc642928ae68d8878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="nesting-of-transactionscope-within-a-service"></a>Aninhamento de TransactionScope em um serviço
Este exemplo consiste de dois cenários que executam a visualização como manipular instâncias de atividade de <xref:System.Activities.Statements.TransactionScope> em um serviço. A transação é iniciada primeiro usando a atividade de <xref:System.Activities.Statements.TransactionScope> para criar uma nova transação no cliente e em <xref:System.ServiceModel.Activities.TransactedReceiveScope> para receber e escopo o tempo de vida de transação no servidor. O primeiro cenário dentro do serviço executa uma atividade new de <xref:System.Activities.Statements.TransactionScope> para demonstrar aninhamento de atividades de <xref:System.Activities.Statements.TransactionScope> dentro do serviço. O segundo cenário mostra como os intervalos são respeitados dentro das atividades aninhados de <xref:System.Activities.Statements.TransactionScope> .  
  
## <a name="client-application"></a>Aplicativo cliente  
 O aplicativo cliente executa um fluxo de trabalho que inicie uma atividade de <xref:System.Activities.Statements.TransactionScope> , imprimir o ID de transação distribuído, enviar uma mensagem para o servidor, flui a transação, receba a resposta, imprimir o ID de transação distribuído novamente e termina. Isso uma vez para cada cenário de serviço.  
  
## <a name="server-application"></a>Aplicativo para servidores  
 O projeto do servidor é hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost>, que cria o ponto de extremidade para escutar a mensagem de cliente. O fluxo de trabalho é centralizado em <xref:System.ServiceModel.Activities.TransactedReceiveScope>, que recebe a transação fluída de cliente, imprime o ID de transação distribuído e execute uma atividade de <xref:System.Activities.Statements.TransactionScope> do segundo. No primeiro cenário, a transação é concluída com êxito. No segundo cenário, o corpo de atividade de <xref:System.Activities.Statements.TransactionScope> é um cinco atraso e o tempo limite para a transação é definido como dois segundos. Quando o tempo limite de transação a transação é anulada.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução de TransactionServiceExample.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** do **criar** menu.  
  
3.  Depois que a compilação foi bem-sucedida, a solução e selecione **definir projetos de inicialização**. Na caixa de diálogo, selecione **vários projetos de inicialização** e certifique-se de que a ação de ambos os projetos é **iniciar**.  
  
4.  Pressione F5 ou selecione **iniciar depuração** do **depurar** menu. Como alternativa, você pode pressionar CTRL + F5 ou selecionar **Start Without Debugging** do **depurar** menu para executar sem depuração.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
