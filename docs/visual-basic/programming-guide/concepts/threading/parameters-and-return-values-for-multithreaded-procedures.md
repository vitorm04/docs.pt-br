---
title: "Parâmetros e valores de retorno para procedimentos multithread (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 071e0aa916e4b3464c7c0cbff6596cabc6b67906
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="b297d-102">Parâmetros e valores de retorno para procedimentos multithread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b297d-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="b297d-103">Fornecer e retornar valores em um aplicativo multithread é complicado porque o construtor para a classe thread deve ser passado como uma referência para um procedimento que não leva argumentos e não retorna nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="b297d-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="b297d-104">As seções a seguir mostram algumas maneiras simples de fornecer parâmetros e retornar valores de procedimentos em threads separados.</span><span class="sxs-lookup"><span data-stu-id="b297d-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="b297d-105">Fornecendo parâmetros para procedimentos multithread</span><span class="sxs-lookup"><span data-stu-id="b297d-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="b297d-106">A melhor maneira de fornecer parâmetros para uma chamada de método multithread é encapsular o método de destino em uma classe e definir campos para essa classe que servirão de parâmetros para o novo thread.</span><span class="sxs-lookup"><span data-stu-id="b297d-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="b297d-107">A vantagem dessa abordagem é que você pode criar uma nova instância da classe, com seus próprios parâmetros, toda vez que desejar iniciar um novo thread.</span><span class="sxs-lookup"><span data-stu-id="b297d-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="b297d-108">Por exemplo, suponha que você tenha uma função que calcula a área de um triângulo, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b297d-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="b297d-109">Você pode escrever uma classe que encapsula a função `CalcArea` e cria campos para armazenar parâmetros de entrada, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b297d-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
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
  
 <span data-ttu-id="b297d-110">Para usar o `AreaClass`, você pode criar um objeto `AreaClass` e definir as propriedades `Base` e `Height` conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b297d-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
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
  
 <span data-ttu-id="b297d-111">Observe que o procedimento `TestArea` não verifica o valor do campo `Area` após chamar o método `CalcArea`.</span><span class="sxs-lookup"><span data-stu-id="b297d-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="b297d-112">Como o `CalcArea` é executado em um thread separado, não há garantia de que o campo `Area` estará definido se você o verificar imediatamente após chamar `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="b297d-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="b297d-113">A próxima seção discute uma maneira melhor de retornar valores de procedimentos multithread.</span><span class="sxs-lookup"><span data-stu-id="b297d-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="b297d-114">Retornando valores de procedimentos multithread</span><span class="sxs-lookup"><span data-stu-id="b297d-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="b297d-115">Retornar valores de procedimentos executados em threads separados é complicado pelo fato de que os procedimentos não podem ser funções e não podem usar argumentos `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="b297d-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="b297d-116">A maneira mais fácil de retornar valores é usar o componente <xref:System.ComponentModel.BackgroundWorker> para gerenciar os threads e acionar um evento quando a tarefa estiver concluída e processar os resultados com um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="b297d-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="b297d-117">O exemplo a seguir retorna um valor acionando um evento de um procedimento em execução em um thread separado:</span><span class="sxs-lookup"><span data-stu-id="b297d-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
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
  
 <span data-ttu-id="b297d-118">Você pode fornecer parâmetros e retornar valores para threads de pool de threads usando a variável de objeto de estado `ByVal` do método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="b297d-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="b297d-119">Os threads do temporizador de thread também dão suporte a um objeto de estado para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="b297d-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="b297d-120">Para obter informações sobre o pool de thread e timers de thread, consulte [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) e [Timers de Thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span><span class="sxs-lookup"><span data-stu-id="b297d-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Thread Timers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b297d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b297d-121">See Also</span></span>  
 [<span data-ttu-id="b297d-122">Instruções passo a passo: multithreading com o componente BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b297d-122">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="b297d-123">Pooling de thread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b297d-123">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="b297d-124">Sincronização de thread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b297d-124">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="b297d-125">Eventos</span><span class="sxs-lookup"><span data-stu-id="b297d-125">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="b297d-126">Aplicativos multithread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b297d-126">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="b297d-127">Delegados</span><span class="sxs-lookup"><span data-stu-id="b297d-127">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="b297d-128">Multithreading em componentes</span><span class="sxs-lookup"><span data-stu-id="b297d-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
