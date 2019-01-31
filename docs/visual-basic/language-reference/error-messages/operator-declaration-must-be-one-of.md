---
title: 'Declaração do operador deve ser um destes: +,-, *,-, -, ^, &amp;, Like, Mod e, Or, Xor, não, <<>>,, <>, <, < =, >, > =, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 7acec56be60f88147bac1ba4179ad0234ea1c6e1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270050"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>Declaração do operador deve ser um destes: +,-, *,\,/, ^, &amp;, Like, Mod e, Or, Xor, não, \< \<, >>...
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
