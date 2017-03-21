---
title: Operador TryCast (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
dev_langs:
- VB
helpviewer_keywords:
- TryCast keyword
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: 17
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
ms.openlocfilehash: 8dea8bfce88581d0cc21dc59b4afb44da27a076e
ms.lasthandoff: 03/13/2017

---
# <a name="trycast-operator-visual-basic"></a>Operador TryCast (Visual Basic)
Introduz uma operação de conversão de tipo que não gera uma exceção.  
  
## <a name="remarks"></a>Comentários  
 Se uma tentativa de conversão falhar, `CType` e `DirectCast` ambos lançar um <xref:System.InvalidCastException>erro.</xref:System.InvalidCastException> Isso pode afetar negativamente o desempenho do seu aplicativo. `TryCast`Retorna [nada](../../../visual-basic/language-reference/nothing.md), de modo que, em vez de ter que lidar com uma possível exceção, você só precisa testar o resultado em `Nothing`.  
  
 Você usa o `TryCast` palavra-chave da mesma maneira que você use o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) palavra-chave. Forneça uma expressão como o primeiro argumento e um tipo que será convertido como o segundo argumento. `TryCast`funciona somente em tipos de referência, como classes e interfaces. Ele requer uma relação de herança ou implementação entre os dois tipos. Isso significa que um tipo deve herdar de ou implementar o outro.  
  
## <a name="errors-and-failures"></a>Erros e falhas  
 `TryCast`gera um erro do compilador se ele detectar que nenhuma relação de herança ou implementação existe. Mas a falta de um erro do compilador não garante uma conversão bem-sucedida. Se a conversão desejada é de restrição, ele pode falhar em tempo de execução. Se isso acontecer, `TryCast` retorna [nada](../../../visual-basic/language-reference/nothing.md).  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 Uma comparação entre as palavras-chave de conversão de tipo é da seguinte maneira.  
  
|Palavra-chave|Tipos de dados|Relacionamento de argumento|Falha de tempo de execução|  
|---|---|---|---|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|Ampliação ou restringir a conversão deve ser definido entre os dois tipos de dados|Lança<xref:System.InvalidCastException></xref:System.InvalidCastException>|  
|[Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md)|Quaisquer tipos de dados|Um tipo deve herdar de ou implementar o outro tipo|Lança<xref:System.InvalidCastException></xref:System.InvalidCastException>|  
|`TryCast`|Somente tipos de referência|Um tipo deve herdar de ou implementar o outro tipo|Retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `TryCast`.  
  
 [!code-vb[VbVbalrKeywords n º&6;](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
