---
title: Parâmetros e valores retornados para procedimentos multi-threaded (C#)
ms.date: 07/20/2015
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
ms.openlocfilehash: 218e297d192d37d55ff391045342262d7bf66a0c
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875113"
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="5dca4-102">Parâmetros e valores retornados para procedimentos multi-threaded (C#)</span><span class="sxs-lookup"><span data-stu-id="5dca4-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="5dca4-103">Fornecer e retornar valores em um aplicativo multithread é complicado porque o construtor para a classe thread deve ser passado como uma referência para um procedimento que não leva argumentos e não retorna nenhum valor.</span><span class="sxs-lookup"><span data-stu-id="5dca4-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="5dca4-104">As seções a seguir mostram algumas maneiras simples de fornecer parâmetros e retornar valores de procedimentos em threads separados.</span><span class="sxs-lookup"><span data-stu-id="5dca4-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="5dca4-105">Fornecendo parâmetros para procedimentos multithread</span><span class="sxs-lookup"><span data-stu-id="5dca4-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="5dca4-106">A melhor maneira de fornecer parâmetros para uma chamada de método multithread é encapsular o método de destino em uma classe e definir campos para essa classe que servirão de parâmetros para o novo thread.</span><span class="sxs-lookup"><span data-stu-id="5dca4-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="5dca4-107">A vantagem dessa abordagem é que você pode criar uma nova instância da classe, com seus próprios parâmetros, toda vez que desejar iniciar um novo thread.</span><span class="sxs-lookup"><span data-stu-id="5dca4-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="5dca4-108">Por exemplo, suponha que você tenha uma função que calcula a área de um triângulo, como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="5dca4-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="5dca4-109">Você pode escrever uma classe que encapsula a função `CalcArea` e cria campos para armazenar parâmetros de entrada, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5dca4-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="5dca4-110">Para usar o `AreaClass`, você pode criar um objeto `AreaClass` e definir as propriedades `Base` e `Height` conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="5dca4-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 <span data-ttu-id="5dca4-111">Observe que o procedimento `TestArea` não verifica o valor do campo `Area` após chamar o método `CalcArea`.</span><span class="sxs-lookup"><span data-stu-id="5dca4-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="5dca4-112">Como o `CalcArea` é executado em um thread separado, não há garantia de que o campo `Area` estará definido se você o verificar imediatamente após chamar `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="5dca4-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="5dca4-113">A próxima seção discute uma maneira melhor de retornar valores de procedimentos multithread.</span><span class="sxs-lookup"><span data-stu-id="5dca4-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="5dca4-114">Retornando valores de procedimentos multithread</span><span class="sxs-lookup"><span data-stu-id="5dca4-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="5dca4-115">Retornar valores de procedimentos executados em threads separados é complicado pelo fato de que os procedimentos não podem ser funções e não podem usar argumentos `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="5dca4-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="5dca4-116">A maneira mais fácil de retornar valores é usar o componente <xref:System.ComponentModel.BackgroundWorker> para gerenciar os threads e acionar um evento quando a tarefa estiver concluída e processar os resultados com um manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5dca4-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="5dca4-117">O exemplo a seguir retorna um valor acionando um evento de um procedimento em execução em um thread separado:</span><span class="sxs-lookup"><span data-stu-id="5dca4-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 <span data-ttu-id="5dca4-118">Você pode fornecer parâmetros e retornar valores para threads de pool de threads usando a variável de objeto de estado `ByVal` do método <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="5dca4-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="5dca4-119">Os threads do temporizador de thread também dão suporte a um objeto de estado para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="5dca4-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="5dca4-120">Para obter informações sobre o pooling de threads e os temporizadores de thread, confira [Pooling de thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) e [Temporizadores](../../../../standard/threading/timers.md).</span><span class="sxs-lookup"><span data-stu-id="5dca4-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Timers](../../../../standard/threading/timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dca4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dca4-121">See Also</span></span>  
 [<span data-ttu-id="5dca4-122">Instruções passo a passo: multithreading com o componente BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="5dca4-122">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [<span data-ttu-id="5dca4-123">Pooling de thread (C#)</span><span class="sxs-lookup"><span data-stu-id="5dca4-123">Thread Pooling (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="5dca4-124">Sincronização de thread (C#)</span><span class="sxs-lookup"><span data-stu-id="5dca4-124">Thread Synchronization (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [<span data-ttu-id="5dca4-125">Eventos</span><span class="sxs-lookup"><span data-stu-id="5dca4-125">Events</span></span>](../../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="5dca4-126">Aplicativos com multithread (C#)</span><span class="sxs-lookup"><span data-stu-id="5dca4-126">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="5dca4-127">Delegados</span><span class="sxs-lookup"><span data-stu-id="5dca4-127">Delegates</span></span>](../../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="5dca4-128">Multithreading em componentes</span><span class="sxs-lookup"><span data-stu-id="5dca4-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
