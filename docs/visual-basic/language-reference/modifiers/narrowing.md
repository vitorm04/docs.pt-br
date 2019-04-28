---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920634"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode não ser capaz de manter alguns dos possíveis valores da classe ou estrutura original.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Convertendo com a palavra-chave Narrowing  
 O procedimento de conversão deve especificar `Public Shared` além `Narrowing`.  
  
 Conversões de estreitamento nem sempre ter êxito em tempo de execução e pode falhar ou causar a perda de dados. Os exemplos são `Long` à `Integer`, `String` para `Date`e um tipo base para um tipo derivado. Essa última conversão é restritiva porque o tipo base não pode conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.  
  
 Se `Option Strict` está `On`, o código de consumo deve usar `CType` para todas as conversões de estreitamento.  
  
 O `Narrowing` palavra-chave pode ser usada neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Como: Definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
