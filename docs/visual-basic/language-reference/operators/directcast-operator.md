---
title: Operador DirectCast (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.directCast
- directCast
dev_langs:
- VB
helpviewer_keywords:
- DirectCast keyword
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
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
ms.openlocfilehash: 9a815a74f53b04315639dcfccae6378b99bf76a2
ms.lasthandoff: 03/13/2017

---
# <a name="directcast-operator-visual-basic"></a>Operador DirectCast (Visual Basic)
Introduz uma operação de conversão de tipo com base em herança ou implementação.  
  
## <a name="remarks"></a>Comentários  
 `DirectCast`Não use o Visual Basic rotinas auxiliares de tempo de execução para conversão, para que possa fornecer um pouco melhor desempenho do que `CType` durante a conversão para e do tipo de dados `Object`.  
  
 Você usa o `DirectCast` palavra-chave semelhante à maneira como você usa o [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) e [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md) palavra-chave. Forneça uma expressão como o primeiro argumento e um tipo que será convertido como o segundo argumento. `DirectCast`requer uma relação de herança ou implementação entre os tipos de dados dos dois argumentos. Isso significa que um tipo deve herdar de ou implementar o outro.  
  
## <a name="errors-and-failures"></a>Erros e falhas  
 `DirectCast`gera um erro do compilador se ele detectar que nenhuma relação de herança ou implementação existe. Mas a falta de um erro do compilador não garante uma conversão bem-sucedida. Se a conversão desejada é de restrição, ele pode falhar em tempo de execução. Se isso acontecer, o tempo de execução gera uma <xref:System.InvalidCastException>erro.</xref:System.InvalidCastException>  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 Uma comparação entre as palavras-chave de conversão de tipo é da seguinte maneira.  
  
|Palavra-chave|Tipos de dados|Relacionamento de argumento|Falha de tempo de execução|  
|---|---|---|---|  
|[Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)|Quaisquer tipos de dados|Ampliação ou restringir a conversão deve ser definido entre os dois tipos de dados|Lança<xref:System.InvalidCastException></xref:System.InvalidCastException>|  
|`DirectCast`|Quaisquer tipos de dados|Um tipo deve herdar de ou implementar o outro tipo|Lança<xref:System.InvalidCastException></xref:System.InvalidCastException>|  
|[Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md)|Somente tipos de referência|Um tipo deve herdar de ou implementar o outro tipo|Retorna [nada](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra dois usos do `DirectCast`, um que falha em tempo de execução e um deles tenha êxito.  
  
 [!code-vb[VbVbalrKeywords n º&1;](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 No exemplo anterior, o tempo de execução do tipo de `q` é `Double`. `CType`é bem-sucedida pois `Double` pode ser convertido em `Integer`. No entanto, o primeiro `DirectCast` falha em tempo de execução porque o tipo de tempo de execução de `Double` não tem nenhuma relação de herança com `Integer`, mesmo que exista uma conversão. A segunda `DirectCast` é bem-sucedida pois ele converte do tipo <xref:System.Windows.Forms.Form>digitar <xref:System.Windows.Forms.Control>, do qual <xref:System.Windows.Forms.Form>herda.</xref:System.Windows.Forms.Form> </xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.Form>  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Convert.ChangeType%2A?displayProperty=fullName></xref:System.Convert.ChangeType%2A?displayProperty=fullName>   
 [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
