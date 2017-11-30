---
title: Widening (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
