---
title: 'Como: Fazer iterações de diretórios de arquivos com PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 208076cb9b7b56ab13458fa0dd4d92f2023106b9
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635838"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Como: Fazer iterações de diretórios de arquivos com PLINQ

Este artigo mostra duas maneiras de paraleletizar operações em diretórios de arquivos. A primeira consulta usa o método <xref:System.IO.Directory.GetFiles%2A> para preencher uma matriz de nomes de arquivo em um diretório e em todos os subdiretórios. Este método pode introduzir latência no início da operação, porque ele não retorna até que toda a matriz seja povoada. No entanto, depois que a matriz é povoada, PLINQ pode processá-lo em paralelo rapidamente.  
  
A segunda consulta usa <xref:System.IO.Directory.EnumerateDirectories%2A> <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> a estática e os métodos, que começam a retornar os resultados imediatamente. Essa abordagem pode ser mais rápida quando você está iterando sobre árvores de diretórios grandes, mas o tempo de processamento em comparação com o primeiro exemplo depende de muitos fatores.  
  
> [!NOTE]
> Esses exemplos destinam-se a demonstrar o uso e podem não ser executados mais rápido do que a consulta seqüencial equivalente LINQ to Objects. Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="getfiles-example"></a>Exemplo getFiles

 Este exemplo mostra como iterar sobre diretórios de arquivos em cenários simples quando você tem acesso a todos os diretórios na árvore, os tamanhos dos arquivos não são grandes e os tempos de acesso não são significativos. Essa abordagem envolve um período de latência no início, enquanto a matriz de nomes de arquivo está sendo construída.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="enumeratefiles-example"></a>Exemplo de EnumerateFiles

 Este exemplo mostra como iterar sobre diretórios de arquivos em cenários simples quando você tem acesso a todos os diretórios na árvore, os tamanhos dos arquivos não são grandes e os tempos de acesso não são significativos. Essa abordagem começa a produzir resultados mais rápido do que o exemplo anterior.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Ao usar <xref:System.IO.Directory.GetFiles%2A>, verifique se você tem permissões suficientes em todos os diretórios na árvore. Caso contrário, uma exceção será lançada e nenhum resultado será devolvido. Ao usar o <xref:System.IO.Directory.EnumerateDirectories%2A> em uma consulta PLINQ, é problemático tratar as exceções de E/S de uma maneira que permita que você continue a iteração. Se o seu código precisar manipular exceções de acesso não autorizado ou de E/S, considere a abordagem descrita em [Como iterar diretórios de arquivos com a classe paralela](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Se a latência de E/S for um problema, por exemplo com E/S de arquivo em uma rede, considere o uso de uma das técnicas de E/S assíncronas descritas em [TPL e programação assíncrona de TPL e .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) e nesta [postagem de blog ](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Confira também

- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
