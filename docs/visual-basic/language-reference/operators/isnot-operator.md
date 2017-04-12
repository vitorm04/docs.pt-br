---
title: Operador IsNot (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isnot
dev_langs:
- VB
helpviewer_keywords:
- IsNot operator
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
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
ms.openlocfilehash: a15a60f6c04c19e34447f6b9e19f7bb484a61d29
ms.lasthandoff: 03/13/2017

---
# <a name="isnot-operator-visual-basic"></a>Operador IsNot (Visual Basic)
Compara duas variáveis de referência de objeto.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Partes  
 `result`  
 Necessário. Um valor `Boolean`.  
  
 `object1`  
 Necessário. Qualquer `Object` variável ou expressão.  
  
 `object2`  
 Necessário. Qualquer `Object` variável ou expressão.  
  
## <a name="remarks"></a>Comentários  
 O `IsNot` operador determina se duas referências de objeto se referem a objetos diferentes. No entanto, ele não realiza comparações de valor. Se `object1` e `object2` se referir à mesma instância de objeto, `result` é `False`; se não, `result` é `True`.  
  
 `IsNot`é o oposto do `Is` operador. A vantagem de `IsNot` é que você pode evitar sintaxes estranhas com `Not` e `Is`, que pode ser difícil de ler.  
  
 Você pode usar o `Is` e `IsNot` operadores para testar objetos de associação antecipada e tardia.  
  
> [!NOTE]
>  O `IsNot` operador não pode ser usado para comparar expressões retornadas do `TypeOf` operador. Em vez disso, você deve usar o `Not` e `Is` operadores.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir usa o `Is` operador e o `IsNot` operador para realizar a mesma comparação.  
  
 [!code-vb[29 VbVbalrOperators](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador is](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Como testar se dois objetos são iguais](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
