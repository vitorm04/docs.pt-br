---
title: Como gravar texto em um arquivo
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c637d9842c05f47bfcaa0431dd2f9f1ee29cc09
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50181232"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="99f08-102">Como gravar texto em um arquivo</span><span class="sxs-lookup"><span data-stu-id="99f08-102">How to: Write Text to a File</span></span>
<span data-ttu-id="99f08-103">Este tópico mostra diferentes maneiras de gravar texto em um arquivo para aplicativos .NET Framework ou aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99f08-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="99f08-104">As classes e métodos seguintes normalmente são usados para gravar texto em um arquivo:</span><span class="sxs-lookup"><span data-stu-id="99f08-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="99f08-105"><xref:System.IO.StreamWriter> - contém métodos para gravar em um arquivo de forma síncrona (<xref:System.IO.StreamWriter.Write%2A> ou <xref:System.IO.TextWriter.WriteLine%2A>) ou assíncrona (<xref:System.IO.StreamWriter.WriteAsync%2A> e <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="99f08-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="99f08-106"><xref:System.IO.File> – a ser usado com aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="99f08-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="99f08-107">Fornece métodos estáticos para gravar texto em um arquivo, como <xref:System.IO.File.WriteAllLines%2A> e <xref:System.IO.File.WriteAllText%2A>, ou para acrescentar texto em um arquivo (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> ou <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="99f08-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="99f08-108"><xref:Windows.Storage.FileIO> – a ser usado com aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99f08-108"><xref:Windows.Storage.FileIO> - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="99f08-109">Contém métodos assíncronos para gravar texto em um arquivo (<xref:Windows.Storage.FileIO.WriteLinesAsync%2A> ou <xref:Windows.Storage.FileIO.WriteTextAsync%2A>) ou acrescentar texto em um arquivo (<xref:Windows.Storage.FileIO.AppendLinesAsync%2A> ou <xref:Windows.Storage.FileIO.AppendTextAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="99f08-109">It contains asynchronous methods to write text to a file (<xref:Windows.Storage.FileIO.WriteLinesAsync%2A> or <xref:Windows.Storage.FileIO.WriteTextAsync%2A>) or to append text to a file (<xref:Windows.Storage.FileIO.AppendLinesAsync%2A> or <xref:Windows.Storage.FileIO.AppendTextAsync%2A>).</span></span>  

- <span data-ttu-id="99f08-110"><xref:System.IO.Path> – a ser usado em cadeias de caracteres que contêm informações de caminho de arquivo ou de diretório.</span><span class="sxs-lookup"><span data-stu-id="99f08-110"><xref:System.IO.Path> - to be used on strings that contain file or directory path information.</span></span> <span data-ttu-id="99f08-111">Contém o método <xref:System.IO.Path.Combine%2A>, que permite a concatenação de cadeias de caracteres para criar um caminho de arquivo ou de diretório.</span><span class="sxs-lookup"><span data-stu-id="99f08-111">It contains the <xref:System.IO.Path.Combine%2A> method, which allows concatenation of strings to build a file or directory path.</span></span>


 <span data-ttu-id="99f08-112">Os exemplos foram mantidos simples de modo que se possa concentrar na tarefa sendo executada.</span><span class="sxs-lookup"><span data-stu-id="99f08-112">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="99f08-113">Por esse motivo, os exemplos executam a verificação de erros mínima e o tratamento de exceções, se houver.</span><span class="sxs-lookup"><span data-stu-id="99f08-113">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="99f08-114">Um aplicativo do mundo real geralmente fornece uma verificação de erros e um tratamento de exceções mais robustos.</span><span class="sxs-lookup"><span data-stu-id="99f08-114">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99f08-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99f08-115">Example</span></span>  
 <span data-ttu-id="99f08-116">O exemplo a seguir mostra como gravar texto sincronicamente em um novo arquivo usando a classe <xref:System.IO.StreamWriter>, uma linha por vez.</span><span class="sxs-lookup"><span data-stu-id="99f08-116">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="99f08-117">O novo arquivo de texto é salvo na pasta Meus documentos do usuário.</span><span class="sxs-lookup"><span data-stu-id="99f08-117">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="99f08-118">Como o objeto <xref:System.IO.StreamWriter> é declarado e instanciado em uma instrução `using`, o método <xref:System.IO.StreamWriter.Dispose%2A> é invocado, o que libera e fecha o fluxo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="99f08-118">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="99f08-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99f08-119">Example</span></span>  
 <span data-ttu-id="99f08-120">O exemplo a seguir mostra como acrescentar o texto a um arquivo existente usando a classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="99f08-120">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="99f08-121">Ele usa o mesmo arquivo de texto do exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="99f08-121">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="99f08-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99f08-122">Example</span></span>  
 <span data-ttu-id="99f08-123">O exemplo a seguir mostra como gravar texto de maneira assíncrona em um novo arquivo usando a classe <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="99f08-123">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="99f08-124">Para invocar o método <xref:System.IO.StreamWriter.WriteAsync%2A>, a chamada de método precisa estar dentro de um método `async`.</span><span class="sxs-lookup"><span data-stu-id="99f08-124">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="99f08-125">O novo arquivo de texto é salvo na pasta Meus documentos do usuário.</span><span class="sxs-lookup"><span data-stu-id="99f08-125">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="99f08-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99f08-126">Example</span></span>  
 <span data-ttu-id="99f08-127">O exemplo a seguir mostra como gravar texto em um novo arquivo e acrescentar novas linhas de texto ao mesmo arquivo usando a classe <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="99f08-127">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="99f08-128">Os métodos <xref:System.IO.File.WriteAllText%2A> e <xref:System.IO.File.AppendAllLines%2A> abrem e fecham o arquivo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="99f08-128">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="99f08-129">Se o caminho que você fornecer ao método <xref:System.IO.File.WriteAllText%2A> já existir, o arquivo será substituído.</span><span class="sxs-lookup"><span data-stu-id="99f08-129">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="99f08-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99f08-130">Example</span></span>  
 <span data-ttu-id="99f08-131">O exemplo a seguir mostra como gravar de maneira assíncrona entradas do usuário para um arquivo de texto em um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99f08-131">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="99f08-132">Devido a considerações de segurança, abrir um arquivo de um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] normalmente requer o uso de um controle <xref:Windows.Storage.Pickers.FileOpenPicker>.</span><span class="sxs-lookup"><span data-stu-id="99f08-132">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a <xref:Windows.Storage.Pickers.FileOpenPicker> control.</span></span> <span data-ttu-id="99f08-133">Neste exemplo, o `FileOpenPicker` é filtrado para mostrar arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="99f08-133">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99f08-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99f08-134">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.Path>  
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="99f08-135">Como enumerar diretórios e arquivos</span><span class="sxs-lookup"><span data-stu-id="99f08-135">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="99f08-136">Como ler e gravar em um arquivo de dados recém-criado</span><span class="sxs-lookup"><span data-stu-id="99f08-136">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="99f08-137">Como abrir e acrescentar a um arquivo de log</span><span class="sxs-lookup"><span data-stu-id="99f08-137">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="99f08-138">Como ler texto de um arquivo</span><span class="sxs-lookup"><span data-stu-id="99f08-138">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="99f08-139">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="99f08-139">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
