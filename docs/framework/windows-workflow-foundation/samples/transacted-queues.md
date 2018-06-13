---
title: Filas transacionadas
ms.date: 03/30/2017
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
ms.openlocfilehash: b125158a113079d87eb6926393d5a2b5fe326824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519675"
---
# <a name="transacted-queues"></a>Filas transacionadas
Este exemplo mostra como integrar a filas e transações no Windows Workflow Foundation (WF) para criar serviços escalonáveis e confiáveis. Um <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` é usado no fluxo de trabalho cliente para enviar a mensagem para uma fila em uma transação usando o <xref:System.ServiceModel.NetMsmqBinding>. <xref:System.ServiceModel.Activities.TransactedReceiveScope> é usado no servidor para receber mensagens de fila e para atualizar o estado de fluxo de trabalho na mesma transação.  
  
## <a name="demonstrates"></a>Demonstra  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>, e correlação conteudo base.  
  
## <a name="discussion"></a>Discussão  
 Para demonstrar os recursos abordados neste exemplo, um serviço do fluxo de trabalho `RewardsPoints` é criado, que mantém registro dos pontos ganhados e usados para uma conta determinada. O cliente usa <xref:System.Activities.WorkflowInvoker> para simular postar várias solicitações a fila. Para enviar uma mensagem à fila em uma transação, a atividade de <xref:System.ServiceModel.Activities.Send> pode ser colocado dentro de <xref:System.Activities.Statements.TransactionScope.Body%2A> de <xref:System.Activities.Statements.TransactionScope>. Nesse exemplo, o cliente é executado primeiro, seguido pelo servidor, para demonstrar como as mensagens na fila podem desacoplar o cliente e aplicativos de servidor.  
  
 Uma vez que o cliente for concluída, o serviço é configurado e hospedado. Portanto, abra começa a processar as mensagens que já foram colocadas na fila. Cada mensagem é recebida e processadas na mesma transação do servidor. Nesse exemplo, a primeira mensagem é recebida uma solicitação de `CreateAccount` que cria a instância e inicializa correlação de conteúdo baseado no nome de conta passado como parte da mensagem de solicitação. Para modelar o tipo de serviço que você pode esperar no mundo real, as seguintes atividades de <xref:System.ServiceModel.Activities.TransactedReceiveScope> que processam `AddPoints` e mensagens de `UsePoints` é paralelamente ramificações colocados dentro de um loop de `while` de modo que possa processar essas mensagens repetidamente em qualquer ordem.  
  
 <xref:System.Activities.Statements.TransactionScope> e <xref:System.ServiceModel.Activities.TransactedReceiveScope> cada um possui um ponto implícito de persistência no final de seus escopos, o que usar essas atividades em [!INCLUDE[wf1](../../../../includes/wf1-md.md)] combinou com as filas é uma maneira confiável de mover o fluxo de trabalho de um estado consistente a seguir, para garantir que as mensagens estivessem perdidas nunca.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar e configurar MSMQ. Consulte [instalar o serviço de enfileiramento](http://go.microsoft.com/fwlink/?LinkId=178526) para obter detalhes.  
  
2.  Certifique-se de que MSDTC está executando executando o comando a seguir na linha de comando. `net start msdtc`  
  
3.  Compile o projeto e o executável, ou abra o projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e selecione a opção de início do menu debug. Primeiro, a fila é criada, o cliente é executada e enviar mensagens a fila, e finalmente inicia o serviço e mensagens são processados. Para sair do programa, pressione ENTER.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
