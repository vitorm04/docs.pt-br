---
title: "Tipos de retorno assíncronos (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 703d3fc3f503017edf38521d77f9b15a92d0ebf3
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="03d6a-102">Tipos de retorno assíncronos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03d6a-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="03d6a-103">Os métodos assíncronos têm três tipos de retornos possíveis: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>e void.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="03d6a-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="03d6a-104">No Visual Basic, o tipo de retorno void é gravado como um [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimento.</span><span class="sxs-lookup"><span data-stu-id="03d6a-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="03d6a-105">Para obter mais informações sobre os métodos assíncronos, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="03d6a-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="03d6a-106">Cada tipo de retorno é examinado em uma das seções a seguir, e você pode encontrar um exemplo completo que usa todos os três tipos no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="03d6a-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="03d6a-107">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="03d6a-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="03d6a-108"><a name="BKMK_TaskTReturnType"></a>Tipo de retorno de Task(T)</span><span class="sxs-lookup"><span data-stu-id="03d6a-108"><a name="BKMK_TaskTReturnType"></a> Task(T) Return Type</span></span>  
 <span data-ttu-id="03d6a-109">O <xref:System.Threading.Tasks.Task%601>retornar o tipo é usado para um método assíncrono que contém um [retornar](../../../../visual-basic/language-reference/statements/return-statement.md) que o operando tem o tipo de instrução `TResult`.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="03d6a-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="03d6a-110">No exemplo a seguir, o `TaskOfT_MethodAsync` método assíncrono contém uma instrução return que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="03d6a-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="03d6a-111">Portanto, a declaração do método deve especificar um tipo de retorno de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="03d6a-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
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
  
 <span data-ttu-id="03d6a-112">Quando `TaskOfT_MethodAsync` é chamado de dentro de uma expressão await, a expressão await recupera o valor inteiro (o valor de `leisureHours`) que é armazenado na tarefa que é retornada pelo `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="03d6a-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="03d6a-113">Para obter mais informações sobre expressões await, consulte [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="03d6a-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="03d6a-114">O código a seguir chama e aguarda o método `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="03d6a-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="03d6a-115">O resultado é atribuído para a `result1` variável.</span><span class="sxs-lookup"><span data-stu-id="03d6a-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="03d6a-116">Você pode entender melhor como isso acontece, separando a chamada para `TaskOfT_MethodAsync` da aplicação do `Await`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="03d6a-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="03d6a-117">Uma chamada ao método `TaskOfT_MethodAsync` que não é aguardada imediatamente retorna um `Task(Of Integer)`, como você esperaria da declaração do método.</span><span class="sxs-lookup"><span data-stu-id="03d6a-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="03d6a-118">A tarefa é atribuída a `integerTask` variável no exemplo.</span><span class="sxs-lookup"><span data-stu-id="03d6a-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="03d6a-119">Porque `integerTask` é um <xref:System.Threading.Tasks.Task%601>, ele contém um <xref:System.Threading.Tasks.Task%601.Result>propriedade do tipo `TResult`.</xref:System.Threading.Tasks.Task%601.Result> </xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="03d6a-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="03d6a-120">Nesse caso, TResult representa um tipo inteiro.</span><span class="sxs-lookup"><span data-stu-id="03d6a-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="03d6a-121">Quando `Await` é aplicado a `integerTask`, a expressão await é avaliada como o conteúdo da <xref:System.Threading.Tasks.Task%601.Result%2A>propriedade `integerTask`.</xref:System.Threading.Tasks.Task%601.Result%2A></span><span class="sxs-lookup"><span data-stu-id="03d6a-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="03d6a-122">O valor é atribuído para a `result2` variável.</span><span class="sxs-lookup"><span data-stu-id="03d6a-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="03d6a-123">O <xref:System.Threading.Tasks.Task%601.Result%2A>é uma propriedade de bloqueio.</xref:System.Threading.Tasks.Task%601.Result%2A></span><span class="sxs-lookup"><span data-stu-id="03d6a-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="03d6a-124">Se você tentar acessá-lo antes de sua tarefa é concluída, o thread que está ativo no momento é bloqueado até que a tarefa seja concluída e o valor está disponível.</span><span class="sxs-lookup"><span data-stu-id="03d6a-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="03d6a-125">Na maioria dos casos, você deve acessar o valor usando `Await` em vez de acessar a propriedade diretamente.</span><span class="sxs-lookup"><span data-stu-id="03d6a-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="03d6a-126">As instruções de exibição no código a seguir, verifique se que os valores da `result1` variável, o `result2` variável e o `Result` são os mesmos.</span><span class="sxs-lookup"><span data-stu-id="03d6a-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="03d6a-127">Lembre-se de que o `Result` propriedade é uma propriedade de bloqueio e não deve ser acessada antes que a tarefa foi esperada.</span><span class="sxs-lookup"><span data-stu-id="03d6a-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <span data-ttu-id="03d6a-128"><a name="BKMK_TaskReturnType"></a>Tipo de retorno de tarefa</span><span class="sxs-lookup"><span data-stu-id="03d6a-128"><a name="BKMK_TaskReturnType"></a> Task Return Type</span></span>  
 <span data-ttu-id="03d6a-129">Os métodos Async que não contêm uma instrução return ou que contêm uma instrução return que não retorna um operando normalmente têm um tipo de retorno de <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="03d6a-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="03d6a-130">Esses métodos seria [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimentos se eles fossem escritos para execução síncrona.</span><span class="sxs-lookup"><span data-stu-id="03d6a-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="03d6a-131">Se você usar um `Task` tipo de retorno para um método assíncrono, um método de chamada pode usar um `Await` operador para suspender a conclusão do chamador até que o método de chamada assíncrona seja concluída.</span><span class="sxs-lookup"><span data-stu-id="03d6a-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="03d6a-132">No exemplo a seguir, o método assíncrono `Task_MethodAsync` não contém uma instrução return.</span><span class="sxs-lookup"><span data-stu-id="03d6a-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="03d6a-133">Portanto, você pode especificar um tipo de retorno de `Task` para o método, que permite `Task_MethodAsync` para ser colocado em espera.</span><span class="sxs-lookup"><span data-stu-id="03d6a-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="03d6a-134">A definição de `Task` tipo não inclui um `Result` propriedade para armazenar um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="03d6a-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
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
  
 <span data-ttu-id="03d6a-135">`Task_MethodAsync`é chamado e esperado, usando uma instrução de espera, em vez de uma expressão await, semelhante à instrução de chamada para um síncrono `Sub` ou método que retorna void.</span><span class="sxs-lookup"><span data-stu-id="03d6a-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="03d6a-136">A aplicação de uma `Await` operador nesse caso não produz um valor.</span><span class="sxs-lookup"><span data-stu-id="03d6a-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="03d6a-137">O código a seguir chama e aguarda o método `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="03d6a-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="03d6a-138">Como o anterior <xref:System.Threading.Tasks.Task%601>exemplo, você pode separar a chamada para `Task_MethodAsync` da aplicação de uma `Await` operador, como mostra o código a seguir.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="03d6a-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="03d6a-139">No entanto, lembre-se de que uma `Task` não tem um `Result` propriedade e que nenhum valor é produzido quando um operador de espera é aplicado a um `Task`.</span><span class="sxs-lookup"><span data-stu-id="03d6a-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="03d6a-140">O código a seguir separa chamada `Task_MethodAsync` de aguardando a tarefa que `Task_MethodAsync` retorna.</span><span class="sxs-lookup"><span data-stu-id="03d6a-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
<span data-ttu-id="03d6a-141"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="03d6a-141"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
##  <span data-ttu-id="03d6a-142"><a name="BKMK_VoidReturnType"></a>Tipo de retorno void</span><span class="sxs-lookup"><span data-stu-id="03d6a-142"><a name="BKMK_VoidReturnType"></a> Void Return Type</span></span>  
 <span data-ttu-id="03d6a-143">O principal uso de `Sub` procedimentos é em manipuladores de eventos, onde não há nenhum tipo de retorno (conhecido como um tipo de retorno void em outras linguagens).</span><span class="sxs-lookup"><span data-stu-id="03d6a-143">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="03d6a-144">Um retorno de void também pode ser usado para substituir os métodos que retornam void ou para métodos que executam atividades que podem ser categorizadas como "disparar e esquecer."</span><span class="sxs-lookup"><span data-stu-id="03d6a-144">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="03d6a-145">No entanto, você deve retornar um `Task` sempre que possível, porque um método async que retorna void não pode ser colocado em espera.</span><span class="sxs-lookup"><span data-stu-id="03d6a-145">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="03d6a-146">Qualquer chamador desse método deve ser capaz de continuar até a conclusão, sem aguardar a conclusão do método assíncrono chamado e o chamador deve ser independente de quaisquer valores ou exceções que gera o método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="03d6a-146">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="03d6a-147">O chamador de um método async que retorna void não pode capturar exceções que são geradas pelo método, e essas exceções sem tratamento provavelmente fazer com que o aplicativo falhar.</span><span class="sxs-lookup"><span data-stu-id="03d6a-147">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="03d6a-148">Se ocorrer uma exceção em um método async que retorna um <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>, a exceção é armazenada na tarefa retornada e relançada quando a tarefa é aguardada.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="03d6a-148">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="03d6a-149">Portanto, certifique-se de que qualquer método assíncrono que pode gerar uma exceção tem um tipo de retorno de <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>e que as chamadas para o método são aguardadas.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="03d6a-149">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="03d6a-150">Para obter mais informações sobre como capturar exceções em métodos assíncronos, consulte [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="03d6a-150">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="03d6a-151">O código a seguir define um manipulador de eventos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="03d6a-151">The following code defines an async event handler.</span></span>  
  
<span data-ttu-id="03d6a-152"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="03d6a-152"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
##  <span data-ttu-id="03d6a-153"><a name="BKMK_Example"></a>Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="03d6a-153"><a name="BKMK_Example"></a> Complete Example</span></span>  
 <span data-ttu-id="03d6a-154">O projeto Windows Presentation Foundation (WPF) a seguir contém exemplos de código deste tópico.</span><span class="sxs-lookup"><span data-stu-id="03d6a-154">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="03d6a-155">Para executar o projeto, execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="03d6a-155">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="03d6a-156">Inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03d6a-156">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="03d6a-157">Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.</span><span class="sxs-lookup"><span data-stu-id="03d6a-157">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="03d6a-158">O **novo projeto** caixa de diálogo é aberta.</span><span class="sxs-lookup"><span data-stu-id="03d6a-158">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="03d6a-159">No **instalados**, **modelos** categoria, escolha **Visual Basic**e, em seguida, escolha **Windows**.</span><span class="sxs-lookup"><span data-stu-id="03d6a-159">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="03d6a-160">Escolha **aplicativo WPF** da lista de tipos de projeto.</span><span class="sxs-lookup"><span data-stu-id="03d6a-160">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="03d6a-161">Digite `AsyncReturnTypes` como o nome do projeto e, em seguida, escolha o **Okey** botão.</span><span class="sxs-lookup"><span data-stu-id="03d6a-161">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="03d6a-162">O novo projeto aparece na **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="03d6a-162">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="03d6a-163">No código de Editor do Visual Studio, escolha o **MainWindow** guia.</span><span class="sxs-lookup"><span data-stu-id="03d6a-163">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="03d6a-164">Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**e, em seguida, escolha **abrir**.</span><span class="sxs-lookup"><span data-stu-id="03d6a-164">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="03d6a-165">No **XAML** janela de MainWindow. XAML, substitua o código pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="03d6a-165">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="03d6a-166">Uma janela simple que contém uma caixa de texto e um botão aparece no **Design** janela de MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="03d6a-166">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="03d6a-167">Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="03d6a-167">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="03d6a-168">Substitua o código em MainWindow.xaml.vb com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="03d6a-168">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
9. <span data-ttu-id="03d6a-169">Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="03d6a-169">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="03d6a-170">A saída a seguir deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="03d6a-170">The following output should appear.</span></span>  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="03d6a-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03d6a-171">See Also</span></span>  
 <span data-ttu-id="03d6a-172"><xref:System.Threading.Tasks.Task.FromResult%2A></xref:System.Threading.Tasks.Task.FromResult%2A></span><span class="sxs-lookup"><span data-stu-id="03d6a-172"><xref:System.Threading.Tasks.Task.FromResult%2A></span></span>   
<span data-ttu-id="03d6a-173"> [Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="03d6a-173"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="03d6a-174"> [Fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md) </span><span class="sxs-lookup"><span data-stu-id="03d6a-174"> [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md) </span></span>  
<span data-ttu-id="03d6a-175"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span><span class="sxs-lookup"><span data-stu-id="03d6a-175"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span></span>  
<span data-ttu-id="03d6a-176"> [Operador Await](../../../../visual-basic/language-reference/operators/await-operator.md)</span><span class="sxs-lookup"><span data-stu-id="03d6a-176"> [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md)</span></span>
