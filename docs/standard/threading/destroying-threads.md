---
title: Destruindo threads
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a41dce5db707d0be49c283256de665d316e1a1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="destroying-threads"></a>Destruindo threads
O <xref:System.Threading.Thread.Abort%2A> método é usado para interromper um thread gerenciado permanentemente. Quando você chama <xref:System.Threading.Thread.Abort%2A>, o common language runtime lança um <xref:System.Threading.ThreadAbortException> no thread de destino, pode capturar o thread de destino. Para obter mais informações, consulte <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Se estiver executando um thread não gerenciado de código ao seu <xref:System.Threading.Thread.Abort%2A> método é chamado, o tempo de execução a marca <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. A exceção é lançada quando o thread retorna para código gerenciado.  
  
 Depois que um thread é interrompido, ele não pode ser reiniciado.  
  
 O <xref:System.Threading.Thread.Abort%2A> método não faz com que o thread anular imediatamente, porque o thread de destino pode capturar o <xref:System.Threading.ThreadAbortException> e execute valores arbitrários de código em um `finally` bloco. Você pode chamar <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> se você precisa esperar até que o thread foi encerrada. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>é uma chamada de bloqueio que não retorna até que o thread realmente parou de executar ou um intervalo de tempo limite opcional. O thread anulado poderia chamar o <xref:System.Threading.Thread.ResetAbort%2A> método ou executar o processamento não associado em um `finally` bloquear, se você não especificar um tempo limite, o tempo de espera não é garantida para terminar.  
  
 Threads que estão aguardando em uma chamada para o <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> método pode ser interrompido por outros threads de chamam <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Tratamento de ThreadAbortException  
 Se você espera que o thread de anulação, como resultado de uma chamada <xref:System.Threading.Thread.Abort%2A> de seu próprio código, ou como resultado de descarregar um domínio de aplicativo no qual o thread está em execução (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> usa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> encerrar threads), o thread deve tratar o <xref:System.Threading.ThreadAbortException> e executar qualquer processamento final em um `finally` cláusula, conforme mostrado no código a seguir.  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.   
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception   
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try   
{  
    // Code that is executing when the thread is aborted.  
}   
catch (ThreadAbortException ex)   
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.   
}  
// Do not put clean-up code here, because the exception   
// is rethrown at the end of the Finally clause.  
```  
  
 Seu código de limpeza deve ser no `catch` cláusula ou o `finally` cláusula, porque um <xref:System.Threading.ThreadAbortException> é lançada novamente pelo sistema no final do `finally` cláusula, ou no final do `catch` cláusula se não houver nenhum `finally` cláusula.  
  
 Você pode impedir que o sistema relançamento de exceção ao chamar o <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> método. No entanto, você deve fazer isso apenas se seu próprio código causado o <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)
