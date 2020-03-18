---
title: 'Como: Escrever caracteres em uma seqüência'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160268"
---
# <a name="how-to-write-characters-to-a-string"></a>Como: Escrever caracteres em uma seqüência
Os exemplos de código a seguir gravam caracteres de forma síncrona ou assíncrona de uma matriz de caracteres em uma cadeia de caracteres.  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>Exemplo: Escreva caracteres sincronizadamente em um aplicativo de console  
 O exemplo a seguir usa um <xref:System.IO.StringWriter> para gravar cinco caracteres de forma síncrona em um objeto <xref:System.Text.StringBuilder>.
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>Exemplo: Escreva caracteres assíncronamente em um aplicativo WPF
 O próximo exemplo é o código por trás de um aplicativo WPF. Na carga de janela, o exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz. Em seguida, ele grava cada letra ou caractere de espaço em branco de forma assíncrona em uma linha separada de um controle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)  
- [I/O do arquivo assíncrono](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Como: Enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Como: Ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Como: Abrir e anexar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Como: Ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Como: Escrever texto para um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Como: Ler caracteres de uma seqüência](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
