---
title: Timers de thread (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
ms.openlocfilehash: 019b8372be63b9a9fdbcee134834a34f6bef2b74
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="thread-timers-visual-basic"></a>Timers de thread (Visual Basic)
A classe <xref:System.Threading.Timer?displayProperty=nameWithType> é útil para executar periodicamente uma tarefa em um thread separado. Por exemplo, você pode usar um temporizador de thread para verificar o status e a integridade de um banco de dados ou para fazer backup de arquivos críticos.  
  
## <a name="thread-timer-example"></a>Exemplo de temporizador de thread  
 O exemplo a seguir inicia uma tarefa a cada dois segundos e usa um sinalizador para iniciar o método <xref:System.IDisposable.Dispose%2A> que interrompe o temporizador. Este exemplo posta o status na janela de saída.  
  
```vb  
Private Class StateObjClass  
    ' Used to hold parameters for calls to TimerTask.  
    Public SomeValue As Integer  
    Public TimerReference As System.Threading.Timer  
    Public TimerCanceled As Boolean  
End Class  
  
Public Sub RunTimer()  
    Dim StateObj As New StateObjClass  
    StateObj.TimerCanceled = False  
    StateObj.SomeValue = 1  
    Dim TimerDelegate As New System.Threading.TimerCallback(AddressOf TimerTask)  
    ' Create a timer that calls a procedure every 2 seconds.  
    ' Note: There is no Start method; the timer starts running as soon as   
    ' the instance is created.  
    Dim TimerItem As New System.Threading.Timer(TimerDelegate, StateObj,  
                                                2000, 2000)  
    ' Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem  
  
    ' Run for ten loops.  
    While StateObj.SomeValue < 10  
        ' Wait one second.  
        System.Threading.Thread.Sleep(1000)  
    End While  
  
    ' Request Dispose of the timer object.  
    StateObj.TimerCanceled = True  
End Sub  
  
Private Sub TimerTask(ByVal StateObj As Object)  
    Dim State As StateObjClass = CType(StateObj, StateObjClass)  
    ' Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(State.SomeValue)  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " & Now.ToString)  
    If State.TimerCanceled Then  
        ' Dispose Requested.  
        State.TimerReference.Dispose()  
        System.Diagnostics.Debug.WriteLine("Done  " & Now)  
    End If  
End Sub  
```  
  
 Temporizadores de thread são particularmente úteis quando o objeto <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> não está disponível, assim como quando você está desenvolvendo aplicativos de console.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading>  
 [Aplicativos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
