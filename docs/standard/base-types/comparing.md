---
title: Comparando cadeias de caracteres no .NET
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
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET Framework], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34aa922155943d1b4d39de2e7c33ebc1228e1083
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="comparing-strings-in-net"></a>Comparando cadeias de caracteres no .NET
O .NET fornece vários métodos para comparar os valores de cadeias de caracteres. A tabela a seguir lista e descreve os métodos de comparação de valores.  
  
|Nome do método|Use|  
|-----------------|---------|  
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|Compara os valores das duas cadeias de caracteres. Retorna um valor inteiro.|  
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|Compara duas cadeias de caracteres sem considerar a cultura local. Retorna um valor inteiro.|  
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|Compara o objeto atual de cadeia de caracteres a outra cadeia de caracteres. Retorna um valor inteiro.|  
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|Determina se uma cadeia de caracteres começa com a cadeia de caracteres passada. Representa um valor Booliano.|  
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|Determina se uma cadeia de caracteres termina com a cadeia de caracteres passada. Representa um valor Booliano.|  
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|Determina se duas cadeias de caracteres são iguais. Representa um valor Booliano.|  
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|Retorna a posição do índice de um caractere ou uma cadeia de caracteres, começando do início da cadeia de caracteres que você está examinando. Retorna um valor inteiro.|  
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|Retorna a posição do índice de um caractere ou uma cadeia de caracteres, começando do fim da cadeia de caracteres que você está examinando. Retorna um valor inteiro.|  
  
## <a name="compare"></a>Comparar  
 Estático <xref:System.String.Compare%2A?displayProperty=nameWithType> método fornece uma maneira completa de comparar duas cadeias de caracteres. Esse método é cultural. Você pode usar essa função para comparar duas cadeias de caracteres ou subcadeias de duas cadeias de caracteres. Além disso, sobrecargas são fornecidas para considerar ou ignorar a variação cultural ou de caso. A tabela a seguir mostra os três valores inteiros que esse método pode retornar.  
  
|Valor retornado|Condição|  
|------------------|---------------|  
|Um inteiro negativo|A primeira cadeia de caracteres precede a segunda cadeia de caracteres na ordem de classificação.<br /><br /> -ou-<br /><br /> A primeira cadeia de caracteres é `null`.|  
|0|A primeira cadeia de caracteres e a segunda cadeia de caracteres são iguais.<br /><br /> -ou-<br /><br /> Ambas as cadeias de caracteres são `null`.|  
|Um inteiro positivo<br /><br /> -ou-<br /><br /> 1|A primeira cadeia de caracteres segue a segunda cadeia de caracteres na ordem de classificação.<br /><br /> -ou-<br /><br /> A segunda cadeia for `null`.|  
  
> [!IMPORTANT]
>  O <xref:System.String.Compare%2A?displayProperty=nameWithType> método é usado principalmente para uso em ordenação ou classificação de cadeias de caracteres. Você não deve usar o <xref:System.String.Compare%2A?displayProperty=nameWithType> método para testar a igualdade (ou seja, para procurar um valor de retorno de 0 com nenhuma relação para se explicitamente uma cadeia de caracteres é menor ou maior que o outro). Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> método.  
  
 O exemplo a seguir usa o <xref:System.String.Compare%2A?displayProperty=nameWithType> método para determinar os valores relativos das duas cadeias de caracteres.  
  
 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]  
  
 Este exemplo exibe `-1` no console.  
  
 O exemplo anterior é sensíveis à cultura por padrão. Para realizar uma comparação de cadeia de caracteres não levam em conta a cultura, use uma sobrecarga de <xref:System.String.Compare%2A?displayProperty=nameWithType> método que permite que você especifique a cultura a ser usada, fornecendo um *cultura* parâmetro. Para obter um exemplo que demonstra como usar o <xref:System.String.Compare%2A?displayProperty=nameWithType> método para executar uma comparação sem diferenciação de cultura, consulte [executar comparações de cadeias de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="compareordinal"></a>CompareOrdinal  
 O <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> método compara dois objetos de cadeia de caracteres sem considerar a cultura local. Os valores de retorno desse método são idênticos aos valores retornados pelo **comparar** método na tabela anterior.  
  
> [!IMPORTANT]
>  O <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> método é usado principalmente para uso em ordenação ou classificação de cadeias de caracteres. Você não deve usar o <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> método para testar a igualdade (ou seja, para procurar um valor de retorno de 0 com nenhuma relação para se explicitamente uma cadeia de caracteres é menor ou maior que o outro). Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> método.  
  
 O exemplo a seguir usa o **CompareOrdinal** método para comparar os valores de duas cadeias de caracteres.  
  
 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]  
  
 Este exemplo exibe `-32` no console.  
  
