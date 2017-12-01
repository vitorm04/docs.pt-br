---
title: "Como: Fazer iterações de diretórios de arquivos com PLINQ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: PLINQ queries, how to iterate directories
ms.assetid: 354e8ce3-35c4-431c-99ca-7661d1f3901b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 40fd9f64b5702f5205b7817f3de1e0a8709c5a63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-iterate-file-directories-with-plinq"></a>Como: Fazer iterações de diretórios de arquivos com PLINQ
Este exemplo mostra duas maneiras de simples para paralelizar a operações em diretórios de arquivos. A primeira consulta usa o <xref:System.IO.Directory.GetFiles%2A> método para preencher uma matriz de nomes de arquivo em um diretório e todos os subdiretórios. Este método não retorna até que a matriz inteira é preenchida e, portanto, ela pode apresentar latência no início da operação. No entanto, depois que a matriz é preenchida, PLINQ pode processá-la em paralelo muito rapidamente.  
  
 A segunda consulta usa estático <xref:System.IO.Directory.EnumerateDirectories%2A> e <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> métodos qual começam a retornar resultados imediatamente. Essa abordagem pode ser mais rápida, quando você estiver iterando em árvores de diretório, embora o tempo de processamento em comparação comparado o primeiro exemplo pode depender de vários fatores.  
  
> [!WARNING]
>  Esses exemplos destinam-se para demonstrar o uso e não podem ser executado mais rápido do que o LINQ sequencial equivalente a consulta de objetos. Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como iterar nos diretórios de arquivos em cenários simples, quando você tem acesso a todos os diretórios na árvore, os tamanhos de arquivos não são muito grandes e os tempos de acesso não são significativos. Essa abordagem envolve um período de latência no início, enquanto a matriz de nomes de arquivo está sendo construída.  
  
 [!code-csharp[PLINQ#33](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#33)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como iterar nos diretórios de arquivos em cenários simples, quando você tem acesso a todos os diretórios na árvore, os tamanhos de arquivos não são muito grandes e os tempos de acesso não são significativos. Essa abordagem começa a produzir resultados mais rápido do que no exemplo anterior.  
  
 [!code-csharp[PLINQ#34](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqfileiteration.cs#34)]  
  
 Ao usar <xref:System.IO.Directory.GetFiles%2A>, certifique-se de que você tem permissões suficientes em todos os diretórios na árvore. Caso contrário, uma exceção será lançada e nenhum resultado será retornado. Ao usar o <xref:System.IO.Directory.EnumerateDirectories%2A> em uma consulta PLINQ, é problemático para lidar com exceções de e/s de maneira normal que permite que você continue a iteração. Se seu código deve manipular exceções de acesso não autorizado ou de e/s, você deve considerar a abordagem descrita no [como: iterar diretórios de arquivos com a classe Parallel](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-the-parallel-class.md).  
  
 Se a latência de e/s é um problema, por exemplo com e/s de arquivo em uma rede, considere usar uma das técnicas de e/s assíncronas descritas em [TPL e estrutura de programação assíncrona tradicional .NET](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md) e neste [postagem de blog ](http://go.microsoft.com/fwlink/?LinkID=186458).  
  
## <a name="see-also"></a>Consulte também  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
