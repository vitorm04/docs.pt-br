---
title: "Par&#226;metros e valores de retorno para procedimentos multithread (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros e valores de retorno para procedimentos multithread (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Fornecer e retornar valores em um aplicativo multithread é complicado porque o construtor para a classe thread deve ser passado como uma referência para um procedimento que não leva argumentos e não retorna nenhum valor. As seções a seguir mostram algumas maneiras simples de fornecer parâmetros e retornar valores de procedimentos em segmentos separados.  
  
## Fornecer parâmetros para procedimentos multithread  
 A melhor maneira de fornecer parâmetros para uma chamada de método com vários segmentos é encapsular o método de destino em uma classe e definir campos para a classe que servirá como parâmetros para o novo thread. A vantagem dessa abordagem é que você pode criar uma nova instância da classe, com seus próprios parâmetros, toda vez que você deseja iniciar um novo segmento. Por exemplo, suponha que você tenha uma função que calcula a área de um triângulo, como no seguinte código:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Você pode escrever uma classe que encapsula o `CalcArea` de função e cria campos para armazenar parâmetros de entrada, da seguinte maneira:  
  
```vb  
Class AreaClass  
    Public Base As Double  
    Public Height As Double  
    Public Area As Double  
    Sub CalcArea()  
        Area = 0.5 * Base * Height  
        MessageBox.Show("The area is: " & Area.ToString)  
    End Sub  
End Class  
```  
  
 Para usar o `AreaClass`, você pode criar um `AreaClass` do objeto e defina a `Base` e `Height` propriedades conforme mostrado no código a seguir:  
  
```vb  
Protected Sub TestArea()  
    Dim AreaObject As New AreaClass  
    Dim Thread As New System.Threading.Thread(  
                        AddressOf AreaObject.CalcArea)  
    AreaObject.Base = 30  
    AreaObject.Height = 40  
    Thread.Start()  
End Sub  
```  
  
 Observe que o `TestArea` procedimento verifica se o valor da `Area` campo depois de chamar o `CalcArea` método. Porque `CalcArea` é executado em um thread separado, o `Area` campo não é garantido para ser definido se você verificar imediatamente depois de chamar `Thread.Start`. A próxima seção discute uma melhor forma para retornar valores de procedimentos multithread.  
  
## Retornar valores de procedimentos multithread  
 Retornar valores de procedimentos executados em segmentos separados é complicado pelo fato de que os procedimentos não podem ser funções e não é possível usar `ByRef` argumentos. A maneira mais fácil de retornar valores é usar o <xref:System.ComponentModel.BackgroundWorker> componente para gerenciar seus segmentos e disparar um evento quando a tarefa estiver concluída e processar os resultados com um manipulador de eventos.  
  
 O exemplo a seguir retorna um valor ao disparar um evento de um procedimento em execução em um thread separado:  
  
```vb  
Private Class AreaClass2  
    Public Base As Double  
    Public Height As Double  
    Function CalcArea() As Double  
        ' Calculate the area of a triangle.  
        Return 0.5 * Base * Height  
    End Function  
End Class  
  
Private WithEvents BackgroundWorker1 As New System.ComponentModel.BackgroundWorker  
  
Private Sub TestArea2()  
    Dim AreaObject2 As New AreaClass2  
    AreaObject2.Base = 30  
    AreaObject2.Height = 40  
  
    ' Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2)  
End Sub  
  
' This method runs on the background thread when it starts.  
Private Sub BackgroundWorker1_DoWork(  
    ByVal sender As Object,   
    ByVal e As System.ComponentModel.DoWorkEventArgs  
    ) Handles BackgroundWorker1.DoWork  
  
    Dim AreaObject2 As AreaClass2 = CType(e.Argument, AreaClass2)  
    ' Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea()  
End Sub  
  
' This method runs on the main thread when the background thread finishes.  
Private Sub BackgroundWorker1_RunWorkerCompleted(  
    ByVal sender As Object,  
    ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
    ) Handles BackgroundWorker1.RunWorkerCompleted  
  
    ' Access the result through the Result property.  
    Dim Area As Double = CDbl(e.Result)  
    MessageBox.Show("The area is: " & Area.ToString)  
End Sub  
```  
  
 Você pode fornecer parâmetros e retornar valores para segmentos de pool de segmentos usando opcional `ByVal` variável de objeto de estado de <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> método. Segmentos timer de segmento também oferecem suporte a um objeto de estado para essa finalidade. Para obter informações sobre o pool de segmento e timers de thread, consulte [Thread Pooling \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Pooling de thread](../Topic/Thread%20Pooling%20\(C%23%20and%20Visual%20Basic\).md) e [Timers de thread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).  
  
## Consulte também  
 [Passo a passo: Multithreading com o componente BackgroundWorker \(Visual Basic\)](../Topic/Walkthrough:%20Multithreading%20with%20the%20BackgroundWorker%20Component%20\(Visual%20Basic\).md)   
 [Thread Pooling \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)   
 [Sincronização de thread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Aplicativos multithread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [Multithreading in Components](../Topic/Multithreading%20in%20Components.md)