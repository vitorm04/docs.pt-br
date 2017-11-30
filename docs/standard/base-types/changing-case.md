---
title: "Alterando a definição de maiúsculas e minúsculas no .NET Framework"
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
helpviewer_keywords:
- strings [.NET Framework], case
- case sensitivity
- ToUpper method
- ToLower method
- uppercase
- lowercase
ms.assetid: 6805f81b-e9ad-4387-9f4c-b9bdb21b87c0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b03dec350d38d15faaa6a0afc6a1f2c31d5c58f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="changing-case-in-net"></a>Caso de alteração no .NET
Se você gravar um aplicativo que aceita a inserção de informações por um usuário, talvez você nunca tenha certeza se ele ou ela usará maiúsculas ou minúsculas para inserir os dados. Muitas vezes, você quer que as cadeias de caracteres tenham a grafia de maiúsculas e minúsculas consistente, especialmente se você estiver exibindo-as na interface do usuário. A tabela a seguir descreve os três métodos de alteração. Os primeiros dois métodos fornecem uma sobrecarga que aceita uma cultura.  
  
|Nome do método|Use|  
|-----------------|---------|  
|<xref:System.String.ToUpper%2A?displayProperty=nameWithType>|Converte todos os caracteres em uma cadeia de caracteres para maiúsculas.|  
|<xref:System.String.ToLower%2A?displayProperty=nameWithType>|Converte todos os caracteres em uma cadeia de caracteres para minúsculas.|  
|<xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType>|Converte uma cadeia de caracteres em maiusculas/minúsculas.|  
  
> [!WARNING]
>  Observe que os métodos <xref:System.String.ToUpper%2A?displayProperty=nameWithType> e <xref:System.String.ToLower%2A?displayProperty=nameWithType> não devem ser usados para converter cadeias de caracteres a fim de compará-las ou testá-las quanto à igualdade. Para obter mais informações, consulte o [Comparando cadeias de caracteres de maiusculas e minúsculas](#Comparing) seção.  
  
<a name="Comparing"></a>   
## <a name="comparing-strings-of-mixed-case"></a>Comparando cadeias de caracteres em maiúsculas e minúsculas  
 Para comparar cadeias de caracteres de maiusculas e minúsculas para determinar sua ordem, chame um das sobrecargas do <xref:System.String.CompareTo%2A?displayProperty=nameWithType> método com um `comparisonType` parâmetro e forneça um valor de <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> para o `comparisonType` argumento. Para obter uma comparação usando uma cultura específica que não seja a cultura atual, chame uma sobrecarga do <xref:System.String.CompareTo%2A?displayProperty=nameWithType> método tanto com um `culture` e `options` parâmetro e forneça um valor de <xref:System.Globalization.CompareOptions.IgnoreCase?displayProperty=nameWithType> como o `options` argumento.  
  
 Para comparar cadeias de caracteres de maiusculas e minúsculas para determinar se eles são iguais, deles, chame um das sobrecargas do <xref:System.String.Equals%2A?displayProperty=nameWithType> método com um `comparisonType` parâmetro e forneça um valor de <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType>, <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType>, ou <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> para o `comparisonType` argumento.  
  
 Para obter mais informações, consulte [Práticas recomendadas para o uso de cadeias de caracteres](../../../docs/standard/base-types/best-practices-strings.md).  
  
## <a name="toupper"></a>ToUpper  
 O <xref:System.String.ToUpper%2A?displayProperty=nameWithType> método altera todos os caracteres em uma cadeia de caracteres em maiusculas. O exemplo a seguir converte a cadeia de caracteres "Olá, mundo!" de maiúsculas e minúsculas para maiúsculas.  
  
 [!code-csharp[Strings.ChangingCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#1)]
 [!code-vb[Strings.ChangingCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#1)]  
  
 O exemplo anterior é sensíveis à cultura por padrão. aplica as convenções de maiusculas e minúsculas da cultura atual. Para realizar uma alteração não levam em conta a cultura ou para aplicar as convenções de maiusculas e minúsculas de uma cultura específica, use o <xref:System.String.ToUpper%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> método de sobrecarga e fornecer um valor de <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ou um <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objeto que representa a cultura especificada para o *cultura* parâmetro. Para obter um exemplo que demonstra como usar o <xref:System.String.ToUpper%2A> método para realizar uma alteração não levam em conta a cultura, consulte [fazendo cultura alterações](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="tolower"></a>ToLower  
 O <xref:System.String.ToLower%2A?displayProperty=nameWithType> método é semelhante ao método anterior, mas em vez disso converte todos os caracteres em uma cadeia de caracteres em minúsculas. O exemplo a seguir converte a cadeia de caracteres "Olá, mundo!" para minúsculas.  
  
 [!code-csharp[Strings.ChangingCase#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.ChangingCase/cs/Example.cs#2)]
 [!code-vb[Strings.ChangingCase#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.ChangingCase/vb/Example.vb#2)]  
  
 O exemplo anterior é sensíveis à cultura por padrão. aplica as convenções de maiusculas e minúsculas da cultura atual. Para realizar uma alteração não levam em conta a cultura ou para aplicar as convenções de maiusculas e minúsculas de uma cultura específica, use o <xref:System.String.ToLower%28System.Globalization.CultureInfo%29?displayProperty=nameWithType> método de sobrecarga e fornecer um valor de <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> ou um <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> objeto que representa a cultura especificada para o *cultura* parâmetro. Para obter um exemplo que demonstra como usar o <xref:System.String.ToLower%28System.Globalization.CultureInfo%29> método para realizar uma alteração não levam em conta a cultura, consulte [fazendo cultura alterações](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md).  
  
## <a name="totitlecase"></a>ToTitleCase  
 O <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> converte o primeiro caractere de cada palavra em maiuscula e os caracteres restantes em minúsculas. No entanto, as palavras que são totalmente maiusculas deveriam para ser acrônimos e não são convertidas.  
  
 O <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> método sensíveis à cultura; ou seja, ele usa as convenções de maiusculas e minúsculas de uma determinada cultura. Para chamar o método, você recuperar o <xref:System.Globalization.TextInfo> objeto que representa as convenções de maiusculas e minúsculas da cultura específica do <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> propriedade de uma determinada cultura.  
  
 O exemplo a seguir passa cada cadeia de caracteres em uma matriz para o <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> método.  As cadeias de caracteres incluem cadeias de caracteres de título adequado como acrônimos. As cadeias de caracteres são convertidas em maiusculas/minúsculas usando as convenções de maiusculas e minúsculas da cultura do inglês (Estados Unidos).  
  
 [!code-csharp[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/cs/totitlecase2.cs#1)]
 [!code-vb[System.Globalization.TextInfo.ToTitleCase#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.globalization.textinfo.totitlecase/vb/totitlecase2.vb#1)]  
  
 Observe que, embora seja sensíveis à cultura, o <xref:System.Globalization.TextInfo.ToTitleCase%2A?displayProperty=nameWithType> método não fornece regras de linguisticamente correta de maiusculas e minúsculas. Por exemplo, no exemplo anterior, o método converte "uma história de duas cidades" para "A história de duas cidades". No entanto, o uso de maiusculas e minúsculas do título linguisticamente correto para a cultura en-US é "Uma história de duas cidades."  
  
## <a name="see-also"></a>Consulte também  
 [Operações básicas de cadeias de caracteres](../../../docs/standard/base-types/basic-string-operations.md)  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
