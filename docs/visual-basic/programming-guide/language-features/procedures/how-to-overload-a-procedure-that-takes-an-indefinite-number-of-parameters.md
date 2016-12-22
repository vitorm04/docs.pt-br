---
title: "Como sobrecarregar um procedimento que use um n&#250;mero indefinido de par&#226;metros (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "sobrecarga de procedimento, número indefinido de parâmetros"
  - "parâmetros de procedimento"
  - "procedimentos, definindo"
  - "procedimentos, várias versões"
  - "procedimentos, sobrecarga"
  - "procedimentos, parâmetros"
  - "código do Visual Basic, procedimentos"
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como sobrecarregar um procedimento que use um n&#250;mero indefinido de par&#226;metros (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se um procedimento tiver um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você não pode definir uma versão sobrecarregada, levando a uma matriz unidimensional para a matriz de parâmetros.  Para obter mais informações, consulte "Implícito sobrecargas para um parâmetro ParamArray" em [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
### Para sobrecarregar um procedimento que leva a um número variável de parâmetros  
  
1.  Verificar que o procedimento e chamando os benefícios de lógica do código de sobrecarregados versões a partir de mais de um `ParamArray` parâmetro.  Consulte "Sobrecargas e ParamArrays" em [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
2.  Determine quais números de valores fornecidos deve aceitar o procedimento na variável parte da lista de parâmetros.  Isso pode incluir o caso de nenhum valor, e pode incluir o caso de uma única matriz unidimensional.  
  
3.  Para cada número aceitável de valores fornecidos, escrever um `Sub` ou `Function` instrução de declaração que define a lista de parâmetros correspondentes.  Não use nenhum a `Optional` ou o `ParamArray` palavra\-chave nesta versão sobrecarregada.  
  
4.  Em cada declaração, preceda a palavra\-chave `Sub` ou `Function` com a palavra\-chave [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md).  
  
5.  Após cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece os valores correspondentes à lista de parâmetros dessa declaração.  
  
6.  Termine cada procedimento com a declaração `End Sub` ou `End Function` como apropriado.  
  
## Exemplo  
 O exemplo a seguir mostra um procedimento definido com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.  
  
 [!code-vb[VbVbcnProcedures#69](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que leva um matriz unidimensional para a matriz de parâmetros.  No entanto, você pode usar as assinaturas das outras sobrecargas implícitas.  As seguintes declarações ilustram isto.  
  
 [!code-vb[VbVbcnProcedures#71](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Não tem o código nas versões sobrecarregadas testar se o código de chamada fornecido um ou mais valores para o `ParamArray` parâmetro, ou em caso afirmativo, quantos.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]passa o controle para a versão da lista de argumentos de chamada de correspondência.  
  
## Compilando o código  
 Porque um procedimento com um `ParamArray` parâmetro é equivalente a um conjunto de versões sobrecarregadas, você não pode sobrecarregar tal um procedimento com uma lista de parâmetros correspondentes a qualquer um dessas sobrecargas implícitas.  Para obter mais informações, consulte [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md).  
  
## Segurança do .NET Framework  
 Sempre que você lidar com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna da sua aplicação.  Se você aceitar uma matriz de parâmetros, você deve testar o comprimento da matriz o código de chamada é passado para ele e execute as etapas apropriadas se ele for muito grande para o seu aplicativo.  
  
## Consulte também  
 [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Parâmetros e argumentos de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Parâmetros opcionais](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Matrizes de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Solucionando problemas de procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Como definir várias versões de um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [Como chamar um procedimento sobrecarregado](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](../Topic/How%20to:%20Overload%20a%20Procedure%20that%20Takes%20Optional%20Parameters%20\(Visual%20Basic\).md)   
 [Resolução de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)