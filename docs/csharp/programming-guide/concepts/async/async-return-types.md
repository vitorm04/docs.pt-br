---
title: "Tipos de retorno ass&#237;ncronos (c#) | Microsoft Docs"
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
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tipos de retorno ass&#237;ncronos (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Os métodos assíncronos têm três tipos de retornos possíveis: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, e void. No Visual Basic, o tipo de retorno void é gravado como um [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimento. Para obter mais informações sobre os métodos assíncronos, consulte [Programação assíncrona com async e await \(c\#\)](../../../../csharp/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md).  
  
 Cada tipo de retorno é examinado em uma das seções a seguir, e você pode encontrar um exemplo completo que usa todos os três tipos no final do tópico.  
  
> [!NOTE]
>  Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
##  <a name="BKMK_TaskTReturnType"></a> Tipo de retorno de Task\(T\)  
 O <xref:System.Threading.Tasks.Task%601> retornar o tipo é usado para um método assíncrono que contém um[retornar](../../../../csharp/language-reference/keywords/return.md) \(c\#\) que o operando tem o tipo de instrução `TResult`.  
  
 No exemplo a seguir, o `TaskOfT_MethodAsync` método assíncrono contém uma instrução return que retorna um número inteiro. Portanto, a declaração do método deve especificar um tipo de retorno de `Task<int>`.  
  
```c#  
// TASK<T> EXAMPLE  
async Task<int> TaskOfT_MethodAsync()  
{  
    // The body of the method is expected to contain an awaited asynchronous  
    // call.  
    // Task.FromResult is a placeholder for actual work that returns a string.  
    var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
    // The method then can process the result in some way.  
    int leisureHours;  
    if (today.First() == 'S')  
        leisureHours = 16;  
    else  
        leisureHours = 5;  
  
    // Because the return statement specifies an operand of type int, the  
    // method must have a return type of Task<int>.  
    return leisureHours;  
}  
```  
  
 Quando `TaskOfT_MethodAsync` é chamado de dentro de uma expressão await, a expressão await recupera o valor inteiro \(o valor de `leisureHours`\) que é armazenado na tarefa que é retornada pelo `TaskOfT_MethodAsync`. Para obter mais informações sobre expressões await, consulte [await](../../../../csharp/language-reference/keywords/await.md).  
  
 O código a seguir chama e aguarda o método `TaskOfT_MethodAsync`. O resultado é atribuído para a `result1` variável.  
  
```c#  
// Call and await the Task<T>-returning async method in the same statement.  
int result1 = await TaskOfT_MethodAsync();  
```  
  
 Você pode entender melhor como isso acontece, separando a chamada para `TaskOfT_MethodAsync` do aplicativo de `await`, como mostra o código a seguir. Uma chamada ao método `TaskOfT_MethodAsync` que não é aguardada imediatamente retorna um `Task<int>`, como você esperaria da declaração do método. A tarefa é atribuída a `integerTask` variável no exemplo. Porque `integerTask` é um <xref:System.Threading.Tasks.Task%601>, ele contém um <xref:System.Threading.Tasks.Task%601.Result> propriedade do tipo `TResult`. Nesse caso, TResult representa um tipo inteiro. Quando `await` é aplicado a `integerTask`, a expressão await é avaliada como o conteúdo da <xref:System.Threading.Tasks.Task%601.Result%2A> propriedade `integerTask`. O valor é atribuído para a `result2` variável.  
  
> [!WARNING]
>  O <xref:System.Threading.Tasks.Task%601.Result%2A> é uma propriedade de bloqueio. Se você tentar acessá\-lo antes de sua tarefa é concluída, o thread que está ativo no momento é bloqueado até que a tarefa seja concluída e o valor está disponível. Na maioria dos casos, você deve acessar o valor usando `await` em vez de acessar a propriedade diretamente.  
  
```c#  
// Call and await in separate statements.  
Task<int> integerTask = TaskOfT_MethodAsync();  
  
// You can do other work that does not rely on integerTask before awaiting.  
textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
int result2 = await integerTask;  
```  
  
 As instruções de exibição no código a seguir, verifique se que os valores da `result1` variável, o `result2` variável e o `Result` são os mesmos. Lembre\-se de que o `Result` propriedade é uma propriedade de bloqueio e não deve ser acessada antes que a tarefa foi esperada.  
  
```c#  
// Display the values of the result1 variable, the result2 variable, and  
// the integerTask.Result property.  
textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
```  
  
##  <a name="BKMK_TaskReturnType"></a> Tipo de retorno de tarefa  
 Os métodos Async que não contêm uma instrução return ou que contêm uma instrução return que não retorna um operando normalmente têm um tipo de retorno de <xref:System.Threading.Tasks.Task>. Esses métodos seria retornam void métodos se eles fossem escritos para execução síncrona. Se você usar um `Task` tipo de retorno para um método assíncrono, um método de chamada pode usar um operador await para suspender a conclusão do chamador até que o método de chamada assíncrona seja concluída.  
  
 No exemplo a seguir, o método assíncrono `Task_MethodAsync` não contém uma instrução return. Portanto, você pode especificar um tipo de retorno de `Task` para o método, que permite `Task_MethodAsync` para ser colocado em espera. A definição de `Task` tipo não inclui um `Result` propriedade para armazenar um valor de retorno.  
  
```c#  
// TASK EXAMPLE  
async Task Task_MethodAsync()  
{  
    // The body of an async method is expected to contain an awaited   
    // asynchronous call.  
    // Task.Delay is a placeholder for actual work.  
    await Task.Delay(2000);  
    // Task.Delay delays the following line by two seconds.  
    textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
    // This method has no return statement, so its return type is Task.    
}  
```  
  
 `Task_MethodAsync` é chamado e esperado, usando uma instrução de espera, em vez de uma expressão await, semelhante à instrução de chamada para um método síncrono que retornam void. Nesse caso, o aplicativo de um operador await não produz um valor.  
  
 O código a seguir chama e aguarda o método `Task_MethodAsync`.  
  
```c#  
// Call and await the Task-returning async method in the same statement.  
await Task_MethodAsync();  
```  
  
 Como o anterior <xref:System.Threading.Tasks.Task%601> exemplo, você pode separar a chamada para `Task_MethodAsync` da aplicação de um operador de espera, como o código a seguir mostra. No entanto, lembre\-se de que um `Task` não tem um `Result` propriedade e que nenhum valor é produzido quando um operador de espera é aplicado a um `Task`.  
  
 O código a seguir separa chamada `Task_MethodAsync` de aguardando a tarefa que `Task_MethodAsync` retorna.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
##  <a name="BKMK_VoidReturnType"></a> Tipo de retorno void  
 O principal uso do tipo de retorno void é em manipuladores de eventos, onde é necessário um tipo de retorno void. Um retorno de void também pode ser usado para substituir os métodos que retornam void ou para métodos que executam atividades que podem ser categorizadas como "disparar e esquecer." No entanto, você deve retornar um `Task` sempre que possível, porque um método async que retorna void não pode ser colocado em espera. Qualquer chamador desse método deve ser capaz de continuar até a conclusão, sem aguardar a conclusão do método assíncrono chamado e o chamador deve ser independente de quaisquer valores ou exceções que gera o método assíncrono.  
  
 O chamador de um método async que retorna void não pode capturar exceções que são geradas pelo método, e essas exceções sem tratamento provavelmente fazer com que o aplicativo falhar. Se ocorrer uma exceção em um método async que retorna um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, a exceção é armazenada na tarefa retornada e relançada quando a tarefa é esperada. Portanto, certifique\-se de que qualquer método assíncrono que pode gerar uma exceção tem um tipo de retorno de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> e que as chamadas para o método são esperadas.  
  
 Para obter mais informações sobre como capturar exceções em métodos assíncronos, consulte [try\-catch](../../../../csharp/language-reference/keywords/try-catch.md) .  
  
 O código a seguir define um manipulador de eventos assíncronos.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
##  <a name="BKMK_Example"></a> Exemplo completo  
 O projeto Windows Presentation Foundation \(WPF\) a seguir contém exemplos de código deste tópico.  
  
 Para executar o projeto, execute as seguintes etapas:  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
     O **novo projeto** caixa de diálogo é aberta.  
  
3.  No **instalados**, **modelos** categoria, escolha Visual c\# e **Windows**. Escolha **aplicativo WPF** da lista de tipos de projeto.  
  
4.  Digite `AsyncReturnTypes` como o nome do projeto e, em seguida, escolha o **OK** botão.  
  
     O novo projeto aparece na **Solution Explorer**.  
  
5.  No código de Editor do Visual Studio, escolha o **MainWindow** guia.  
  
     Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**, e, em seguida, escolha **Abrir**.  
  
6.  No **XAML** janela de MainWindow. XAML, substitua o código pelo código a seguir.  
  
    ```c#  
    <Window x:Class="AsyncReturnTypes.MainWindow"  
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
  
7.  Em **Solution Explorer**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir código**.  
  
8.  Substitua o código no MainWindow.xaml.cs com o código a seguir.  
  
    ```c#  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Data;  
    using System.Windows.Documents;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    using System.Windows.Media.Imaging;  
    using System.Windows.Navigation;  
    using System.Windows.Shapes;  
  
    namespace AsyncReturnTypes  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            // VOID EXAMPLE  
            private async void button1_Click(object sender, RoutedEventArgs e)  
            {  
                textBox1.Clear();  
  
                // Start the process and await its completion. DriverAsync is a   
                // Task-returning async method.  
                await DriverAsync();  
  
                // Say goodbye.  
                textBox1.Text += "\r\nAll done, exiting button-click event handler.";  
            }  
  
            async Task DriverAsync()  
            {  
                // Task<T>   
                // Call and await the Task<T>-returning async method in the same statement.  
                int result1 = await TaskOfT_MethodAsync();  
  
                // Call and await in separate statements.  
                Task<int> integerTask = TaskOfT_MethodAsync();  
  
                // You can do other work that does not rely on integerTask before awaiting.  
                textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
                int result2 = await integerTask;  
  
                // Display the values of the result1 variable, the result2 variable, and  
                // the integerTask.Result property.  
                textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
                textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
                textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
  
                // Task  
                // Call and await the Task-returning async method in the same statement.  
                await Task_MethodAsync();  
  
                // Call and await in separate statements.  
                Task simpleTask = Task_MethodAsync();  
  
                // You can do other work that does not rely on simpleTask before awaiting.  
                textBox1.Text += String.Format("\r\nApplication can continue working while the Task runs. . . .\r\n");  
  
                await simpleTask;  
            }  
  
            // TASK<T> EXAMPLE  
            async Task<int> TaskOfT_MethodAsync()  
            {  
                // The body of the method is expected to contain an awaited asynchronous  
                // call.  
                // Task.FromResult is a placeholder for actual work that returns a string.  
                var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
                // The method then can process the result in some way.  
                int leisureHours;  
                if (today.First() == 'S')  
                    leisureHours = 16;  
                else  
                    leisureHours = 5;  
  
                // Because the return statement specifies an operand of type int, the  
                // method must have a return type of Task<int>.  
                return leisureHours;  
            }  
  
            // TASK EXAMPLE  
            async Task Task_MethodAsync()  
            {  
                // The body of an async method is expected to contain an awaited   
                // asynchronous call.  
                // Task.Delay is a placeholder for actual work.  
                await Task.Delay(2000);  
                // Task.Delay delays the following line by two seconds.  
                textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
                // This method has no return statement, so its return type is Task.    
            }  
        }  
    }  
    ```  
  
9. Escolha a tecla F5 para executar o programa e, em seguida, escolha o **Iniciar** botão.  
  
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
  
## Consulte também  
 <xref:System.Threading.Tasks.Task.FromResult%2A>   
 [Passo a passo: Acessando a Web usando o async e await \(c\#\)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Fluxo de controle em programas assíncronos \(c\#\)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)   
 [async](../../../../visual-basic/language-reference/modifiers/async.md)   
 [await](../../../../csharp/language-reference/keywords/await.md)