---
title: Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 026dd59db135e8b195ae014aaff5e3a6a7846fc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a>Como sobrecarregar um procedimento que use um número indefinido de parâmetros (Visual Basic)
Se um procedimento tem um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro, você não pode definir uma versão sobrecarregada colocar uma matriz unidimensional para a matriz de parâmetros. Para obter mais informações, consulte "Implícita sobrecargas para um parâmetro ParamArray" em [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a>Para sobrecarregar um procedimento que usa um número variável de parâmetros  
  
1.  Verificar se o procedimento e chamar os benefícios de lógica de código de sobrecarregado versões mais de um `ParamArray` parâmetro. Consulte "Sobrecargas e ParamArrays" [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
2.  Determine quais números de valores fornecidos o procedimento deve aceitar a variável parte da lista de parâmetros. Isso pode incluir o caso de nenhum valor, e podem incluir no caso de uma matriz unidimensional.  
  
3.  Para cada número aceitável de valores fornecidos, escreva uma `Sub` ou `Function` declaração que define a lista de parâmetros correspondentes. Não use o `Optional` ou `ParamArray` palavra-chave nesta versão sobrecarregados.  
  
4.  Em cada declaração, preceda o `Sub` ou `Function` palavra-chave with a [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.  
  
5.  Seguindo cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece valores correspondentes à lista de parâmetros que da declaração.  
  
6.  Termine cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um procedimento definido com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro e, em seguida, um conjunto equivalente de procedimentos sobrecarregados.  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros. No entanto, você pode usar as assinaturas das outras sobrecargas implícitas. As declarações a seguir ilustram isso.  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 Não tem o código nas versões sobrecarregados testar se o código de chamada fornecido um ou mais valores para o `ParamArray` parâmetro, ou em caso afirmativo, a quantidade. Visual Basic passa o controle para a versão correspondente a lista de argumentos de chamada.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Porque um procedimento com um `ParamArray` parâmetro é equivalente a um conjunto de versões sobrecarregadas, você não pode sobrecarregar tal procedimento com uma lista de parâmetros que corresponde a qualquer essas sobrecargas implícitas. Para obter mais informações, consulte [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre que você lidar com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo. Se você aceitar uma matriz de parâmetros, deve-se de teste para o comprimento da matriz passado pelo código de chamada e execute as etapas apropriadas se ele é muito grande para o seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Parâmetros Opcionais](./optional-parameters.md)  
 [Matrizes de Parâmetros](./parameter-arrays.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)  
 [Como definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Como chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)  
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Resolução de Sobrecarga](./overload-resolution.md)
