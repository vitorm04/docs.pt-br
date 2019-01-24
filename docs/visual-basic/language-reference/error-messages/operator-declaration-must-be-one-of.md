---
title: 'Declaração do operador deve ser um destes: +,-, *,-, -, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: f32935dd4aaccd3040655b418badc13c1988c1b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622267"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>Declaração do operador deve ser um destes: +,-, *,\,/, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;...
Você pode declarar somente um operador que é qualificado para a sobrecarga. A tabela a seguir lista os operadores que você pode declarar.  
  
|Tipo|Operadores|  
|----------|---------------|  
|Unário|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binário|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversão (unário)|`CType`|  
  
 Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.  
  
 **ID do erro:** BC33000  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Selecione um operador do conjunto de operadores sobrecarregáveis.  
  
2.  Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie um `Function` procedimento que usa os parâmetros apropriados e retorna o valor apropriado.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Procedimentos de Operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Como: Definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Como: Definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
