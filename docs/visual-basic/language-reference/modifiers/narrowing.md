---
title: Narrowing
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
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351471"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura em um tipo que pode não ser capaz de conter alguns dos valores possíveis da classe ou estrutura original.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Convertendo com a palavra-chave Narrowing  
 O procedimento de conversão deve especificar `Public Shared` além de `Narrowing`.  
  
 As conversões redutoras nem sempre são bem sucedidas em tempo de execução e podem falhar ou incorrer em perda de dados. Os exemplos são `Long` para `Integer`, `String` para `Date`e um tipo base para um tipo derivado. Essa última conversão é restrita porque o tipo base pode não conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.  
  
 Se `Option Strict` for `On`, o código de consumo deverá usar `CType` para todas as conversões redutoras.  
  
 A palavra-chave `Narrowing` pode ser usada neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md)
- [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Como definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
