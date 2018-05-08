---
title: Tipos de retorno assíncronos (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 0c6c02efd282f8581f3dc85905149acf7b3ea6ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="async-return-types-visual-basic"></a>Tipos de retorno assíncronos (Visual Basic)
Os métodos assíncronos ter três tipos de retorno possíveis: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>e void. No Visual Basic, o tipo de retorno void é gravado como um procedimento [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md). Para obter mais informações sobre os métodos assíncronos, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Cada tipo de retorno é examinado em uma das seções a seguir e você pode encontrar um exemplo completo que usa todos os três tipos no final do tópico.  
  
> [!NOTE]
>  Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.  
  
##  <a name="BKMK_TaskTReturnType"></a> Tipo de retorno Task(T)  
 O <xref:System.Threading.Tasks.Task%601> retornar o tipo é usado para um método assíncrono que contém um [retornar](../../../../visual-basic/language-reference/statements/return-statement.md) em que o operando tem o tipo de instrução `TResult`.  
  
 No exemplo a seguir, o método assíncrono `TaskOfT_MethodAsync` contém uma instrução return que retorna um número inteiro. Portanto, a declaração do método deve especificar um tipo de retorno de `Task(Of Integer)`.  
  
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
  
 Quando `TaskOfT_MethodAsync` é chamado de dentro de uma expressão await, a expressão await recupera o valor inteiro (o valor de `leisureHours`) que está armazenado na tarefa que é retornada pelo `TaskOfT_MethodAsync`. Para obter mais informações sobre expressões de espera, consulte [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 O código a seguir chama e aguarda o método `TaskOfT_MethodAsync`. O resultado é atribuído à variável `result1`.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Você pode entender melhor como isso acontece, separando a chamada ao `TaskOfT_MethodAsync` da aplicação do `Await`, como mostrado no código a seguir. Uma chamada ao método `TaskOfT_MethodAsync` que não é aguardada imediatamente, retorna um `Task(Of Integer)`, como você esperaria da declaração do método. A tarefa é atribuída à variável `integerTask` no exemplo. Já que `integerTask` é um <xref:System.Threading.Tasks.Task%601>, ele contém uma propriedade <xref:System.Threading.Tasks.Task%601.Result> do tipo `TResult`. Nesse caso, TResult representa um tipo inteiro. Quando `Await` é aplicado à `integerTask`, a expressão await é avaliada como o conteúdo da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`. O valor é atribuído à variável `result2`.  
  
> [!WARNING]
>  A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> é uma propriedade de bloqueio. Se você tentar acessá-la antes que sua tarefa seja concluída, o thread que está ativo no momento será bloqueado até que a tarefa seja concluída e o valor esteja disponível. Na maioria dos casos, você deve acessar o valor usando `Await` em vez de acessar a propriedade diretamente.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 As instruções de exibição no código a seguir verificam se os valores da variável `result1`, da variável `result2` e da propriedade `Result` são os mesmos. Lembre-se que a propriedade `Result` é uma propriedade de bloqueio e não deve ser acessada antes que sua tarefa tenha sido aguardada.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a> Tipo de retorno Task  
 Os métodos assíncronos que não contêm uma instrução return ou que contém uma instrução de retorno que não retorna um operando normalmente têm um tipo de retorno <xref:System.Threading.Tasks.Task>. Esses métodos seria [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimentos se elas tivessem sido escritas para executar de forma síncrona. Se você usar um tipo de retorno `Task` para um método assíncrono, um método de chamada poderá usar um operador `Await` para suspender a conclusão do chamador até que o método assíncrono chamado seja concluído.  
  
 No exemplo a seguir, o método assíncrono `Task_MethodAsync` não contém uma instrução return. Portanto, você especifica um tipo de retorno de `Task` para o método, que permite que `Task_MethodAsync` seja aguardado. A definição do tipo `Task` não inclui uma propriedade `Result` para armazenar um valor retornado.  
  
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
  
 `Task_MethodAsync` é chamado e aguardada usando uma instrução de espera, em vez de uma expressão await, semelhante à instrução de chamada para um síncrono `Sub` ou método de retorno de void. A aplicação de um `Await` operador nesse caso não produz um valor.  
  
 O código a seguir chama e aguarda o método `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Como anterior <xref:System.Threading.Tasks.Task%601> exemplo, você pode separar a chamada para `Task_MethodAsync` da aplicação de um `Await` operador, como mostra o código a seguir. No entanto, lembre-se que uma `Task` não tem uma propriedade `Result` e que nenhum valor será produzido quando um operador await for aplicado a uma `Task`.  
  
 O código a seguir separa a chamada ao `Task_MethodAsync` da espera pela tarefa que `Task_MethodAsync` retorna.  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <a name="BKMK_VoidReturnType"></a> Tipo de retorno void  
 O principal uso de `Sub` procedimentos é em manipuladores de eventos, onde não há nenhum tipo de retorno (conhecido como um tipo de retorno void em outros idiomas). Um retorno void também pode ser usado para substituir métodos de retorno void ou para métodos que realizam atividades que podem ser categorizadas como "disparar e esquecer". No entanto, você deve retornar uma `Task` sempre que possível, porque um método assíncrono de retorno void não pode ser aguardado. Qualquer chamador desse método deve ser capaz de continuar até a conclusão, sem aguardar a conclusão do método assíncrono chamado e o chamador deve ser independente de todos os valores ou exceções gerados pelo método assíncrono.  
  
 O chamador de um método assíncrono de retorno void não pode capturar exceções que são lançadas pelo método e essas exceções sem tratamento provavelmente causarão falha do seu aplicativo. Se ocorrer uma exceção em um método assíncrono que retorna um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, a exceção é armazenada na tarefa retornada e lançada novamente quando a tarefa é esperada. Portanto, verifique se qualquer método assíncrono que pode produzir uma exceção tem um tipo de retorno de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> e que as chamadas ao método são aguardadas.  
  
 Para obter mais informações sobre como capturar exceções nos métodos assíncronos, consulte a [Instrução Try... Catch... Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 O código a seguir define um manipulador de eventos assíncrono.  
  
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
  
##  <a name="BKMK_Example"></a> Exemplo completo  
 O projeto WPF (Windows Presentation Foundation) a seguir contém os exemplos de código deste tópico.  
  
 Para executar o projeto, realize as seguintes etapas:  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  No **instalado**, **modelos** categoria, escolha **Visual Basic**e, em seguida, escolha **Windows**. Escolha **Aplicativo WPF** na lista de tipos de projeto.  
  
4.  Digite `AsyncReturnTypes` como o nome do projeto e, em seguida, escolha o botão **OK**.  
  
     O novo projeto aparece no **Gerenciador de Soluções**.  
  
5.  No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.  
  
     Se a guia não estiver visível, abra o menu de atalho para MainWindow.xaml no **Gerenciador de Soluções** e, em seguida, escolha **Abrir**.  
  
6.  Na janela **XAML** de MainWindow.xaml, substitua o código pelo código a seguir.  
  
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
  
     Uma janela simples, contendo uma caixa de texto e um botão, aparecerá na janela **Design** de MainWindow.xaml.  
  
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
  
9. Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.  
  
     A saída a seguir deverá aparecer.  
  
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
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [Instruções passo a passo: acessando a Web usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Fluxo de controle em programas assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
 [Operador Await](../../../../visual-basic/language-reference/operators/await-operator.md)
