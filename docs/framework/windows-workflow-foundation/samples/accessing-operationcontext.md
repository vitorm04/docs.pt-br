---
title: Acessando OperationContext
ms.date: 03/30/2017
ms.assetid: 4e92efe8-7e79-41f3-b50e-bdc38b9f41f8
ms.openlocfilehash: 5a2731c7918c216221b0adcafd5c804e80f36dfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182857"
---
# <a name="accessing-operationcontext"></a>Acessando OperationContext
Esta amostra demonstra como as<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send>atividades de mensagens ( e <xref:System.ServiceModel.OperationContext.Current%2A> ) podem ser usadas com uma atividade de escopo personalizada para acessar e anexar ou recuperar um cabeçalho de mensagem personalizado dentro de uma mensagem de saída ou de entrada.  
  
## <a name="demonstrates"></a>Demonstra  
 Atividades de mensagem, <xref:System.ServiceModel.Activities.ISendMessageCallback>, <xref:System.ServiceModel.Activities.IReceiveMessageCallback>.  
  
## <a name="discussion"></a>Discussão  
 Este exemplo mostra como usar pontos de extensibilidade (<xref:System.ServiceModel.Activities.ISendMessageCallback>) <xref:System.ServiceModel.Activities.IReceiveMessageCallback>) nas atividades de mensagem para acessar <xref:System.ServiceModel.OperationContext.Current%2A>. As callbacks são registrados no runtime de fluxo de trabalho como uma implementação de <xref:System.Activities.IExecutionProperty> que é pegarada por atividades de mensagem em cima de execução. Quaisquer atividades de mensagem no mesmo define o escopo como essa implementação de <xref:System.Activities.IExecutionProperty> é afetado. Em particular, este exemplo usa uma atividade personalizado de escopo para forçar o comportamento de retorno de chamada. <xref:System.ServiceModel.Activities.ISendMessageCallback> é usado no fluxo de trabalho de cliente para incluir <xref:System.Activities.WorkflowApplication.Id%2A> de fluxo de trabalho como <xref:System.ServiceModel.Channels.MessageHeader>de saída. Este cabeçalho é capturado no serviço usando <xref:System.ServiceModel.Activities.IReceiveMessageCallback> e o valor de cabeçalho é impresso - ao console.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Este exemplo exibe um serviço de fluxo de trabalho usando pontos de extremidade HTTP. Para executar esta amostra, devem ser adicionados ACLs url adequados (consulte [Configurando HTTP e HTTPS](../../wcf/feature-details/configuring-http-and-https.md) para detalhes), executando o Visual Studio como Administrador ou executando o seguinte comando em um prompt elevado para adicionar as ACLs apropriadas. Certifique-se de que seu domínio e nome de usuário são substituídos.  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. Uma vez que o URL ACLs é adicionado, use as seguintes etapas.  
  
    1. Compile a solução.  
  
    2. Defina vários projetos de inicialização clicando com o botão direito do mouse na solução e selecionando **Projetos de Inicialização definidas**.  
  
    3. Adicione **serviço** e **cliente** (nessa ordem) como vários projetos de inicialinicial.  
  
    4. Execute o aplicativo. O console de cliente mostra um fluxo de trabalho que executa duas vezes na janela de serviço mostra a ID da instância desses fluxos de trabalho.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\Accessing Operation Context`
