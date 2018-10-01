---
title: Como ler texto de um arquivo
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
ms.openlocfilehash: 8f979f3d09079f36d12408d0a82ef58e603da859
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47203171"
---
# <a name="how-to-read-text-from-a-file"></a>Como ler texto de um arquivo
Os exemplos a seguir mostram como ler de forma síncrona e assíncrona o texto de um arquivo de texto usando o .NET para aplicativos de área de trabalho. Nos dois exemplos, ao criar uma instância da classe <xref:System.IO.StreamReader>, você fornece o caminho relativo ou absoluto para o arquivo. Os exemplos a seguir supõem que o arquivo denominado TestFile.txt está na mesma pasta que o aplicativo.  
  
 Esses exemplos de código não se aplicam ao desenvolvimento para Aplicativos da Windows Store porque o Windows Runtime fornece tipos diferentes de fluxos para ler e gravar em arquivos. Para obter um exemplo que mostra como ler o texto de um arquivo em um aplicativo da Windows Store, veja [Início rápido: ler e gravar arquivos](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)). Para obter exemplos que mostram como converter entre fluxos do .NET Framework e fluxos do Windows Runtime, veja [Como converter entre fluxos do .NET Framework e do Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
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
- [NIB: Como criar uma listagem de diretório](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [Início rápido: ler e gravar arquivos](https://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
- [Como converter entre fluxos do .NET Framework e do Tempo de Execução do Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [Como ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Como abrir e acrescentar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Como gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Como ler caracteres de uma cadeia de caracteres](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Como gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
