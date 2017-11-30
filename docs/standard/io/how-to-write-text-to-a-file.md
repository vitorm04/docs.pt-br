---
title: Como gravar texto em um arquivo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9605e514be380415d3c8b66ed28ae7de0a52ca1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="7adfe-102">Como gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="7adfe-102">How to: Write Text to a File</span></span>
<span data-ttu-id="7adfe-103">Este tópico mostra diferentes maneiras você pode escrever texto em um arquivo para aplicativos do .NET Framework ou [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7adfe-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="7adfe-104">As seguintes classes e métodos normalmente são usados para gravar texto em um arquivo:</span><span class="sxs-lookup"><span data-stu-id="7adfe-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="7adfe-105"><xref:System.IO.StreamWriter>-contém métodos para gravar um arquivo de forma síncrona (<xref:System.IO.StreamWriter.Write%2A> ou <xref:System.IO.TextWriter.WriteLine%2A>) ou assíncrona (<xref:System.IO.StreamWriter.WriteAsync%2A> e <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="7adfe-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="7adfe-106"><xref:System.IO.File>– a ser usado com aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7adfe-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="7adfe-107">Fornece métodos estáticos para gravar texto em um arquivo, como <xref:System.IO.File.WriteAllLines%2A> e <xref:System.IO.File.WriteAllText%2A>, ou para acrescentar o texto em um arquivo (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> ou <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="7adfe-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="7adfe-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - a ser usado com [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="7adfe-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="7adfe-109">Contém métodos assíncronos para gravar texto em um arquivo ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) ou [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) ou acrescentar o texto em um arquivo ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) ou [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span><span class="sxs-lookup"><span data-stu-id="7adfe-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  
  
 <span data-ttu-id="7adfe-110">Os exemplos foram mantidos simples para se concentrar na tarefa que está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="7adfe-110">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="7adfe-111">Por esse motivo, os exemplos executam verificação de erro mínimo e a manipulação de exceção, se houver.</span><span class="sxs-lookup"><span data-stu-id="7adfe-111">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="7adfe-112">Um aplicativo do mundo real geralmente fornece verificação de erros mais robusta e manipulação de exceção.</span><span class="sxs-lookup"><span data-stu-id="7adfe-112">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7adfe-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7adfe-113">Example</span></span>  
 <span data-ttu-id="7adfe-114">O exemplo a seguir mostra como sincronicamente gravar texto em um novo arquivo usando o <xref:System.IO.StreamWriter> de classe, uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="7adfe-114">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="7adfe-115">O novo arquivo de texto é salvo para a pasta Meus documentos do usuário.</span><span class="sxs-lookup"><span data-stu-id="7adfe-115">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="7adfe-116">Porque o <xref:System.IO.StreamWriter> o objeto é declarado e instanciado em um `using` instrução, o <xref:System.IO.StreamWriter.Dispose%2A> método é invocado automaticamente libera e fecha o fluxo.</span><span class="sxs-lookup"><span data-stu-id="7adfe-116">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="7adfe-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7adfe-117">Example</span></span>  
 <span data-ttu-id="7adfe-118">O exemplo a seguir mostra como acrescentar o texto para um arquivo existente usando o <xref:System.IO.StreamWriter> classe.</span><span class="sxs-lookup"><span data-stu-id="7adfe-118">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="7adfe-119">Ele usa o mesmo arquivo de texto do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="7adfe-119">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="7adfe-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7adfe-120">Example</span></span>  
 <span data-ttu-id="7adfe-121">O exemplo a seguir mostra como gravar texto de maneira assíncrona em um novo arquivo usando o <xref:System.IO.StreamWriter> classe.</span><span class="sxs-lookup"><span data-stu-id="7adfe-121">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="7adfe-122">Para invocar o <xref:System.IO.StreamWriter.WriteAsync%2A> método, a chamada do método precisa estar dentro de um `async` método.</span><span class="sxs-lookup"><span data-stu-id="7adfe-122">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="7adfe-123">O novo arquivo de texto é salvo para a pasta Meus documentos do usuário.</span><span class="sxs-lookup"><span data-stu-id="7adfe-123">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="7adfe-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7adfe-124">Example</span></span>  
 <span data-ttu-id="7adfe-125">O exemplo a seguir mostra como gravar texto em um novo arquivo e acrescentar novas linhas de texto para o mesmo arquivo usando o <xref:System.IO.File> classe.</span><span class="sxs-lookup"><span data-stu-id="7adfe-125">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="7adfe-126">O <xref:System.IO.File.WriteAllText%2A> e <xref:System.IO.File.AppendAllLines%2A> métodos abrir e fechar o arquivo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7adfe-126">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="7adfe-127">Se o caminho que você fornecer para o <xref:System.IO.File.WriteAllText%2A> método já existe, o arquivo será substituído.</span><span class="sxs-lookup"><span data-stu-id="7adfe-127">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="7adfe-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7adfe-128">Example</span></span>  
 <span data-ttu-id="7adfe-129">O exemplo a seguir mostra como gravar de maneira assíncrona entradas do usuário para um arquivo de texto em um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7adfe-129">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="7adfe-130">Devido a considerações de segurança, abertura de um arquivo de um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo normalmente requer o uso de um [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) controle.</span><span class="sxs-lookup"><span data-stu-id="7adfe-130">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="7adfe-131">Neste exemplo, o `FileOpenPicker` é filtrado para mostrar arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="7adfe-131">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a><span data-ttu-id="7adfe-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7adfe-132">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7adfe-133">Como enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="7adfe-133">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="7adfe-134">Como ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="7adfe-134">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="7adfe-135">Como abrir e acrescentar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="7adfe-135">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="7adfe-136">Como ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="7adfe-136">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="7adfe-137">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="7adfe-137">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
