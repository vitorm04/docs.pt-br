---
title: Chave (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
ms.openlocfilehash: 92d54e3135142bc02a17f3ce5ac078a356c139be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599838"
---
# <a name="key-visual-basic"></a>Chave (Visual Basic)
O `Key` palavra-chave permite que você especifique o comportamento para propriedades de tipos anônimos. Somente as propriedades que você designar como propriedades de chave participam de testes de igualdade entre instâncias de tipo anônimo ou cálculo de valores de código de hash. Os valores das propriedades de chave não podem ser alterados.  
  
 Designar uma propriedade de um tipo anônimo como uma propriedade de chave, colocando a palavra-chave `Key` na frente de sua declaração na lista de inicialização. No exemplo a seguir, `Airline` e `FlightNo` são propriedades de chave, mas `Gate` não é.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 Quando um novo tipo anônimo é criado, ele herda diretamente de <xref:System.Object>. O compilador desautoriza três membros herdados: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, e <xref:System.Object.ToString%2A>. O código de substituição que é produzido para <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> baseia-se em Propriedades de chave. Se não houver nenhuma propriedade de chave do tipo, <xref:System.Object.GetHashCode%2A> e <xref:System.Object.Equals%2A> não serão substituídos.  
  
## <a name="equality"></a>Igualdade  
 Duas instâncias de tipo anônimo são iguais se estes forem instâncias do mesmo tipo e se os valores de suas propriedades de chave são iguais. Nos exemplos a seguir, `flight2` é igual a `flight1` do exemplo anterior porque eles são instâncias do mesmo anônimo tipo e têm valores correspondentes para suas propriedades de chave. No entanto, `flight3` não é igual a `flight1` porque ele tem um valor diferente para uma propriedade de chave, `FlightNo`. Instância `flight4` não é do mesmo tipo como `flight1` porque eles designar propriedades diferentes como propriedades de chave.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 Se duas instâncias são declaradas com apenas propriedades não-chave, idênticas em nome, tipo, ordem e valor, as duas instâncias não são iguais. Uma instância sem propriedades de chave é igual somente a mesmo.  
  
 Para obter mais informações sobre as condições sob as quais duas instâncias de tipo anônimo são instâncias do mesmo tipo anônimo, consulte [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Cálculo de hash de código  
 Como <xref:System.Object.Equals%2A>, a função de hash que é definida em <xref:System.Object.GetHashCode%2A> para um tipo anônimo baseado nas propriedades do tipo de chave. Os exemplos a seguir mostram a interação entre propriedades de chave e hash de valores de código.  
  
 Instâncias de um tipo anônimo que têm os mesmos valores para todas as propriedades de chave têm o mesmo valor de código de hash, mesmo se as propriedades não-chave não têm valores correspondentes. A instrução a seguir retorna `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 Instâncias de um tipo anônimo que têm valores diferentes para uma ou mais propriedades de chave têm valores de código hash diferente. A instrução a seguir retorna `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 Instâncias de tipos anônimos que designar propriedades diferentes como propriedades de chave não são instâncias do mesmo tipo. Tiverem valores de código hash diferente, mesmo quando os nomes e valores de todas as propriedades são os mesmos. A instrução a seguir retorna `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>Valores somente leitura  
 Os valores das propriedades de chave não podem ser alterados. Por exemplo, em `flight1` nos exemplos anteriores, o `Airline` e `FlightNo` campos são somente leitura, mas `Gate` pode ser alterado.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Definição do Tipo Anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
