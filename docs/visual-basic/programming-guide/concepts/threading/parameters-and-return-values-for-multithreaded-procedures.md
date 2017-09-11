---
title: "Parâmetros e valores de retorno para procedimentos multithread (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: cbdce172-7ff6-41a9-bb21-53a7c6f538a5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 6d1eb53454b6e0d964be15df2e320ce189e7d875
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-visual-basic"></a><span data-ttu-id="098ed-102">Parâmetros e valores de retorno para procedimentos multithread (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="098ed-102">Parameters and Return Values for Multithreaded Procedures (Visual Basic)</span></span>
<span data-ttu-id="098ed-103">Fornecer e retornar valores em um aplicativo multithread é complicado porque o construtor para a classe thread deve ser passado como uma referência para um procedimento que não leva argumentos e não retorna nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="098ed-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="098ed-104">As seções a seguir mostram algumas maneiras simples de fornecer parâmetros e retornar valores de procedimentos em segmentos separados.</span><span class="sxs-lookup"><span data-stu-id="098ed-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="098ed-105">Fornecer parâmetros para procedimentos multithread</span><span class="sxs-lookup"><span data-stu-id="098ed-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="098ed-106">A melhor maneira de fornecer parâmetros para uma chamada de método com vários segmentos é encapsular o método de destino em uma classe e definir campos para a classe que servirá como parâmetros para o novo thread.</span><span class="sxs-lookup"><span data-stu-id="098ed-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="098ed-107">A vantagem dessa abordagem é que você pode criar uma nova instância da classe, com seus próprios parâmetros, toda vez que você deseja iniciar um novo segmento.</span><span class="sxs-lookup"><span data-stu-id="098ed-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="098ed-108">Por exemplo, suponha que você tenha uma função que calcula a área de um triângulo, como no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="098ed-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```vb  
Function CalcArea(ByVal Base As Double, ByVal Height As Double) As Double  
    CalcArea = 0.5 * Base * Height  
End Function  
```  
  
 <span data-ttu-id="098ed-109">Você pode escrever uma classe que encapsula o `CalcArea` de função e cria campos para armazenar parâmetros de entrada, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="098ed-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
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
  
 <span data-ttu-id="098ed-110">Para usar o `AreaClass`, você pode criar um `AreaClass` do objeto e defina o `Base` e `Height` propriedades conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="098ed-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
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
  
 <span data-ttu-id="098ed-111">Observe que o `TestArea` procedimento verifica se o valor da `Area` campo depois de chamar o `CalcArea` método.</span><span class="sxs-lookup"><span data-stu-id="098ed-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="098ed-112">Porque `CalcArea` é executado em um thread separado, o `Area` campo não é garantido para ser definido se você verificar imediatamente depois de chamar `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="098ed-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="098ed-113">A próxima seção discute uma melhor forma para retornar valores de procedimentos multithread.</span><span class="sxs-lookup"><span data-stu-id="098ed-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="098ed-114">Retornar valores de procedimentos multithread</span><span class="sxs-lookup"><span data-stu-id="098ed-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="098ed-115">Retornar valores de procedimentos executados em segmentos separados é complicado pelo fato de que os procedimentos não podem ser funções e não é possível usar `ByRef` argumentos.</span><span class="sxs-lookup"><span data-stu-id="098ed-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="098ed-116">A maneira mais fácil de retornar valores é usar o <xref:System.ComponentModel.BackgroundWorker>componente para gerenciar seus segmentos e disparar um evento quando a tarefa estiver concluída e processar os resultados com um manipulador de eventos.</xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="098ed-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="098ed-117">O exemplo a seguir retorna um valor ao disparar um evento de um procedimento em execução em um thread separado:</span><span class="sxs-lookup"><span data-stu-id="098ed-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
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
  
 <span data-ttu-id="098ed-118">Você pode fornecer parâmetros e retornar valores para segmentos de pool de segmentos usando opcional `ByVal` variável de objeto de estado de <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>método.</xref:System.Threading.ThreadPool.QueueUserWorkItem%2A></span><span class="sxs-lookup"><span data-stu-id="098ed-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="098ed-119">Segmentos timer de segmento também oferecem suporte a um objeto de estado para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="098ed-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="098ed-120">Para obter informações sobre o pool de segmento e timers de thread, consulte [(Visual Basic) do pool de segmentos](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) e [Timers de Thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span><span class="sxs-lookup"><span data-stu-id="098ed-120">For information on thread pooling and thread timers, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)[Thread Pooling](http://msdn.microsoft.com/library/4b8bb2c8-8ca4-457c-9afd-d11bc9a05701) and [Thread Timers (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098ed-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="098ed-121">See Also</span></span>  
 <span data-ttu-id="098ed-122">[Passo a passo: Multithreading com o componente BackgroundWorker (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span><span class="sxs-lookup"><span data-stu-id="098ed-122">[Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span></span>  
<span data-ttu-id="098ed-123"> [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span><span class="sxs-lookup"><span data-stu-id="098ed-123"> [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md) </span></span>  
<span data-ttu-id="098ed-124"> [Sincronização de thread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="098ed-124"> [Thread Synchronization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
<span data-ttu-id="098ed-125"> [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="098ed-125"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="098ed-126"> [Aplicativos multithread (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="098ed-126"> [Multithreaded Applications (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
<span data-ttu-id="098ed-127"> [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="098ed-127"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="098ed-128"> [Multithreading em componentes](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)</span><span class="sxs-lookup"><span data-stu-id="098ed-128"> [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)</span></span>
