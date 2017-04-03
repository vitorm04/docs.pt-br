---
title: "Tipos de retorno assíncronos (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4c1bab99fc1139f03e5f754cfecaee392b947171
ms.lasthandoff: 03/13/2017

---
# <a name="async-return-types-c"></a>Tipos de retorno assíncronos (C#)
Os métodos assíncronos têm três tipos de retorno possíveis: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> e void. No Visual Basic, o tipo de retorno void é gravado como um procedimento [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md). Para obter mais informações sobre os métodos assíncronos, consulte [Programação assíncrona com async e await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
 Cada tipo de retorno é examinado em uma das seções a seguir e você pode encontrar um exemplo completo que usa todos os três tipos no final do tópico.  
  
> [!NOTE]
>  Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.  
  
##  <a name="BKMK_TaskTReturnType"></a> Tipo de retorno Task(T)  
 O tipo de retorno <xref:System.Threading.Tasks.Task%601> é usado para um método assíncrono que contém uma instrução [return](../../../../csharp/language-reference/keywords/return.md) (C#), na qual o operando tem o tipo `TResult`.  
  
 No exemplo a seguir, o método assíncrono `TaskOfT_MethodAsync` contém uma instrução return que retorna um número inteiro. Portanto, a declaração do método deve especificar um tipo de retorno de `Task<int>`.  
  
```cs  
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
  
 Quando `TaskOfT_MethodAsync` é chamado de dentro de uma expressão await, a expressão await recupera o valor inteiro (o valor de `leisureHours`) que está armazenado na tarefa que é retornada pelo `TaskOfT_MethodAsync`. Para obter mais informações sobre expressões await, consulte [await](../../../../csharp/language-reference/keywords/await.md).  
  
 O código a seguir chama e aguarda o método `TaskOfT_MethodAsync`. O resultado é atribuído à variável `result1`.  
  
```cs  
// Call and await the Task<T>-returning async method in the same statement.  
int result1 = await TaskOfT_MethodAsync();  
```  
  
 Você pode entender melhor como isso acontece, separando a chamada ao `TaskOfT_MethodAsync` da aplicação do `await`, como mostrado no código a seguir. Uma chamada ao método `TaskOfT_MethodAsync` que não é aguardada imediatamente, retorna um `Task<int>`, como você esperaria da declaração do método. A tarefa é atribuída à variável `integerTask` no exemplo. Como `integerTask` é uma <xref:System.Threading.Tasks.Task%601>, ela contém uma propriedade <xref:System.Threading.Tasks.Task%601.Result> do tipo `TResult`. Nesse caso, TResult representa um tipo inteiro. Quando `await` é aplicado à `integerTask`, a expressão await é avaliada como o conteúdo da propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`. O valor é atribuído à variável `result2`.  
  
> [!WARNING]
>  A propriedade <xref:System.Threading.Tasks.Task%601.Result%2A> é uma propriedade de bloqueio. Se você tentar acessá-la antes que sua tarefa seja concluída, o thread que está ativo no momento será bloqueado até que a tarefa seja concluída e o valor esteja disponível. Na maioria dos casos, você deve acessar o valor usando `await` em vez de acessar a propriedade diretamente.  
  
```cs  
// Call and await in separate statements.  
Task<int> integerTask = TaskOfT_MethodAsync();  
  
// You can do other work that does not rely on integerTask before awaiting.  
textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
int result2 = await integerTask;  
```  
  
 As instruções de exibição no código a seguir verificam se os valores da variável `result1`, da variável `result2` e da propriedade `Result` são os mesmos. Lembre-se que a propriedade `Result` é uma propriedade de bloqueio e não deve ser acessada antes que sua tarefa tenha sido aguardada.  
  
```cs  
// Display the values of the result1 variable, the result2 variable, and  
// the integerTask.Result property.  
textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
```  
  
##  <a name="BKMK_TaskReturnType"></a> Tipo de retorno Task  
 Os métodos assíncronos que não contêm uma instrução return ou que contêm uma instrução return que não retorna um operando, normalmente têm um tipo de retorno de <xref:System.Threading.Tasks.Task>. Esses métodos seriam métodos de retorno void se eles fossem escritos para serem executados de forma síncrona. Se você usar um tipo de retorno `Task` para um método assíncrono, um método de chamada poderá usar um operador await para suspender a conclusão do chamador até que o método assíncrono chamado seja concluído.  
  
 No exemplo a seguir, o método assíncrono `Task_MethodAsync` não contém uma instrução return. Portanto, você especifica um tipo de retorno de `Task` para o método, que permite que `Task_MethodAsync` seja aguardado. A definição do tipo `Task` não inclui uma propriedade `Result` para armazenar um valor retornado.  
  
```cs  
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
  
 O `Task_MethodAsync` é chamado e aguardado, usando uma instrução await, em vez de uma expressão await, semelhante à instrução de chamada a um método síncrono de retorno void. A aplicação de um operador await, nesse caso, não produz um valor.  
  
 O código a seguir chama e aguarda o método `Task_MethodAsync`.  
  
```cs  
// Call and await the Task-returning async method in the same statement.  
await Task_MethodAsync();  
```  
  
 Como no exemplo <xref:System.Threading.Tasks.Task%601> anterior, você pode separar a chamada ao `Task_MethodAsync`, da aplicação de um operador await, como mostrado no código a seguir. No entanto, lembre-se que uma `Task` não tem uma propriedade `Result` e que nenhum valor será produzido quando um operador await for aplicado a uma `Task`.  
  
 O código a seguir separa a chamada ao `Task_MethodAsync` da espera pela tarefa que `Task_MethodAsync` retorna.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
##  <a name="BKMK_VoidReturnType"></a> Tipo de retorno void  
 O principal uso do tipo de retorno void é em manipuladores de eventos, nos quais um tipo de retorno void é necessário. Um retorno void também pode ser usado para substituir métodos de retorno void ou para métodos que realizam atividades que podem ser categorizadas como "disparar e esquecer". No entanto, você deve retornar uma `Task` sempre que possível, porque um método assíncrono de retorno void não pode ser aguardado. Qualquer chamador desse método deve ser capaz de continuar até a conclusão, sem aguardar a conclusão do método assíncrono chamado e o chamador deve ser independente de todos os valores ou exceções gerados pelo método assíncrono.  
  
 O chamador de um método assíncrono de retorno void não pode capturar exceções que são lançadas pelo método e essas exceções sem tratamento provavelmente causarão falha do seu aplicativo. Se ocorrer uma exceção em um método assíncrono que retorna uma <xref:System.Threading.Tasks.Task> ou uma <xref:System.Threading.Tasks.Task%601>, a exceção será armazenada na tarefa retornada e relançada quando a tarefa for aguardada. Portanto, verifique se qualquer método assíncrono que pode produzir uma exceção tem um tipo de retorno de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> e que as chamadas ao método são aguardadas.  
  
 Para obter mais informações sobre como capturar exceções nos métodos assíncronos, consulte [try-catch](../../../../csharp/language-reference/keywords/try-catch.md).  
  
 O código a seguir define um manipulador de eventos assíncrono.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
##  <a name="BKMK_Example"></a> Exemplo completo  
 O projeto WPF (Windows Presentation Foundation) a seguir contém os exemplos de código deste tópico.  
  
 Para executar o projeto, realize as seguintes etapas:  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  Em **Instalado**, categoria **Modelos**, escolha Visual C# e, em seguida, escolha **Windows**. Escolha **Aplicativo WPF** na lista de tipos de projeto.  
  
4.  Digite `AsyncReturnTypes` como o nome do projeto e, em seguida, escolha o botão **OK**.  
  
     O novo projeto aparece no **Gerenciador de Soluções**.  
  
5.  No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.  
  
     Se a guia não estiver visível, abra o menu de atalho para MainWindow.xaml no **Gerenciador de Soluções** e, em seguida, escolha **Abrir**.  
  
6.  Na janela **XAML** de MainWindow.xaml, substitua o código pelo código a seguir.  
  
    ```cs  
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
  
     Uma janela simples, contendo uma caixa de texto e um botão, aparecerá na janela **Design** de MainWindow.xaml.  
  
7.  No **Gerenciador de Soluções**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir Código**.  
  
8.  Substitua o código em MainWindow.xaml.cs pelo código a seguir.  
  
    ```cs  
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
 [Passo a passo: acessando a Web usando async e await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Fluxo de controle em programas assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
 [async](../../../../csharp/language-reference/keywords/async.md)   
 [await](../../../../csharp/language-reference/keywords/await.md)
