---
title: Tipos de retorno assíncrono (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 387b75db3078afb92e6fc3ad7607b293abb0c851
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351953"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="b5cf7-102">Tipos de retorno assíncrono (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5cf7-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="b5cf7-103">Os métodos Async têm três tipos de retorno possíveis: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> e void.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="b5cf7-104">No Visual Basic, o tipo de retorno void é gravado como um procedimento [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b5cf7-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="b5cf7-105">Para obter mais informações sobre métodos assíncronos, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5cf7-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="b5cf7-106">Cada tipo de retorno é examinado em uma das seções a seguir e você pode encontrar um exemplo completo que usa todos os três tipos no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5cf7-107">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="b5cf7-108">Tipo de retorno Task(T)</span><span class="sxs-lookup"><span data-stu-id="b5cf7-108">Task(T) Return Type</span></span>  
 <span data-ttu-id="b5cf7-109">O tipo de retorno <xref:System.Threading.Tasks.Task%601> é usado para um método assíncrono que contém uma instrução de [retorno](../../../../visual-basic/language-reference/statements/return-statement.md) na qual o operando tem o tipo `TResult`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="b5cf7-110">No exemplo a seguir, o método assíncrono `TaskOfT_MethodAsync` contém uma instrução return que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="b5cf7-111">Portanto, a declaração do método deve especificar um tipo de retorno de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 <span data-ttu-id="b5cf7-112">Quando `TaskOfT_MethodAsync` é chamado de dentro de uma expressão await, a expressão await recupera o valor inteiro (o valor de `leisureHours`) que está armazenado na tarefa que é retornada pelo `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="b5cf7-113">Para obter mais informações sobre expressões Await, consulte [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b5cf7-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="b5cf7-114">O código a seguir chama e aguarda o método `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="b5cf7-115">O resultado é atribuído à variável `result1`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="b5cf7-116">Você pode entender melhor como isso acontece, separando a chamada ao `TaskOfT_MethodAsync` da aplicação do `Await`, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="b5cf7-117">Uma chamada ao método `TaskOfT_MethodAsync` que não é aguardada imediatamente, retorna um `Task(Of Integer)`, como você esperaria da declaração do método.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="b5cf7-118">A tarefa é atribuída à variável `integerTask` no exemplo.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="b5cf7-119">Já que `integerTask` é um <xref:System.Threading.Tasks.Task%601>, ele contém uma propriedade <xref:System.Threading.Tasks.Task%601.Result> do tipo `TResult`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="b5cf7-120">Nesse caso, TResult representa um tipo inteiro.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="b5cf7-121">Quando `Await` é aplicado à `integerTask`, a expressão await é avaliada como o conteúdo da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="b5cf7-122">O valor é atribuído à variável `result2`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="b5cf7-123">A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> é uma propriedade de bloqueio.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="b5cf7-124">Se você tentar acessá-la antes que sua tarefa seja concluída, o thread que está ativo no momento será bloqueado até que a tarefa seja concluída e o valor esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="b5cf7-125">Na maioria dos casos, você deve acessar o valor usando `Await` em vez de acessar a propriedade diretamente.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="b5cf7-126">As instruções de exibição no código a seguir verificam se os valores da variável `result1`, da variável `result2` e da propriedade `Result` são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="b5cf7-127">Lembre-se que a propriedade `Result` é uma propriedade de bloqueio e não deve ser acessada antes que sua tarefa tenha sido aguardada.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
## <a name="BKMK_TaskReturnType"></a> <span data-ttu-id="b5cf7-128">Tipo de retorno Task</span><span class="sxs-lookup"><span data-stu-id="b5cf7-128">Task Return Type</span></span>  
 <span data-ttu-id="b5cf7-129">Os métodos assíncronos que não contêm uma instrução Return ou que contêm uma instrução Return que não retorna um operando geralmente têm um tipo de retorno de <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="b5cf7-130">Esses métodos seriam procedimentos [sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) se fossem escritos para serem executados de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="b5cf7-131">Se você usar um tipo de retorno `Task` para um método assíncrono, um método de chamada poderá usar um operador `Await` para suspender a conclusão do chamador até que o método assíncrono chamado seja concluído.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="b5cf7-132">No exemplo a seguir, o método assíncrono `Task_MethodAsync` não contém uma instrução return.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="b5cf7-133">Portanto, você especifica um tipo de retorno de `Task` para o método, que permite que `Task_MethodAsync` seja aguardado.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="b5cf7-134">A definição do tipo `Task` não inclui uma propriedade `Result` para armazenar um valor retornado.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 <span data-ttu-id="b5cf7-135">`Task_MethodAsync` é chamado e aguardado usando uma instrução Await em vez de uma expressão Await, semelhante à instrução de chamada para um método síncrono de retorno de `Sub` ou void.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="b5cf7-136">O aplicativo de um operador `Await` nesse caso não produz um valor.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="b5cf7-137">O código a seguir chama e aguarda o método `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="b5cf7-138">Como no exemplo anterior <xref:System.Threading.Tasks.Task%601>, você pode separar a chamada para `Task_MethodAsync` do aplicativo de um operador `Await`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="b5cf7-139">No entanto, lembre-se que uma `Task` não tem uma propriedade `Result` e que nenhum valor será produzido quando um operador await for aplicado a uma `Task`.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="b5cf7-140">O código a seguir separa a chamada ao `Task_MethodAsync` da espera pela tarefa que `Task_MethodAsync` retorna.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
## <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="b5cf7-141">Tipo de retorno void</span><span class="sxs-lookup"><span data-stu-id="b5cf7-141">Void Return Type</span></span>  
 <span data-ttu-id="b5cf7-142">O uso principal dos procedimentos `Sub` é em manipuladores de eventos, em que não há nenhum tipo de retorno (chamado de tipo de retorno void em outras linguagens).</span><span class="sxs-lookup"><span data-stu-id="b5cf7-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="b5cf7-143">Um retorno void também pode ser usado para substituir métodos de retorno void ou para métodos que realizam atividades que podem ser categorizadas como "disparar e esquecer".</span><span class="sxs-lookup"><span data-stu-id="b5cf7-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="b5cf7-144">No entanto, você deve retornar uma `Task` sempre que possível, porque um método assíncrono de retorno void não pode ser aguardado.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="b5cf7-145">Qualquer chamador desse método deve ser capaz de continuar até a conclusão, sem aguardar a conclusão do método assíncrono chamado e o chamador deve ser independente de todos os valores ou exceções gerados pelo método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="b5cf7-146">O chamador de um método assíncrono de retorno void não pode capturar exceções que são lançadas pelo método e essas exceções sem tratamento provavelmente causarão falha do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="b5cf7-147">Se ocorrer uma exceção em um método assíncrono que retorna um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, a exceção é armazenada na tarefa retornada e relançada quando a tarefa é esperada.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="b5cf7-148">Portanto, verifique se qualquer método assíncrono que pode produzir uma exceção tem um tipo de retorno de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> e que as chamadas ao método são aguardadas.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="b5cf7-149">Para obter mais informações sobre como capturar exceções nos métodos assíncronos, consulte a [Instrução Try... Catch... Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b5cf7-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="b5cf7-150">O código a seguir define um manipulador de eventos assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-150">The following code defines an async event handler.</span></span>  
  
```vb  
' SUB EXAMPLE  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
    textBox1.Clear()  
  
    ' Start the process and await its completion. DriverAsync is a   
    ' Task-returning async method.  
    Await DriverAsync()  
  
    ' Say goodbye.  
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
End Sub  
```  
  
## <a name="BKMK_Example"></a> <span data-ttu-id="b5cf7-151">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="b5cf7-151">Complete Example</span></span>  
 <span data-ttu-id="b5cf7-152">O projeto WPF (Windows Presentation Foundation) a seguir contém os exemplos de código deste tópico.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="b5cf7-153">Para executar o projeto, realize as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="b5cf7-153">To run the project, perform the following steps:</span></span>  
  
1. <span data-ttu-id="b5cf7-154">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-154">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="b5cf7-155">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="b5cf7-156">A caixa de diálogo **Novo Projeto** é aberta.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-156">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="b5cf7-157">Na categoria **instalado**, **modelos** , escolha **Visual Basic**e, em seguida, escolha **Windows**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="b5cf7-158">Escolha **Aplicativo WPF** na lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4. <span data-ttu-id="b5cf7-159">Digite `AsyncReturnTypes` como o nome do projeto e, em seguida, escolha o botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="b5cf7-160">O novo projeto aparece no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-160">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="b5cf7-161">No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="b5cf7-162">Se a guia não estiver visível, abra o menu de atalho para MainWindow.xaml no **Gerenciador de Soluções** e, em seguida, escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6. <span data-ttu-id="b5cf7-163">Na janela **XAML** de MainWindow.xaml, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="b5cf7-164">Uma janela simples, contendo uma caixa de texto e um botão, aparecerá na janela **Design** de MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7. <span data-ttu-id="b5cf7-165">No **Gerenciador de soluções**, abra o menu de atalho para MainWindow. XAML. vb e escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8. <span data-ttu-id="b5cf7-166">Substitua o código em MainWindow. XAML. vb pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. <span data-ttu-id="b5cf7-167">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="b5cf7-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="b5cf7-168">A saída a seguir deve aparecer:</span><span class="sxs-lookup"><span data-stu-id="b5cf7-168">The following output should appear:</span></span>  
  
    ```console  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b5cf7-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5cf7-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="b5cf7-170">Passo a passo: Acessando a Web usando Async e Await (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="b5cf7-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="b5cf7-171">Fluxo de controle em programas assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5cf7-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="b5cf7-172">Async</span><span class="sxs-lookup"><span data-stu-id="b5cf7-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="b5cf7-173">Operador Await</span><span class="sxs-lookup"><span data-stu-id="b5cf7-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
