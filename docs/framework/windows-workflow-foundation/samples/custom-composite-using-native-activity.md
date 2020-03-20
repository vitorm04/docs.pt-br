---
title: Atividade nativo de usar composta personalizada
ms.date: 03/30/2017
ms.assetid: ef9e739c-8a8a-4d11-9e25-cb42c62e3c76
ms.openlocfilehash: 2b922ef721ab4d125f390e908eb8ea4d3b087035
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142791"
---
# <a name="custom-composite-using-native-activity"></a>Atividade nativo de usar composta personalizada
Este exemplo demonstra como escrever <xref:System.Activities.NativeActivity> que agenda outros objetos de <xref:System.Activities.Activity> para controlar o fluxo de execução de um fluxo de trabalho. Este exemplo usar dois fluxos comuns de controle, e quando sequência, para demonstrar como fazer isso.

## <a name="sample-details"></a>Detalhes de exemplo
 Iniciando com `MySequence`, a primeira coisa para observar que é derivada de <xref:System.Activities.NativeActivity>. <xref:System.Activities.NativeActivity> é o objeto de <xref:System.Activities.Activity> que expõe a largura total do runtime de fluxo de trabalho com <xref:System.Activities.NativeActivityContext> passado para o método de `Execute` .

 `MySequence` expõe uma coleção pública de objetos <xref:System.Activities.Activity> que obtém preenchido pelo autor de fluxo de trabalho. Antes que o fluxo de trabalho é executado, o runtime de fluxo de trabalho chama o método de <xref:System.Activities.Activity.CacheMetadata%2A> em cada atividade em um fluxo de trabalho. Durante esse processo, o runtime estabelecer relações pai-filho para o escopo de dados e o gerenciamento de tempo de vida. A implementação <xref:System.Activities.Activity.CacheMetadata%2A> padrão do <xref:System.ComponentModel.TypeDescriptor> método usa `MySequence` a classe de instância <xref:System.Activities.Activity> <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Activity> para a atividade `MySequence` para adicionar qualquer propriedade pública de tipo ou> como filhos da atividade.

 Sempre que uma atividade expõe uma coleção pública de atividades filhos, é provável estado filho de compartilhamento dessas atividades. É uma prática recomendada para atividades pai, nesse caso `MySequence`, também expor uma coleção de variáveis com que as atividades filho podem fazer isso. Assim como as <xref:System.Activities.Activity.CacheMetadata%2A> atividades infantis, <xref:System.Activities.Variable> <xref:System.Collections.IEnumerable> \< <xref:System.Activities.Variable> o método adiciona propriedades `MySequence` públicas de tipo ou> como variáveis associadas à atividade.

 Além de variáveis públicas, que são manipulados pelos filhos de `MySequence`, `MySequence` também deve manter controle de onde está em execução de seus filhos. Usa uma variável particular, `currentIndex`, para fazer isso. Esta variável é registrado como parte do ambiente de `MySequence` adicionando uma chamada para o método de <xref:System.Activities.NativeActivityMetadata.AddImplementationVariable%2A> no método de `MySequence` de atividade de <xref:System.Activities.Activity.CacheMetadata%2A> . Os <xref:System.Activities.Activity> objetos `MySequence` `Activities` adicionados à coleção não podem acessar variáveis adicionadas dessa forma.

 Quando `MySequence` é executado em runtime, o runtime chama o método de <xref:System.Activities.NativeActivity.Execute%2A> , passando <xref:System.Activities.NativeActivityContext>. <xref:System.Activities.NativeActivityContext> é o proxy de atividade de novo em runtime para desreferenciar argumentos e variáveis bem como agendar outros objetos de <xref:System.Activities.Activity> , ou `ActivityDelegates`. `MySequence` usa um método de `InternalExecute` para encapsular a lógica de agendar o primeiro filho e todos os filhos subsequentes em um único método. Inicia desreferenciando `currentIndex`. Se for igual a contagem na coleção de `Activities` , então a sequência está concluída, a atividade retorna agendar sem qualquer trabalho e o runtime movê-lo no estado de <xref:System.Activities.ActivityInstanceState.Closed> . Se `currentIndex` for menor que a contagem de atividades, `Activities` a `MySequence` <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>próxima criança é obtida a <xref:System.Activities.CompletionCallback> partir da `InternalExecute` coleta e chamadas, passando a criança a ser agendada e que aponta para o método. Finalmente, `currentIndex` é incrementado e o controle é rendido de volta para o runtime. Como uma instância de `MySequence` tem um objeto filho de <xref:System.Activities.Activity> agendada, o runtime considera-o estar no estado executando.

 Quando a atividade filho termina, <xref:System.Activities.CompletionCallback> é executado. O loop continua a parte superior. Como `Execute`, <xref:System.Activities.CompletionCallback> leva <xref:System.Activities.NativeActivityContext>, fornecendo acesso do implementador em runtime.

 `MyWhile`difere de `MySequence` que ele agenda <xref:System.Activities.Activity> um único objeto repetidamente, <xref:System.Activities.Activity%601> e na\> `Condition` qual ele usa um<bool nomeado para determinar se esse agendamento deve ocorrer. Como `MySequence`, `MyWhile` usa um método de `InternalExecute` para centralizar sua lógica de programação. Ele agenda `Condition` <xref:System.Activities.Activity> o<\> bool com um <xref:System.Activities.CompletionCallback%601> \<> bool chamado `OnEvaluationCompleted`. Quando a execução de `Condition` é concluída, o resultado fica disponível com esse <xref:System.Activities.CompletionCallback> em um parâmetro fortemente tipado chamado `result`. Se `true`, `MyWhile` chama o <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, passando o objeto e em `Body` de <xref:System.Activities.Activity>`InternalExecute` como <xref:System.Activities.CompletionCallback>. Quando a execução de `Body` terminar, `Condition` obtém agendada novamente em `InternalExecute`, iniciar o loop sobre novamente. Quando `Condition` retorna `false`, uma instância de `MyWhile` fornece o controle de volta para o runtime sem agendar `Body` e o runtime movê-lo ao estado de <xref:System.Activities.ActivityInstanceState.Closed> .

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Abra a solução de amostra Composite.sln no Visual Studio 2010.

2. Compile e execute a solução.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\CustomCompositeNativeActivity`
