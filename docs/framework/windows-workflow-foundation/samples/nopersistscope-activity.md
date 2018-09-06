---
title: Atividade de NoPersistScope
ms.date: 03/30/2017
ms.assetid: 9a0baeb7-a05c-4fac-b905-252758cb71bb
ms.openlocfilehash: 6543756594b6734aec39bf22c5ab6215605341b1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038777"
---
# <a name="nopersistscope-activity"></a>Atividade de NoPersistScope
Este exemplo mostra como manipular um estado não-serializáveis e descartável em um fluxo de trabalho. É importante que fluxos de trabalho não tentam manter o estado não-serializáveis e também é importante para objetos descartáveis ser limpado depois que são usados no fluxo de trabalho.  
  
## <a name="demonstrates"></a>Demonstra  
 atividade personalizado e designer de`NoPersistScope` .  
  
## <a name="using-the-nopersistzone-activity"></a>Usando a atividade de NoPersistZone  
 Quando o fluxo de trabalho de exemplo é executado, uma atividade personalizado chamada `CreateTextWriter` cria um objeto do tipo <xref:System.IO.TextWriter> e salvá-los em uma variável de fluxo de trabalho. <xref:System.IO.TextWriter> é um objeto de <xref:System.IDisposable> . Este <xref:System.IO.TextWriter>, que é configurada para gravar em um arquivo denominado “out.txt” no diretório em que o exemplo reproduz, é usado por uma atividade de <xref:System.Activities.Statements.WriteLine> como ecoa qualquer texto que você digita no console.  
  
 A lógica de eco executam em uma atividade de `NoPersistScope` (o código para que também é a parte deste exemplo), que impede o fluxo de trabalho é mantido. Se você digitar `unload` no console, o host tenta persistir a instância de fluxo de trabalho, mas esse tempo limite da operação porque o fluxo de trabalho permanece dentro de um `NoPersistScope`. O fluxo de trabalho também utiliza uma atividade personalizado chamada `Dispose` para descartar o objeto de <xref:System.IO.TextWriter> quando o fluxo de trabalho usando o terminar. A atividade de `Dispose` é colocado dentro do bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> de atividade de <xref:System.Activities.Statements.TryCatch> em que a variável de <xref:System.IO.TextWriter> é declarado, para garantir que é executado se uma exceção deve ocorrer durante a execução do bloco try.  
  
 Você pode digitar em `exit` para concluir a instância de fluxo de trabalho e sair do programa.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução de NoPersistZone.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para criar a solução, pressione CTRL + SHIFT + B ou selecione **compilar solução** da **Build** menu.  
  
3.  Depois que a compilação foi bem-sucedida, pressione F5 ou selecione **iniciar depuração** da **depurar** menu como alternativa, você pode pressionar CTRL + F5 ou selecione **Start Without Debugging** das **Depurar** menu para executar sem depuração.  
  
#### <a name="to-cleanup-optional"></a>A limpeza (opcional)  
  
1.  Para remover a instância Store SQL, Cleanup.cmd execução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NoPersistScope`