---
title: 'Como: Fazer várias solicitações da Web em paralelo usando async e await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 57c40626fcaf0c52d09fa3a2c8b74ba8b7816677
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600238"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Como: Fazer várias solicitações da Web em paralelo usando async e await (C#)
Em um método assíncrono, as tarefas são iniciadas quando elas são criadas. O operador [await](../../../../csharp/language-reference/keywords/await.md) é aplicado à tarefa no ponto do método em que o processamento não pode continuar até que a tarefa seja concluída. Geralmente, uma tarefa é aguardada assim que ela é criada, como mostrado no exemplo a seguir.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 No entanto, você pode separar a criação da tarefa da espera da tarefa se o programa tiver outro trabalho a realizar, que não depende da conclusão da tarefa.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Entre o início de uma tarefa e a espera por ela, você pode iniciar outras tarefas. As tarefas adicionais são executadas implicitamente em paralelo, mas não são criados threads adicionais.  
  
 O programa a seguir inicia três downloads assíncronos na Web e, em seguida, os aguarda na ordem em que foram chamados. Observe ao executar o programa, que as tarefas nem sempre são concluídas na ordem em que foram criadas e aguardadas. Eles começam a ser executadas quando são criadas e uma ou mais tarefas podem terminar antes que o método alcance as expressões await.  
  
> [!NOTE]
>  Para concluir esse projeto, você precisa ter o Visual Studio 2012 ou posterior e o .NET Framework 4.5 ou posterior instalados no seu computador.  
  
 Para obter outro exemplo que inicia várias tarefas ao mesmo tempo, confira [Como: Estender o passo a passo assíncrono usando Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Você pode baixar o código deste exemplo de [Exemplos de código para desenvolvedores](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Para configurar o projeto  
  
1. Para configurar um aplicativo WPF, complete as etapas a seguir. Encontre instruções detalhadas para essas etapas em [Passo a passo: Acessando a Web usando async e await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Crie um aplicativo WPF que contenha uma caixa de texto e um botão. Dê o nome `startButton` para o botão e `resultsTextBox`, para a caixa de texto.  
  
    - Adicione uma referência para <xref:System.Net.Http>.  
  
    - No arquivo MainWindow.xaml.cs, adicione uma diretiva `using` para `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Para adicionar o código  
  
1. Na janela de design, MainWindow.xaml, clique duas vezes no botão para criar o manipulador de eventos `startButton_Click` no MainWindow.xaml.cs.  
  
2. Copie o seguinte código e cole-o no corpo do `startButton_Click` em MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     O código chama um método assíncrono, `CreateMultipleTasksAsync`, que controla o aplicativo.  
  
3. Adicione os seguintes métodos de suporte ao projeto:  
  
    - O `ProcessURLAsync` usa um método <xref:System.Net.Http.HttpClient> para baixar o conteúdo de um site como uma matriz de bytes. Em seguida, o método de suporte `ProcessURLAsync` exibe e retorna o comprimento da matriz.  
  
    - O `DisplayResults` exibe o número de bytes na matriz de bytes para cada URL. Essa exibição mostra quando cada tarefa termina o download.  
  
     Copie os seguintes métodos e cole-os depois do manipulador de eventos `startButton_Click` em MainWindow.xaml.cs.  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. Finalmente, defina o método `CreateMultipleTasksAsync`, que executa as seguintes etapas.  
  
    - O método declara um objeto `HttpClient`, que você precisa para acessar o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> em `ProcessURLAsync`.  
  
    - O método cria e inicia três tarefas do tipo <xref:System.Threading.Tasks.Task%601>, em que `TResult` é um inteiro. Conforme cada tarefa termina, `DisplayResults` exibe a URL da tarefa e o comprimento do conteúdo baixado. Como as tarefas estão em execução de maneira assíncrona, a ordem na qual os resultados são exibidos pode diferir da ordem na qual elas foram declaradas.  
  
    - O método aguarda a conclusão de cada tarefa. Cada operador `await` suspende a execução de `CreateMultipleTasksAsync` até que a tarefa aguardada seja concluída. O operador também recupera o valor retornado da chamada ao `ProcessURLAsync` de cada tarefa concluída.  
  
    - Quando as tarefas forem concluídas e os valores inteiros forem recuperados, o método somará os comprimentos dos sites e exibirá o resultado.  
  
     Copie o seguinte método e cole-o em sua solução.  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults   
        // displays its length.  
        Task<int> download1 =   
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.  
  
     Execute o programa várias vezes para ver que as três tarefas nem sempre são concluídas na mesma ordem e que a ordem em que elas são concluídas não é, necessariamente, a ordem em que elas foram criadas e aguardadas.  
  
## <a name="example"></a>Exemplo  
 O código a seguir contem o exemplo completo.  
  
```csharp  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
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
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults   
            // displays its length.  
            Task<int> download1 =   
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Passo a passo: acesso à Web com o uso de Async e Await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programação assíncrona com async e await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Como: estender o passo a passo Async usando Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
