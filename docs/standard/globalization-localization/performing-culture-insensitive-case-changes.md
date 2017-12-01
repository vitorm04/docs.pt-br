---
title: "Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura"
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
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a>Executando alterações de maiúsculas e minúsculas que não levam em conta a cultura
O <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, e <xref:System.Char.ToLower%2A?displayProperty=nameWithType> métodos fornecem sobrecargas que não aceitam quaisquer parâmetros. Por padrão, essas sobrecargas sem parâmetros realizar alterações com base no valor da <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>. Isso produz resultados diferencia maiusculas de minúsculas podem variar de acordo com a cultura. Para tornar claro se você quer que as alterações casos ser sensíveis à cultura ou não levam em conta a cultura, você deve usar as sobrecargas desses métodos que exigem que você especificar explicitamente um `culture` parâmetro. Alterações de maiusculas sensíveis à cultura, especifique `CultureInfo.CurrentCulture` para o `culture` parâmetro. Alterações de maiusculas não levam em conta a cultura, especifique `CultureInfo.InvariantCulture` para o `culture` parâmetro.  
  
 Em geral, cadeias de caracteres são convertidas em um caso padrão para habilitar a pesquisa mais fácil mais tarde. Quando cadeias de caracteres são usadas dessa maneira, você deve especificar `CultureInfo.InvariantCulture` para o `culture` parâmetro, porque o valor de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> poderá alterar entre a hora em que o caso é alterado e a hora em que a pesquisa ocorre.  
  
 Se uma decisão de segurança é baseada em uma operação de alteração, a operação deve ser sem diferenciação de cultura para garantir que o resultado não é afetado pelo valor da `CultureInfo.CurrentCulture`. Consulte a seção "Cadeia de caracteres comparações que Use a cultura atual" o [práticas recomendadas para usar cadeias de caracteres](../../../docs/standard/base-types/best-practices-strings.md) artigo para um exemplo que demonstra as operações de cadeia de caracteres como sensíveis à cultura pode produzir resultados inconsistentes.  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>Usando os Métodos String.ToUpper e String.ToLower  
 Para maior clareza do código, é recomendável que você sempre use sobrecargas do `String.ToUpper` e `String.ToLower` métodos que permitem que você especifique um `culture` parâmetro explicitamente. Por exemplo, o código a seguir realiza uma pesquisa de identificador. O `key.ToLower` operação sensíveis à cultura por padrão, mas esse comportamento não está claro de ler o código.  
  
### <a name="example"></a>Exemplo  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 Se você quiser que o `key.ToLower` operação sem diferenciação de cultura, você deve alterar o exemplo anterior da seguinte forma para usar explicitamente o `CultureInfo.InvariantCulture` ao alterar o caso.  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>Usando os Métodos Char.ToUpper e Char.ToLower  
 Embora o `Char.ToUpper` e `Char.ToLower` métodos têm as mesmas características como o `String.ToUpper` e `String.ToLower` métodos, somente culturas afetados são turco (Turquia) e Azerbaidjano (Azerbaijão, latino). Essas são apenas duas culturas com diferenças de maiusculas e minúsculas do caractere único. Para obter mais detalhes sobre esse mapeamento de maiusculas exclusivo, consulte a seção "Maiusculas e minúsculas" a <xref:System.String> tópico sobre a classe. Para maior clareza do código e garantir resultados consistentes, é recomendável que você sempre use as sobrecargas desses métodos que permitem que você especifique explicitamente um `culture` parâmetro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [Executando operações de cadeia de caracteres que não levam em conta a cultura](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
