---
title: Operador TypeOf (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- TypeOf
- vb.TypeOf
dev_langs:
- VB
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: c01eb32b3548f5479cc653d745637c9834eec6ce
ms.lasthandoff: 03/13/2017

---
# <a name="typeof-operator-visual-basic"></a>Operador TypeOf (Visual Basic)
Compara uma variável de referência de objeto para um tipo de dados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = TypeOf objectexpression Is typename  
```  
  
```  
  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Retornado. Um valor `Boolean`.  
  
 `objectexpression`  
 Necessário. Qualquer expressão que é avaliada como um tipo de referência.  
  
 `typename`  
 Necessário. Qualquer tipo de dados nome.  
  
## <a name="remarks"></a>Comentários  
 O `TypeOf` operador determina se o tempo de execução de tipo de `objectexpression` é compatível com `typename`. A compatibilidade depende da categoria de tipo de `typename`. A tabela a seguir mostra como compatibilidade é determinada.  
  
|Categoria de tipo de`typename`|Critério de compatibilidade|  
|---------------------------------|-----------------------------|  
|Classe|`objectexpression`é do tipo `typename` ou herda de`typename`|  
|Estrutura|`objectexpression`é do tipo`typename`|  
|Interface|`objectexpression`implementa `typename` ou herda de uma classe que implementa`typename`|  
  
 Se o tipo de tempo de execução do `objectexpression` satisfaz o critério de compatibilidade, `result` é `True`. Caso contrário, `result` é `False`.  Se `objectexpression` for nulo, `TypeOf`... `Is` retorna `False`, e... `IsNot` returns `True`.  
  
 `TypeOf`é sempre usado com a `Is` palavra-chave para construir um `TypeOf`... `Is` expressão, ou com o `IsNot` palavra-chave para construir um `TypeOf`... `IsNot` expressão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa `TypeOf`... `Is` para testar a compatibilidade das duas variáveis de referência com vários tipos de dados do objeto.  
  
 [!code-vb[VbVbalrOperators&#39;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 A variável `refInteger` tem um tipo de tempo de execução de `Integer`. Ele é compatível com `Integer` , mas não com `Double`. A variável `refForm` tem um tipo de tempo de execução de <xref:System.Windows.Forms.Form>.</xref:System.Windows.Forms.Form> Ele é compatível com <xref:System.Windows.Forms.Form>porque é seu tipo, com <xref:System.Windows.Forms.Control>porque <xref:System.Windows.Forms.Form>herda de <xref:System.Windows.Forms.Control>e com <xref:System.ComponentModel.IComponent>porque <xref:System.Windows.Forms.Form>herda de <xref:System.ComponentModel.Component>, que implementa o <xref:System.ComponentModel.IComponent>.</xref:System.ComponentModel.IComponent> </xref:System.ComponentModel.Component> </xref:System.Windows.Forms.Form> </xref:System.ComponentModel.IComponent> </xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.Form> </xref:System.Windows.Forms.Control> </xref:System.Windows.Forms.Form> No entanto, `refForm` não é compatível com <xref:System.Windows.Forms.Label>.</xref:System.Windows.Forms.Label>  
  
## <a name="see-also"></a>Consulte também  
 [Operador is](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Operadores de comparação em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
