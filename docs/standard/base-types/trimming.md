---
title: Cortando e removendo caracteres de cadeias de caracteres no .NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fde24a97234d275d3d599f13bfc4063af939507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a>Cortando e removendo caracteres de cadeias de caracteres no .NET
Se estiver analisando as palavras individuais de uma sentença, você poderá encontrar palavras com espaços em branco em ambas as extremidades da palavra. Nessa situação, você pode usar um dos métodos de corte na classe **System.String** para remover qualquer número de espaços ou de outros caracteres de uma posição especificada na cadeia de caracteres. A tabela a seguir descreve os métodos de corte disponíveis.  
  
|Nome do método|Use|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|Remove os espaços em branco ou caracteres especificados em uma matriz de caracteres do início e do final de uma cadeia de caracteres.|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|Remove os caracteres especificados em uma matriz de caracteres do final de uma cadeia de caracteres.|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|Remove os caracteres especificados em uma matriz de caracteres do início de uma cadeia de caracteres.|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|Remove um número especificado de caracteres de uma posição de índice especificada em uma cadeia de caracteres.|  
  
## <a name="trim"></a>Trim  
 Você pode facilmente remover espaços em branco de ambas as extremidades de uma cadeia de caracteres usando o <xref:System.String.Trim%2A?displayProperty=nameWithType> método, conforme mostrado no exemplo a seguir.  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 Você também poderá remover os caracteres que especificar em uma matriz de caracteres do início e do final de uma cadeia de caracteres. O exemplo a seguir remove caracteres de espaço em branco, pontos e asteriscos.  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a>TrimEnd  
 O método **String.TrimEnd** remove os caracteres do final de uma cadeia de caracteres, criando um novo objeto de cadeia de caracteres. Uma matriz de caracteres é passada para este método para especificar os caracteres a seres removidos. A ordem dos elementos na matriz de caracteres não afeta a operação de corte. O corte é interrompido quando um caractere não especificado na matriz é encontrado.  
  
 O exemplo a seguir remove as últimas letras de uma cadeia de caracteres usando o **TrimEnd** método. Neste exemplo, as posições do caractere `'r'` e do caractere `'W'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa. Observe que este código remove a última palavra de `MyString` mais uma parte da primeira.  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 Esse código exibe `He` no console.  
  
 O exemplo a seguir remove as últimas palavras de uma cadeia de caracteres usando o método **TrimEnd**. Nesse código, há uma vírgula após a palavra `Hello` e, como a vírgula não está especificada na matriz de caracteres para cortar, o corte termina na vírgula.  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 Esse código exibe `Hello,` no console.  
  
## <a name="trimstart"></a>TrimStart  
 O método **String.TrimStart** é semelhante ao método **String.TrimEnd**, exceto que ele cria uma nova cadeia de caracteres removendo caracteres do início de um objeto de cadeia de caracteres existente. Uma matriz de caracteres é passada para o método **TrimStart** para especificar os caracteres a serem removidos. Assim como acontece com o método **TrimEnd**, a ordem dos elementos na matriz de caracteres não afeta a operação de corte. O corte é interrompido quando um caractere não especificado na matriz é encontrado.  
  
 O exemplo a seguir remove a primeira palavra de uma cadeia de caracteres. Neste exemplo, as posições do caractere `'l'` e do caractere `'H'` estão invertidas para ilustrar que a ordem dos caracteres na matriz não importa.  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 Esse código exibe `World!` no console.  
  
## <a name="remove"></a>Remover  
 O <xref:System.String.Remove%2A?displayProperty=nameWithType> método Remove um número especificado de caracteres que começam com uma posição especificada em uma cadeia de caracteres existente. Este método assume um índice baseado em zero.  
  
 O exemplo a seguir remove dez caracteres de uma cadeia de caracteres começando na posição cinco de um índice baseado em zero da cadeia de caracteres.  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 Você também pode remover um caractere especificado ou uma subcadeia de caracteres de uma cadeia de caracteres chamando o <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> método e especificando uma cadeia de caracteres vazia (<xref:System.String.Empty?displayProperty=nameWithType>) como a substituição. O exemplo a seguir remove todas as vírgulas de uma cadeia de caracteres.  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a>Consulte também  
 [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)
