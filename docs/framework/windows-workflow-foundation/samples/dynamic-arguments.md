---
title: "Argumentos dinâmicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 122ad479-d306-4602-a943-5aefe711329d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 582f8815bd121199e564af7d1806f2e76f4595cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamic-arguments"></a>Argumentos dinâmicos
Este exemplo demonstra como implementar uma atividade para os argumentos são definidos pelo consumidor da atividade em vez do autor de atividade. Isso substituindo a maneira que o tempo de execução constrói os metadados de atividade.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Antes de execução, o tempo de execução cria uma descrição de uma atividade examinando os membros públicos de tipo de atividade e automaticamente declarando argumentos, variáveis, atividades filhos, e representantes de atividade como parte de metadados de uma atividade. Isso para garantir a compilação correta de um fluxo de trabalho bem como para gerenciar relações de tempo de execução e regras de tempo de vida. Normalmente um autor de atividade define argumentos de uma atividade especificando os membros públicos o tipo de atividade que derivam de <xref:System.Activities.Argument>. Para cada membro público que deriva de <xref:System.Activities.Argument>, o tempo de execução cria <xref:System.Activities.RuntimeArgument> e associá-lo ao usuário fornecido o argumento definido nesse membro. Em alguns casos, no entanto, o consumidor da atividade fornece alguma configuração que determina o conjunto de argumentos. As substituições <xref:System.Activities.Activity.CacheMetadata%2A> de um autor de atividade para personalizar os metadados de atividade de forma são compiladas, que incluem o conjunto de argumentos associados com a atividade.  
  
 Este exemplo demonstra como compilar dinamicamente uma lista de argumentos para uma atividade que invoca um método. O consumidor da atividade especifica o tipo e o nome do método deseja chamar juntamente com uma coleção de argumentos a serem passados ao método.  
  
> [!NOTE]
>  O propósito deste exemplo é demonstrar como substituir <xref:System.Activities.CodeActivity.CacheMetadata%2A> e como usar <xref:System.Activities.RuntimeArgument>. Há várias restrições em relação aos tipos de métodos que esta atividade pode chamar. Por exemplo, não funciona com genéricos ou matrizes de parâmetros. A atividade de <xref:System.Activities.Statements.InvokeMethod> que envia in.NET Framework trata esses casos e mais.  
  
 A atividade de `MethodInvoke` substitui <xref:System.Activities.CodeActivity.CacheMetadata%2A> e começa criando <xref:System.Activities.RuntimeArgument> para manipular qualquer resultado de invocação do método. Este <xref:System.Activities.RuntimeArgument> associa a <xref:System.Activities.OutArgument> publicamente configuráveis chamado `Result`. Se `MethodInvoke.Result` é `null`, o tempo de execução preenche automaticamente com <xref:System.Activities.OutArgument> configurado com a expressão padrão para seu tipo. Esse comportamento significa que um autor de atividade nunca precisa verificar se uma propriedade do argumento é `null`.  
  
 Em seguida, a substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> determina `MethodInfo` que usa para a chamada ao usuário fornecido `MethodName` e `TargetType`. O método de `DetermineMethodInfo` utiliza o parâmetro de <xref:System.Activities.CodeActivityMetadata> passado para a substituição de <xref:System.Activities.CodeActivity.CacheMetadata%2A> de modo que todos os erros de configuração podem ser reportado como erros de validação. Isso é feito chamando `metadata.AddValidationError`.  
  
 Uma vez que `MethodInfo` foi definido, o exemplo efetua iterações sobre os parâmetros de `MethodInfo` . Para cada parâmetro, cria <xref:System.Activities.RuntimeArgument> e associá-lo ao argumento correspondente no usuário fornecido a coleção de propriedade de `Parameters` . Finalmente, a coleção de <xref:System.Activities.RuntimeArgument>s está associada com a atividade chamando `metadata.SetArgumentsCollection`.  
  
 Observe que a resolução do argumento pode ser feita usando <xref:System.Activities.RuntimeArgument>, como no caso de `resultArgument` ou do argumento fornecido, como no caso de coleção de `Parameters` .  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de DynamicArguments.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\DynamicArguments`