---
title: 'Passo a passo: Acessando a Web usando Async e Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 7154ea12f2660074e3ad8251b9baaa3eeb3d453c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Passo a passo: Acessando a Web usando Async e Await (Visual Basic)
É possível escrever programas assíncronos de forma mais fácil e intuitiva usando funcionalidades async/await. Você pode escrever código assíncrono que se parece com código síncrono e deixar que o compilador trate das complicadas continuações e funções de retorno de chamada que um código assíncrono normalmente envolve.  
  
 Para obter mais informações sobre o recurso assíncronas, consulte [programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Este passo a passo começa com um aplicativo WPF (Windows Presentation Foundation) síncrono que soma o número de bytes em uma lista de sites. Em seguida, converte o aplicativo em uma solução assíncrona usando os novos recursos.  
  
 Se não quiser compilar os aplicativos, você poderá baixar "Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)" nas [Amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
 Neste passo a passo, você realizará as seguintes tarefas:  
  
-   [Criar um aplicativo WPF](#CreateWPFApp)  
  
-   [Projetar um MainWindow WPF simples](#MainWindow)  
  
-   [Adicionar uma referência](#AddRef)  
  
-   [Para adicionar instruções Imports necessárias](#ImportsState)  
  
-   [Criar um aplicativo síncrono](#synchronous)  
  
-   [Testar a solução síncrona](#testSynch)  
  
-   [Converter GetURLContents em um método assíncrono](#GetURLContents)  
  
-   [Converter SumPageSizes em um método assíncrono](#SumPageSizes)  
  
-   [Converter startButton_Click em um método assíncrono](#startButton)  
  
-   [Testar a solução assíncrona](#testAsynch)  
  
-   [Substituir o método GetURLContentsAsync por um método .NET Framework](#GetURLContentsAsync)  
  
-   [Exemplo](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>Pré-requisitos  
 O Visual Studio 2012 ou posterior deve estar instalado em seu computador. Para obter mais informações, consulte o [site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).  
  
###  <a name="CreateWPFApp"></a> Criar um aplicativo WPF  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **Arquivo**, **Novo**, **Projeto**.  
  
     A caixa de diálogo **Novo Projeto** é aberta.  
  
3.  No **modelos instalados** painel, escolha Visual Basic e, em seguida, escolha **aplicativo WPF** da lista de tipos de projeto.  
  
4.  Na caixa de texto **Nome**, insira `AsyncExampleWPF` e, em seguida, escolha o botão **OK**.  
  
     O novo projeto aparece no **Gerenciador de Soluções**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> Projetar um MainWindow WPF simples  
  
1.  No Editor do Visual Studio Code, escolha a guia **MainWindow.xaml**.  
  
2.  Se a janela **Caixa de Ferramentas** não estiver visível, abra o menu **Exibir** e, em seguida, escolha **Caixa de Ferramentas**.  
  
3.  Adicione um controle **Botão** e um controle **Caixa de Texto** à janela **MainWindow**.  
  
4.  Realce o controle **Caixa de Texto** e, na janela **Propriedades**, defina os seguintes valores:  
  
    -   Defina a propriedade **Nome** como `resultsTextBox`.  
  
    -   Defina a propriedade **Altura** como 250.  
  
    -   Defina a propriedade **Largura** como 500.  
  
    -   Na guia **Texto**, especifique uma fonte com espaçamento uniforme, como Lucida Console ou Global Monospace.  
  
5.  Realce o controle **Botão** e, na janela **Propriedades**, defina os seguintes valores:  
  
    -   Defina a propriedade **Nome** como `startButton`.  
  
    -   Altere o valor da propriedade **Conteúdo** de **Botão** para **Iniciar**.  
  
6.  Posicione a caixa de texto e o botão de modo que ambos sejam exibidos na janela **MainWindow**.  
  
     Para obter mais informações sobre o Designer XAML do WPF, consulte [Criando uma interface do usuário usando o Designer XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> Adicionar uma referência  
  
1.  No **Gerenciador de Soluções**, realce o nome do projeto.  
  
2.  Na barra de menus, escolha **Projeto**, **Adicionar Referência**.  
  
     A caixa de diálogo **Gerenciador de Referências** é exibida.  
  
3.  Na parte superior da caixa de diálogo, verifique se seu projeto é voltado para o .NET Framework 4.5 ou posterior.  
  
4.  Na área **Assemblies**, escolha **Framework** se ele ainda não estiver escolhido.  
  
5.  Na lista de nomes, marque a caixa de seleção **System.Net.Http**.  
  
6.  Escolha o botão **OK** para fechar a caixa de diálogo.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a> Para adicionar instruções Imports necessárias  
  
1.  Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.  
  
2.  Adicione o seguinte `Imports` instruções na parte superior do arquivo de código, se eles não ainda estiver presentes.  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> Criar um aplicativo síncrono  
  
1.  Na janela de design, MainWindow. XAML, clique duas vezes o **iniciar** botão para criar o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.  
  
2.  Em MainWindow.xaml.vb, copie o seguinte código no corpo da `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     O código chama o método que aciona o aplicativo, `SumPageSizes` e exibe uma mensagem quando o controle retorna para `startButton_Click`.  
  
3.  O código para a solução síncrona contém os quatro métodos a seguir:  
  
    -   `SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e chama `GetURLContents` e `DisplayResults` para processar cada URL.  
  
    -   `SetUpURLList`, que cria e retorna uma lista de endereços web.  
  
    -   `GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.  
  
    -   `DisplayResults`, que exibe o número de bytes na matriz de bytes de cada URL.  
  
     Copie os quatro métodos a seguir e, em seguida, cole-os no `startButton_Click` MainWindow.xaml.vb manipulador de eventos:  
  
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
###  <a name="testSynch"></a> Testar a solução síncrona  
  
1.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.  
  
     Uma saída semelhante à lista a seguir deve aparecer.  
  
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
  
     Observe que são necessários alguns segundos para exibir as contagens. Durante esse tempo, o thread da interface do usuário é bloqueado enquanto espera que os recursos solicitados sejam baixados. Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição após escolher o botão **Iniciar**. Esses esforços falham até que as contagens de bytes comecem a aparecer. Se um site não estiver respondendo, você não terá nenhuma indicação de qual site falhou. É difícil até mesmo parar de esperar e fechar o programa.  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> Converter GetURLContents em um método assíncrono  
  
1.  Para converter a solução síncrona em uma solução assíncrona, o melhor lugar para começar é em `GetURLContents`, porque é pelas chamadas para o método <xref:System.Net.HttpWebRequest.GetResponse%2A> de <xref:System.Net.HttpWebRequest> e para o método <xref:System.IO.Stream.CopyTo%2A> de <xref:System.IO.Stream> que o aplicativo acessa a Web. O .NET Framework facilita a conversão fornecendo versões assíncronas dos dois métodos.  
  
     Para obter mais informações sobre os métodos usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Conforme você seguir as etapas neste passo a passo, vários erros de compilador serão exibidos. Você pode ignorá-los e continuar com o passo a passo.  
  
     Altere o método chamado na terceira linha de `GetURLContents` de `GetResponse` para o método <xref:System.Net.WebRequest.GetResponseAsync%2A> assíncrono, baseado em tarefas.  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync` retorna um <xref:System.Threading.Tasks.Task%601>. Nesse caso, a *variável de retorno de tarefa*, `TResult`, tem o tipo <xref:System.Net.WebResponse>. A tarefa é uma promessa de produzir um objeto `WebResponse` verdadeiro após os dados solicitados terem sido baixados e a tarefa ter sido executada até a conclusão.  
  
     Para recuperar o `WebResponse` o valor da tarefa, aplique um [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operador à chamada para `GetResponseAsync`, como mostra o código a seguir.  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     O operador `Await` suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída. Enquanto isso, o controle retorna para o chamador do método atual. Neste exemplo, o método atual é `GetURLContents` e o chamador é `SumPageSizes`. Quando a tarefa é concluída, o objeto `WebResponse` prometido é produzido como o valor da tarefa aguardada e é atribuído à variável `response`.  
  
     A instrução anterior pode ser separada em duas instruções a seguir para esclarecer o que acontece.  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`. Em seguida, uma `Await` operador é aplicado para a tarefa para recuperar o `WebResponse` valor.  
  
     Se o método assíncrono tem trabalho a fazer que não depende da conclusão da tarefa, o método pode continuar com esse trabalho entre essas duas instruções, após a chamada para o método assíncrono e antes que o operador await é aplicado. Para obter exemplos, consulte [como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) e [como: estender a Async Walkthrough por usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Como você adicionou o operador `Await` na etapa anterior, um erro do compilador ocorre. O operador pode ser usado somente em métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador. Ignore o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` por uma chamada para `CopyToAsync`.  
  
    -   Altere o nome do método que é chamado para <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   O método `CopyTo` ou `CopyToAsync` copia bytes para seu argumento, `content` e não retorna um valor significativo. Na versão síncrona, a chamada para `CopyTo` é uma instrução simples que não retorna um valor. A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>. A tarefa funciona como "Task(void)" e permite que o método seja aguardado. Aplique `Await` ou `await` à chamada para `CopyToAsync`, como mostra o código a seguir.  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         A instrução anterior abrevia as duas linhas de código a seguir.  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  Tudo o que resta fazer em `GetURLContents` é ajustar a assinatura do método. Você pode usar o `Await` operador somente em métodos que são marcados com o [Async](../../../../visual-basic/language-reference/modifiers/async.md) modificador. Adicione o modificador para marcar o método como um *método assíncrono*, como mostra o código a seguir.  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  O tipo de retorno de um método assíncrono só pode ser <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. No Visual Basic, o método deve ser um `Function` que retorna um `Task` ou um `Task(Of T)`, ou o método deve ser um `Sub`. Normalmente, um `Sub` método é usado somente em um manipulador de eventos assíncrono, onde `Sub` é necessária. Em outros casos, você usa `Task(T)` se o método concluída tem uma [retornar](../../../../visual-basic/language-reference/statements/return-statement.md) instrução que retorna um valor do tipo T, e você usar `Task` se o método concluída não retornar um valor significativo.  
  
     Para obter mais informações, consulte [tipos de retorno Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
     O método `GetURLContents` tem uma instrução de retorno e a instrução retorna uma matriz de bytes. Portanto, o tipo de retorno da versão assíncrona é Task(T), em que T é uma matriz de bytes. Faça as seguintes alterações na assinatura do método:  
  
    -   Altere o tipo de retorno para `Task(Of Byte())`.  
  
    -   Por convenção, métodos assíncronos têm nomes que terminam em "Async", então renomeie o método `GetURLContentsAsync`.  
  
     O código a seguir mostra essas alterações.  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     Com essas poucas alterações, a conversão de `GetURLContents` em um método assíncrono é concluída.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> Converter SumPageSizes em um método assíncrono  
  
1.  Repita as etapas do procedimento anterior para `SumPageSizes`. Primeiro, altere a chamada para `GetURLContents` para uma chamada assíncrona.  
  
    -   Altere o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync`, se ainda não tiver feito isso.  
  
    -   Aplique `Await` à tarefa que `GetURLContentsAsync` retorna para obter o valor da matriz de bytes.  
  
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
  
    -   Marque o método com o modificador `Async`.  
  
    -   Acrescente "Async" ao nome do método.  
  
    -   Não há nenhuma variável de retorno de tarefa, T, desta vez porque `SumPageSizesAsync` não retorna um valor para T. (O método não tem uma instrução `Return`.) No entanto, o método deve retornar um `Task` para que possa ser aguardado. Portanto, alterar o tipo de método de `Sub` para `Function`. O tipo de retorno da função é `Task`.  
  
     O código a seguir mostra essas alterações.  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     A conversão de `SumPageSizes` em `SumPageSizesAsync` está concluída.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> Converter startButton_Click em um método assíncrono  
  
1.  No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync`, se ainda não tiver feito isso.  
  
2.  Como `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.  
  
     A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`. A chamada retorna um `Task` e não um `Task(T)`.  
  
     Assim como nos procedimentos anteriores, você pode converter a chamada usando uma instrução ou duas instruções. O código a seguir mostra essas alterações.  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  Para evitar inserir novamente a operação por acidente, adicione a seguinte instrução à parte superior de `startButton_Click` para desabilitar o botão **Iniciar**.  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     É possível reabilitar o botão no final do manipulador de eventos.  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     Para obter mais informações sobre reentrância, consulte [tratando a reentrada em aplicativos assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Por fim, adicione o modificador `Async` à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     Normalmente, os nomes dos manipuladores de eventos não são alterados. O tipo de retorno não é alterado para `Task` como manipuladores de eventos devem ser `Sub` procedimentos no Visual Basic.  
  
     A conversão do projeto de um processamento síncrono em um assíncrono está concluída.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> Testar a solução assíncrona  
  
1.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.  
  
2.  Uma saída semelhante à saída da solução síncrona deve aparecer. No entanto, observe as diferenças a seguir.  
  
    -   Os resultados não ocorrem todos ao mesmo tempo, após a conclusão do processamento. Por exemplo, os dois programas contêm uma linha em `startButton_Click` que desmarca a caixa de texto. A intenção é desmarcar a caixa de texto entre as execuções se você escolher o botão **Iniciar** pela segunda vez, após um conjunto de resultados ter aparecido. Na versão síncrona, a caixa de texto é desmarcada logo antes das contagens aparecerem pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário fica livre para executar outras tarefas. Na versão assíncrona, a caixa de texto é limpa imediatamente após você escolher o botão **Iniciar**.  
  
    -   Mais importante, o thread da interface do usuário não é bloqueado durante os downloads. Você pode mover ou redimensionar a janela enquanto os recursos da Web estão sendo baixados, contados e exibido. Se um dos sites estiver lento ou não estiver respondendo, você poderá cancelar a operação escolhendo o botão **Fechar** (o x no campo vermelho no canto superior direito).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> Substituir o método GetURLContentsAsync por um método .NET Framework  
  
1.  O .NET Framework 4.5 fornece vários métodos assíncronos que você pode usar. Um deles, o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> de <xref:System.Net.Http.HttpClient>, faz exatamente o que é necessário para este passo a passo. Você pode usá-lo em vez do método `GetURLContentsAsync` que criou em um procedimento anterior.  
  
     A primeira etapa é criar um objeto `HttpClient` no método `SumPageSizesAsync`. Adicione a declaração a seguir ao início do método.  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  Em `SumPageSizesAsync,`, substitua a chamada para seu método `GetURLContentsAsync` por uma chamada para o método `HttpClient`.  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  Remova ou comente o método `GetURLContentsAsync` que você escreveu.  
  
4.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.  
  
     O comportamento desta versão do projeto deve corresponder ao comportamento que o procedimento "Testar a solução assíncrona" descreve, mas com ainda menos esforço para você.  
  
##  <a name="BKMK_CompleteCodeExamples"></a> Exemplo  
 O código a seguir contém o exemplo completo da conversão de uma solução síncrona em uma solução assíncrona usando o método `GetURLContentsAsync` assíncrono que você escreveu. Observe que ele se assemelha muito à solução síncrona original.  
  
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
 [Exemplo de assincronia: acessando o passo a passo da Web (C# e Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [Operador Await](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
 [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Tipos de retorno assíncronos (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [TAP (programação assíncrona baseada em tarefas)](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [Como estender as instruções passo a passo assíncronas usando Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [Como fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
