---
title: "Passando argumentos por posição e nome (Visual Basic) | Documentos do Microsoft"
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
- arguments [Visual Basic], passing by name
- procedures, arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments, passing arguments
- arguments [Visual Basic], passing by position
- Function procedures, passing arguments
- named parameters, passing arguments
- named arguments
- passing parameters, named parameter arguments
- passing parameters, by position
- procedures, calling
- named parameters
- Sub procedures, passing arguments
- argument passing
- passing parameters, by name
- argument passing, by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: 13
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
ms.openlocfilehash: 0f7e64fabca2214aeb0d55ae7cbddf9a6c25d9d8
ms.lasthandoff: 03/13/2017

---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Passando argumentos por posição e nome (Visual Basic)
Quando você chama um `Sub` ou `Function` procedimento, você pode passar argumentos *por posição* — na ordem em que aparecem na definição do procedimento — ou você pode passá-los *por nome*, independentemente da posição.  
  
 Quando você passa um argumento pelo nome, especifique o argumento declarado do nome seguido por dois-pontos e um sinal de igual (`:=`), seguido pelo valor do argumento. Você pode fornecer argumentos nomeados em qualquer ordem.  
  
 Por exemplo, a seguinte `Sub` procedimento utiliza três argumentos:  
  
 [!code-vb[41 VbVbcnProcedures](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Quando você chamar esse procedimento, você pode fornecer os argumentos por posição, por nome ou usando uma mistura de ambos.  
  
## <a name="passing-arguments-by-position"></a>Passando argumentos por posição  
 Você pode chamar o procedimento `studentInfo` com seus argumentos passados por posição e delimitados por vírgulas, como mostrado no exemplo a seguir:  
  
 [!code-vb[VbVbcnProcedures&42;](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 Se você omitir um argumento opcional em uma lista de argumentos posicionais, você deve manter seu lugar com uma vírgula. A exemplo a seguir chama `studentInfo` sem o `age` argumento:  
  
 [!code-vb[VbVbcnProcedures&#43;](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>Passando argumentos por nome  
 Como alternativa, você pode chamar `studentInfo` com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo a seguir:  
  
 [!code-vb[VbVbcnProcedures&#44;](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>Misturando argumentos por posição e nome  
 Você pode fornecer argumentos por posição e por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:  
  
 [!code-vb[45 VbVbcnProcedures](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 No exemplo anterior, nenhuma vírgula extra é necessária para manter o lugar do omitido `age` argumento, uma vez que `birth` é passado por nome.  
  
 Quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro. Depois que você fornecer um argumento pelo nome, os argumentos restantes devem ser todos por nome.  
  
## <a name="supplying-optional-arguments-by-name"></a>Fornecendo argumentos opcionais por nome  
 Passando argumentos por nome é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional. Se você fornecer argumentos pelo nome, você não precisa usar vírgulas consecutivas para indicar argumentos posicionais ausentes. Passando argumentos por nome também facilita manter controle de quais argumentos você está passando e quais você está omitindo.  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrições no fornecimento de argumentos por nome  
 Você não pode passar argumentos pelo nome para evitar digitar argumentos necessários. Você pode omitir somente os argumentos opcionais.  
  
 Você não pode passar uma matriz de parâmetros por nome. Isso ocorre porque quando você chama o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros e o compilador não pode associar mais de um argumento com um único nome.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](./passing-arguments-by-value-and-by-reference.md)   
 [Parâmetros opcionais](./optional-parameters.md)   
 [Matrizes de parâmetros](./parameter-arrays.md)   
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
