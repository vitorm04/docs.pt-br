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
# <a name="how-to-write-text-to-a-file"></a>Como gravar texto em um arquivo
Este tópico mostra diferentes maneiras você pode escrever texto em um arquivo para aplicativos do .NET Framework ou [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos. As seguintes classes e métodos normalmente são usados para gravar texto em um arquivo:  
  
-   <xref:System.IO.StreamWriter>-contém métodos para gravar um arquivo de forma síncrona (<xref:System.IO.StreamWriter.Write%2A> ou <xref:System.IO.TextWriter.WriteLine%2A>) ou assíncrona (<xref:System.IO.StreamWriter.WriteAsync%2A> e <xref:System.IO.StreamWriter.WriteLineAsync%2A>).  
  
-   <xref:System.IO.File>– a ser usado com aplicativos do .NET Framework. Fornece métodos estáticos para gravar texto em um arquivo, como <xref:System.IO.File.WriteAllLines%2A> e <xref:System.IO.File.WriteAllText%2A>, ou para acrescentar o texto em um arquivo (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> ou <xref:System.IO.File.AppendText%2A>).  
  
-   [FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - a ser usado com [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativos. Contém métodos assíncronos para gravar texto em um arquivo ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) ou [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) ou acrescentar o texto em um arquivo ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) ou [ AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).  
  
 Os exemplos foram mantidos simples para se concentrar na tarefa que está sendo executada. Por esse motivo, os exemplos executam verificação de erro mínimo e a manipulação de exceção, se houver. Um aplicativo do mundo real geralmente fornece verificação de erros mais robusta e manipulação de exceção.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como sincronicamente gravar texto em um novo arquivo usando o <xref:System.IO.StreamWriter> de classe, uma linha por vez. O novo arquivo de texto é salvo para a pasta Meus documentos do usuário. Porque o <xref:System.IO.StreamWriter> o objeto é declarado e instanciado em um `using` instrução, o <xref:System.IO.StreamWriter.Dispose%2A> método é invocado automaticamente libera e fecha o fluxo.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como acrescentar o texto para um arquivo existente usando o <xref:System.IO.StreamWriter> classe. Ele usa o mesmo arquivo de texto do exemplo anterior.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como gravar texto de maneira assíncrona em um novo arquivo usando o <xref:System.IO.StreamWriter> classe. Para invocar o <xref:System.IO.StreamWriter.WriteAsync%2A> método, a chamada do método precisa estar dentro de um `async` método. O novo arquivo de texto é salvo para a pasta Meus documentos do usuário.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como gravar texto em um novo arquivo e acrescentar novas linhas de texto para o mesmo arquivo usando o <xref:System.IO.File> classe. O <xref:System.IO.File.WriteAllText%2A> e <xref:System.IO.File.AppendAllLines%2A> métodos abrir e fechar o arquivo automaticamente. Se o caminho que você fornecer para o <xref:System.IO.File.WriteAllText%2A> método já existe, o arquivo será substituído.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como gravar de maneira assíncrona entradas do usuário para um arquivo de texto em um aplicativo [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Devido a considerações de segurança, abertura de um arquivo de um [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplicativo normalmente requer o uso de um [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) controle. Neste exemplo, o `FileOpenPicker` é filtrado para mostrar arquivos de texto.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [Como enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Como ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Como abrir e acrescentar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Como ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
