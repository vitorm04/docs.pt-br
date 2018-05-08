---
title: 'Declaração do operador deve ser um dos: +,-, *,-, -, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt; , &gt;=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: eb1e7e8088ec8661be2469aff043c0f1a96e4d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>Declaração do operador deve ser um dos: +,-, *,\,/, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;...
Você pode declarar somente um operador que é qualificado para a sobrecarga. A tabela a seguir lista os operadores que você pode declarar.  
  
|Tipo|Operadores|  
|----------|---------------|  
|Unário|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binário|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversão (unário)|`CType`|  
  
 Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.  
  
 **ID do erro:** BC33000  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Selecione um operador de conjunto de operadores que pode ser sobrecarregados.  
  
2.  Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie um `Function` procedimento que usa os parâmetros apropriados e retorna o valor apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Procedimentos de Operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
