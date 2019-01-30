---
title: 'Como: Ler texto de um arquivo'
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f667b0a757a676788b693691504512dfc227a7e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646666"
---
# <a name="how-to-read-text-from-a-file"></a>Como: Ler texto de um arquivo
Os exemplos a seguir mostram como ler de forma síncrona e assíncrona o texto de um arquivo de texto usando o .NET para aplicativos de área de trabalho. Nos dois exemplos, ao criar uma instância da classe <xref:System.IO.StreamReader>, você fornece o caminho relativo ou absoluto para o arquivo. Os exemplos a seguir supõem que o arquivo denominado TestFile.txt está na mesma pasta que o aplicativo.  
  
 Esses exemplos de código não se aplicam ao desenvolvimento para Aplicativos da Windows Store porque o Windows Runtime fornece tipos diferentes de fluxos para ler e gravar em arquivos. Para obter um exemplo que mostra como ler texto de um arquivo em um aplicativo da Windows Store, confira [Início Rápido: Lendo e gravando arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Para obter exemplos que mostram como fazer a conversão entre fluxos do .NET Framework e fluxos do Windows Runtime, confira [Como: Fazer a conversão entre fluxos do .NET Framework e fluxos do Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## <a name="example"></a>Exemplo  
 O primeiro exemplo mostra uma operação de leitura síncrona em um aplicativo de console. Neste exemplo, o arquivo de texto é aberto usando um leitor de fluxo, o conteúdo é copiado para uma cadeia de caracteres e a cadeia de caracteres é enviada para o console.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma operação de leitura assíncrona em um aplicativo do WPF (Windows Presentation Foundation).  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO.StreamReader>
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- [E/S de arquivo assíncrona](../../../docs/standard/io/asynchronous-file-i-o.md)
- [NIB: Como: Criar uma listagem de diretório](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [Início Rápido: Lendo e gravando arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)
- [Como: Fazer a conversão entre fluxos do .NET Framework e fluxos do Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
- [Como: Ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Como: Abrir um arquivo de log e fazer acréscimos a ele](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Como: Gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [Como: Ler caracteres de uma cadeia de caracteres](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
- [Como: Gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
