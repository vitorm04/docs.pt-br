---
title: Tipo de dados booliano (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a>Tipo de dados booliano (Visual Basic)
Contém valores que podem ser apenas `True` ou `False`. As palavras-chave `True` e `False` correspondem aos dois estados de `Boolean` variáveis.  
  
## <a name="remarks"></a>Comentários  
 Use o [(Visual Basic) do tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) conter valores de dois estados, como verdadeiro/falso, Sim/Não, ou ativado/desativado.  
  
 O valor padrão de `Boolean` é `False`.  
  
 `Boolean`valores não são armazenados como números, e os valores armazenados não devem ser equivalentes a números. Você nunca deve gravar códigos que contem com valores numéricos equivalentes para `True` e `False`. Sempre que possível, você deve restringir o uso de `Boolean` variáveis para os valores lógicos para os quais eles são criados.  
  
## <a name="type-conversions"></a>Conversões de tipo  
 Quando o Visual Basic converte valores de tipo de dados numéricos para `Boolean`, 0 se torna `False` e todos os outros valores tornam-se `True`. Quando o Visual Basic converte `Boolean` valores para tipos numéricos, `False` se torna 0 e `True` torna-se -1.  
  
 Ao converter entre `Boolean` valores e tipos de dados numéricos, tenha em mente que os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as palavras-chave de conversão do Visual Basic. Isso ocorre porque a conversão do Visual Basic retém o comportamento compatível com versões anteriores. Para obter mais informações, consulte "Tipo booleano não converter para tipo numérico com precisão" em [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Números negativos.** `Boolean`não é um tipo numérico e não pode representar um valor negativo. Em qualquer caso, você não deve usar `Boolean` para armazenar valores numéricos.  
  
-   **Caracteres de tipo.** `Boolean`não tem o caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** O tipo correspondente no .NET Framework é a estrutura <xref:System.Boolean?displayProperty=nameWithType>.  
  
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
 <xref:System.Boolean?displayProperty=nameWithType>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [Solução de problemas de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
