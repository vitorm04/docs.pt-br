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
ms.openlocfilehash: e13a773f0b585a5c8803a77c7aaad441d90dfe75
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842298"
---
# <a name="key-visual-basic"></a>Chave (Visual Basic)
O `Key` palavra-chave permite que você especifique o comportamento para propriedades de tipos anônimos. Somente as propriedades que você designar como propriedades de chave participarem de testes de igualdade entre instâncias de tipo anônimo ou cálculo dos valores de código de hash. Os valores das propriedades de chave não podem ser alterados.  
  
 Você designa uma propriedade de um tipo anônimo como uma propriedade de chave, colocando a palavra-chave `Key` na frente de sua declaração na lista de inicialização. No exemplo a seguir `Airline` e `FlightNo` são propriedades de chave, mas `Gate` não é.  
  
 [!code-vb[VbVbalrAnonymousTypes#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#26)]  
  
 Quando um novo tipo anônimo é criado, ele herda diretamente de <xref:System.Object>. O compilador substitui três membros herdados: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, e <xref:System.Object.ToString%2A>. O código de substituição que é produzido para <xref:System.Object.Equals%2A> e <xref:System.Object.GetHashCode%2A> baseia-se nas propriedades de chave. Se não houver nenhuma propriedade de chave no tipo, <xref:System.Object.GetHashCode%2A> e <xref:System.Object.Equals%2A> não são substituídas.  
  
## <a name="equality"></a>Igualdade  
 Duas instâncias de tipo anônimo são iguais se eles forem instâncias do mesmo tipo e se os valores de suas propriedades de chave são iguais. Nos exemplos a seguir `flight2` é igual a `flight1` do exemplo anterior porque eles são instâncias do mesmo anônimo tipo e têm valores correspondentes para suas propriedades de chave. No entanto, `flight3` não é igual a `flight1` porque ele tem um valor diferente para uma propriedade de chave, `FlightNo`. Instância `flight4` não é do mesmo tipo que `flight1` porque eles designar propriedades diferentes como propriedades de chave.  
  
 [!code-vb[VbVbalrAnonymousTypes#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#27)]  
  
 Se duas instâncias são declaradas com apenas propriedades não chave, idênticas em nome, tipo, ordem e valor, as duas instâncias não são iguais. Uma instância sem propriedades de chave é igual somente a mesmo.  
  
 Para obter mais informações sobre as condições sob as quais duas instâncias de tipo anônimo são instâncias do mesmo tipo anônimo, consulte [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="hash-code-calculation"></a>Cálculo de hash de código  
 Como o <xref:System.Object.Equals%2A>, a função de hash que é definida em <xref:System.Object.GetHashCode%2A> para um tipo anônimo se baseia nas propriedades do tipo de chave. Os exemplos a seguir mostram a interação entre propriedades de chave e hash de valores de código.  
  
 Instâncias de um tipo anônimo que têm os mesmos valores para todas as propriedades de chave têm o mesmo valor de código de hash, mesmo se as propriedades não chave não têm valores correspondentes. A instrução a seguir retorna `True`.  
  
 [!code-vb[VbVbalrAnonymousTypes#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#37)]  
  
 Instâncias de um tipo anônimo que têm valores diferentes para um ou mais propriedades de chave têm valores de código de hash diferente. A instrução a seguir retorna `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#38)]  
  
 Instâncias de tipos anônimos que designar propriedades diferentes como propriedades de chave não são instâncias do mesmo tipo. Elas têm valores de código de hash diferente, mesmo quando os nomes e valores de todas as propriedades são os mesmos. A instrução a seguir retorna `False`.  
  
 [!code-vb[VbVbalrAnonymousTypes#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#39)]  
  
## <a name="read-only-values"></a>Valores somente leitura  
 Os valores das propriedades de chave não podem ser alterados. Por exemplo, na `flight1` nos exemplos anteriores, o `Airline` e `FlightNo` campos são somente leitura, mas `Gate` pode ser alterado.  
  
 [!code-vb[VbVbalrAnonymousTypes#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#28)]  
  
## <a name="see-also"></a>Consulte também

- [Definição do Tipo Anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)
- [Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
