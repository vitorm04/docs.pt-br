---
title: Parâmetros e valores de retorno para procedimentos multithread (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
ms.openlocfilehash: 545da3e89d44c29c67784b5f01812d87350030c6
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874605"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a>Parâmetros e valores de retorno para procedimentos multithread (Visual Basic)
Fornecer e retornar valores em um aplicativo multithread é complicado porque o construtor para a classe thread deve ser passado como uma referência para um procedimento que não leva argumentos e não retorna nenhum valor. As seções a seguir mostram algumas maneiras simples de fornecer parâmetros e retornar valores de procedimentos em threads separados.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Fornecendo parâmetros para procedimentos multithread  
 A melhor maneira de fornecer parâmetros para uma chamada de método multithread é encapsular o método de destino em uma classe e definir campos para essa classe que servirão de parâmetros para o novo thread. A vantagem dessa abordagem é que você pode criar uma nova instância da classe, com seus próprios parâmetros, toda vez que desejar iniciar um novo thread. Por exemplo, suponha que você tenha uma função que calcula a área de um triângulo, como no código a seguir:  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 Você pode escrever uma classe que encapsula a função `CalcArea` e cria campos para armazenar parâmetros de entrada, da seguinte maneira:  
  
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
  
 Para usar o `AreaClass`, você pode criar um objeto `AreaClass` e definir as propriedades `Base` e `Height` conforme mostrado no código a seguir:  
  
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
  
 Observe que o procedimento `TestArea` não verifica o valor do campo `Area` após chamar o método `CalcArea`. Como o `CalcArea` é executado em um thread separado, não há garantia de que o campo `Area` estará definido se você o verificar imediatamente após chamar `Thread.Start`. A próxima seção discute uma maneira melhor de retornar valores de procedimentos multithread.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Retornando valores de procedimentos multithread  
 Retornar valores de procedimentos executados em threads separados é complicado pelo fato de que os procedimentos não podem ser funções e não podem usar argumentos `ByRef`. A maneira mais fácil de retornar valores é usar o componente <xref:System.ComponentModel.BackgroundWorker> para gerenciar os threads e acionar um evento quando a tarefa estiver concluída e processar os resultados com um manipulador de eventos.  
  
 O exemplo a seguir retorna um valor acionando um evento de um procedimento em execução em um thread separado:  
  
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
  
 Você pode fornecer parâmetros e retornar valores para threads de pool de threads usando a variável de objeto de estado `ByVal` do método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>. Os threads do temporizador de thread também dão suporte a um objeto de estado para essa finalidade. Para obter informações sobre o pool de thread e temporizadores de thread, consulte [(Visual Basic) do pool de segmentos](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Pooling de threads](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) e [temporizadores](../../../../standard/threading/timers.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instruções passo a passo: multithreading com o componente BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [Pooling de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [Sincronização de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Aplicativos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Multithreading em componentes](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
