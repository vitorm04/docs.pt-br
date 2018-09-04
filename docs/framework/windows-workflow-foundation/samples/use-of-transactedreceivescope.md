---
title: Uso de TransactedReceiveScope
ms.date: 03/30/2017
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
ms.openlocfilehash: bc1c418f3fa116f5e1c1647af3543a38122842f5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501636"
---
# <a name="use-of-transactedreceivescope"></a>Uso de TransactedReceiveScope
Este exemplo mostra como fluir uma transação de um cliente a um servidor usando <xref:System.Activities.Statements.TransactionScope> para criar uma nova transação no cliente e em <xref:System.ServiceModel.Activities.TransactedReceiveScope> para receber uma mensagem com uma transação fluída e definir o escopo o tempo de vida de transação no servidor. O exemplo consiste de dois projetos que preenchem as funções de cliente e servidor.  
  
## <a name="client-application"></a>Aplicativo cliente  
 O aplicativo cliente executa um fluxo de trabalho que imprimir o ID de transação distribuído, enviar uma mensagem para o servidor, flui a transação, receba a resposta, imprimir o ID de transação distribuído novamente e termina. Quando o ID de transação distribuído é inicialmente cópias, é GUID vazio porque a transação é ainda apenas local.  
  
## <a name="server-application"></a>Aplicativo para servidores  
 O projeto do servidor é semelhante, no entanto, o fluxo de trabalho é hospedado em <xref:System.ServiceModel.Activities.WorkflowServiceHost> porque ele deve escutar em um ponto de extremidade para a mensagem de cliente. O fluxo de trabalho é centralizado em <xref:System.ServiceModel.Activities.TransactedReceiveScope>, que recebe a transação fluída de cliente, cópias que a mensagem que foi enviada, imprime o ID de transação distribuído e envia a resposta para o cliente. A identificação de transação é distribuído agora GUID não vazio e se uma atividade transação- ciente foi adicionada ao corpo de <xref:System.ServiceModel.Activities.TransactedReceiveScope>, teria executado na transação fluída.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução de TransactedReceiveScope.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** da **Build** menu.  
  
3.  Depois que a compilação foi bem-sucedida, a solução com o botão direito e selecione **definir projetos de inicialização**. Na caixa de diálogo, selecione **vários projetos de inicialização** e verifique se a ação para ambos os projetos é **iniciar**.  
  
4.  Pressione F5 ou selecione **iniciar depuração** da **depurar** menu. Como alternativa, você pode pressionar CTRL + F5 ou selecione **Start Without Debugging** da **depurar** menu para executar sem depuração.  
  
    > [!NOTE]
    >  O servidor deve executar antes de iniciar o cliente. A saída da janela do console que hospeda o serviço indicam quando seguir o iniciarão.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`