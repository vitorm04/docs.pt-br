---
title: 'Instruções passo a passo: acessando a Web e usando Async e Await'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: c13e592eb155d14c2e7cb2388a96925a7f1fa413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349090"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)

É possível escrever programas assíncronos de forma mais fácil e intuitiva usando funcionalidades async/await. Você pode escrever código assíncrono que se parece com código síncrono e deixar que o compilador trate das complicadas continuações e funções de retorno de chamada que um código assíncrono normalmente envolve.

For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Este passo a passo começa com um aplicativo WPF (Windows Presentation Foundation) síncrono que soma o número de bytes em uma lista de sites. Em seguida, converte o aplicativo em uma solução assíncrona usando os novos recursos.

Se não quiser compilar os aplicativos, você poderá baixar "Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)" nas [Amostras de código do desenvolvedor](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

Neste passo a passo, você realizará as seguintes tarefas:

> [!div class="checklist"]
>
> - [Create a WPF application](#create-a-wpf-application)
> - [Design a simple WPF MainWindow](#design-a-simple-wpf-mainwindow)
> - [Add a reference](#add-a-reference)
> - [Add necessary Imports statements](#add-necessary-imports-statements)
> - [Create a synchronous application](#create-a-synchronous-application)
> - [Test the synchronous solution](#test-the-synchronous-solution)
> - [Convert GetURLContents to an asynchronous method](#convert-geturlcontents-to-an-asynchronous-method)
> - [Convert SumPageSizes to an asynchronous method](#convert-sumpagesizes-to-an-asynchronous-method)
> - [Convert startButton_Click to an asynchronous method](#convert-startbutton_click-to-an-asynchronous-method)
> - [Test the asynchronous solution](#test-the-asynchronous-solution)
> - [Replace the GetURLContentsAsync method with a .NET Framework method](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

See the [Example](#example) section for the complete asynchronous example.

## <a name="prerequisites"></a>Prerequisites

O Visual Studio 2012 ou posterior deve estar instalado em seu computador. For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.

## <a name="create-a-wpf-application"></a>Criar um aplicativo WPF

1. Inicie o Visual Studio.

2. Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.

    A caixa de diálogo **Novo Projeto** é aberta.

3. In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.

4. Na caixa de texto **Nome**, insira `AsyncExampleWPF` e, em seguida, escolha o botão **OK**.

    O novo projeto aparece no **Gerenciador de Soluções**.

## <a name="design-a-simple-wpf-mainwindow"></a>Projetar um MainWindow WPF simples

1. No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.

2. Se a janela **Caixa de Ferramentas** não estiver visível, abra o menu **Exibir** e, em seguida, escolha **Caixa de Ferramentas**.

3. Adicione um controle **Botão** e um controle **Caixa de Texto** à janela **MainWindow**.

4. Realce o controle **Caixa de Texto** e, na janela **Propriedades**, defina os seguintes valores:

    - Defina a propriedade **Nome** como `resultsTextBox`.

    - Defina a propriedade **Altura** como 250.

    - Defina a propriedade **Largura** como 500.

    - Na guia **Texto**, especifique uma fonte com espaçamento uniforme, como Lucida Console ou Global Monospace.

5. Realce o controle **Botão** e, na janela **Propriedades**, defina os seguintes valores:

    - Defina a propriedade **Nome** como `startButton`.

    - Altere o valor da propriedade **Conteúdo** de **Botão** para **Iniciar**.

6. Posicione a caixa de texto e o botão de modo que ambos sejam exibidos na janela **MainWindow**.

    Para obter mais informações sobre o Designer XAML do WPF, consulte [Criando uma interface do usuário usando o Designer XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Adicionar uma referência

1. No **Gerenciador de Soluções**, realce o nome do projeto.

2. Na barra de menus, escolha **Projeto**, **Adicionar Referência**.

    A caixa de diálogo **Gerenciador de Referências** é exibida.

3. Na parte superior da caixa de diálogo, verifique se seu projeto é voltado para o .NET Framework 4.5 ou posterior.

4. Na área **Assemblies**, escolha **Framework** se ele ainda não estiver escolhido.

5. Na lista de nomes, marque a caixa de seleção **System.Net.Http**.

6. Escolha o botão **OK** para fechar a caixa de diálogo.

## <a name="add-necessary-imports-statements"></a>Add necessary Imports statements

1. In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.

2. Add the following `Imports` statements at the top of the code file if they’re not already present.

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a>Create a synchronous application

1. In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.

2. In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    O código chama o método que aciona o aplicativo, `SumPageSizes` e exibe uma mensagem quando o controle retorna para `startButton_Click`.

3. O código para a solução síncrona contém os quatro métodos a seguir:

    - `SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e chama `GetURLContents` e `DisplayResults` para processar cada URL.

    - `SetUpURLList`, que cria e retorna uma lista de endereços web.

    - `GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.

    - `DisplayResults`, que exibe o número de bytes na matriz de bytes de cada URL.

    Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a>Testar a solução síncrona

1. Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.

    Uma saída semelhante à lista a seguir deve aparecer:

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    Observe que são necessários alguns segundos para exibir as contagens. Durante esse tempo, o thread da interface do usuário é bloqueado enquanto espera que os recursos solicitados sejam baixados. Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição após escolher o botão **Iniciar**. Esses esforços falham até que as contagens de bytes comecem a aparecer. Se um site não estiver respondendo, você não terá nenhuma indicação de qual site falhou. É difícil até mesmo parar de esperar e fechar o programa.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Converter GetURLContents em um método assíncrono

1. To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web. O .NET Framework facilita a conversão fornecendo versões assíncronas dos dois métodos.

    Para obter mais informações sobre os métodos usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Conforme você seguir as etapas neste passo a passo, vários erros de compilador serão exibidos. Você pode ignorá-los e continuar com o passo a passo.

    Altere o método chamado na terceira linha de `GetURLContents` de `GetResponse` para o método <xref:System.Net.WebRequest.GetResponseAsync%2A> assíncrono, baseado em tarefas.

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. `GetResponseAsync` retorna um <xref:System.Threading.Tasks.Task%601>. Nesse caso, a *variável de retorno de tarefa*, `TResult`, tem o tipo <xref:System.Net.WebResponse>. A tarefa é uma promessa de produzir um objeto `WebResponse` verdadeiro após os dados solicitados terem sido baixados e a tarefa ter sido executada até a conclusão.

    To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    O operador `Await` suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída. Enquanto isso, o controle retorna para o chamador do método atual. Neste exemplo, o método atual é `GetURLContents` e o chamador é `SumPageSizes`. Quando a tarefa é concluída, o objeto `WebResponse` prometido é produzido como o valor da tarefa aguardada e é atribuído à variável `response`.

    A instrução anterior pode ser separada em duas instruções a seguir para esclarecer o que acontece.

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`. Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.

    If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Como você adicionou o operador `Await` na etapa anterior, um erro do compilador ocorre. The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier. Ignore o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` por uma chamada para `CopyToAsync`.

    - Altere o nome do método que é chamado para <xref:System.IO.Stream.CopyToAsync%2A>.

    - O método `CopyTo` ou `CopyToAsync` copia bytes para seu argumento, `content` e não retorna um valor significativo. Na versão síncrona, a chamada para `CopyTo` é uma instrução simples que não retorna um valor. A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>. A tarefa funciona como "Task(void)" e permite que o método seja aguardado. Aplique `Await` ou `await` à chamada para `CopyToAsync`, como mostra o código a seguir.

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         A instrução anterior abrevia as duas linhas de código a seguir.

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. Tudo o que resta fazer em `GetURLContents` é ajustar a assinatura do método. You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier. Adicione o modificador para marcar o método como um *método assíncrono*, como mostra o código a seguir.

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`. Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required. In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.

    For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

    O método `GetURLContents` tem uma instrução de retorno e a instrução retorna uma matriz de bytes. Portanto, o tipo de retorno da versão assíncrona é Task(T), em que T é uma matriz de bytes. Faça as seguintes alterações na assinatura do método:

    - Altere o tipo de retorno para `Task(Of Byte())`.

    - Por convenção, métodos assíncronos têm nomes que terminam em "Async", então renomeie o método `GetURLContentsAsync`.

    O código a seguir mostra essas alterações.

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    Com essas poucas alterações, a conversão de `GetURLContents` em um método assíncrono é concluída.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Converter SumPageSizes em um método assíncrono

1. Repita as etapas do procedimento anterior para `SumPageSizes`. Primeiro, altere a chamada para `GetURLContents` para uma chamada assíncrona.

    - Altere o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync`, se ainda não tiver feito isso.

    - Aplique `Await` à tarefa que `GetURLContentsAsync` retorna para obter o valor da matriz de bytes.

    O código a seguir mostra essas alterações.

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    A atribuição anterior abrevia as duas linhas de código a seguir.

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. Faça as seguintes alterações na assinatura do método:

    - Marque o método com o modificador `Async`.

    - Acrescente "Async" ao nome do método.

    - There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable. Therefore, change the method type from `Sub` to `Function`. The return type of the function is `Task`.

    O código a seguir mostra essas alterações.

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    A conversão de `SumPageSizes` em `SumPageSizesAsync` está concluída.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Converter startButton_Click em um método assíncrono

1. No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync`, se ainda não tiver feito isso.

2. Como `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.

    A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`. A chamada retorna um `Task` e não um `Task(T)`.

    Assim como nos procedimentos anteriores, você pode converter a chamada usando uma instrução ou duas instruções. O código a seguir mostra essas alterações.

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. Para evitar inserir novamente a operação por acidente, adicione a seguinte instrução à parte superior de `startButton_Click` para desabilitar o botão **Iniciar**.

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    É possível reabilitar o botão no final do manipulador de eventos.

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4. Por fim, adicione o modificador `Async` à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    Normalmente, os nomes dos manipuladores de eventos não são alterados. The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.

    A conversão do projeto de um processamento síncrono em um assíncrono está concluída.

## <a name="test-the-asynchronous-solution"></a>Testar a solução assíncrona

1. Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.

2. Uma saída semelhante à saída da solução síncrona deve aparecer. No entanto, observe as diferenças a seguir.

    - Os resultados não ocorrem todos ao mesmo tempo, após a conclusão do processamento. Por exemplo, os dois programas contêm uma linha em `startButton_Click` que desmarca a caixa de texto. A intenção é desmarcar a caixa de texto entre as execuções se você escolher o botão **Iniciar** pela segunda vez, após um conjunto de resultados ter aparecido. Na versão síncrona, a caixa de texto é desmarcada logo antes das contagens aparecerem pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário fica livre para executar outras tarefas. Na versão assíncrona, a caixa de texto é limpa imediatamente após você escolher o botão **Iniciar**.

    - Mais importante, o thread da interface do usuário não é bloqueado durante os downloads. Você pode mover ou redimensionar a janela enquanto os recursos da Web estão sendo baixados, contados e exibido. Se um dos sites estiver lento ou não estiver respondendo, você poderá cancelar a operação escolhendo o botão **Fechar** (o x no campo vermelho no canto superior direito).

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a>Replace the GetURLContentsAsync method with a .NET Framework method

1. The .NET Framework provides many async methods that you can use. One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough. Você pode usá-lo em vez do método `GetURLContentsAsync` que criou em um procedimento anterior.

    The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method. Adicione a declaração a seguir ao início do método.

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. Em `SumPageSizesAsync,`, substitua a chamada para seu método `GetURLContentsAsync` por uma chamada para o método `HttpClient`.

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. Remova ou comente o método `GetURLContentsAsync` que você escreveu.

4. Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.

    O comportamento desta versão do projeto deve corresponder ao comportamento que o procedimento "Testar a solução assíncrona" descreve, mas com ainda menos esforço para você.

## <a name="example"></a>Exemplo

The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method. Observe que ele se assemelha muito à solução síncrona original.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

O código a seguir contém o exemplo completo da solução que usa o método `HttpClient`, `GetByteArrayAsync`.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a>Consulte também

- [Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Operador Await](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [TAP (programação assíncrona baseada em tarefas)](https://go.microsoft.com/fwlink/?LinkId=204847)
- [Como estender as instruções passo a passo assíncronas usando Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Como fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
