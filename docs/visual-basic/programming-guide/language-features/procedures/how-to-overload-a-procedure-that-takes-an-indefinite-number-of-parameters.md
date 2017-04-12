---
title: "Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros (Visual Basic) | Documentos do Microsoft"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c7e09bd482e35c7ce7f28a6cc7de0379b7cc89f6
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)
Se um procedimento tem um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você não pode definir uma versão sobrecarregada, levando a uma matriz unidimensional para a matriz de parâmetros. Para obter mais informações, consulte "Implícita sobrecargas para um parâmetro ParamArray" [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Para sobrecarregar um procedimento que recebe um número variável de parâmetros  
  
1.  Verificar se o procedimento e chamar os benefícios da lógica de código de versões sobrecarregadas mais do que de um `ParamArray` parâmetro. Consulte "Sobrecargas e ParamArrays" [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
2.  Determine quais números de valores fornecidos o procedimento deve aceitar a variável parte da lista de parâmetros. Isso pode incluir o caso de nenhum valor, e podem incluir o caso de uma única matriz unidimensional.  
  
3.  Para cada número aceitável de valores fornecidos, escreva uma `Sub` ou `Function` declaração que define a lista de parâmetros correspondente. Não usar o `Optional` ou `ParamArray` palavra-chave nesta versão sobrecarregada.  
  
4.  Em cada declaração, preceda o `Sub` ou `Function` palavra-chave com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.  
  
5.  Seguindo cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece valores correspondentes à lista de parâmetros da declaração.  
  
6.  Termine cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um procedimento definido com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.  
  
 [!code-vb[VbVbcnProcedures&#69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros. No entanto, você pode usar as assinaturas das outras sobrecargas implícitas. As declarações a seguir ilustram isso.  
  
 [!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 O código nas versões sobrecarregadas não precisa testar se o código de chamada fornecido um ou mais valores para o `ParamArray` parâmetro, ou em caso afirmativo, quantos. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]passa o controle para a versão correspondente a lista de argumentos de chamada.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Porque um procedimento com um `ParamArray` parâmetro é equivalente a um conjunto de versões sobrecarregadas, você não pode sobrecarregar tal procedimento com uma lista de parâmetros correspondente a qualquer essas sobrecargas implícitas. Para obter mais informações, consulte [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros, deve testar o comprimento da matriz, o código de chamada passado para ele e tomar as medidas adequadas se ele for muito grande para seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Parâmetros opcionais](./optional-parameters.md)   
 [Matrizes de parâmetros](./parameter-arrays.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Procedimentos de solução de problemas](./troubleshooting-procedures.md)   
 [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)   
 [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Resolução de Sobrecarga](./overload-resolution.md)
