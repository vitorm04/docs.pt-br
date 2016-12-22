---
title: "Timers de thread (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 52ed71e8-4fd9-43a4-ae40-04cce7cff23f
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Timers de thread (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:System.Threading.Timer?displayProperty=fullName> classe é útil para executar periodicamente uma tarefa em um thread separado. Por exemplo, você poderia usar um timer de segmento para verificar o status e a integridade de um banco de dados ou para fazer backup de arquivos críticos.  
  
## Exemplo de Timer de segmento  
 O exemplo a seguir inicia uma tarefa a cada dois segundos e usa um sinalizador para iniciar o <xref:System.IDisposable.Dispose%2A> método que interrompe o timer. Este exemplo envia o status para a janela de saída.  
  
```c#  
private class StateObjClass  
{  
    // Used to hold parameters for calls to TimerTask.  
    public int SomeValue;  
    public System.Threading.Timer TimerReference;  
    public bool TimerCanceled;  
}  
  
public void RunTimer()  
{  
    StateObjClass StateObj = new StateObjClass();  
    StateObj.TimerCanceled = false;  
    StateObj.SomeValue = 1;  
    System.Threading.TimerCallback TimerDelegate =  
        new System.Threading.TimerCallback(TimerTask);  
  
    // Create a timer that calls a procedure every 2 seconds.  
    // Note: There is no Start method; the timer starts running as soon as   
    // the instance is created.  
    System.Threading.Timer TimerItem =  
        new System.Threading.Timer(TimerDelegate, StateObj, 2000, 2000);  
  
    // Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem;    
  
    // Run for ten loops.  
    while (StateObj.SomeValue < 10)   
    {  
        // Wait one second.  
        System.Threading.Thread.Sleep(1000);    
    }  
  
    // Request Dispose of the timer object.  
    StateObj.TimerCanceled = true;    
}  
  
private void TimerTask(object StateObj)  
{  
    StateObjClass State = (StateObjClass)StateObj;  
    // Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(ref State.SomeValue);  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " + DateTime.Now.ToString());  
    if (State.TimerCanceled)      
    // Dispose Requested.  
    {  
        State.TimerReference.Dispose();  
        System.Diagnostics.Debug.WriteLine("Done  " + DateTime.Now.ToString());  
    }  
}  
```  
  
 Timers de thread são particularmente úteis quando o <xref:System.Windows.Forms.Timer?displayProperty=fullName> objeto está indisponível, como quando você estiver desenvolvendo aplicativos de console.  
  
## Consulte também  
 <xref:System.Threading>   
 [Aplicativos multithread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)