---
title: Widening
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
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347839"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura em um tipo que pode conter todos os valores possíveis da classe ou estrutura original.  
  
## <a name="converting-with-the-widening-keyword"></a>Convertendo com a palavra-chave Widening  
 O procedimento de conversão deve especificar `Public Shared` além de `Widening`.  
  
 Conversões de alargamento sempre são bem sucedidos em tempo de execução e nunca incorrem em perda de dados. Os exemplos são `Single` para `Double`, `Char` para `String`e um tipo derivado para seu tipo base. Essa última conversão está se ampliando porque o tipo derivado contém todos os membros do tipo base e, portanto, é uma instância do tipo base.  
  
 O código de consumo não precisa usar `CType` para conversões de alargamento, mesmo que `Option Strict` seja `On`.  
  
 A palavra-chave `Widening` pode ser usada neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Para obter exemplos de definições de ampliação e limitação de operadores de conversão, consulte [como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Consulte também

- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
