---
title: 'Como: Fazer iterações de diretórios de arquivos com PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
ms.openlocfilehash: 90afc767e422515c6122b8a6ef0e63ffc07caf3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091375"
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Como: Fazer iterações de diretórios de arquivos com PLINQ
Este exemplo mostra duas maneiras simples de paralelizar operações em diretórios de arquivos. A primeira consulta usa o método <xref:System.IO.Directory.GetFiles%2A> para preencher uma matriz de nomes de arquivo em um diretório e em todos os subdiretórios. Este método não retorna até que toda a matriz esteja preenchida e, portanto, pode apresentar latência no início da operação. No entanto, após o preenchimento da matriz, PLINQ pode processá-la em paralelo rapidamente.  
  
 A segunda consulta usa métodos <xref:System.IO.Directory.EnumerateDirectories%2A> e <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> estáticos que começam a retornar os resultados imediatamente. Essa abordagem pode ser mais rápida quando você estiver iterando em árvores de diretório grandes, embora o tempo de processamento em comparação o primeiro exemplo possa depender de vários fatores.  
  
> [!WARNING]
> Esses exemplos têm como objetivo demonstrar o uso, e talvez não executem tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como iterar nos diretórios de arquivos em cenários simples, quando você tem acesso a todos os diretórios na árvore, os tamanhos de arquivos não são muito grandes e os tempos de acesso não são consideráveis. Essa abordagem envolve um período de latência no início, enquanto a matriz de nomes de arquivo está sendo construída.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como iterar nos diretórios de arquivos em cenários simples, quando você tem acesso a todos os diretórios na árvore, os tamanhos de arquivos não são muito grandes e os tempos de acesso não são consideráveis. Essa abordagem começa a produzir resultados mais rápido do que o exemplo anterior.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Ao usar <xref:System.IO.Directory.GetFiles%2A>, verifique se você tem permissões suficientes em todos os diretórios na árvore. Caso contrário, uma exceção será lançada e nenhum resultado retornará. Ao usar o <xref:System.IO.Directory.EnumerateDirectories%2A> em uma consulta PLINQ, é problemático tratar as exceções de E/S de uma maneira que permita que você continue a iteração. Se o seu código precisar manipular exceções de acesso não autorizado ou de E/S, considere a abordagem descrita em [Como iterar diretórios de arquivos com a classe paralela](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Se a latência de E/S for um problema, por exemplo com E/S de arquivo em uma rede, considere o uso de uma das técnicas de E/S assíncronas descritas em [TPL e programação assíncrona de TPL e .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) e nesta [postagem de blog ](https://devblogs.microsoft.com/pfxteam/parallel-extensions-and-io/).  
  
## <a name="see-also"></a>Consulte também

- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
