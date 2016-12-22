---
title: "Passo a passo: Acessando a Web usando o async e await (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "CSharp"
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passo a passo: Acessando a Web usando o async e await (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode escrever programas assíncronos intuitivamente e mais facilmente usando os recursos que foram introduzidos no [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)]. Você pode escrever código assíncrono que se parece com o código síncrono e deixar que o compilador lidar com as funções de retorno de chamada difícil e continuações normalmente envolve um código assíncrono.  
  
 Para obter mais informações sobre o recurso Async, consulte [Programação assíncrona com async e await \(c\#\)](../../../../csharp/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md).  
  
 Este passo a passo começa com um aplicativo Windows Presentation Foundation \(WPF\) síncrono que some o número de bytes em uma lista de sites. Passo a passo, em seguida, converte o aplicativo para uma solução assíncrona usando os novos recursos.  
  
 Se você não quiser criar os aplicativos por conta própria, você pode baixar "exemplo de assincronia: acessando o passo a passo da Web \(c\# e Visual Basic\)" do [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
 Neste passo a passo, você deve concluir as seguintes tarefas:  
  
-   [Para criar um aplicativo WPF](#CreateWPFApp)  
  
-   [Para criar um simples MainWindow WPF](#MainWindow)  
  
-   [Para adicionar uma referência](#AddRef)  
  
-   [Para adicionar as diretivas using necessárias](#usingDir)  
  
-   [Para criar um aplicativo síncrono](#synchronous)  
  
-   [Para testar a solução síncrona](#testSynch)  
  
-   [Para converter GetURLContents em um método assíncrono](#GetURLContents)  
  
-   [Para converter SumPageSizes em um método assíncrono](#SumPageSizes)  
  
-   [Para converter startButton_Click em um método assíncrono](#startButton)  
  
-   [Para testar a solução assíncrona](#testAsynch)  
  
-   [Para substituir o método GetURLContentsAsync com um método do .NET Framework](#GetURLContentsAsync)  
  
-   [Exemplo](#BKMK_CompleteCodeExamples)  
  
## Pré-requisitos  
 Visual Studio 2012 ou posterior deve ser instalado em seu computador. Para obter mais informações, consulte o [site da Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).  
  
###  <a name="CreateWPFApp"></a> Para criar um aplicativo WPF  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
     O **novo projeto** caixa de diálogo é aberta.  
  
3.  No **modelos instalados** painel, escolha Visual c\# e escolha **aplicativo WPF** da lista de tipos de projeto.  
  
4.  No **nome** texto, digite `AsyncExampleWPF`, e, em seguida, escolha o **OK** botão.  
  
     O novo projeto aparece na **Solution Explorer**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> Para criar um simples MainWindow WPF  
  
1.  No código de Editor do Visual Studio, escolha o **MainWindow** guia.  
  
2.  Se o **Toolbox** janela não estiver visível, abra o **exibição** menu e, em seguida, escolha **Toolbox**.  
  
3.  Adicione um **botão** controle e um **TextBox** o controle para o **MainWindow** janela.  
  
4.  Realce o **TextBox** controle e, no **propriedades** janela, defina os seguintes valores:  
  
    -   Definir o **nome** propriedade `resultsTextBox`.  
  
    -   Definir o **Altura** propriedade para 250.  
  
    -   Definir o **largura** propriedade a 500.  
  
    -   Sobre o **texto** especifique uma fonte monoespaçada, como Lucida Console ou Monospace Global.  
  
5.  Realce o **botão** controle e, no **propriedades** janela, defina os seguintes valores:  
  
    -   Definir o **nome** propriedade `startButton`.  
  
    -   Altere o valor da **conteúdo** propriedade **botão** para **Iniciar**.  
  
6.  Posicione a caixa de texto e o botão para que ambos sejam exibidos no **MainWindow** janela.  
  
     Para obter mais informações sobre o WPF XAML Designer, consulte [Criando uma interface de usuário usando o Designer XAML](/visual-studio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> Para adicionar uma referência  
  
1.  Em **Solution Explorer**, realce o nome do projeto.  
  
2.  Na barra de menus, escolha **projeto**, **Adicionar referência**.  
  
     O **Gerenciador de referências** caixa de diálogo é exibida.  
  
3.  Na parte superior da caixa de diálogo, verifique se o seu projeto é voltado para o .NET Framework 4.5 ou posterior.  
  
4.  No **Assemblies** área, escolha **Framework** se ele já não é escolhido.  
  
5.  Na lista de nomes, selecione o **System.Net.Http** caixa de seleção.  
  
6.  Escolha o **OK** botão para fechar a caixa de diálogo.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a> Para adicionar as diretivas using necessárias  
  
1.  Em **Solution Explorer**, abra o menu de atalho de MainWindow.xaml.cs e, em seguida, escolha **Exibir código**.  
  
2.  Adicione o seguinte `using` diretivas na parte superior do arquivo de código, se eles não ainda estiver presentes.  
  
    ```c#  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> Para criar um aplicativo síncrono  
  
1.  Na janela de design, MainWindow. XAML, clique duas vezes o **Iniciar** botão para criar o `startButton_Click` MainWindow.xaml.cs manipulador de eventos.  
  
2.  Em MainWindow.xaml.cs, copie o seguinte código no corpo da `startButton_Click`:  
  
    ```c#  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     O código chama o método que acionam o aplicativo, `SumPageSizes`, e exibe uma mensagem quando o controle retorna para `startButton_Click`.  
  
3.  O código para a solução síncrona contém os quatro métodos a seguir:  
  
    -   `SumPageSizes`, que obtém uma lista de URLs de página da Web de `SetUpURLList` e, em seguida, chama `GetURLContents` e `DisplayResults` para processar cada URL.  
  
    -   `SetUpURLList`, que cria e retorna uma lista de endereços da web.  
  
    -   `GetURLContents`, que baixa o conteúdo de cada site e retorna o conteúdo como uma matriz de bytes.  
  
    -   `DisplayResults`, que exibe o número de bytes na matriz de bytes para cada URL.  
  
     Copie os quatro métodos e colá\-los sob o `startButton_Click` MainWindow.xaml.cs manipulador de eventos:  
  
    ```c#  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
        {   
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/en-us/library/hh290136.aspx",  
            "http://msdn.microsoft.com/en-us/library/ee256749.aspx",  
            "http://msdn.microsoft.com/en-us/library/hh290138.aspx",  
            "http://msdn.microsoft.com/en-us/library/hh290140.aspx",  
            "http://msdn.microsoft.com/en-us/library/dd470362.aspx",  
            "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
            "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
            "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> Para testar a solução síncrona  
  
1.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **Iniciar** botão.  
  
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
  
     Observe que levará alguns segundos para exibir as contagens. Durante esse tempo, o thread de interface do usuário é bloqueado enquanto aguarda recursos solicitados fazer o download. Como resultado, você não pode mover, maximizar, minimizar ou até mesmo fechar a janela de exibição depois de escolher o  **Iniciar** botão. Esses esforços falham até que as contagens de byte começam a aparecer. Se um site não estiver respondendo, você pode ter nenhuma indicação de qual site falhou. É difícil até mesmo pare de esperar e fecha o programa.  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> Para converter GetURLContents em um método assíncrono  
  
1.  Para converter a solução síncrona em uma solução assíncrona, o melhor lugar para começar é em `GetURLContents` porque as chamadas para o <xref:System.Net.HttpWebRequest> método <xref:System.Net.HttpWebRequest.GetResponse%2A> e o <xref:System.IO.Stream> método <xref:System.IO.Stream.CopyTo%2A> são onde o aplicativo acessa a web. O .NET Framework facilita a conversão ao fornecer versões assíncronas dos dois métodos.  
  
     Para obter mais informações sobre os métodos que são usados em `GetURLContents`, consulte <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Quando você seguir as etapas neste passo a passo, vários erros de compilador são exibidas. Você pode ignorá\-las e continuar com o passo a passo.  
  
     Alterar o método é chamado na terceira linha da `GetURLContents` de `GetResponse` assíncrono, baseado em tarefa <xref:System.Net.WebRequest.GetResponseAsync%2A> método.  
  
    ```c#  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  `GetResponseAsync` Retorna um <xref:System.Threading.Tasks.Task%601>. Nesse caso, o *variável de retorno de tarefa*, `TResult`, tem o tipo <xref:System.Net.WebResponse>. A tarefa é uma promessa de produzir um verdadeiro `WebResponse` depois que os dados solicitados foi baixados e a tarefa foi executada até a conclusão do objeto.  
  
     Para recuperar o `WebResponse` o valor da tarefa, aplique um [await](../../../../csharp/language-reference/keywords/await.md) operador da chamada `GetResponseAsync`, como mostra o código a seguir.  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
     O `await` operador suspende a execução do método atual, `GetURLContents`, até que a tarefa aguardada seja concluída. Enquanto isso, o controle retorna para o chamador do método atual. Neste exemplo, o método atual é `GetURLContents`, e o chamador é `SumPageSizes`. Quando a tarefa é concluída, o prometido `WebResponse` objeto é produzido como o valor da tarefa awaited e atribuído à variável `response`.  
  
     A instrução anterior pode ser separada em duas instruções a seguir para esclarecer o que acontece.  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
     A chamada para `webReq.GetResponseAsync` retorna um `Task(Of WebResponse)` ou `Task<WebResponse>`. Em seguida, um operador de espera é aplicado à tarefa para recuperar o `WebResponse` valor.  
  
     Se seu método assíncrono tem trabalho a fazer que não depende da conclusão da tarefa, o método pode continuar com esse trabalho entre essas duas instruções após a chamada para o método assíncrono e antes do `await` operador é aplicado. Para obter exemplos, consulte [Como: fazer várias solicitações da Web em paralelo usando async e await \(c\#\)](../Topic/How%20to:%20Make%20Multiple%20Web%20Requests%20in%20Parallel%20by%20Using%20async%20and%20await%20\(C%23\).md) e [Como: estender o async passo a passo pelo usando WhenAll \(c\#\)](../Topic/How%20to:%20Extend%20the%20async%20Walkthrough%20by%20Using%20Task.WhenAll%20\(C%23\).md).  
  
3.  Como você adicionou o `await` operador na etapa anterior, um erro do compilador ocorre. O operador pode ser usado apenas nos métodos que são marcados com o [async](../../../../visual-basic/language-reference/modifiers/async.md) modificador. Ignorar o erro enquanto você repetir as etapas de conversão para substituir a chamada para `CopyTo` com uma chamada para `CopyToAsync`.  
  
    -   Alterar o nome do método que é chamado para <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   O `CopyTo` ou `CopyToAsync` método copia bytes para o argumento `content`, e não retorna um valor significativo. Na versão síncrona, a chamada para `CopyTo` é uma simple instrução que não retorna um valor. A versão assíncrona, `CopyToAsync`, retorna um <xref:System.Threading.Tasks.Task>. A tarefa funciona como "Task\(void\)" e permite que o método a ser aguardado. Aplicar `Await` ou `await` para a chamada para `CopyToAsync`, como mostra o código a seguir.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
         A instrução anterior abrevia as duas linhas de código a seguir.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
4.  Tudo o que resta a ser feito em `GetURLContents` é ajustar a assinatura do método. Você pode usar o `await` operador apenas nos métodos que são marcados com o [async](../../../../visual-basic/language-reference/modifiers/async.md) modificador. Adicione o modificador para marcar o método como um *método assíncrono*, como mostra o código a seguir.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
5.  O tipo de retorno de um método assíncrono só pode ser <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, ou `void` em c\#. Normalmente, um tipo de retorno de `void` é usado somente em um manipulador de eventos assíncronos, onde `void` é necessária. Em outros casos, você usa `Task(T)` se o método concluído tiver um [retornar](../../../../csharp/language-reference/keywords/return.md) instrução que retorna um valor do tipo T, e você usar `Task` se o método concluído não retorna um valor significativo. Você pode pensar a `Task` retornar o tipo como significando "Task\(void\)".  
  
     Para obter mais informações, consulte [Tipos de retorno assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
     Método `GetURLContents` possui uma instrução de retorno, e a instrução retorna uma matriz de bytes. Portanto, o tipo de retorno da versão async é Task\(T\), onde T é uma matriz de bytes. Faça as seguintes alterações na assinatura do método:  
  
    -   Alterar o tipo de retorno para `Task<byte[]>`.  
  
    -   Por convenção, os métodos assíncronos têm nomes que terminam em "Async", então renomear o método `GetURLContentsAsync`.  
  
     O código a seguir mostra essas alterações.  
  
    ```c#  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     Com essas poucas alterações, a conversão de `GetURLContents` para um método assíncrono é concluído.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> Para converter SumPageSizes em um método assíncrono  
  
1.  Repita as etapas do procedimento anterior para `SumPageSizes`. Primeiro, altere a chamada a `GetURLContents` para uma chamada assíncrona.  
  
    -   Alterar o nome do método que é chamado de `GetURLContents` para `GetURLContentsAsync`, se você ainda não fez isso.  
  
    -   Aplicar `await` à tarefa que `GetURLContentsAsync` retorna o byte de obter o valor de matriz.  
  
     O código a seguir mostra essas alterações.  
  
    ```c#  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     A atribuição anterior abrevia as duas linhas de código a seguir.  
  
    ```c#  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  Faça as seguintes alterações na assinatura do método:  
  
    -   Marcar o método com o `async` modificador.  
  
    -   Adicione "Async" para o nome do método.  
  
    -   Não há nenhuma variável de retorno de tarefa, T, neste momento porque `SumPageSizesAsync` não retorna um valor de T. \(O método não tem `return` instrução.\) No entanto, o método deve retornar um `Task` para awaitable. Portanto, alterar o tipo de retorno do método de `void` para `Task`.  
  
     O código a seguir mostra essas alterações.  
  
    ```c#  
    private async Task SumPageSizesAsync()  
    ```  
  
     A conversão de `SumPageSizes` para `SumPageSizesAsync` for concluída.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> Para converter startButton\_Click em um método assíncrono  
  
1.  No manipulador de eventos, altere o nome do método chamado de `SumPageSizes` para `SumPageSizesAsync`, se você ainda não fez isso.  
  
2.  Porque `SumPageSizesAsync` é um método assíncrono, altere o código no manipulador de eventos para aguardar o resultado.  
  
     A chamada para `SumPageSizesAsync` espelha a chamada para `CopyToAsync` em `GetURLContentsAsync`. A chamada retorna um `Task`, e não um `Task(T)`.  
  
     Como em procedimentos anteriores, você pode converter a chamada por meio de uma instrução ou duas instruções. O código a seguir mostra essas alterações.  
  
    ```c#  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  Para evitar que acidentalmente redigitando a operação, adicione a seguinte instrução na parte superior do `startButton_Click` para desabilitar o **Iniciar** botão.  
  
    ```c#  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     Você pode reabilitar o botão no final do manipulador de eventos.  
  
    ```c#  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     Para obter mais informações sobre reentrância, consulte [Tratando a reentrada em aplicativos assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Finalmente, adicione o `async` modificador à declaração de modo que o manipulador de eventos pode esperar `SumPagSizesAsync`.  
  
    ```c#  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     Normalmente, os nomes de manipuladores de eventos não são alterados. O tipo de retorno não é alterado para `Task` como manipuladores de eventos devem retornar `void`.  
  
     A conversão do projeto de processamento síncrono para assíncrono é concluída.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> Para testar a solução assíncrona  
  
1.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **Iniciar** botão.  
  
2.  A saída que é semelhante à saída da solução síncrona deve aparecer. No entanto, observe as seguintes diferenças.  
  
    -   Os resultados não ocorrem ao mesmo tempo, após o processamento é concluído. Por exemplo, os dois programas contêm uma linha no `startButton_Click` que desmarca a caixa de texto. A intenção é desmarcar a caixa de texto entre as execuções, se você escolher o **Iniciar** botão pela segunda vez, depois que um conjunto de resultados apareceu. Na versão síncrona, a caixa de texto é limpo antes que as contagens são exibidos pela segunda vez, quando os downloads são concluídos e o thread da interface do usuário está livre para executar outras tarefas. A versão assíncrona, a caixa de texto limpa imediatamente depois que você escolher o **Iniciar** botão.  
  
    -   Mais importante, o thread de interface do usuário não é bloqueado durante os downloads. Você pode mover ou redimensionar a janela enquanto os recursos da web estão sendo baixados, contados e exibido. Se um dos sites está lento ou não responder, você pode cancelar a operação, escolhendo o **Fechar** botão \(o x no campo vermelho no canto superior direito\).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> Para substituir o método GetURLContentsAsync com um método do .NET Framework  
  
1.  O .NET Framework 4.5 fornece vários métodos assíncronos que você pode usar. Um deles, o <xref:System.Net.Http.HttpClient> método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, exatamente o que você precisa para este passo a passo. Você pode usá\-lo em vez do `GetURLContentsAsync` método que você criou em um procedimento anterior.  
  
     A primeira etapa é criar um `HttpClient` objeto no método `SumPageSizesAsync`. Adicione a seguinte declaração no início do método.  
  
    ```c#  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  Em `SumPageSizesAsync,` Substitua a chamada para o `GetURLContentsAsync` método com uma chamada para o `HttpClient` método.  
  
    ```  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  Remova ou comente o `GetURLContentsAsync` método que você escreveu.  
  
4.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **Iniciar** botão.  
  
     O comportamento desta versão do projeto deve corresponder ao comportamento que descreve o procedimento "para testar a solução assíncrona" mas com o mesmo menos esforço do que você.  
  
##  <a name="BKMK_CompleteCodeExamples"></a> Exemplo  
 O código a seguir contém o exemplo completo de conversão de um síncrono para uma solução assíncrona usando assíncrona `GetURLContentsAsync` método que você escreveu. Observe que ele fortemente se assemelha a solução síncrona original.  
  
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
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/en-us/library/hh290136.aspx",  
                "http://msdn.microsoft.com/en-us/library/ee256749.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290138.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290140.aspx",  
                "http://msdn.microsoft.com/en-us/library/dd470362.aspx",  
                "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
                "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
                "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 O código a seguir contém o exemplo completo da solução que usa o `HttpClient` método `GetByteArrayAsync`.  
  
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
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/en-us/library/hh290136.aspx",  
                "http://msdn.microsoft.com/en-us/library/ee256749.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290138.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290140.aspx",  
                "http://msdn.microsoft.com/en-us/library/dd470362.aspx",  
                "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
                "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
                "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## Consulte também  
 [Exemplo de assincronia: Acessando o passo a passo da Web \(c\# e Visual Basic\)](http://go.microsoft.com/fwlink/?LinkId=255191)   
 [async](../../../../visual-basic/language-reference/modifiers/async.md)   
 [await](../../../../csharp/language-reference/keywords/await.md)   
 [Programação assíncrona com async e await \(c\#\)](../../../../csharp/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)   
 [Tipos de retorno assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)   
 [Programação assíncrona baseado em tarefa \(TAP\)](http://go.microsoft.com/fwlink/?LinkId=204847)   
 [Como: estender o async passo a passo pelo usando WhenAll \(c\#\)](../Topic/How%20to:%20Extend%20the%20async%20Walkthrough%20by%20Using%20Task.WhenAll%20\(C%23\).md)   
 [Como: fazer várias solicitações da Web em paralelo usando async e await \(c\#\)](../Topic/How%20to:%20Make%20Multiple%20Web%20Requests%20in%20Parallel%20by%20Using%20async%20and%20await%20\(C%23\).md)