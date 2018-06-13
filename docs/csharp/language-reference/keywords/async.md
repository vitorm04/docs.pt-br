---
title: async (Referência de C#)
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 47c13f960cb6b70205feabfa0488e584ad6a098f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216932"
---
# <a name="async-c-reference"></a>async (Referência de C#)
Use o modificador `async` para especificar que um método, uma [expressão lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ou um [método anônimo](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) é assíncrono. Se você usar esse modificador em um método ou expressão, ele será referido como um *método assíncrono*. O exemplo a seguir define um método assíncrono chamado `ExampleMethodAsync`: 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
Se você for iniciante em programação assíncrona ou não compreender como um método assíncrono usa a palavra-chave `await` para fazer trabalhos potencialmente longos sem bloquear o thread do chamador, leia a introdução em [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md). O código a seguir é encontrado dentro de um método assíncrono e chama o método <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType>: 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
Um método assíncrono será executado de forma síncrona até atingir sua primeira expressão `await` e, nesse ponto, ele será suspenso até que a tarefa aguardada seja concluída. Enquanto isso, o controle será retornado ao chamador do método, como exibido no exemplo da próxima seção.  
  
Se o método que a palavra-chave `async` modifica não contiver uma expressão ou instrução `await`, ele será executado de forma síncrona. Um aviso do compilador o alertará sobre quaisquer métodos assíncronos que não contenham instruções `await`, pois essa situação poderá indicar um erro. Consulte [Aviso do compilador (nível 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).  
  
 A palavra-chave `async` é contextual, pois ela será uma palavra-chave somente quando modificar um método, uma expressão lambda ou um método anônimo. Em todos os outros contextos, ela será interpretada como um identificador.  
  
## <a name="example"></a>Exemplo  
O exemplo a seguir mostra a estrutura e o fluxo de controle entre um manipulador de eventos assíncronos, `StartButton_Click` e um método assíncrono, `ExampleMethodAsync`. O resultado do método assíncrono é o número de caracteres de uma página da Web. O código será adequado para um aplicativo do WPF (Windows Presentation Foundation) ou da Windows Store que você criar no Visual Studio, consulte os comentários do código para configurar o aplicativo.  

Você pode executar esse código no Visual Studio como um aplicativo do WPF (Windows Presentation Foundation) ou um aplicativo da Windows Store. Você precisa de um controle de botão chamado `StartButton` e de um controle de caixa de texto chamado `ResultsTextBox`. Lembre-se de definir os nomes e o manipulador para que você tenha algo assim:  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
Para executar o código como um aplicativo WPF:  

- Cole este código na classe `MainWindow` em MainWindow.xaml.cs.  
- Adicione uma referência a System.Net.Http.  
- Adicione uma diretiva `using` a System.Net.Http.  
  
Para executar o código como um aplicativo da Windows Store:  
- Cole este código na classe `MainPage` em MainPage.xaml.cs.  
- Adicione usando diretivas para System.Net.Http e System.Threading.Tasks.  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  Para obter mais informações sobre tarefas e o código que é executado enquanto aguarda uma tarefa, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md). Para obter um exemplo WPF completo que usa elementos semelhantes, consulte o [Passo a passo: acessando a Web usando async e await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
## <a name="return-types"></a>Tipos de Retorno  
Um método assíncrono pode conter os seguintes tipos de retorno:

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- [void](../../../csharp/language-reference/keywords/void.md), que só deve ser usado para manipuladores de eventos.
- Começando com o C# 7.0, qualquer tipo que tenha um método acessível `GetAwaiter`. O tipo `System.Threading.Tasks.ValueTask<TResult>` é um exemplo de uma implementação assim. Ele está disponível ao adicionar o pacote NuGet `System.Threading.Tasks.Extensions`. 

O método assíncrono não pode declarar os parâmetros [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nem [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) e também não pode ter um [valor retornado por referência](../../programming-guide/classes-and-structs/ref-returns.md), mas pode chamar métodos que tenham esses parâmetros.  
  
Você especificará `Task<TResult>` como o tipo de retorno de um método assíncrono se a instrução [return](../../../csharp/language-reference/keywords/return.md) do método especificar um operando do tipo `TResult`. Você usará `Task` se nenhum valor significativo for retornado quando o método for concluído. Isto é, uma chamada ao método retorna uma `Task`, mas quando a `Task` for concluída, qualquer expressão `await` que esteja aguardando a `Task` será avaliada como `void`.  
  
O tipo de retorno `void` é usado principalmente para definir manipuladores de eventos que exigem esse tipo de retorno. O chamador de um método assíncrono de retorno `void` não pode aguardá-lo e capturar exceções acionadas pelo método.  

Começando com o C# 7.0, você retorna outro tipo, geralmente um tipo de valor, que tenha um método `GetAwaiter` para minimizar as alocações de memória nas seções do código críticas quanto ao desempenho. 

Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [await](../../../csharp/language-reference/keywords/await.md)  
 [Instruções passo a passo: acessando a Web e usando Async e Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md)
