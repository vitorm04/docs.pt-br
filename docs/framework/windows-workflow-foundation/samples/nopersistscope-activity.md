---
title: Atividade de NoPersistScope
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: e4779bf28fc2fc1341cce5134a872b108278611c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="nopersistscope-activity"></a>Atividade de NoPersistScope
Este exemplo mostra como manipular um estado não-serializáveis e descartável em um fluxo de trabalho. É importante que fluxos de trabalho não tentam manter o estado não-serializáveis e também é importante para objetos descartáveis ser limpado depois que são usados no fluxo de trabalho.  
  
## <a name="demonstrates"></a>Demonstra  
 atividade personalizado e designer de`NoPersistScope` .  
  
## <a name="using-the-nopersistzone-activity"></a>Usando a atividade de NoPersistZone  
 Quando o fluxo de trabalho de exemplo é executado, uma atividade personalizado chamada `CreateTextWriter` cria um objeto do tipo <xref:System.IO.TextWriter> e salvá-los em uma variável de fluxo de trabalho. <xref:System.IO.TextWriter> é um objeto de <xref:System.IDisposable> . Este <xref:System.IO.TextWriter>, que é configurada para gravar em um arquivo denominado “out.txt” no diretório em que o exemplo reproduz, é usado por uma atividade de <xref:System.Activities.Statements.WriteLine> como ecoa qualquer texto que você digita no console.  
  
 A lógica de eco executam em uma atividade de `NoPersistScope` (o código para que também é a parte deste exemplo), que impede o fluxo de trabalho é mantido. Se você digitar `unload` no console do, o host tenta manter a instância de fluxo de trabalho, mas esse tempo limite da operação porque o fluxo de trabalho permanece em um `NoPersistScope`. O fluxo de trabalho também utiliza uma atividade personalizado chamada `Dispose` para descartar o objeto de <xref:System.IO.TextWriter> quando o fluxo de trabalho usando o terminar. A atividade de `Dispose` é colocado dentro do bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> de atividade de <xref:System.Activities.Statements.TryCatch> em que a variável de <xref:System.IO.TextWriter> é declarado, para garantir que é executado se uma exceção deve ocorrer durante a execução do bloco try.  
  
 Você pode digitar `exit` para concluir a instância de fluxo de trabalho e sair do programa.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução de NoPersistZone.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** do **criar** menu.  
  
3.  Depois que a compilação foi bem-sucedida, pressione F5 ou selecione **iniciar depuração** do **depurar** menu como alternativa, você pode pressionar CTRL + F5 ou selecionar **Start Without Debugging** da **Depurar** menu para executar sem depuração.  
  
#### <a name="to-cleanup-optional"></a>A limpeza (opcional)  
  
1.  Para remover a instância Store SQL, Cleanup.cmd execução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`