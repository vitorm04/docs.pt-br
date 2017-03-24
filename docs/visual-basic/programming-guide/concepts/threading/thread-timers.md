---
title: Thread Timers (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 809cba93-cc93-4e21-afda-f299f9a39818
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9ea657482d4e8e1465d9bc6ae3f94915badee512
ms.lasthandoff: 03/13/2017

---
# <a name="thread-timers-visual-basic"></a>Timers de thread (Visual Basic)
O <xref:System.Threading.Timer?displayProperty=fullName>classe é útil para executar periodicamente uma tarefa em um thread separado.</xref:System.Threading.Timer?displayProperty=fullName> Por exemplo, você poderia usar um timer de segmento para verificar o status e a integridade de um banco de dados ou para fazer backup de arquivos críticos.  
  
## <a name="thread-timer-example"></a>Exemplo de Timer de segmento  
 O exemplo a seguir inicia uma tarefa a cada dois segundos e usa um sinalizador para iniciar o <xref:System.IDisposable.Dispose%2A>método que interrompe o timer.</xref:System.IDisposable.Dispose%2A> Este exemplo envia o status para a janela de saída.  
  
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
  
 Timers de thread são particularmente úteis quando o <xref:System.Windows.Forms.Timer?displayProperty=fullName>objeto está indisponível, como quando você estiver desenvolvendo aplicativos de console.</xref:System.Windows.Forms.Timer?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading></xref:System.Threading>   
 [Aplicativos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)
