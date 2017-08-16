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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 703d3fc3f503017edf38521d77f9b15a92d0ebf3
ms.lasthandoff: 03/13/2017

---
# <a name="async-return-types-visual-basic"></a>Tipos de retorno assíncronos (Visual Basic)
Os métodos assíncronos têm três tipos de retornos possíveis: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>e void.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601> No Visual Basic, o tipo de retorno void é gravado como um [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimento. Para obter mais informações sobre os métodos assíncronos, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Cada tipo de retorno é examinado em uma das seções a seguir, e você pode encontrar um exemplo completo que usa todos os três tipos no final do tópico.  
  
> [!NOTE]
>  Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
##  <a name="BKMK_TaskTReturnType"></a>Tipo de retorno de Task(T)  
 O <xref:System.Threading.Tasks.Task%601>retornar o tipo é usado para um método assíncrono que contém um [retornar](../../../../visual-basic/language-reference/statements/return-statement.md) que o operando tem o tipo de instrução `TResult`.</xref:System.Threading.Tasks.Task%601>  
  
 No exemplo a seguir, o `TaskOfT_MethodAsync` método assíncrono contém uma instrução return que retorna um número inteiro. Portanto, a declaração do método deve especificar um tipo de retorno de `Task(Of Integer)`.  
  
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
  
 Quando `TaskOfT_MethodAsync` é chamado de dentro de uma expressão await, a expressão await recupera o valor inteiro (o valor de `leisureHours`) que é armazenado na tarefa que é retornada pelo `TaskOfT_MethodAsync`. Para obter mais informações sobre expressões await, consulte [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 O código a seguir chama e aguarda o método `TaskOfT_MethodAsync`. O resultado é atribuído para a `result1` variável.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Você pode entender melhor como isso acontece, separando a chamada para `TaskOfT_MethodAsync` da aplicação do `Await`, como mostra o código a seguir. Uma chamada ao método `TaskOfT_MethodAsync` que não é aguardada imediatamente retorna um `Task(Of Integer)`, como você esperaria da declaração do método. A tarefa é atribuída a `integerTask` variável no exemplo. Porque `integerTask` é um <xref:System.Threading.Tasks.Task%601>, ele contém um <xref:System.Threading.Tasks.Task%601.Result>propriedade do tipo `TResult`.</xref:System.Threading.Tasks.Task%601.Result> </xref:System.Threading.Tasks.Task%601> Nesse caso, TResult representa um tipo inteiro. Quando `Await` é aplicado a `integerTask`, a expressão await é avaliada como o conteúdo da <xref:System.Threading.Tasks.Task%601.Result%2A>propriedade `integerTask`.</xref:System.Threading.Tasks.Task%601.Result%2A> O valor é atribuído para a `result2` variável.  
  
> [!WARNING]
>  O <xref:System.Threading.Tasks.Task%601.Result%2A>é uma propriedade de bloqueio.</xref:System.Threading.Tasks.Task%601.Result%2A> Se você tentar acessá-lo antes de sua tarefa é concluída, o thread que está ativo no momento é bloqueado até que a tarefa seja concluída e o valor está disponível. Na maioria dos casos, você deve acessar o valor usando `Await` em vez de acessar a propriedade diretamente.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 As instruções de exibição no código a seguir, verifique se que os valores da `result1` variável, o `result2` variável e o `Result` são os mesmos. Lembre-se de que o `Result` propriedade é uma propriedade de bloqueio e não deve ser acessada antes que a tarefa foi esperada.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a>Tipo de retorno de tarefa  
 Os métodos Async que não contêm uma instrução return ou que contêm uma instrução return que não retorna um operando normalmente têm um tipo de retorno de <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> Esses métodos seria [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimentos se eles fossem escritos para execução síncrona. Se você usar um `Task` tipo de retorno para um método assíncrono, um método de chamada pode usar um `Await` operador para suspender a conclusão do chamador até que o método de chamada assíncrona seja concluída.  
  
 No exemplo a seguir, o método assíncrono `Task_MethodAsync` não contém uma instrução return. Portanto, você pode especificar um tipo de retorno de `Task` para o método, que permite `Task_MethodAsync` para ser colocado em espera. A definição de `Task` tipo não inclui um `Result` propriedade para armazenar um valor de retorno.  
  
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
  
 `Task_MethodAsync`é chamado e esperado, usando uma instrução de espera, em vez de uma expressão await, semelhante à instrução de chamada para um síncrono `Sub` ou método que retorna void. A aplicação de uma `Await` operador nesse caso não produz um valor.  
  
 O código a seguir chama e aguarda o método `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Como o anterior <xref:System.Threading.Tasks.Task%601>exemplo, você pode separar a chamada para `Task_MethodAsync` da aplicação de uma `Await` operador, como mostra o código a seguir.</xref:System.Threading.Tasks.Task%601> No entanto, lembre-se de que uma `Task` não tem um `Result` propriedade e que nenhum valor é produzido quando um operador de espera é aplicado a um `Task`.  
  
 O código a seguir separa chamada `Task_MethodAsync` de aguardando a tarefa que `Task_MethodAsync` retorna.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
##  <a name="BKMK_VoidReturnType"></a>Tipo de retorno void  
 O principal uso de `Sub` procedimentos é em manipuladores de eventos, onde não há nenhum tipo de retorno (conhecido como um tipo de retorno void em outras linguagens). Um retorno de void também pode ser usado para substituir os métodos que retornam void ou para métodos que executam atividades que podem ser categorizadas como "disparar e esquecer." No entanto, você deve retornar um `Task` sempre que possível, porque um método async que retorna void não pode ser colocado em espera. Qualquer chamador desse método deve ser capaz de continuar até a conclusão, sem aguardar a conclusão do método assíncrono chamado e o chamador deve ser independente de quaisquer valores ou exceções que gera o método assíncrono.  
  
 O chamador de um método async que retorna void não pode capturar exceções que são geradas pelo método, e essas exceções sem tratamento provavelmente fazer com que o aplicativo falhar. Se ocorrer uma exceção em um método async que retorna um <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>, a exceção é armazenada na tarefa retornada e relançada quando a tarefa é aguardada.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> Portanto, certifique-se de que qualquer método assíncrono que pode gerar uma exceção tem um tipo de retorno de <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>e que as chamadas para o método são aguardadas.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task>  
  
 Para obter mais informações sobre como capturar exceções em métodos assíncronos, consulte [Try... Catch... Instrução Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 O código a seguir define um manipulador de eventos assíncronos.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
##  <a name="BKMK_Example"></a>Exemplo completo  
 O projeto Windows Presentation Foundation (WPF) a seguir contém exemplos de código deste tópico.  
  
 Para executar o projeto, execute as seguintes etapas:  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     O **novo projeto** caixa de diálogo é aberta.  
  
3.  No **instalados**, **modelos** categoria, escolha **Visual Basic**e, em seguida, escolha **Windows**. Escolha **aplicativo WPF** da lista de tipos de projeto.  
  
4.  Digite `AsyncReturnTypes` como o nome do projeto e, em seguida, escolha o **Okey** botão.  
  
     O novo projeto aparece na **Solution Explorer**.  
  
5.  No código de Editor do Visual Studio, escolha o **MainWindow** guia.  
  
     Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**e, em seguida, escolha **abrir**.  
  
6.  No **XAML** janela de MainWindow. XAML, substitua o código pelo código a seguir.  
  
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
  
     Uma janela simple que contém uma caixa de texto e um botão aparece no **Design** janela de MainWindow. XAML.  
  
7.  Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.  
  
8.  Substitua o código em MainWindow.xaml.vb com o código a seguir.  
  
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
  
9. Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.  
  
     A saída a seguir deve aparecer.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Tasks.Task.FromResult%2A></xref:System.Threading.Tasks.Task.FromResult%2A>   
 [Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)   
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)   
 [Operador Await](../../../../visual-basic/language-reference/operators/await-operator.md)
