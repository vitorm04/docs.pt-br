---
title: Chave (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AnonymousKey
dev_langs:
- VB
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: 22
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
ms.openlocfilehash: 99c2142937f0425bde83758ad5f1426472bb5211
ms.lasthandoff: 03/13/2017

---
# <a name="key-visual-basic"></a>Chave (Visual Basic)
O `Key` palavra-chave permite que você especifique o comportamento para propriedades de tipos anônimos. Somente as propriedades que você designar como propriedades de chave participam de testes de igualdade entre instâncias de tipo anônimo ou cálculo dos valores de código de hash. Os valores das propriedades de chave não podem ser alterados.  
  
 Você designa uma propriedade de um tipo anônimo como uma propriedade-chave colocando a palavra-chave `Key` na frente de sua declaração na lista de inicialização. No exemplo a seguir, `Airline` e `FlightNo` propriedades-chave, mas `Gate` não é.  
  
 [!code-vb[VbVbalrAnonymousTypes&#26;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 Quando um novo tipo anônimo é criado, ele herda diretamente de <xref:System.Object>.</xref:System.Object> O compilador desautoriza três membros herdados: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>e <xref:System.Object.ToString%2A>.</xref:System.Object.ToString%2A> </xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A> O código de substituição é gerada para <xref:System.Object.Equals%2A>e <xref:System.Object.GetHashCode%2A>baseado nas propriedades de chave.</xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A> Se não houver nenhuma propriedade de chave no tipo, <xref:System.Object.GetHashCode%2A>e <xref:System.Object.Equals%2A>não são substituídas.</xref:System.Object.Equals%2A> </xref:System.Object.GetHashCode%2A>  
  
## <a name="equality"></a>Igualdade  
 Duas instâncias de tipo anônimo são iguais se são instâncias do mesmo tipo e se os valores de suas propriedades de chave são iguais. Nos exemplos a seguir, `flight2` é igual a `flight1` do exemplo anterior porque eles são instâncias do mesmo anônimo tipo e têm valores correspondentes para suas propriedades de chave. No entanto, `flight3` não é igual a `flight1` porque ele tem um valor diferente para uma propriedade de chave, `FlightNo`. Instância `flight4` não é do mesmo tipo como `flight1` porque eles designar propriedades diferentes como propriedades de chave.  
  
 [!code-vb[VbVbalrAnonymousTypes&#27;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 Se duas instâncias são declaradas com apenas propriedades não-chave, idênticas em nome, tipo, ordem e valor, as duas instâncias não são iguais. Uma instância sem propriedades-chave é igual somente a mesmo.  
  
 Para obter mais informações sobre as condições sob as quais duas instâncias de tipo anônimo são instâncias do mesmo tipo anônimo, consulte [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Cálculo de código de hash  
 Como <xref:System.Object.Equals%2A>, a função de hash que é definida em <xref:System.Object.GetHashCode%2A>para um tipo anônimo é com base nas propriedades do tipo de chave.</xref:System.Object.GetHashCode%2A> </xref:System.Object.Equals%2A> Os exemplos a seguir mostram a interação entre propriedades de chave e hash de valores de código.  
  
 Instâncias de um tipo anônimo que têm os mesmos valores para todas as propriedades de chave têm o mesmo valor de código de hash, mesmo se as propriedades não-chave não tiver valores correspondentes. A instrução a seguir retorna `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes&#37;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 Instâncias de um tipo anônimo que têm valores diferentes para uma ou mais propriedades de chave têm valores de código de hash diferente. A instrução a seguir retorna `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes&38;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 Instâncias de tipos anônimos que designar propriedades diferentes como propriedades de chave não são instâncias do mesmo tipo. Elas têm valores de código de hash diferente mesmo quando os nomes e valores de todas as propriedades são os mesmos. A instrução a seguir retorna `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes&#39;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a>Valores somente leitura  
 Os valores das propriedades de chave não podem ser alterados. Por exemplo, em `flight1` nos exemplos anteriores, o `Airline` e `FlightNo` campos são somente leitura, mas `Gate` pode ser alterado.  
  
 [!code-vb[VbVbalrAnonymousTypes&#28;](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Definição de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [Como: inferir nomes de propriedade e tipos nas declarações de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
