---
title: "Passando argumentos por posi&#231;&#227;o e nome (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "argumentos de passagem :="
  - "transmissão de argumentos"
  - "transmissão de argumentos, por posição"
  - "argumentos [Visual Basic], listagem por nome"
  - "argumentos [Visual Basic], transmitindo por nome"
  - "argumentos [Visual Basic], transmitindo por posição"
  - "Procedimentos de função, argumentos de passagem"
  - "argumentos nomeados"
  - "argumentos nomeados, argumentos de passagem"
  - "parâmetros nomeados"
  - "parâmetros nomeados, argumentos de passagem"
  - "passando parâmetros, por nome"
  - "passando parâmetros, por posição"
  - "passando parâmetros, argumentos de parâmetro nomeado"
  - "argumentos de procedimento"
  - "procedimentos, argumentos"
  - "procedimentos, Chamando "
  - "Subprocedimentos, argumentos de passagem"
  - "código do Visual Basic, procedimentos"
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Passando argumentos por posi&#231;&#227;o e nome (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você chama um procedimento `Sub` ou `Function`, você pode passar argumentos *pela posição*  — na ordem em que aparecem na definição do procedimento — ou você pode passá\-los  *pelo nome* , sem consideração à posição.  
  
 Quando você passa um argumento pelo nome, você especifica o nome declarado do argumento seguido por dois\-pontos e um sinal de igualdade \(`:=`\), seguido do valor do  argumento.  Você pode fornecer argumentos nomeados em qualquer ordem.  
  
 Por exemplo, o procedimento `Sub` a seguir utiliza três argumentos:  
  
 [!code-vb[VbVbcnProcedures#41](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 Quando você chamar esse procedimento, você poderá fornecer os argumentos por posição, por nome, ou usando uma mistura dos dois.  
  
## Passando argumentos por posição  
 Você pode chamar o procedimento  `studentInfo`  com seus argumentos passados por posição e delimitados por vírgulas, como mostrado no exemplo o seguir:  
  
 [!code-vb[VbVbcnProcedures#42](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 Se você omitir um argumento opcional em um lista de argumentos posicionais, você deve manter seu lugar com uma vírgula.  O exemplo a seguir chama  `studentInfo`  sem o argumento  `age` :  
  
 [!code-vb[VbVbcnProcedures#43](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## Passando argumentos por nome  
 Como alternativa, você pode chamar  `studentInfo`  com os argumentos passados pelo nome, também delimitado por vírgulas, como mostrado no exemplo o seguir:  
  
 [!code-vb[VbVbcnProcedures#44](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## Misturando argumentos por posição e por nome  
 Você pode fornecer argumentos tanto por posição quanto por nome em uma única chamada de procedimento, conforme mostrado no exemplo a seguir:  
  
 [!code-vb[VbVbcnProcedures#45](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 No exemplo anterior, não é necessária uma vírgula extra para manter o lugar do argumento  `age`  omitido, desde que  `birth`  seja passado por nome.  
  
 Quando você fornecer argumentos por uma mistura de posição e nome, os argumentos posicionais devem todos vir primeiro.  Depois que você fornecer um argumento pelo nome, os argumentos restantes devem ser todos por nome.  
  
## Fornecendo argumentos opcionais por nome  
 Passar argumentos por nome é especialmente útil quando você chama um procedimento que tem mais de um argumento opcional.  Se você fornecer argumentos pelo nome, não é necessário usar vírgulas consecutivas para indicar argumentos posicionais ausentes.  Passar argumentos por nome também facilita manter controle de quais argumentos você está passando e quais você está omitindo.  
  
## Restrições no fornecimento de argumentos por nome  
 Não é possível passar argumentos pelo nome para evitar digitar argumentos necessários.  Você pode omitir somente os argumentos opcionais.  
  
 Você não pode passar uma matriz de parâmetros por nome.  Isso ocorre porque quando você chama o procedimento, você fornece um número indefinido de argumentos separados por vírgula para a matriz de parâmetros, e o compilador não pode associar um único nome a mais de um argumento.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Como passar argumentos para um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-pass-arguments-to-a-procedure.md)   
 [Passando argumentos por valor e por referência](../../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)   
 [Parâmetros opcionais](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Matrizes de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md)   
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)