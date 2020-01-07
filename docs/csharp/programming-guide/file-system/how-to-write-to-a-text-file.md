---
title: Como escrever em um guia de programação de C# arquivos de texto
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: c0b6646e0d7f453dc9021a7470a3671f11ea0653
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635412"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Como gravar em um arquivo de texto (C# guia de programação)
Estes exemplos mostram várias maneiras de gravar textos em um arquivo. Os dois primeiros exemplos usam métodos de conveniência estáticos na classe <xref:System.IO.File?displayProperty=nameWithType> para gravar cada elemento de qualquer `IEnumerable<string>` e uma cadeia de caracteres em um arquivo de texto. O exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente enquanto escreve no arquivo. Os exemplos de 1 a 3 substituem todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto em um arquivo existente.  
  
 Todos esses exemplos gravam literais de cadeia de caracteres em arquivos. Se você quiser formatar o texto gravado em um arquivo, use o método <xref:System.String.Format%2A> ou o recurso de [interpolação de cadeia de caracteres](../../language-reference/tokens/interpolated.md) do C#.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Programação Robusta  
 As seguintes condições podem causar uma exceção:  
  
- O arquivo existe e é somente leitura.  
  
- O nome do caminho pode ser muito longo.  
  
- O disco pode estar cheio.  
  
## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Sistema de arquivos e o Registro (Guia de Programação em C#)](./index.md)
- [Exemplo: salvar uma coleção no armazenamento de aplicativos](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
