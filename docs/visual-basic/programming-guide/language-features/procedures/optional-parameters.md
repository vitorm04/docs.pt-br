---
title: "Parâmetros opcionais (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- parameters, optional
- Visual Basic code, procedures
- procedures, optional arguments
- optional arguments
- named arguments, and optional arguments
- optional parameters
- Optional keyword, optional arguments
- arguments [Visual Basic], optional
- optional arguments, and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: 18
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 47365799fea95273874b581646b24757eeb9d718
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="optional-parameters-visual-basic"></a>Parâmetros opcionais (Visual Basic)
Você pode especificar que um parâmetro de procedimento é opcional e nenhum argumento precisa ser fornecido para ele quando o procedimento é chamado. *Parâmetros opcionais* são indicadas pelo `Optional` palavra-chave na definição do procedimento. As seguintes regras se aplicam:  
  
-   Cada parâmetro opcional na definição do procedimento deve especificar um valor padrão.  
  
-   O valor padrão para um parâmetro opcional deve ser uma expressão constante.  
  
-   Todo parâmetro após um parâmetro opcional na definição do procedimento também deve ser opcional.  
  
 A sintaxe a seguir mostra uma declaração de procedimento com um parâmetro opcional:  
  
```  
Sub sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a>Chamando procedimentos com parâmetros opcionais  
 Ao chamar um procedimento com um parâmetro opcional, você pode escolher se deseja fornecer o argumento. Caso contrário, o procedimento usa o valor padrão declarado para esse parâmetro.  
  
 Ao omitir um ou mais argumentos opcionais no lista de argumentos, você use sucessivas vírgulas para marcar as posições. A chamada de exemplo a seguir fornece o primeiro e o quarto argumentos, mas não o segundo ou terceiro:  
  
```  
sub name(argument 1, , , argument 4)  
```  
  
 O exemplo a seguir faz várias chamadas para a função `MsgBox`. `MsgBox` tem um parâmetro obrigatório e dois parâmetros opcionais.  
  
 A primeira chamada para `MsgBox` fornece todos os três argumentos na ordem que `MsgBox` os define. A segunda chamada fornece apenas o argumento necessário. A terceira e a quarta chamadas fornecem o primeiro e o terceiro argumentos. A terceira chamada faz isso por posição, e a quarta chamada faz isso por nome.  
  
 [!code-vb[47 VbVbcnProcedures](./codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a>Determinando se um argumento opcional está presente  
 Um procedimento não pode detectar no tempo de execução se um determinado argumento foi omitido ou o código de chamada forneceu explicitamente o valor padrão. Se você precisar fazer essa distinção, defina um valor improvável como o padrão. O procedimento a seguir define o parâmetro opcional `office`e testa seu valor padrão, `QJZ`, para ver se ele foi omitido na chamada:  
  
 [!code-vb[46 VbVbcnProcedures](./codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 Se o parâmetro opcional for um tipo de referência como `String`, você poderá usar `Nothing` como valor padrão, desde que não seja um valor esperado para o argumento.  
  
## <a name="optional-parameters-and-overloading"></a>Parâmetros opcionais e sobrecarga  
 Outra maneira de definir um procedimento com parâmetros opcionais é usar a sobrecarga. Se você tiver um parâmetro opcional, poderá definir duas versões sobrecarregadas do procedimento, uma aceitando o parâmetro e outra sem ele. Essa abordagem torna-se mais complicada à medida que o número de parâmetros opcionais aumenta. No entanto, sua vantagem é que você pode ter certeza absoluta se o programa de chamada forneceu cada argumento opcional.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md)   
 [Matrizes de parâmetros](./parameter-arrays.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)

