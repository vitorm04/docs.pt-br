---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50116c6212e919d4b9b35fc933d80dee14bd4ecf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode não ser capaz de armazenar alguns dos possíveis valores da classe ou estrutura original.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Convertendo com a palavra-chave Narrowing  
 O procedimento de conversão deve especificar `Public Shared` além `Narrowing`.  
  
 Conversões de estreitamento nem sempre bem-sucedidas em tempo de execução e podem falhar ou provoca perda de dados. Os exemplos são `Long` para `Integer`, `String` para `Date`e um tipo base para um tipo derivado. Este último conversão é restritiva porque o tipo base não pode conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.  
  
 Se `Option Strict` é `On`, o código de consumo deve usar `CType` para todas as conversões de estreitamento.  
  
 O `Narrowing` palavra-chave pode ser usado neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
