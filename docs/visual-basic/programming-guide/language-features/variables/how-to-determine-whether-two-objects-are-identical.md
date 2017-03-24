---
title: "Como: determinar se dois objetos são idênticos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- testing, objects
- objects [Visual Basic], comparing
- object variables, determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
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
ms.openlocfilehash: 3a853d9f958829eeb0fb42ecbcdae7ba912c89ed
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Como determinar se dois objetos são idênticos (Visual Basic)
Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], duas referências de variáveis são consideradas idênticas se seus ponteiros são os mesmos, ou seja, se as duas variáveis apontam para a mesma instância de classe na memória. Por exemplo, em um aplicativo Windows Forms, convém fazer uma comparação para determinar se a instância atual (`Me`) é o mesmo que uma determinada instância, como `Form2`.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece dois operadores para comparar ponteiros. O [operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) retorna `True` se os objetos são idênticos e o [operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) retorna `True` se não forem.  
  
## <a name="determining-if-two-objects-are-identical"></a>Determinando se dois objetos são idênticos  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Para determinar se dois objetos são idênticos  
  
1.  Configurar um `Boolean` para testar os dois objetos.  
  
2.  Na sua expressão de teste, use o `Is` operador com os dois objetos como operandos.  
  
     `Is`Retorna `True` se os dois objetos apontam para a mesma instância de classe.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Determinando se dois objetos não são idênticos  
 Às vezes você deseja realizar uma ação se dois objetos não são idênticos, e pode ser complicado combinar `Not` e `Is`, por exemplo `If Not obj1 Is obj2`. Nesse caso, você pode usar o `IsNot` operador.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Para determinar se dois objetos não são idênticos  
  
1.  Configurar um `Boolean` para testar os dois objetos.  
  
2.  Na sua expressão de teste, use o `IsNot` operador com os dois objetos como operandos.  
  
     `IsNot`Retorna `True` se os objetos não apontam para a mesma instância de classe.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir testa pares de `Object` variáveis para ver se eles apontam para a mesma instância de classe.  
  
 [!code-vb[VbVbalrKeywords&#14;](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 O exemplo anterior exibe a saída a seguir.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Consulte também  
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Valores de variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [Operador is](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Como: determinar se dois objetos estão relacionados](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)   
 [Me, My, MyBase e MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
