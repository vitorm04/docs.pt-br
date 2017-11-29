---
title: "Como escrever em um arquivo de texto (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Como escrever em um arquivo de texto (Guia de Programação em C#)
Estes exemplos mostram várias maneiras de gravar textos em um arquivo.  Os dois primeiros exemplos usam métodos de conveniência estáticos na classe <xref:System.IO.File?displayProperty=nameWithType> para gravar cada elemento de qualquer IEnumerable\<string> e uma cadeia de caracteres em um arquivo de texto.  O exemplo 3 mostra como adicionar texto a um arquivo quando você precisa processar cada linha individualmente enquanto escreve no arquivo.  Os exemplos de 1 a 3 substituem todo o conteúdo existente no arquivo, mas o exemplo 4 mostra como adicionar texto em um arquivo existente.  
  
 Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.  Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 Esses exemplos todos gravam literais de cadeia de caracteres em arquivos, mas é mais provável que você deseje usar o método <xref:System.String.Format%2A> que tem vários controles para diferentes tipos de valores justificados à direita ou à esquerda, com ou sem preenchimento, e assim por diante.  Você também pode usar o recurso [interpolação de cadeia de caracteres](../../../csharp/language-reference/keywords/interpolated-strings.md) do C#.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   O arquivo existe e é somente leitura.  
  
-   O nome do caminho pode ser muito longo.  
  
-   O disco pode estar cheio.  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Sistema de arquivos e o Registro (Guia de Programação em C#)](../../../csharp/programming-guide/file-system/index.md)  
 [Exemplo: salvar uma coleção no armazenamento de aplicativos](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
