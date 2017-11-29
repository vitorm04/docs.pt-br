---
title: "Matrizes de parâmetros (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a>Matrizes de parâmetros (Visual Basic)
Normalmente, você não pode chamar um procedimento com mais argumentos do que especifica a declaração de procedimento. Quando você precisar de um número indefinido de argumentos, você pode declarar uma *matriz de parâmetro*, que permite que um procedimento aceitar uma matriz de valores para um parâmetro. Você não precisa saber o número de elementos na matriz de parâmetros quando você define o procedimento. O tamanho da matriz é determinado individualmente por cada chamada ao procedimento.  
  
## <a name="declaring-a-paramarray"></a>Declarando um ParamArray  
 Você usa o [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) palavra-chave para denotar uma matriz de parâmetro na lista de parâmetros. As seguintes regras se aplicam:  
  
-   Um procedimento pode definir apenas uma matriz de parâmetro, e ele deve ser o último parâmetro na definição do procedimento.  
  
-   A matriz de parâmetros deve ser transmitida por valor. É uma boa prática para incluir explicitamente de programação de [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) palavra-chave na definição do procedimento.  
  
-   A matriz de parâmetros é automaticamente opcional. O valor padrão é uma matriz unidimensional vazia do tipo de elemento da matriz de parâmetros.  
  
-   Todos os parâmetros que precedem a matriz de parâmetros devem ser necessários. A matriz de parâmetros deve ser o parâmetro opcional somente.  
  
## <a name="calling-a-paramarray"></a>Chamando um ParamArray  
 Quando você chama um procedimento que define uma matriz de parâmetros, você pode fornecer o argumento em qualquer uma das seguintes maneiras:  
  
-   Nada — ou seja, você pode omitir o [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argumento. Nesse caso, uma matriz vazia é passada para o procedimento. Você também pode passar o [nada](../../../../visual-basic/language-reference/nothing.md) palavra-chave com o mesmo efeito.  
  
-   Uma lista de um número arbitrário de argumentos, separados por vírgulas. O tipo de dados de cada argumento deve ser implicitamente conversível para o `ParamArray` tipo de elemento.  
  
-   Uma matriz com o mesmo tipo de elemento do tipo de elemento da matriz de parâmetros.  
  
 Em todos os casos, o código dentro do procedimento trata a matriz de parâmetros como uma matriz unidimensional com elementos do mesmo tipo de dados como o `ParamArray` tipo de dados.  
  
> [!IMPORTANT]
>  Sempre que você lidar com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros, você deve testar o tamanho da matriz que o código de chamada passado. Execute as etapas apropriadas se ele é muito grande para o seu aplicativo. Para obter mais informações, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define e chama a função `calcSum`. O `ParamArray` modificador para o parâmetro `args` permite que a função aceite um número variável de argumentos.  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 O exemplo a seguir define um procedimento com uma matriz de parâmetros e retorna os valores de todos os elementos da matriz passados para a matriz de parâmetros.  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)  
 [Parâmetros Opcionais](./optional-parameters.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)
