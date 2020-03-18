---
title: Como ler a partir de um arquivo de texto - C# Guia de Programação
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705009"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Como ler a partir de um arquivo de texto (C# Guia de programação)
Este exemplo lê o conteúdo de um arquivo de texto usando os métodos estáticos <xref:System.IO.File.ReadAllText%2A> e <xref:System.IO.File.ReadAllLines%2A> da classe <xref:System.IO.File?displayProperty=nameWithType>.  
  
Para um exemplo <xref:System.IO.StreamReader>que usa, consulte [Como ler um arquivo de texto uma linha de cada vez](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Os arquivos usados neste exemplo são criados no tópico [Como escrever em um arquivo de texto](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código e cole-o em um aplicativo de console em C#.  
  
Se você não estiver usando os arquivos de texto de Como `ReadAllText` `ReadAllLines` escrever para um arquivo de [texto,](./how-to-write-to-a-text-file.md)substitua o argumento para e com o caminho e nome do arquivo apropriados em seu computador.
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
- O arquivo não existe ou não existe no local especificado. Verifique o caminho e a ortografia do nome do arquivo.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Não confie no nome de um arquivo para determinar o conteúdo do arquivo. Por exemplo, o arquivo `myFile.cs` pode não ser um arquivo de origem do C#.  
  
## <a name="see-also"></a>Confira também

- <xref:System.IO?displayProperty=nameWithType>
- [C# Guia de Programação](../index.md)
- [Sistema de arquivos e o Registro (Guia de Programação em C#)](./index.md)
