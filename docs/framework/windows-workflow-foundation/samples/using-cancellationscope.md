---
title: Usando CancellationScope
ms.date: 03/30/2017
ms.assetid: 39c5c338-b316-43d6-b7fe-a543281dd1ec
ms.openlocfilehash: 82d44fff869f207c09dc7685fc3470630e001a59
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401776"
---
# <a name="using-cancellationscope"></a>Usando CancellationScope
Este exemplo demonstra como usar a atividade de <xref:System.Activities.Statements.CancellationScope> para cancelar o trabalho em um aplicativo.  
  
 Muitos componentes e serviços de camada intermediária dependem de compilação conhecido de programação de transações para manipular o cancelar para eles.  No entanto, há muitas situações em que o trabalho que não pode ser feito em uma transação deve ser cancelado.  Usar o botão é mais difícil de usar transações, porque o trabalho que deve ser cancelado deve primeiro ser controlado. [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ajuda você com o isto fornecendo uma atividade de <xref:System.Activities.Statements.CancellationScope> .  
  
 Cancelamento pode ser disparado de uma atividade ou pai da atividade.  As atividades filho são agendadas pela atividade pai (como <xref:System.Activities.Statements.Sequence>, <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.Flowchart>, ou uma atividade composto personalizado).  A atividade pai pode cancelar atividades filho por alguma razão.  Por exemplo, uma atividade de <xref:System.Activities.Statements.Parallel> com três ramificações filhos cancelará as ramificações filhos restantes sempre que conclui uma ramificação e a expressão de <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> avalia a `true`. O fluxo de trabalho também pode ser cancelado externamente pelo aplicativo host chamando <xref:System.Activities.WorkflowApplication.Cancel%2A>.  
  
 Para usar a atividade de <xref:System.Activities.Statements.CancellationScope> , coloque o trabalho que precisa ser cancelado na propriedade de <xref:System.Activities.Statements.CancellationScope.Body%2A> , e colocar o trabalho que é executado após o botão na propriedade de <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> .  
  
 Este exemplo demonstra cancelar uma atividade de dentro da atividade própria.  
  
 O cenário que o exemplo usa para demonstrar a atividade de <xref:System.Activities.Statements.CancellationScope> é um cliente que deseja comprar o mais rápido possível um tíquete a Miami. Há duas agências de processamento que desejam o negócio. O exemplo usa dois <xref:System.Activities.Statements.CancellationScope> dentro de uma atividade de <xref:System.Activities.Statements.Parallel> para modelar essa lógica comercial. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> de atividade de <xref:System.Activities.Statements.Parallel> é definido como `true`; desde que <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> é verificado após qualquer ramificação concluir, isso fará com o restante a ramificação ser cancelado após o primeiro ramificação completa. O aplicativo cliente solicita que ambas as agências comprem a permissão, e quando primeiro confirma que o tíquete foi comprado, o aplicativo cancela a ordem na outra agência.  
  
## <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de CancelationScopeXAML.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\CancellationScope`