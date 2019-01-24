---
title: Widening (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 3b9d1ec15c6c2000fb0842abe25848f853cdf986
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703699"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode conter todos os possíveis valores da classe ou estrutura original.  
  
## <a name="converting-with-the-widening-keyword"></a>Convertendo com a palavra-chave Widening  
 O procedimento de conversão deve especificar `Public Shared` além `Widening`.  
  
 Conversões de ampliação sempre ter êxito em tempo de execução e nunca incorrerá em perda de dados. Os exemplos são `Single` à `Double`, `Char` para `String`e um tipo derivado para seu tipo base. Essa última conversão está ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.  
  
 O código de consumo não precisa usar `CType` para conversões de ampliação, mesmo que `Option Strict` é `On`.  
  
 O `Widening` palavra-chave pode ser usada neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Por exemplo as definições de ampliação e redução de operadores de conversão, consulte [como: Definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Consulte também
- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Como: Definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Como: Definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
