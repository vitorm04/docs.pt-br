---
title: Narrowing (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.narrowing
dev_langs:
- VB
helpviewer_keywords:
- conversions, type
- type conversion
- conversions, data type
- Narrowing keyword
- data type conversion
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: aefade302aaeac0ef984ede33819a4eadbc73954
ms.lasthandoff: 03/13/2017

---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
Indica que um operador de conversão (`CType`) converte uma classe ou estrutura em um tipo que pode não ser capaz de armazenar alguns dos possíveis valores da classe ou estrutura original.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Convertendo com a palavra-chave Narrowing  
 O procedimento de conversão deve especificar `Public Shared` além `Narrowing`.  
  
 Conversões de estreitamento nem sempre bem-sucedidas em tempo de execução e podem falhar ou provoca perda de dados. Os exemplos são `Long` para `Integer`, `String` para `Date`e um tipo base para um tipo derivado. Esse último conversão é restritiva porque o tipo base pode não conter todos os membros do tipo derivado e, portanto, não é uma instância do tipo derivado.  
  
 Se `Option Strict` é `On`, o código de consumo deve usar `CType` para todas as conversões de redução.  
  
 O `Narrowing` palavra-chave pode ser usada neste contexto:  
  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Conversões entre](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
