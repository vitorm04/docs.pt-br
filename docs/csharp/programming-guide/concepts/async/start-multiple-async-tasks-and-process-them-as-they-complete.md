---
title: "Iniciar v&#225;rias tarefas ass&#237;ncronas e process&#225;-las na conclus&#227;o (c#) | Microsoft Docs"
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
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Iniciar v&#225;rias tarefas ass&#237;ncronas e process&#225;-las na conclus&#227;o (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Usando <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, você pode iniciar várias tarefas ao mesmo tempo e processá\-los individualmente eles estiverem concluídos, em vez de processá\-los na ordem em que eles são iniciados.  
  
 O exemplo a seguir usa uma consulta para criar uma coleção de tarefas. Cada tarefa baixa o conteúdo de um site específico. Em cada iteração de um pouco de loop, uma chamada aguardada para `WhenAny` retorna a tarefa na coleção de tarefas que conclui o download primeiro. Essa tarefa é removida da coleção e processada. O loop é repetido até que a coleção não contém mais tarefas.  
  
> [!NOTE]
>  Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
## Baixando o exemplo  
 Você pode baixar o projeto completo do Windows Presentation Foundation \(WPF\) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.  
  
1.  Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **Abrir**, **projeto\/solução**.  
  
3.  No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução \(. sln\) para AsyncFineTuningCS.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **ProcessTasksAsTheyFinish** do projeto e escolha **Set as StartUp Project**.  
  
5.  Escolha a tecla F5 para executar o projeto.  
  
     Escolha as teclas Ctrl \+ F5 para executar o projeto sem depurá\-lo.  
  
6.  Execute o projeto várias vezes para verificar se os comprimentos baixados sempre não aparecem na mesma ordem.  
  
 Se você não quiser baixar o projeto, você pode examinar o arquivo MainWindow.xaml.cs no final deste tópico.  
  
## Compilando o exemplo  
 Este exemplo adiciona o código desenvolvido em [Cancelar as demais tarefas assíncronas depois que uma for concluída \(c\#\)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída](../Topic/Cancel%20Remaining%20Async%20Tasks%20after%20One%20Is%20Complete%20\(C%23%20and%20Visual%20Basic\).md) e usa a mesma interface do usuário.  
  
 Para criar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **CancelAfterOneTask** como o **projeto de inicialização**. Adicione as alterações neste tópico para o `AccessTheWebAsync` método nesse projeto. As alterações são marcadas com asteriscos.  
  
 O **CancelAfterOneTask** projeto já inclui uma consulta que, quando executado, cria uma coleção de tarefas. Cada chamada para `ProcessURLAsync` no código a seguir retorna um <xref:System.Threading.Tasks.Task%601> onde `TResult` é um inteiro.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 No arquivo de MainWindow.xaml.cs do projeto, faça as seguintes alterações para o `AccessTheWebAsync` método.  
  
-   Execute a consulta aplicando <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> em vez de <xref:System.Linq.Enumerable.ToArray%2A>.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
-   Adicionar um while loop que executa as seguintes etapas para cada tarefa na coleção.  
  
    1.  Espera de uma chamada para `WhenAny` para identificar a primeira tarefa na coleção para concluir o download.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
    2.  Remove essa tarefa da coleção.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
    3.  Espera de `firstFinishedTask`, que é retornado por uma chamada para `ProcessURLAsync`. O `firstFinishedTask` variável é um <xref:System.Threading.Tasks.Task%601> onde `TReturn` é um inteiro. A tarefa já foi concluída, mas você espera para recuperar o tamanho do site baixado, como mostra o exemplo a seguir.  
  
        ```c#  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        VBCopy Code  
        Dim length = Await firstFinishedTask  
        ```  
  
 Você deve executar o projeto várias vezes para verificar se os comprimentos baixados sempre não aparecem na mesma ordem.  
  
> [!CAUTION]
>  Você pode usar `WhenAny` em um loop, conforme descrito no exemplo, para resolver problemas que envolvem um pequeno número de tarefas. No entanto, outras abordagens são mais eficientes se você tiver um grande número de tarefas para processar. Para obter mais informações e exemplos, consulte [tarefas de processamento como eles completa](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
## Exemplo completo  
 O código a seguir é o texto completo do arquivo MainWindow.xaml.cs para o exemplo. Asteriscos marcam os elementos que foram adicionados para esse exemplo.  
  
 Observe que você deve adicionar uma referência para <xref:System.Net.Http>.  
  
 Você pode baixar o projeto de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
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
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive.  
using System.Threading;  
  
namespace ProcessTasksAsTheyFinish  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;  
        }  
  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURL(url, client, ct);  
  
            // ***Use ToList to execute the query and start the tasks.   
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
  
            // ***Add a loop to process the tasks one at a time until none remain.  
            while (downloadTasks.Count > 0)  
            {  
                    // Identify the first task that completes.  
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
                    // ***Remove the selected task from the list so that you don't  
                    // process it more than once.  
                    downloadTasks.Remove(firstFinishedTask);  
  
                    // Await the completed task.  
                    int length = await firstFinishedTask;  
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290136.aspx",  
                "http://msdn.microsoft.com/en-us/library/dd470362.aspx",  
                "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
                "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
                "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
    }  
}  
  
// Sample Output:  
  
// Length of the download:  226093  
// Length of the download:  412588  
// Length of the download:  175490  
// Length of the download:  204890  
// Length of the download:  158855  
// Length of the download:  145790  
// Length of the download:  44908  
// Downloads complete.  
```  
  
## Consulte também  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [Ajustando seu aplicativo Async \(c\#\)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Programação assíncrona com async e await \(c\#\)](../../../../csharp/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)   
 [Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046)