---
title: "Usando o Async para acesso a arquivos (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Usando o Async para acesso a arquivos (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode usar o recurso async para acessar arquivos. Usando o recurso async, você pode chamar métodos assíncronos sem usar retornos de chamada ou dividir seu código em vários métodos ou expressões lambda. Para tornar síncrono um código assíncrono, basta chamar um método assíncrono em vez de um método síncrono e adicione algumas palavras\-chave no código.  
  
 Você pode considerar os motivos para a adição de assincronia para chamadas de acesso do arquivo:  
  
-   Assincronia torna os aplicativos de interface do usuário mais responsiva porque o thread de interface do usuário que inicia a operação pode executar outro trabalho. Se o thread de interface do usuário deve executar o código que leva muito tempo \(por exemplo, mais de 50 milissegundos\), a interface do usuário pode congelar até que a e\/s é concluída e o thread da interface do usuário pode processar teclado e entrados e outros eventos de mouse novamente.  
  
-   A assincronia melhora a escalabilidade do ASP.NET e outros aplicativos baseados em servidor, reduzindo a necessidade de threads. Se o aplicativo usa um thread dedicado por resposta e mil solicitações são tratadas simultaneamente, mil threads são necessários. Operações assíncronas normalmente não precisam usar um thread durante a espera. Eles usam o thread de conclusão de e\/s existente brevemente no final.  
  
-   A latência de uma operação de acesso de arquivo pode ser muito baixa em condições atuais, mas a latência pode aumentar consideravelmente no futuro. Por exemplo, um arquivo pode ser movido para um servidor que esteja em todo o mundo.  
  
-   A sobrecarga de usar o recurso Async é pequena.  
  
-   Tarefas assíncronas facilmente podem ser executadas em paralelo.  
  
## Executando os exemplos  
 Para executar os exemplos neste tópico, você pode criar um **aplicativo WPF** ou um **Windows Forms Application** e, em seguida, adicione um **botão**. O botão `Click` evento, adicione uma chamada para o primeiro método em cada exemplo.  
  
 Nos exemplos a seguir, incluem o seguinte `using` instruções.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## Uso da classe FileStream  
 Os exemplos neste tópico usam o <xref:System.IO.FileStream> classe, que tem uma opção que faz com que a e\/s assíncrona ocorrer no nível do sistema operacional. Usando essa opção, você pode evitar o bloqueio de um thread de ThreadPool em muitos casos. Para habilitar essa opção, você deve especificar o `useAsync=true` ou `options=FileOptions.Asynchronous` argumento na chamada do construtor.  
  
 Você não pode usar essa opção com <xref:System.IO.StreamReader> e <xref:System.IO.StreamWriter> se você abri\-los diretamente, especificando um caminho de arquivo. No entanto, você pode usar essa opção se você fornecer um <xref:System.IO.Stream> que o <xref:System.IO.FileStream> classe aberto. Observe que chamadas assíncronas são mais rápidas em aplicativos de interface do usuário mesmo se um thread de ThreadPool é bloqueado, pois o thread de interface do usuário não é bloqueado durante a espera.  
  
## Escrevendo texto  
 O exemplo a seguir grava um arquivo de texto. Cada instrução de espera, o método sai imediatamente. Quando o arquivo de e\/s for concluído, o método continua a instrução que segue a instrução de espera. Observe que o modificador async é a definição de métodos que usam a instrução de espera.  
  
```c#  
public async void ProcessWrite()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 O exemplo original tem a instrução `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, que é uma contração das duas instruções a seguir:  
  
```c#  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 A primeira instrução retorna uma tarefa e faz com que o processamento de arquivos iniciar. A segunda instrução com o await faz com que o método sair imediatamente e retornar uma tarefa diferente. Ao concluir o processamento posterior de arquivos, execução retornará para a instrução que segue a espera. Para obter mais informações, consulte  [Fluxo de controle em programas assíncronos \(c\#\)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## Lendo texto  
 O exemplo a seguir lê o texto de um arquivo. O texto é armazenada em buffer e, nesse caso, é colocado em um <xref:System.Text.StringBuilder>. Diferentemente do exemplo anterior, a avaliação de esperar o produz um valor. O <xref:System.IO.Stream.ReadAsync%2A> método retorna um <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>\>, portanto, a avaliação de await produz uma `Int32` valor \(`numRead`\) após a conclusão da operação. Para obter mais informações, consulte [Tipos de retorno assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
```c#  
public async void ProcessRead()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## E\/s assíncrona paralela  
 O exemplo a seguir demonstra o processamento paralelo escrevendo 10 arquivos de texto. Para cada arquivo, o <xref:System.IO.Stream.WriteAsync%2A> método retorna uma tarefa que é adicionada a uma lista de tarefas. O `await Task.WhenAll(tasks);` instrução sai do método e currículos dentro do método quando o processamento de arquivo é concluída para todas as tarefas.  
  
 O exemplo fecha todos <xref:System.IO.FileStream> instâncias em um `finally` Bloquear depois de concluir as tarefas. Se cada `FileStream` foi criado em uma `using` instrução, o `FileStream` pode ser descartado antes que a tarefa foi concluída.  
  
 Observe que qualquer aumento de desempenho é quase que totalmente do processamento paralelo e não o processamento assíncrono. As vantagens de assincronia são que não bloqueia vários threads, e que não bloqueia o thread de interface do usuário.  
  
```c#  
public async void ProcessWriteMult()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 Ao usar o <xref:System.IO.Stream.WriteAsync%2A> e <xref:System.IO.Stream.ReadAsync%2A> métodos, você pode especificar um <xref:System.Threading.CancellationToken>, que pode ser usada para cancelar o fluxo intermediário da operação. Para obter mais informações, consulte [Ajustando seu aplicativo Async \(c\#\)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) e [Cancelamento em threads gerenciados](../Topic/Cancellation%20in%20Managed%20Threads.md).  
  
## Consulte também  
 [Programação assíncrona com async e await \(c\#\)](../../../../csharp/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)   
 [Tipos de retorno assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)   
 [Fluxo de controle em programas assíncronos \(c\#\)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)