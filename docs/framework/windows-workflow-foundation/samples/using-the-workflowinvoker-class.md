---
title: Usando a classe de WorkflowInvoker
ms.date: 03/30/2017
ms.assetid: 0a966164-3990-4e78-8aa2-c6797ebbee94
ms.openlocfilehash: 70fc94b1f190236cb2cb40c407e0172f0213fb7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33515808"
---
# <a name="using-the-workflowinvoker-class"></a>Usando a classe de WorkflowInvoker
Este exemplo demonstra como usar a classe de <xref:System.Activities.WorkflowInvoker> para chamar uma atividade como se fosse um método.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Usar a classe de <xref:System.Activities.WorkflowInvoker> é a maneira mais simples para executar uma atividade. É criada diretamente executando uma atividade como se fosse um chamada de método. É um leve, alto executando, a API fácil de usar para uso em cenários onde a execução de uma atividade não requer a infraestrutura do controle fornecida por outras variações de hospedagem.  
  
 O exemplo usa uma atividade personalizada que é derivada de <xref:System.Activities.CodeActivity%601>< Int32\> chamado `Add` que adiciona dois <xref:System.Activities.InArgument%601>, `X` e `Y`e retorna um `Result` <xref:System.Activities.OutArgument%601>. (<xref:System.Activities.CodeActivity%601>\<T > derivado <xref:System.Activities.Activity%601>< T\>, que tem um <xref:System.Activities.OutArgument%601> \<T > denominado `Result`.) Um `Dictionary` \<de cadeia de caracteres, objeto > é usado para passar argumentos para uma atividade que está sendo invocada pelo <xref:System.Activities.WorkflowInvoker>. A chave do dicionário corresponde ao nome de um argumento na chamada atividade. O valor associado com uma chave específica é associado ao argumento identificado por chave.  
  
 O exemplo chama <xref:System.Activities.WorkflowInvoker.Invoke%2A> e passa um dicionário que contém valores para `X` e `Y`. A classe de <xref:System.Activities.WorkflowInvoker> associa esses valores para os argumentos de atividade de `Add` , executa a atividade, e retorna o resultado.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Invoker.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\WorkflowInvoker`