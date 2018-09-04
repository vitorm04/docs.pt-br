---
title: OperationScope
ms.date: 03/30/2017
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
ms.openlocfilehash: 562fd9c8ff964cb997012d49600bce73d4441465
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554063"
---
# <a name="operationscope"></a>OperationScope
Este exemplo demonstra como as atividades, <xref:System.ServiceModel.Activities.Receive> e <xref:System.ServiceModel.Activities.SendReply> de mensagens podem ser usados para expor uma atividade personalizado existente como uma operação em um serviço de fluxo de trabalho. Este exemplo inclui uma nova atividade personalizado chamada `OperationScope`. Se destina a tornar o desenvolvimento de um serviço de fluxo de trabalho permitir que os usuários criarem o corpo das operações separadamente como atividades personalizados e então facilmente expostos como as operações de serviço usando a atividade de `OperationScope` . Por exemplo, uma atividade personalizado de `Add` que aceita dois argumentos e retornos de `in` um argumento de `out` pode ser exposta como uma operação de `Add` no serviço de fluxo de trabalho soltando na `OperationScope`.  
  
 O escopo inspecionando a atividade fornecida como o corpo. Todos os argumentos desatados de `in` são considerados para ser entradas de mensagens de entrada. Todos os argumentos de `out` , independentemente se estão associados, são considerados para ser saída na mensagem subsequente de resposta. O nome da operação expõe é tirado de nome para exibição de atividade de `OperationScope` . O resultado final é que a atividade de corpo está envolvida em <xref:System.ServiceModel.Activities.Receive> e em <xref:System.ServiceModel.Activities.SendReply> com os parâmetros de mensagens associadas a atividade de argumentos.  
  
 Este exemplo exibe um serviço de fluxo de trabalho usando pontos de extremidade HTTP. Para executar, o URL apropriado ACLs deve ser adicionado. Para obter mais informações, consulte [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353). Executando o seguinte comando em um prompt elevado adiciona as ACLs apropriado (certifique-se de que seu domínio e nome de usuário são substituídos por % domínio %\\% UserName %).  
  
 **Netsh http adicionar url urlacl =http://+:8000/ usuário = % domínio %\\% UserName %**  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução de OperationScope.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Definir vários projetos de inicialização clicando duas vezes a solução no Gerenciador de soluções e selecionando **definir projetos de inicialização**. Adicione o cenário e o Scenario_Client (nessa ordem) como vários projetos inicialização.  
  
3.  Pressione CTRL+SHIFT+B para criar a solução.  
  
    > [!WARNING]
    >  Essa etapa é necessária para exibir o fluxo de trabalho BankService.xaml devido à atividade personalizado `OperationScope`.  
  
4.  Pressione CTRL+F5 para executar o aplicativo. O console de Scenario_Client solicitará entrada e saída correspondentes são considerados no console de cenário.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`