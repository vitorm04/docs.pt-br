---
title: "Passando argumentos por posição e nome (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passando argumentos por posição e nome (Visual Basic)
Quando você chama um `Sub` ou `Function` procedimento, você pode passar argumentos *por posição* — na ordem em que aparecem na definição do procedimento — ou você pode passá-los *por nome*, sem consideração à posição.  
  
 Quando você passar um argumento por nome, especifique o argumento declarado do nome seguido por dois-pontos e um sinal de igual (`:=`), seguido pelo valor do argumento. Você pode fornecer argumentos nomeados em qualquer ordem.  
  
 Por exemplo, a seguinte `Sub` procedimento utiliza três argumentos:  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Quando você chamar esse procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma combinação dos dois.  
  
## <a name="passing-arguments-by-position"></a>Passando argumentos por posição  
 Você pode chamar o procedimento `studentInfo` com os argumentos transmitidos por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 Se você omitir um argumento opcional em uma lista de argumento posicional, você deve manter seu lugar com uma vírgula. A exemplo a seguir chama `studentInfo` sem o `age` argumento:  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>Passando argumentos por nome  
 Como alternativa, você pode chamar `studentInfo` com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo a seguir:  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Misturando argumentos por posição e nome  
 Você pode fornecer argumentos por posição e por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 No exemplo anterior, é necessária para manter o lugar do omitido sem uma vírgula extra `age` argumento, pois `birth` é passado por nome.  
  
 Quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro. Depois que você fornecer um argumento pelo nome, os argumentos restantes devem ser por nome.  
  
## <a name="supplying-optional-arguments-by-name"></a>Fornecendo argumentos opcionais por nome  
 Passando argumentos por nome é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional. Se você fornecer argumentos pelo nome, você não precisa usar vírgulas consecutivas para indicar argumentos posicionais ausentes. Passando argumentos por nome também torna mais fácil controlar quais argumentos que você está passando e quais você está omitindo.  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrições no fornecimento de argumentos por nome  
 Você não pode passar argumentos por nome para evitar digitar argumentos necessários. Você pode omitir somente os argumentos opcionais.  
  
 Você não pode passar uma matriz de parâmetros por nome. Isso ocorre porque quando você chamar o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros, e o compilador não é possível associar mais de um argumento com um único nome.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Passando Argumentos por Valor e por Referência](./passing-arguments-by-value-and-by-reference.md)  
 [Parâmetros Opcionais](./optional-parameters.md)  
 [Matrizes de Parâmetros](./parameter-arrays.md)  
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
