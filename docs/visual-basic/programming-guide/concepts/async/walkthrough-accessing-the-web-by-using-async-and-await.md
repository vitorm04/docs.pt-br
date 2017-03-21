---
title: Acessando a Web com Async e Await (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
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
ms.openlocfilehash: 643fff648336c664961ad7956308acbaea262f61
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)
Você pode escrever programas assíncronos intuitivamente e mais facilmente usando os recursos que foram introduzidos no [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)]. Você pode escrever código assíncrono que se parece com o código síncrono e deixar que o compilador lidar com as funções de retorno de chamada difícil e continuações normalmente envolve um código assíncrono.  
  
 Para obter mais informações sobre o recurso Async, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Este passo a passo começa com um aplicativo Windows Presentation Foundation (WPF) síncrono que some o número de bytes em uma lista de sites. Passo a passo, em seguida, converte o aplicativo para uma solução assíncrona usando os novos recursos.  
  
 Se você não quiser criar os aplicativos por conta própria, você pode baixar "exemplo de assincronia: acessando o passo a passo da Web (c# e Visual Basic)" do [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
 Neste passo a passo, você deve concluir as seguintes tarefas:  
  
-   [Para criar um aplicativo WPF](#CreateWPFApp)  
  
-   [Para criar um simples MainWindow WPF](#MainWindow)  
  
-   [Para adicionar uma referência](#AddRef)  
  
-   [Para adicionar instruções Imports necessárias](#ImportsState)  
  
-   [Para criar um aplicativo síncrono](#synchronous)  
  
-   [Para testar a solução síncrona](#testSynch)  
  
-   [Para converter GetURLContents em um método assíncrono](#GetURLContents)  
  
-   [Para converter SumPageSizes em um método assíncrono](#SumPageSizes)  
  
-   [Para converter startButton_Click em um método assíncrono](#startButton)  
  
-   [Para testar a solução assíncrona](#testAsynch)  
  
-   [Para substituir o método GetURLContentsAsync com um método do .NET Framework](#GetURLContentsAsync)  
  
-   [Exemplo](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Visual Studio 2012 ou posterior deve ser instalado em seu computador. Para obter mais informações, consulte o [site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).  
  
###  <a name="CreateWPFApp"></a>Para criar um aplicativo WPF  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     O **novo projeto** caixa de diálogo é aberta.  
  
3.  No **modelos instalados** painel, escolha Visual Basic e, em seguida, escolha **aplicativo WPF** da lista de tipos de projeto.  
  
4.  No **nome** texto, digite `AsyncExampleWPF`e, em seguida, escolha o **Okey** botão.  
  
     O novo projeto aparece na **Solution Explorer**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a>Para criar um simples MainWindow WPF  
  
1.  No código de Editor do Visual Studio, escolha o **MainWindow** guia.  
  
2.  Se o **Toolbox** janela não estiver visível, abra o **exibição** menu e, em seguida, escolha **ferramentas**.  
  
3.  Adicionar uma **botão** controle e um **TextBox** o controle para o **MainWindow** janela.  
  
4.  Realce o **TextBox** controle e, no **propriedades** janela, defina os seguintes valores:  
  
    -   Definir o **nome** propriedade `resultsTextBox`.  
  
    -   Definir o **altura** propriedade para 250.  
  
    -   Definir o **largura** propriedade a 500.  
  
    -   Sobre o **texto** , especifique uma fonte monoespaçada, como Lucida Console ou Monospace Global.  
  
5.  Realce o **botão** controle e, no **propriedades** janela, defina os seguintes valores:  
  
    -   Definir o **nome** propriedade `startButton`.  
  
    -   Altere o valor da **conteúdo** propriedade **botão** para **iniciar**.  
  
6.  Posicione a caixa de texto e o botão para que ambos sejam exibidos no **MainWindow** janela.  
  
     Para obter mais informações sobre o WPF XAML Designer, consulte [criando uma interface do usuário usando o Designer XAML](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a>Para adicionar uma referência  
  
1.  Em **Solution Explorer**, realce o nome do projeto.  
  
2.  Na barra de menus, escolha **projeto**, **adicionar referência**.  
  
     O **Gerenciador de referências** caixa de diálogo é exibida.  
  
3.  Na parte superior da caixa de diálogo, verifique se o seu projeto é voltado para o .NET Framework 4.5 ou posterior.  
  
4.  No **Assemblies** área, escolha **Framework** se ele já não é escolhido.  
  
5.  Na lista de nomes, selecione o **System.Net.Http** caixa de seleção.  
  
6.  Escolha o **Okey** para fechar a caixa de diálogo.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a>Para adicionar instruções Imports necessárias  
  
1.  Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.  
  
2.  Adicione o seguinte `Imports` instruções na parte superior do arquivo de código, se eles não ainda estiver presentes.  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a>Para criar um aplicativo síncrono  
  
1.  Na janela de design, MainWindow. XAML, clique duas vezes o **iniciar** botão para criar o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.  
  
2.  Em MainWindow.xaml.vb, copie o seguinte código no corpo da `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     O código chama o método que acionam o aplicativo `SumPageSizes`e exibe uma mensagem quando o controle retorna para `startButton_Click`.  
  
3.  O código para a solução síncrona contém os quatro métodos a seguir:  
  
    -   `SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e, em seguida, chama `GetURLContents` e `DisplayResults` para processar cada URL.  
  
    -   `SetUpURLList`, que cria e retorna uma lista de endereços da web.  
  
    -   `GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.  
  
    -   `DisplayResults`, que exibe o número de bytes na matriz de bytes para cada URL.  
  
     Copie os quatro métodos e colá-los sob o `startButton_Click` manipulador de eventos MainWindow.xaml.vb:  
  
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
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a>Para testar a solução síncrona  
  
1.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.  
  
     Saída semelhante a lista a seguir deve aparecer.  
  
    ```  
  
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
  
     Observe que levará alguns segundos para exibir as contagens. Durante esse tempo, o thread de interface do usuário é bloqueado enquanto aguarda recursos solicitados fazer o download. Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição depois de escolher o **iniciar** botão. Esses esforços falham até que as contagens de byte começam a aparecer. Se um site não estiver respondendo, você pode ter nenhuma indicação de qual site falhou. É difícil até mesmo pare de esperar e fecha o programa.  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a>Para converter GetURLContents em um método assíncrono  
  
1.  Para converter a solução síncrona em uma solução assíncrona, o melhor lugar para começar é em `GetURLContents` porque as chamadas para o <xref:System.Net.HttpWebRequest>método <xref:System.Net.HttpWebRequest.GetResponse%2A>e o <xref:System.IO.Stream>método <xref:System.IO.Stream.CopyTo%2A>são onde o aplicativo acessa a web.</xref:System.IO.Stream.CopyTo%2A> </xref:System.IO.Stream> </xref:System.Net.HttpWebRequest.GetResponse%2A> </xref:System.Net.HttpWebRequest> O .NET Framework facilita a conversão ao fornecer versões assíncronas dos dois métodos.  
  
     Para obter mais informações sobre os métodos que são usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.</xref:System.Net.WebRequest>  
  
    > [!NOTE]
    >  Quando você seguir as etapas neste passo a passo, vários erros de compilador são exibidas. Você pode ignorá-las e continuar com o passo a passo.  
  
     Alterar o método é chamado na terceira linha da `GetURLContents` de `GetResponse` assíncrono, baseado em tarefa <xref:System.Net.WebRequest.GetResponseAsync%2A>método.</xref:System.Net.WebRequest.GetResponseAsync%2A>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync`Retorna um <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> Nesse caso, o *variável de retorno de tarefa*, `TResult`, tem o tipo <xref:System.Net.WebResponse>.</xref:System.Net.WebResponse> A tarefa é uma promessa de produzir um verdadeiro `WebResponse` depois que os dados solicitados foi baixados e a tarefa foi executada até a conclusão do objeto.  
  
     Para recuperar o `WebResponse` o valor da tarefa, aplique um [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operador da chamada `GetResponseAsync`, como mostra o código a seguir.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
     O `Await` operador suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída. Enquanto isso, o controle retorna para o chamador do método atual. Neste exemplo, o método atual é `GetURLContents`, e o chamador é `SumPageSizes`. Quando a tarefa é concluída, o prometido `WebResponse` objeto é produzido como o valor da tarefa awaited e atribuído à variável `response`.  
  
     The previous statement can be separated into the following two statements to clarify what happens.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
     A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`. Um `Await` operador é aplicado à tarefa para recuperar o `WebResponse` valor.  
  
     If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Como você adicionou o `Await` operador na etapa anterior, um erro do compilador ocorre. O operador pode ser usado apenas nos métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador. Ignorar o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` com uma chamada para `CopyToAsync`.  
  
    -   Alterar o nome do método que é chamado para <xref:System.IO.Stream.CopyToAsync%2A>.</xref:System.IO.Stream.CopyToAsync%2A>  
  
    -   O `CopyTo` ou `CopyToAsync` método copia bytes para o argumento `content`e não retorna um valor significativo. Na versão síncrona, a chamada para `CopyTo` é uma simple instrução que não retorna um valor. A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> A tarefa funciona como "Task(void)" e permite que o método a ser aguardado. Aplicar `Await` ou `await` da chamada `CopyToAsync`, como mostra o código a seguir.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
         A instrução anterior abrevia as duas linhas de código a seguir.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
4.  Tudo o que resta a ser feito em `GetURLContents` é ajustar a assinatura do método. Você pode usar o `Await` operador apenas nos métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador. Adicione o modificador para marcar o método como uma *método assíncrono*, como mostra o código a seguir.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
5.  O tipo de retorno de um método assíncrono só pode ser <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task> No Visual Basic, o método deve ser um `Function` que retorna um `Task` ou um `Task(Of T)`, ou o método deve ser um `Sub`. Normalmente, um `Sub` método é usado somente em um manipulador de eventos assíncronos, onde `Sub` é necessária. Em outros casos, você usa `Task(T)` se o método concluído tiver uma [retornar](../../../../visual-basic/language-reference/statements/return-statement.md) instrução que retorna um valor do tipo T, e você usar `Task` se o método concluído não retorna um valor significativo.  
  
     Para obter mais informações, consulte [assíncronas retornam tipos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
     Método `GetURLContents` possui uma instrução de retorno, e a instrução retorna uma matriz de bytes. Portanto, o tipo de retorno da versão async é Task(T), onde T é uma matriz de bytes. Faça as seguintes alterações na assinatura do método:  
  
    -   Alterar o tipo de retorno para `Task(Of Byte())`.  
  
    -   Por convenção, os métodos assíncronos têm nomes que terminam em "Async", então renomear o método `GetURLContentsAsync`.  
  
     O código a seguir mostra essas alterações.  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     Com essas poucas alterações, a conversão de `GetURLContents` para um método assíncrono é concluído.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a>Para converter SumPageSizes em um método assíncrono  
  
1.  Repita as etapas do procedimento anterior para `SumPageSizes`. Primeiro, altere a chamada a `GetURLContents` para uma chamada assíncrona.  
  
    -   Alterar o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync`, se você ainda não fez isso.  
  
    -   Aplicar `Await` para a tarefa que `GetURLContentsAsync` retorna o byte de obter o valor de matriz.  
  
     O código a seguir mostra essas alterações.  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     A atribuição anterior abrevia as duas linhas de código a seguir.  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
  
    ```  
  
2.  Faça as seguintes alterações na assinatura do método:  
  
    -   Marcar o método com o `Async` modificador.  
  
    -   Adicione "Async" para o nome do método.  
  
    -   Não há nenhuma variável de retorno de tarefa, T, neste momento porque `SumPageSizesAsync` não retorna um valor de T. (O método não tem `Return` instrução.) No entanto, o método deve retornar um `Task` para awaitable. Portanto, altere o tipo de método de `Sub` para `Function`. O tipo de retorno da função é `Task`.  
  
     O código a seguir mostra essas alterações.  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     A conversão de `SumPageSizes` para `SumPageSizesAsync` for concluída.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a>Para converter startButton_Click em um método assíncrono  
  
1.  No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync`, se você ainda não fez isso.  
  
2.  Porque `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.  
  
     A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`. A chamada retorna um `Task`, e não um `Task(T)`.  
  
     Como em procedimentos anteriores, você pode converter a chamada por meio de uma instrução ou duas instruções. O código a seguir mostra essas alterações.  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  Para evitar que acidentalmente redigitando a operação, adicione a seguinte instrução na parte superior do `startButton_Click` para desabilitar o **iniciar** botão.  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     Você pode reabilitar o botão no final do manipulador de eventos.  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     Para obter mais informações sobre reentrância, consulte [tratando reentrada em aplicativos assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Finalmente, adicione o `Async` modificador à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     Normalmente, os nomes de manipuladores de eventos não são alterados. O tipo de retorno não é alterado para `Task` como manipuladores de eventos devem ser `Sub` procedimentos no Visual Basic.  
  
     A conversão do projeto de processamento síncrono para assíncrono é concluída.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a>Para testar a solução assíncrona  
  
1.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.  
  
2.  A saída que é semelhante à saída da solução síncrona deve aparecer. No entanto, observe as seguintes diferenças.  
  
    -   Os resultados não ocorrem ao mesmo tempo, após o processamento é concluído. Por exemplo, os dois programas contêm uma linha no `startButton_Click` que desmarca a caixa de texto. A intenção é desmarcar a caixa de texto entre as execuções, se você escolher o **iniciar** botão pela segunda vez, depois que um conjunto de resultados apareceu. Na versão síncrona, a caixa de texto é limpo antes que as contagens são exibidos pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário está livre para executar outras tarefas. A versão assíncrona, a caixa de texto limpa imediatamente depois que você escolher o **iniciar** botão.  
  
    -   Mais importante, o thread de interface do usuário não é bloqueado durante os downloads. Você pode mover ou redimensionar a janela enquanto os recursos da web estão sendo baixados, contados e exibido. Se um dos sites está lento ou não responder, você pode cancelar a operação, escolhendo o **fechar** botão (o x no campo vermelho no canto superior direito).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a>Para substituir o método GetURLContentsAsync com um método do .NET Framework  
  
1.  O .NET Framework 4.5 fornece vários métodos assíncronos que você pode usar. Um deles, o <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, exatamente o que você precisa para este passo a passo.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> </xref:System.Net.Http.HttpClient> Você pode usá-lo em vez do `GetURLContentsAsync` método que você criou em um procedimento anterior.  
  
     A primeira etapa é criar um `HttpClient` objeto no método `SumPageSizesAsync`. Adicione a seguinte declaração no início do método.  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  Em `SumPageSizesAsync,` substitua a chamada para o `GetURLContentsAsync` método com uma chamada para o `HttpClient` método.  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  Remova ou comente o `GetURLContentsAsync` método que você escreveu.  
  
4.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.  
  
     O comportamento desta versão do projeto deve corresponder ao comportamento que descreve o procedimento "para testar a solução assíncrona" mas com o mesmo menos esforço do que você.  
  
##  <a name="BKMK_CompleteCodeExamples"></a> Exemplo  
 O código a seguir contém o exemplo completo de conversão de um síncrono para uma solução assíncrona usando assíncrona `GetURLContentsAsync` método que você escreveu. Observe que ele fortemente se assemelha a solução síncrona original.  
  
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
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 O código a seguir contém o exemplo completo da solução que usa o `HttpClient` método `GetByteArrayAsync`.  
  
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
  
        '' Two-step async call.  
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
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de assincronia: Acessando o passo a passo da Web (c# e Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191)   
 [Operador await](../../../../visual-basic/language-reference/operators/await-operator.md)   
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)   
 [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [Programação assíncrona baseado em tarefa (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847)   
 [Como: estender o passo a passo assíncronas usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)   
 [Como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
