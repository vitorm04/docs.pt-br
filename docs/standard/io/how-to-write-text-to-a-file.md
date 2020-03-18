---
title: 'Como: Escrever texto para um arquivo'
ms.date: 01/04/2019
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
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160242"
---
# <a name="how-to-write-text-to-a-file"></a>Como: Escrever texto para um arquivo
Este tópico mostra diferentes maneiras de gravar um texto em um arquivo para um aplicativo .NET.

As classes e métodos seguintes normalmente são usados para gravar texto em um arquivo:  
  
- <xref:System.IO.StreamWriter> contém métodos para gravação síncrona (<xref:System.IO.StreamWriter.Write%2A> ou <xref:System.IO.TextWriter.WriteLine%2A>) ou assíncrona (<xref:System.IO.StreamWriter.WriteAsync%2A> e <xref:System.IO.StreamWriter.WriteLineAsync%2A>) em um arquivo.  
  
- <xref:System.IO.File> fornece métodos estáticos para gravar um texto em um arquivo, como <xref:System.IO.File.WriteAllLines%2A> e <xref:System.IO.File.WriteAllText%2A>, ou para acrescentar um texto a um arquivo, como <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> e <xref:System.IO.File.AppendText%2A>.  
  
- <xref:System.IO.Path> destina-se a cadeias de caracteres que contêm informações de caminho de arquivo ou diretório. Ele contém o método <xref:System.IO.Path.Combine%2A> e, no .NET Core 2.1 e posterior, os métodos <xref:System.IO.Path.Join%2A> e <xref:System.IO.Path.TryJoin%2A>, que permitem que a concatenação de cadeias de caracteres crie um caminho de arquivo ou diretório.

> [!NOTE]
> Os exemplos a seguir mostram apenas a quantidade mínima de código necessário. Um aplicativo do mundo real geralmente fornece verificação de erros e tratamento de exceção mais robustos.  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a>Exemplo: Escreva texto sincronicamente com streamwriter

O exemplo a seguir mostra como usar a classe <xref:System.IO.StreamWriter> para gravar um texto de forma síncrona em um novo arquivo, uma linha por vez. Como o objeto <xref:System.IO.StreamWriter> é declarado e instanciado em uma instrução `using`, o método <xref:System.IO.StreamWriter.Dispose%2A> é invocado, o que libera e fecha o fluxo automaticamente.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a>Exemplo: Texto de apêndice sincronicamente com StreamWriter

O exemplo a seguir mostra como usar a classe <xref:System.IO.StreamWriter> para acrescentar um texto de forma síncrona ao arquivo de texto criado no primeiro exemplo.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a>Exemplo: Escreva texto assíncronamente com streamwriter

O exemplo a seguir mostra como gravar texto de maneira assíncrona em um novo arquivo usando a classe <xref:System.IO.StreamWriter>. Para invocar o método <xref:System.IO.StreamWriter.WriteAsync%2A>, a chamada de método precisa estar dentro de um método `async`. O exemplo em C# exige o C# 7.1 ou posterior, o que adiciona suporte ao modificador `async` no ponto de entrada do programa.

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a>Exemplo: Escreva e apêndice texto com a classe Arquivo

O exemplo a seguir mostra como gravar texto em um novo arquivo e acrescentar novas linhas de texto ao mesmo arquivo usando a classe <xref:System.IO.File>. Os métodos <xref:System.IO.File.WriteAllText%2A> e <xref:System.IO.File.AppendAllLines%2A> abrem e fecham o arquivo automaticamente. Se o caminho que você fornecer ao método <xref:System.IO.File.WriteAllText%2A> já existir, o arquivo será substituído.  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a>Confira também

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [Como: Enumerar diretórios e arquivos](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [Como: Ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [Como: Abrir e anexar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [Como: Ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
