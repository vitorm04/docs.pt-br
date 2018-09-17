---
title: Destruindo threads
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET Framework], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a243c95aff77a5de2b3af15542c0bcc44870333
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45645795"
---
# <a name="destroying-threads"></a>Destruindo threads
O método <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> é usado para interromper um thread gerenciado permanentemente. Quando você chama <xref:System.Threading.Thread.Abort%2A>, o CLR lança um <xref:System.Threading.ThreadAbortException> no thread de destino, que o thread de destino pode capturar. Para obter mais informações, consulte <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Se um thread estiver executando um código não gerenciado quando seu método <xref:System.Threading.Thread.Abort%2A> for chamado, o tempo de execução o marca <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>. A exceção é lançada quando o thread retorna para código gerenciado.  
  
 Após a anulação de um thread, ele não poderá ser reiniciado.  
  
 O método <xref:System.Threading.Thread.Abort%2A> não causa a anulação imediata do thread, porque o thread de destino pode capturar o <xref:System.Threading.ThreadAbortException> e executar valores arbitrários de código em um bloco `finally`. Você poderá chamar <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> se precisar esperar até que o thread seja encerrado. <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> é uma chamada de bloqueio que não retorna até que o thread realmente tenha parado de executar ou um intervalo de tempo limite opcional tenha transcorrido. O thread anulado poderia chamar o método <xref:System.Threading.Thread.ResetAbort%2A> ou executar o processamento não associado em um bloqueio `finally`, então se você não especificar um tempo limite, não será garantido o término da espera.  
  
 Os threads que estão aguardando uma chamada para o método <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> podem ser interrompidos por outros threads de chamam <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.  
  
## <a name="handling-threadabortexception"></a>Como lidar com a ThreadAbortException  
 Se você espera que o thread seja anulado, como resultado de uma chamada a <xref:System.Threading.Thread.Abort%2A> de seu próprio código, ou como resultado do descarregamento de um domínio de aplicativo no qual o thread está em execução (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> usa <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> para encerrar os threads), o thread deverá tratar de <xref:System.Threading.ThreadAbortException> e executar qualquer processamento final em uma cláusula `finally`, conforme mostrado no código a seguir.  
  
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
  
 Seu código de limpeza deve estar na cláusula `catch` ou na cláusula `finally`, porque uma <xref:System.Threading.ThreadAbortException> é lançada novamente pelo sistema no final da cláusula `finally` ou no final da cláusula `catch` se não houver nenhuma cláusula `finally`.  
  
 Você pode impedir que o sistema relance a exceção chamando o método <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType>. No entanto, você deve fazer isso apenas se seu próprio código tiver causado a <xref:System.Threading.ThreadAbortException>.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- [Usando threads e threading](../../../docs/standard/threading/using-threads-and-threading.md)
