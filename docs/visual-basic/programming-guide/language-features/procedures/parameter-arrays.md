---
title: "Matrizes de parâmetros (Visual Basic) | Documentos do Microsoft"
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
- parameter arrays, about parameter arrays
- ParamArray keyword, parameter arrays
- Visual Basic code, procedures
- parameters, parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures, indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: 26
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 3538c474108f0abd31dcffb89141acc98e37f11f
ms.lasthandoff: 03/13/2017

---
# <a name="parameter-arrays-visual-basic"></a>Matrizes de parâmetros (Visual Basic)
Normalmente, você não pode chamar um procedimento com mais argumentos do que especifica a declaração de procedimento. Quando você precisar de um número indefinido de argumentos, você pode declarar uma *matriz de parâmetros*, que permite que um procedimento aceitar uma matriz de valores para um parâmetro. Você não precisa saber o número de elementos na matriz de parâmetros quando você define o procedimento. O tamanho da matriz é determinado individualmente por cada chamada ao procedimento.  
  
## <a name="declaring-a-paramarray"></a>Declarando um ParamArray  
 Você usa o [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) palavra-chave para denotar uma matriz de parâmetros na lista de parâmetros. As seguintes regras se aplicam:  
  
-   Um procedimento pode definir apenas uma matriz de parâmetros, e ele deve ser o último parâmetro na definição do procedimento.  
  
-   A matriz de parâmetros deve ser passada por valor. É uma boa prática para incluir explicitamente de programação a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) palavra-chave na definição do procedimento.  
  
-   A matriz de parâmetros é automaticamente opcional. O valor padrão é uma matriz unidimensional vazia do tipo de elemento da matriz de parâmetros.  
  
-   Todos os parâmetros que precedem a matriz de parâmetros devem ser necessários. A matriz de parâmetros deve ser o único parâmetro opcional.  
  
## <a name="calling-a-paramarray"></a>Chamando um ParamArray  
 Quando você chama um procedimento que define uma matriz de parâmetros, você pode fornecer o argumento em qualquer uma das seguintes maneiras:  
  
-   Nada — ou seja, você pode omitir o [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argumento. Nesse caso, uma matriz vazia é passada para o procedimento. Você também pode passar o [nada](../../../../visual-basic/language-reference/nothing.md) palavra-chave, com o mesmo efeito.  
  
-   Uma lista de um número arbitrário de argumentos, separados por vírgulas. O tipo de dados de cada argumento deve ser implicitamente conversível para o `ParamArray` tipo de elemento.  
  
-   Uma matriz com o mesmo tipo de elemento do tipo de elemento da matriz de parâmetros.  
  
 Em todos os casos, o código dentro do procedimento trata a matriz de parâmetros como uma matriz unidimensional com elementos do mesmo tipo de dados como o `ParamArray` tipo de dados.  
  
> [!IMPORTANT]
>  Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros, você deve testar o tamanho da matriz que o código de chamada passado para ele. Execute as etapas apropriadas se ele for muito grande para seu aplicativo. Para obter mais informações, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define e chama a função `calcSum`. O `ParamArray` modificador para o parâmetro `args` permite que a função aceite um número variável de argumentos.  
  
 [!code-vb[VbVbalrStatements&#26;](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 O exemplo a seguir define um procedimento com uma matriz de parâmetros e retorna os valores de todos os elementos da matriz passados à matriz de parâmetros.  
  
 [!code-vb[48 VbVbcnProcedures](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[49 VbVbcnProcedures](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.UBound%2A></xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md)   
 [Parâmetros opcionais](./optional-parameters.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)
