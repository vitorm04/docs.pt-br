---
title: "async (referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8734f639e45f12ddd987a1c34e7f3ac38aa7d73f
ms.lasthandoff: 03/13/2017

---
# <a name="async-c-reference"></a>async (Referência de C#)
Use o modificador `async` para especificar que um método, uma [expressão lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ou um [método anônimo](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) é assíncrono. Se você usar esse modificador em um método ou expressão, ele será referido como um método assíncrono.  
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
  
```  
  
 Se você for iniciante em programação assíncrona ou não compreender como um método assíncrono usa a palavra-chave `await` para fazer trabalhos potencialmente longos sem bloquear o thread do chamador, leia a introdução em [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).  
  
```  
string contents = await contentsTask;  
```  
  
 O método será executado de forma síncrona até atingir sua primeira expressão `await` e, nesse ponto, ele será suspenso até que a tarefa aguardada seja concluída. Enquanto isso, o controle será retornado ao chamador do método, como exibido no exemplo da próxima seção.  
  
 Se o método que a palavra-chave `async` modifica não contiver uma expressão ou instrução `await`, ele será executado de forma síncrona. Um aviso do compilador o alertará sobre quaisquer métodos assíncronos que não contenham `await`, pois essa situação poderá indicar um erro. Consulte [Aviso do compilador (nível 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 A palavra-chave `async` é contextual, pois ela será uma palavra-chave somente quando modificar um método, uma expressão lambda ou um método anônimo. Em todos os outros contextos, ela será interpretada como um identificador.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a estrutura e o fluxo de controle entre um manipulador de eventos assíncronos, `StartButton_Click` e um método assíncrono, `ExampleMethodAsync`. O resultado do método assíncrono é o comprimento de um site baixado. O código será adequado para um aplicativo do Windows Presentation Foundation (WPF) ou da Windows Store que você criar no Visual Studio; consulte os comentários do código para configurar o aplicativo.  
  
```csharp  
// You can run this code in Visual Studio 2013 as a WPF app or a Windows Store app.  
// You need a button (StartButton) and a textbox (ResultsTextBox).  
// Remember to set the names and handler so that you have something like this:  
// <Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
//         Click="StartButton_Click" Name="StartButton"/>  
// <TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
//          Text="TextBox" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
  
// To run the code as a WPF app:  
//    paste this code into the MainWindow class in MainWindow.xaml.cs,  
//    add a reference to System.Net.Http, and  
//    add a using directive for System.Net.Http.  
  
// To run the code as a Windows Store app:  
//    paste this code into the MainPage class in MainPage.xaml.cs, and  
//    add using directives for System.Net.Http and System.Threading.Tasks.  
  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ExampleMethodAsync returns a Task<int>, which means that the method  
    // eventually produces an int result. However, ExampleMethodAsync returns  
    // the Task<int> value as soon as it reaches an await.  
    ResultsTextBox.Text += "\n";  
    try  
    {  
        int length = await ExampleMethodAsync();  
        // Note that you could put "await ExampleMethodAsync()" in the next line where  
        // "length" is, but due to when '+=' fetches the value of ResultsTextBox, you  
        // would not see the global side effect of ExampleMethodAsync setting the text.  
        ResultsTextBox.Text += String.Format("Length: {0}\n", length);  
    }  
    catch (Exception)  
    {  
        // Process the exception if one occurs.  
    }  
}  
  
public async Task<int> ExampleMethodAsync()  
{  
    var httpClient = new HttpClient();  
    int exampleInt = (await httpClient.GetStringAsync("http://msdn.microsoft.com")).Length;  
    ResultsTextBox.Text += "Preparing to finish ExampleMethodAsync.\n";  
    // After the following return statement, any method that's awaiting  
    // ExampleMethodAsync (in this case, StartButton_Click) can get the   
    // integer result.  
    return exampleInt;  
}  
// Output:  
// Preparing to finish ExampleMethodAsync.  
// Length: 53292  
  
```  
  
> [!IMPORTANT]
>  Para obter mais informações sobre tarefas e o código que é executado enquanto aguarda uma tarefa, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md). Para obter um exemplo WPF completo que usa elementos semelhantes, consulte o [Passo a passo: acessando a Web usando async e await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). É possível baixar o código do passo a passo em [Exemplos de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
## <a name="return-types"></a>Tipos de Retorno  
 Um método assíncrono pode ter um tipo de retorno <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601> ou [void](../../../csharp/language-reference/keywords/void.md). O método não pode declarar nenhum parâmetro [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md), mas pode chamar métodos com tais parâmetros.  
  
 Você especificará `Task<TResult>` como o tipo de retorno de um método assíncrono se a instrução [return](../../../csharp/language-reference/keywords/return.md) do método especificar um operando do tipo `TResult`. Você usará `Task` se nenhum valor significativo for retornado quando o método for concluído. Isto é, uma chamada ao método retorna uma `Task`, mas quando a `Task` for concluída, qualquer expressão `await` que esteja aguardando a `Task` será avaliada como `void`.  
  
 O tipo de retorno `void` é usado principalmente para definir manipuladores de eventos que exigem esse tipo de retorno. O chamador de um método assíncrono de retorno `void` não pode aguardá-lo e capturar exceções acionadas pelo método.  
  
 Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [await](../../../csharp/language-reference/keywords/await.md)   
 [Passo a passo: acessando a Web usando async e await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md)
