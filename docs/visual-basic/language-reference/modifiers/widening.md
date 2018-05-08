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
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura para um tipo que pode conter todos os possíveis valores da classe ou estrutura original.  
  
## <a name="converting-with-the-widening-keyword"></a>Convertendo com a palavra-chave Widening  
 O procedimento de conversão deve especificar `Public Shared` além `Widening`.  
  
 Conversões ampliadoras sempre são bem-sucedidas em tempo de execução e nunca provocam perda de dados. Os exemplos são `Single` para `Double`, `Char` para `String`e um tipo derivado para seu tipo base. Essa última conversão está ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.  
  
 O código não precisa usar `CType` para ampliação conversões, mesmo se `Option Strict` é `On`.  
  
 O `Widening` palavra-chave pode ser usado neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Por exemplo, definições de widening e narrowing operadores de conversão, consulte [como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
