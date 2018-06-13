---
title: Acessando OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: cefbc3b10114b427518e640809462eedb131d695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516627"
---
# <a name="accessing-operationcontext"></a>Acessando OperationContext
Este exemplo demonstra como as atividades de mensagens (<xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.Send>) pode ser usado com uma atividade de escopo personalizado para acessar <xref:System.ServiceModel.OperationContext.Current%2A> e anexar ou recuperar um cabeçalho de mensagem personalizada em uma mensagem de entrada ou de saída.  
  
## <a name="demonstrates"></a>Demonstra  
 Atividades de mensagem, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como usar pontos de extensibilidade (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) nas atividades de mensagem para acessar <xref:System.ServiceModel.OperationContext.Current%2A>. As callbacks são registrados no tempo de execução de fluxo de trabalho como uma implementação de <xref:System.Activities.IExecutionProperty> que é pegarada por atividades de mensagem em cima de execução. Quaisquer atividades de mensagem no mesmo define o escopo como essa implementação de <xref:System.Activities.IExecutionProperty> é afetado. Em particular, este exemplo usa uma atividade personalizado de escopo para forçar o comportamento de retorno de chamada. <xref:System.ServiceModel.Activities.ISendMessageCallback> é usado no fluxo de trabalho de cliente para incluir <xref:System.Activities.WorkflowApplication.Id%2A> de fluxo de trabalho como <xref:System.ServiceModel.Channels.MessageHeader>de saída. Este cabeçalho é capturado no serviço usando <xref:System.ServiceModel.Activities.IReceiveMessageCallback> e o valor de cabeçalho é impresso - ao console.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Este exemplo exibe um serviço de fluxo de trabalho usando pontos de extremidade HTTP. Para executar este exemplo, adequado ACLs de URL deve ser adicionado (consulte [Configurando HTTP e HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes), executando o Visual Studio como administrador ou executando o seguinte comando em um prompt elevado para adicionar as ACLs corretas. Certifique-se de que seu domínio e nome de usuário são substituídos.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Uma vez que o URL ACLs é adicionado, use as seguintes etapas.  
  
    1.  Compile a solução.  
  
    2.  Definir vários projetos de inicialização, clicando duas vezes a solução e selecionando **definir projetos de inicialização**.  
  
    3.  Adicionar **Service** e **cliente** (nessa ordem) como vários projetos de inicialização.  
  
    4.  Execute o aplicativo. O console de cliente mostra um fluxo de trabalho que executa duas vezes na janela de serviço mostra a ID da instância desses fluxos de trabalho.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