## <a name="compareto"></a>CompareTo  
 O <xref:System.String.CompareTo%2A?displayProperty=nameWithType> método compara a cadeia de caracteres que encapsula o objeto string atual com outro objeto ou cadeia de caracteres. Os valores de retorno desse método são idênticos aos valores retornados pelo método <xref:System.String.Compare%2A?displayProperty=nameWithType> na tabela anterior.  
  
> [!IMPORTANT]
>  O <xref:System.String.CompareTo%2A?displayProperty=nameWithType> método é usado principalmente para uso em ordenação ou classificação de cadeias de caracteres. Você não deve usar o <xref:System.String.CompareTo%2A?displayProperty=nameWithType> método para testar a igualdade (ou seja, para procurar um valor de retorno de 0 com nenhuma relação para se explicitamente uma cadeia de caracteres é menor ou maior que o outro). Em vez disso, para determinar se duas cadeias de caracteres são iguais, use o <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> método.  
  
 O exemplo a seguir usa o método <xref:System.String.CompareTo%2A?displayProperty=nameWithType> para comparar o objeto `string1` ao objeto `string2`.  
  
 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]  
  
 Este exemplo exibe `-1` no console.  
  
 Todas as sobrecargas do <xref:System.String.CompareTo%2A?displayProperty=nameWithType> método executar comparações de cultura e diferencia maiusculas de minúsculas por padrão. Nenhuma sobrecarga desse método é fornecidas que permitem que você execute uma comparação sem diferenciação de cultura. Para maior clareza do código, é recomendável que você use o **Compare** método em vez disso, especificando <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> para operações sensíveis à cultura ou <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> para operações de cultura. Para obter exemplos que demonstram como usar o **Compare** método para executar comparações sensíveis à cultura e cultura, consulte [executando cultura comparações de cadeia de caracteres](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md).  
  
## <a name="equals"></a>Igual a  
 O método **String.Equals** pode facilmente determinar se duas cadeias de caracteres são as mesmas. Este método diferencia maiusculas de minúsculas retorna um **true** ou **false** valor booliano. Ele pode ser usado de uma classe existente, conforme ilustrado no exemplo a seguir. O exemplo a seguir usa o **é igual a** método para determinar se um objeto de cadeia de caracteres contém a frase "Olá, mundo".  
  
 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]  
  
 Este exemplo exibe `True` no console.  
  
 Esse método também pode ser usado como um método estático. O exemplo a seguir compara dois objetos de cadeia de caracteres usando um método estático.  
  
 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]  
  
 Este exemplo exibe `True` no console.  
  
## <a name="startswith-and-endswith"></a>StartsWith e EndsWith  
 Você pode usar o método **String.StartsWith** para determinar se um objeto de cadeia de caracteres começa com os mesmos caracteres que englobam outra cadeia de caracteres. Este método diferencia maiusculas de minúsculas retorna **true** se o objeto atual de cadeia de caracteres começa com a cadeia de caracteres transmitida e **false** se não existir. O exemplo a seguir usa esse método para determinar se um objeto de cadeia de caracteres começa com "Hello".  
  
 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]  
  
 Este exemplo exibe `True` no console.  
  
 O método **String.EndsWith** compara uma cadeia de caracteres passada com os caracteres que existem no final do objeto de cadeia de caracteres atual. Ele também retorna um valor Booliano. O exemplo a seguir verifica o fim de uma cadeia de caracteres usando o **EndsWith** método.  
  
 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]  
  
 Este exemplo exibe `False` no console.  
  
## <a name="indexof-and-lastindexof"></a>IndexOf e LastIndexOf  
 Você pode usar o método **String.IndexOf** para determinar a posição da primeira ocorrência de um determinado caractere dentro de uma cadeia de caracteres. Esse método que diferencia maiúsculas de minúsculas inicia a contagem do início de uma cadeia de caracteres e retorna a posição de um caractere passado usando um índice baseado em zero. Se o caractere não for encontrado, um valor de -1 será retornado.  
  
 O exemplo a seguir usa o **IndexOf** método para procurar a primeira ocorrência da '`l`' caractere em uma cadeia de caracteres.  
  
 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]  
  
 Este exemplo exibe `2` no console.  
  
 O **LastIndexOf** método é semelhante do **String. IndexOf** método, exceto que ela retorna a posição da última ocorrência de um determinado caractere dentro de uma cadeia de caracteres. Ele diferencia maiúsculas de minúsculas e usa um índice baseado em zero.  
  
 O exemplo a seguir usa o **LastIndexOf** método para pesquisar a última ocorrência da '`l`' caractere em uma cadeia de caracteres.  
  
 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]  
  
 Este exemplo exibe `9` no console.  
  
 Os dois métodos são úteis quando usados em conjunto com o método **String.Remove**. Você pode usar o **IndexOf** ou **LastIndexOf** métodos para recuperar a posição de um caractere e, em seguida, fornecer essa posição para o **remover** método para remover um caractere ou uma palavra que começa com esse caractere.  
  
## <a name="see-also"></a>Consulte também  
 [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
