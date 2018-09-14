---
title: Escopo de trem de transação
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: fa1da6df5ad5256665610c9b3c2df7d706cef63c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597206"
---
# <a name="transaction-convoy-scope"></a>Escopo de trem de transação
Este exemplo demonstra como criar um padrão paralelo de atividade de mensagem de trem em conjunto com <xref:System.ServiceModel.Activities.TransactedReceiveScope> para modelar um protocolo onde um número de operações podem ocorrer em qualquer ordem todo na mesma transação. Este exemplo também demonstra como <xref:System.ServiceModel.Activities.TransactedReceiveScope> automaticamente cria uma nova quando uma transação não é fluído para o servidor, portanto o cliente não usa nenhuma transações.  
  
 O exemplo consiste de dois projetos de fluxo de trabalho que representam o cliente e o servidor. O projeto do cliente executa um fluxo de trabalho que ele enviando uma mensagem para ao fluxo de trabalho do servidor, que inicializa uma correlação e inicia um escopo transacional para o resto das atividades de mensagem. A atividade de <xref:System.Activities.Statements.Sequence> de cliente contém um par de <xref:System.ServiceModel.Activities.Send> inicial e de <xref:System.ServiceModel.Activities.ReceiveReply> e então uma atividade de <xref:System.Activities.Statements.Parallel> com três ramificações. Cada ramificação envia uma mensagem unidirecional para o servidor. A propriedade de <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> de atividade de <xref:System.Activities.Statements.Parallel> é definida como `false` para que todos os três ramificações terminem.  
  
 O fluxo de trabalho do servidor é semelhante ao fluxo de trabalho de cliente a não ser que as atividades de mensagens sejam orientadas para o lado do servidor de comunicação e sejam contidas dentro de uma atividade de <xref:System.ServiceModel.Activities.TransactedReceiveScope> de modo que todo o trabalho feito executado na mesma transação. Quando a primeira mensagem é colocada no servidor, uma transação é criada e feita ambiente para o escopo do corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope> de modo que quaisquer atividades dentro desse escopo pode acessar a transação. Após isso, tudo recebe executa paralelamente. Tudo recebe deve executar exatamente uma vez como descrito pela condição de conclusão na atividade paralela. Um ponto implícito de persistência existe no final do corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope> e a operação de persistência também é executada sob a mesma transação.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de ParallelConvoySample.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Certifique-se de que ambos os projetos estão definidos iniciar.  
  
    1.  Na **Gerenciador de soluções**, a solução com o botão direito e selecione **definir projetos de inicialização**.  
  
    2.  Selecione **vários projetos de inicialização** e verifique se a ação para ambos os projetos é definida como **iniciar**.  
  
4.  Para executar a solução, pressione CTRL+F5.  
  
     O servidor imprime `Server is running`, que indica que o servidor está pronto.  
  
     Pressione qualquer chave na janela do console cliente para iniciar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`