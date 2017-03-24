---
title: Tipo de dados Boolean (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
dev_langs:
- VB
helpviewer_keywords:
- Boolean data type
- Boolean values, False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values, True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7ec46a491373d370993e0f400c97630420165b87
ms.lasthandoff: 03/13/2017

---
# <a name="boolean-data-type-visual-basic"></a>Tipo de dados booliano (Visual Basic)
Contém os valores que podem ser apenas `True` ou `False`. As palavras-chave `True` e `False` correspondem aos dois estados de `Boolean` variáveis.  
  
## <a name="remarks"></a>Comentários  
 Use o [(Visual Basic) do tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) para conter valores de dois estados, como verdadeiro/falso, Sim/não ou ativado/desativado.  
  
 O valor padrão de `Boolean` é `False`.  
  
 `Boolean`valores não são armazenados como números, e não são os valores armazenados sejam equivalentes a números. Você nunca deve escrever código que dependa de valores numéricos equivalentes para `True` e `False`. Sempre que possível, você deve restringir o uso de `Boolean` variáveis para os valores lógicos para que elas são criadas.  
  
## <a name="type-conversions"></a>Conversões de tipo  
 Quando o Visual Basic converte valores de tipos de dados numéricos para `Boolean`, 0 se torna `False` e todos os outros valores tornam-se `True`. Quando Visual Basic converte `Boolean` valores para tipos numéricos, `False` se torna 0 e `True` torna-se -1.  
  
 Ao converter entre `Boolean` valores e tipos de dados numéricos, tenha em mente que os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as palavras-chave de conversão do Visual Basic. Isso ocorre porque a conversão Visual Basic retém o comportamento compatível com versões anteriores. Para obter mais informações, consulte "Tipo booleano não converter para tipo numérico com precisão" em [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** `Boolean`não é um tipo numérico e não pode representar um valor negativo. Em qualquer caso, você não deve usar `Boolean` para armazenar valores numéricos.  
  
-   **Caracteres de tipo.** `Boolean`não possui caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é o <xref:System.Boolean?displayProperty=fullName>estrutura.</xref:System.Boolean?displayProperty=fullName>  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `runningVB` é um `Boolean` variável, que armazena um simples configuração Sim/não.  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Boolean?displayProperty=fullName></xref:System.Boolean?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
