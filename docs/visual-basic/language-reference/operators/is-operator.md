---
title: Operador is (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.is
dev_langs:
- VB
helpviewer_keywords:
- comparison operators
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 223d164e310e96ba80d1c3d65e0c8312300d0477
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="is-operator-visual-basic"></a>Operador Is (Visual Basic)
Compara duas variáveis de referência de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Qualquer `Boolean` valor.  
  
 `object1`  
 Necessário. Qualquer `Object` nome.  
  
 `object2`  
 Necessário. Qualquer `Object` nome.  
  
## <a name="remarks"></a>Comentários  
 O `Is` operador determina se duas referências de objeto se referem ao mesmo objeto. No entanto, ele não realiza comparações de valor. Se `object1` e `object2` se referir à mesma instância de objeto, `result` é `True`; se não, `result` é `False`.  
  
 `Is`também pode ser usado com o `TypeOf` palavra-chave para tornar um `TypeOf`... `Is` expressão, que testa se uma variável de objeto é compatível com um tipo de dados.  
  
> [!NOTE]
>  O `Is` palavra-chave também é usada a [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Is` operador para comparar pares de referências de objeto. Os resultados são atribuídos a um `Boolean` valor representando se os dois objetos são idênticos.  
  
 [!code-vb[VbVbalrOperators&#27;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Conforme demonstrado no exemplo anterior, você pode usar o `Is` operador para o teste com associação antecipada e objetos com associação tardia.  
  
## <a name="see-also"></a>Consulte também  
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Operadores de comparação em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

